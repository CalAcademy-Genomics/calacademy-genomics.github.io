---
title: Sample Location Tracker
layout: default
nav_order: 5
---

# CCG Sample Location Tracker
{: .no_toc }

Track the physical location of samples within CCG freezers.
{: .fs-6 .fw-300 }

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
  .flash { animation: flash-bg 0.6s; }
  @keyframes flash-bg { 0% { background: #d4edda; } 100% { background: transparent; } }
</style>

<!-- ── Add Sample Form ── -->
<div class="tracker-form" id="add-form">
  <div style="display:grid; grid-template-columns: 1fr 1fr; gap: 0 1rem;">
    <div>
      <label for="sample-id">Sample ID</label>
      <input type="text" id="sample-id" placeholder="e.g., CAS-12345">
    </div>
    <div>
      <label for="species">Species</label>
      <input type="text" id="species" placeholder="e.g., Solanum nelsonii">
    </div>
    <div>
      <label for="freezer-type">Freezer Type</label>
      <select id="freezer-type" onchange="updateFreezerOptions()">
        <option value="-80">-80°C</option>
        <option value="-20">-20°C</option>
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
      <input type="text" id="box" placeholder="e.g., Box 3, Slot 12">
    </div>
  </div>
  <label for="notes">Notes (optional)</label>
  <textarea id="notes" rows="2" placeholder="Any additional info"></textarea>
  <br>
  <button class="btn-add" onclick="addSample()">Add Sample</button>
</div>

<!-- ── Toolbar ── -->
<div class="toolbar">
  <input type="text" id="search" placeholder="Search samples..." oninput="renderTable()">
  <select id="filter-freezer-type" onchange="renderTable()">
    <option value="">All freezer types</option>
    <option value="-80">-80°C only</option>
    <option value="-20">-20°C only</option>
  </select>
  <span class="count-badge" id="count-badge">0 samples</span>
  <button class="btn-export" onclick="exportCSV()">Export CSV</button>
  <button class="btn-import" onclick="document.getElementById('import-file').click()">Import CSV</button>
  <input type="file" id="import-file" accept=".csv" onchange="importCSV(event)">
  <button class="btn-clear" onclick="clearAll()">Clear All</button>
</div>

<!-- ── Table ── -->
<table id="sample-table">
  <thead>
    <tr>
      <th onclick="sortBy('sampleId')">Sample ID</th>
      <th onclick="sortBy('species')">Species</th>
      <th onclick="sortBy('freezerType')">Freezer Type</th>
      <th onclick="sortBy('freezerId')">Freezer</th>
      <th onclick="sortBy('shelf')">Shelf</th>
      <th onclick="sortBy('box')">Box / Position</th>
      <th onclick="sortBy('notes')">Notes</th>
      <th onclick="sortBy('dateAdded')">Date Added</th>
      <th>Action</th>
    </tr>
  </thead>
  <tbody id="sample-tbody"></tbody>
</table>

<script>
  // ── Freezer definitions ──
  const FREEZERS = {
    '-80': [
      { id: '1', label: '-80°C Freezer 1' },
      { id: '2', label: '-80°C Freezer 2' },
      { id: '3', label: '-80°C Freezer 3' }
    ],
    '-20': [
      { id: 'A', label: '-20°C Freezer A' },
      { id: 'B', label: '-20°C Freezer B' },
      { id: 'C', label: '-20°C Freezer C' }
    ]
  };

  const STORAGE_KEY = 'ccg_sample_tracker';
  let samples = JSON.parse(localStorage.getItem(STORAGE_KEY) || '[]');
  let sortField = 'dateAdded';
  let sortAsc = false;

  // ── Freezer dropdown ──
  function updateFreezerOptions() {
    const type = document.getElementById('freezer-type').value;
    const sel = document.getElementById('freezer-id');
    sel.innerHTML = '';
    FREEZERS[type].forEach(f => {
      const opt = document.createElement('option');
      opt.value = f.id;
      opt.textContent = f.label;
      sel.appendChild(opt);
    });
  }

  // ── Add sample ──
  function addSample() {
    const sampleId = document.getElementById('sample-id').value.trim();
    const species = document.getElementById('species').value.trim();
    if (!sampleId) { alert('Sample ID is required.'); return; }

    const entry = {
      id: Date.now().toString(36) + Math.random().toString(36).slice(2, 6),
      sampleId,
      species,
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

    // reset form
    document.getElementById('sample-id').value = '';
    document.getElementById('species').value = '';
    document.getElementById('box').value = '';
    document.getElementById('notes').value = '';
    document.getElementById('sample-id').focus();
  }

  // ── Delete sample ──
  function deleteSample(id) {
    if (!confirm('Remove this sample?')) return;
    samples = samples.filter(s => s.id !== id);
    save();
    renderTable();
  }

  // ── Clear all ──
  function clearAll() {
    if (!confirm('Delete ALL samples? This cannot be undone.')) return;
    samples = [];
    save();
    renderTable();
  }

  // ── Sorting ──
  function sortBy(field) {
    if (sortField === field) { sortAsc = !sortAsc; }
    else { sortField = field; sortAsc = true; }
    renderTable();
  }

  // ── Render ──
  function renderTable() {
    const query = document.getElementById('search').value.toLowerCase();
    const filterType = document.getElementById('filter-freezer-type').value;

    let filtered = samples.filter(s => {
      if (filterType && s.freezerType !== filterType) return false;
      if (query) {
        const haystack = [s.sampleId, s.species, s.freezerId, s.shelf, s.box, s.notes, s.dateAdded].join(' ').toLowerCase();
        if (!haystack.includes(query)) return false;
      }
      return true;
    });

    filtered.sort((a, b) => {
      let va = (a[sortField] || '').toString().toLowerCase();
      let vb = (b[sortField] || '').toString().toLowerCase();
      if (va < vb) return sortAsc ? -1 : 1;
      if (va > vb) return sortAsc ? 1 : -1;
      return 0;
    });

    const tbody = document.getElementById('sample-tbody');
    tbody.innerHTML = '';

    filtered.forEach(s => {
      const freezerLabel = s.freezerType + '°C #' + s.freezerId;
      const tr = document.createElement('tr');
      tr.innerHTML =
        '<td>' + esc(s.sampleId) + '</td>' +
        '<td><em>' + esc(s.species) + '</em></td>' +
        '<td>' + esc(s.freezerType) + '°C</td>' +
        '<td>' + esc(s.freezerId) + '</td>' +
        '<td>' + esc(s.shelf) + '</td>' +
        '<td>' + esc(s.box) + '</td>' +
        '<td>' + esc(s.notes) + '</td>' +
        '<td>' + esc(s.dateAdded) + '</td>' +
        '<td><button class="btn-danger" onclick="deleteSample(\'' + s.id + '\')">Remove</button></td>';
      tbody.appendChild(tr);
    });

    document.getElementById('count-badge').textContent = filtered.length + ' of ' + samples.length + ' samples';
  }

  // ── Export CSV ──
  function exportCSV() {
    if (!samples.length) { alert('No samples to export.'); return; }
    const headers = ['Sample ID','Species','Freezer Type','Freezer','Shelf','Box/Position','Notes','Date Added'];
    const rows = samples.map(s => [s.sampleId, s.species, s.freezerType, s.freezerId, s.shelf, s.box, s.notes, s.dateAdded]);
    let csv = [headers, ...rows].map(r => r.map(c => '"' + String(c).replace(/"/g, '""') + '"').join(',')).join('\n');
    const blob = new Blob([csv], { type: 'text/csv' });
    const a = document.createElement('a');
    a.href = URL.createObjectURL(blob);
    a.download = 'ccg_samples_' + new Date().toISOString().slice(0,10) + '.csv';
    a.click();
  }

  // ── Import CSV ──
  function importCSV(event) {
    const file = event.target.files[0];
    if (!file) return;
    const reader = new FileReader();
    reader.onload = function(e) {
      const lines = e.target.result.split('\n').filter(l => l.trim());
      // skip header
      let imported = 0;
      for (let i = 1; i < lines.length; i++) {
        const cols = parseCSVLine(lines[i]);
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
      event.target.value = '';
    };
    reader.readAsText(file);
  }

  // ── CSV line parser (handles quoted fields) ──
  function parseCSVLine(line) {
    const result = [];
    let current = '';
    let inQuotes = false;
    for (let i = 0; i < line.length; i++) {
      const ch = line[i];
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

  // ── Helpers ──
  function esc(str) {
    const d = document.createElement('div');
    d.textContent = str || '';
    return d.innerHTML;
  }

  function save() {
    localStorage.setItem(STORAGE_KEY, JSON.stringify(samples));
  }

  // ── Init ──
  updateFreezerOptions();
  renderTable();
</script>
