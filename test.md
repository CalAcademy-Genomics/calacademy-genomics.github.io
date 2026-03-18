---
title: Sample Location Tracker
layout: default
nav_order: 5
---

# CCG Sample Location Tracker
{: .no_toc }

Track the physical location of samples within CCG freezers.
{: .fs-6 .fw-300 }

<div markdown="0">

<style>
  .tracker-form { background: #f5f6fa; padding: 1.5rem; border-radius: 8px; margin-bottom: 1.5rem; }
  .tracker-form label { display: block; font-weight: 600; margin-top: 0.75rem; }
  .tracker-form input, .tracker-form select, .tracker-form textarea {
    width: 100%; padding: 0.4rem; margin-top: 0.25rem;
    border: 1px solid #ccc; border-radius: 4px; font-size: 0.95rem;
  }
  .tracker-form button { margin-top: 1rem; padding: 0.5rem 1.25rem; border: none; border-radius: 4px; cursor: pointer; font-size: 0.95rem; }
  .btn-add { background: #2869e6; color: #fff; }
  .btn-add:hover { background: #1b4fb5; }
  .btn-export { background: #27ae60; color: #fff; }
  .btn-export:hover { background: #1e8e4e; }
  .btn-import { background: #8e44ad; color: #fff; }
  .btn-import:hover { background: #6c3483; }
  .btn-clear { background: #e67e22; color: #fff; }
  .btn-clear:hover { background: #d35400; }
  .btn-danger { background: #e74c3c; color: #fff; font-size: 0.8rem; padding: 0.25rem 0.6rem; border: none; border-radius: 4px; cursor: pointer; }
  .btn-danger:hover { background: #c0392b; }
  #sample-table { width: 100%; border-collapse: collapse; margin-top: 1rem; font-size: 0.9rem; }
  #sample-table th, #sample-table td { border: 1px solid #ddd; padding: 0.5rem; text-align: left; }
  #sample-table th { background: #2869e6; color: #fff; cursor: pointer; user-select: none; }
  #sample-table th:hover { background: #1b4fb5; }
  #sample-table tr:nth-child(even) { background: #f9f9f9; }
  .toolbar { display: flex; gap: 0.5rem; flex-wrap: wrap; margin-bottom: 1rem; align-items: center; }
  .toolbar input[type="text"] { flex: 1; min-width: 200px; padding: 0.4rem; border: 1px solid #ccc; border-radius: 4px; }
  .count-badge { background: #eee; padding: 0.3rem 0.7rem; border-radius: 12px; font-size: 0.85rem; white-space: nowrap; }
  #import-file { display: none; }
</style>

<div class="tracker-form" id="add-form">
  <div style="display:grid; grid-template-columns: 1fr 1fr; gap: 0 1rem;">
    <div>
      <label for="sample-id">Sample ID</label>
      <input type="text" id="sample-id" placeholder="e.g., CAS-12345" />
    </div>
    <div>
      <label for="species">Species</label>
      <input type="text" id="species" placeholder="e.g., Solanum nelsonii" />
    </div>
    <div>
      <label for="freezer-type">Freezer Type</label>
      <select id="freezer-type">
        <option value="-80">-80 C</option>
        <option value="-20">-20 C</option>
      </select>
    </div>
    <div>
      <label for="freezer-id">Freezer</label>
      <select id="freezer-id"></select>
    </div>
    <div>
      <label for="shelf">Shelf</label>
      <select id="shelf">
        <option value="1">Shelf 1</option>
        <option value="2">Shelf 2</option>
        <option value="3">Shelf 3</option>
        <option value="4">Shelf 4</option>
      </select>
    </div>
    <div>
      <label for="box">Box / Position (optional)</label>
      <input type="text" id="box" placeholder="e.g., Box 3, Slot 12" />
    </div>
  </div>
  <label for="notes">Notes (optional)</label>
  <textarea id="notes" rows="2" placeholder="Any additional info"></textarea>
  <br />
  <button class="btn-add" id="btn-add-sample" type="button">Add Sample</button>
</div>

<div class="toolbar">
  <input type="text" id="search" placeholder="Search samples..." />
  <select id="filter-freezer-type">
    <option value="">All freezer types</option>
    <option value="-80">-80 C only</option>
    <option value="-20">-20 C only</option>
  </select>
  <span class="count-badge" id="count-badge">0 samples</span>
  <button class="btn-export" id="btn-export" type="button">Export CSV</button>
  <button class="btn-import" id="btn-import" type="button">Import CSV</button>
  <input type="file" id="import-file" accept=".csv" />
  <button class="btn-clear" id="btn-clear" type="button">Clear All</button>
</div>

<table id="sample-table">
  <thead>
    <tr>
      <th data-sort="sampleId">Sample ID</th>
      <th data-sort="species">Species</th>
      <th data-sort="freezerType">Freezer Type</th>
      <th data-sort="freezerId">Freezer</th>
      <th data-sort="shelf">Shelf</th>
      <th data-sort="box">Box / Position</th>
      <th data-sort="notes">Notes</th>
      <th data-sort="dateAdded">Date Added</th>
      <th>Action</th>
    </tr>
  </thead>
  <tbody id="sample-tbody"></tbody>
</table>

<script>
(function() {
  var FREEZERS = {
    '-80': [
      { id: '1', label: '-80 C Freezer 1' },
      { id: '2', label: '-80 C Freezer 2' },
      { id: '3', label: '-80 C Freezer 3' }
    ],
    '-20': [
      { id: 'A', label: '-20 C Freezer A' },
      { id: 'B', label: '-20 C Freezer B' },
      { id: 'C', label: '-20 C Freezer C' }
    ]
  };

  var STORAGE_KEY = 'ccg_sample_tracker';
  var samples = JSON.parse(localStorage.getItem(STORAGE_KEY) || '[]');
  var sortField = 'dateAdded';
  var sortAsc = false;

  function esc(str) {
    var d = document.createElement('div');
    d.textContent = str || '';
    return d.innerHTML;
  }

  function save() {
    localStorage.setItem(STORAGE_KEY, JSON.stringify(samples));
  }

  function updateFreezerOptions() {
    var type = document.getElementById('freezer-type').value;
    var sel = document.getElementById('freezer-id');
    sel.innerHTML = '';
    var list = FREEZERS[type] || [];
    for (var i = 0; i < list.length; i++) {
      var opt = document.createElement('option');
      opt.value = list[i].id;
      opt.textContent = list[i].label;
      sel.appendChild(opt);
    }
  }

  function addSample() {
    var sampleId = document.getElementById('sample-id').value.trim();
    var species = document.getElementById('species').value.trim();
    if (!sampleId) { alert('Sample ID is required.'); return; }

    var entry = {
      id: Date.now().toString(36) + Math.random().toString(36).slice(2, 6),
      sampleId: sampleId,
      species: species,
      freezerType: document.getElementById('freezer-type').value,
      freezerId: document.getElementById('freezer-id').value,
      shelf: document.getElementById('shelf').value,
      box: document.getElementById('box').value.trim(),
      notes: document.getElementById('notes').value.trim(),
      dateAdded: new Date().toISOString().slice(0, 10)
    };

    samples.push(entry);
    save();
    renderTable();

    document.getElementById('sample-id').value = '';
    document.getElementById('species').value = '';
    document.getElementById('box').value = '';
    document.getElementById('notes').value = '';
    document.getElementById('sample-id').focus();
  }

  function deleteSample(id) {
    if (!confirm('Remove this sample?')) return;
    samples = samples.filter(function(s) { return s.id !== id; });
    save();
    renderTable();
  }

  function renderTable() {
    var query = document.getElementById('search').value.toLowerCase();
    var filterType = document.getElementById('filter-freezer-type').value;

    var filtered = samples.filter(function(s) {
      if (filterType && s.freezerType !== filterType) return false;
      if (query) {
        var haystack = [s.sampleId, s.species, s.freezerId, s.shelf, s.box, s.notes, s.dateAdded].join(' ').toLowerCase();
        if (haystack.indexOf(query) === -1) return false;
      }
      return true;
    });

    filtered.sort(function(a, b) {
      var va = (a[sortField] || '').toString().toLowerCase();
      var vb = (b[sortField] || '').toString().toLowerCase();
      if (va < vb) return sortAsc ? -1 : 1;
      if (va > vb) return sortAsc ? 1 : -1;
      return 0;
    });

    var tbody = document.getElementById('sample-tbody');
    tbody.innerHTML = '';

    for (var i = 0; i < filtered.length; i++) {
      var s = filtered[i];
      var tr = document.createElement('tr');

      tr.innerHTML =
        '<td>' + esc(s.sampleId) + '</td>' +
        '<td><em>' + esc(s.species) + '</em></td>' +
        '<td>' + esc(s.freezerType) + ' C</td>' +
        '<td>' + esc(s.freezerId) + '</td>' +
        '<td>' + esc(s.shelf) + '</td>' +
        '<td>' + esc(s.box) + '</td>' +
        '<td>' + esc(s.notes) + '</td>' +
        '<td>' + esc(s.dateAdded) + '</td>' +
        '<td><button class="btn-danger" type="button" data-delete-id="' + esc(s.id) + '">Remove</button></td>';

      tbody.appendChild(tr);
    }

    // attach delete handlers via delegation
    tbody.onclick = function(e) {
      var btn = e.target;
      if (btn.hasAttribute('data-delete-id')) {
        deleteSample(btn.getAttribute('data-delete-id'));
      }
    };

    document.getElementById('count-badge').textContent = filtered.length + ' of ' + samples.length + ' samples';
  }

  function exportCSV() {
    if (!samples.length) { alert('No samples to export.'); return; }
    var headers = ['Sample ID','Species','Freezer Type','Freezer','Shelf','Box/Position','Notes','Date Added'];
    var rows = samples.map(function(s) {
      return [s.sampleId, s.species, s.freezerType, s.freezerId, s.shelf, s.box, s.notes, s.dateAdded];
    });
    var all = [headers].concat(rows);
    var csv = all.map(function(r) {
      return r.map(function(c) { return '"' + String(c).replace(/"/g, '""') + '"'; }).join(',');
    }).join('\n');
    var blob = new Blob([csv], { type: 'text/csv' });
    var a = document.createElement('a');
    a.href = URL.createObjectURL(blob);
    a.download = 'ccg_samples_' + new Date().toISOString().slice(0, 10) + '.csv';
    a.click();
  }

  function parseCSVLine(line) {
    var result = [];
    var current = '';
    var inQuotes = false;
    for (var i = 0; i < line.length; i++) {
      var ch = line[i];
      if (inQuotes) {
        if (ch === '"' && line[i + 1] === '"') { current += '"'; i++; }
        else if (ch === '"') { inQuotes = false; }
        else { current += ch; }
      } else {
        if (ch === '"') { inQuotes = true; }
        else if (ch === ',') { result.push(current.trim()); current = ''; }
        else { current += ch; }
      }
    }
    result.push(current.trim());
    return result;
  }

  function importCSV(fileInput) {
    var file = fileInput.files[0];
    if (!file) return;
    var reader = new FileReader();
    reader.onload = function(e) {
      var lines = e.target.result.split('\n').filter(function(l) { return l.trim(); });
      var imported = 0;
      for (var i = 1; i < lines.length; i++) {
        var cols = parseCSVLine(lines[i]);
        if (cols.length < 4) continue;
        samples.push({
          id: Date.now().toString(36) + Math.random().toString(36).slice(2, 6) + i,
          sampleId: cols[0] || '',
          species: cols[1] || '',
          freezerType: cols[2] || '-80',
          freezerId: cols[3] || '',
          shelf: cols[4] || '1',
          box: cols[5] || '',
          notes: cols[6] || '',
          dateAdded: cols[7] || new Date().toISOString().slice(0, 10)
        });
        imported++;
      }
      save();
      renderTable();
      alert('Imported ' + imported + ' samples.');
      fileInput.value = '';
    };
    reader.readAsText(file);
  }

  // ── Wire up all event listeners ──
  document.getElementById('btn-add-sample').addEventListener('click', addSample);
  document.getElementById('freezer-type').addEventListener('change', updateFreezerOptions);
  document.getElementById('search').addEventListener('input', renderTable);
  document.getElementById('filter-freezer-type').addEventListener('change', renderTable);
  document.getElementById('btn-export').addEventListener('click', exportCSV);
  document.getElementById('btn-import').addEventListener('click', function() {
    document.getElementById('import-file').click();
  });
  document.getElementById('import-file').addEventListener('change', function() {
    importCSV(this);
  });
  document.getElementById('btn-clear').addEventListener('click', function() {
    if (!confirm('Delete ALL samples? This cannot be undone.')) return;
    samples = [];
    save();
    renderTable();
  });

  // sortable column headers
  var headers = document.querySelectorAll('#sample-table th[data-sort]');
  for (var h = 0; h < headers.length; h++) {
    (function(header) {
      header.addEventListener('click', function() {
        var field = header.getAttribute('data-sort');
        if (sortField === field) { sortAsc = !sortAsc; }
        else { sortField = field; sortAsc = true; }
        renderTable();
      });
    })(headers[h]);
  }

  // allow Enter key to submit form
  document.getElementById('add-form').addEventListener('keydown', function(e) {
    if (e.key === 'Enter' && e.target.tagName !== 'TEXTAREA') {
      e.preventDefault();
      addSample();
    }
  });

  // ── Initialize ──
  updateFreezerOptions();
  renderTable();
})();
</script>

</div>
