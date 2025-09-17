# Web-CV.TRAKA-NUSA-ABADI-FIBER-

<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>CV. Traka Nusa Abadi - Pencatatan Pembelian Bahan</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');
  body, html {
    margin: 0; padding: 0; height: 100%;
    font-family: 'Roboto', sans-serif;
    background: url('https://images.unsplash.com/photo-1581093588401-1a7a7a7a7a7a?auto=format&fit=crop&w=1350&q=80') no-repeat center center fixed;
    background-size: cover;
  }
  .overlay {
    background-color: rgba(0,0,0,0.7);
    position: fixed; top:0; left:0; right:0; bottom:0;
    display: flex; justify-content: center; align-items: center;
  }
  #loginBox {
    background: #222;
    padding: 30px;
    border-radius: 8px;
    width: 320px;
    box-shadow: 0 0 15px #000;
    color: #fff;
  }
  #loginBox h2 {
    margin-bottom: 20px;
    text-align: center;
  }
  #loginBox input[type=text], #loginBox input[type=password] {
    width: 100%;
    padding: 10px;
    margin: 8px 0 16px 0;
    border: none;
    border-radius: 4px;
  }
  #loginBox button {
    width: 100%;
    padding: 10px;
    background-color: #0a74da;
    border: none;
    border-radius: 4px;
    color: white;
    font-weight: bold;
    cursor: pointer;
  }
  #loginBox button:hover {
    background-color: #095bb5;
  }
  #app {
    display: none;
    padding: 20px;
    background-color: rgba(255,255,255,0.95);
    min-height: 100vh;
  }
  h1 {
    text-align: center;
    color: #0a74da;
  }
  form {
    max-width: 900px;
    margin: 0 auto 20px auto;
    background: #f9f9f9;
    padding: 15px;
    border-radius: 8px;
    box-shadow: 0 0 10px #ccc;
  }
  form > div {
    margin-bottom: 12px;
  }
  label {
    display: block;
    font-weight: bold;
    margin-bottom: 4px;
  }
  input[type=text], input[type=number], input[type=date], select {
    width: 100%;
    padding: 8px;
    box-sizing: border-box;
  }
  table {
    width: 100%;
    border-collapse: collapse;
    max-width: 900px;
    margin: 0 auto 30px auto;
  }
  th, td {
    border: 1px solid #ddd;
    padding: 8px;
    text-align: center;
  }
  th {
    background-color: #0a74da;
    color: white;
  }
  #filterSection {
    max-width: 900px;
    margin: 0 auto 20px auto;
    background: #f1f1f1;
    padding: 10px;
    border-radius: 8px;
  }
  #filterSection label {
    margin-right: 10px;
  }
  button.printBtn {
    background-color: #28a745;
    color: white;
    border: none;
    padding: 10px 15px;
    border-radius: 5px;
    cursor: pointer;
    margin-left: 10px;
  }
  button.printBtn:hover {
    background-color: #218838;
  }
  #logoutBtn {
    position: fixed;
    top: 15px;
    right: 15px;
    background-color: #dc3545;
    color: white;
    border: none;
    padding: 8px 12px;
    border-radius: 5px;
    cursor: pointer;
  }
  #logoutBtn:hover {
    background-color: #c82333;
  }
  @media print {
    body * {
      visibility: hidden;
    }
    #printArea, #printArea * {
      visibility: visible;
    }
    #printArea {
      position: absolute;
      left: 0; top: 0;
      width: 100%;
    }
  }
</style>
</head>
<body>

<div class="overlay" id="loginScreen">
  <div id="loginBox">
    <h2>Login CV. Traka Nusa Abadi</h2>
    <input type="text" id="username" placeholder="Username" autocomplete="off" />
    <input type="password" id="password" placeholder="Password" autocomplete="off" />
    <button id="loginBtn">Login</button>
    <p id="loginError" style="color:#f44336; display:none; margin-top:10px;">Username atau password salah!</p>
  </div>
</div>

<div id="app">
  <button id="logoutBtn">Logout</button>
  <h1>CV. Traka Nusa Abadi - Pencatatan Pembelian Bahan</h1>

  <form id="purchaseForm">
    <div>
      <label for="tanggal">Tanggal Pembelian:</label>
      <input type="date" id="tanggal" required />
    </div>
    <div>
      <label for="namaToko">Nama dan Alamat Toko:</label>
      <input type="text" id="namaToko" placeholder="Contoh: Toko ABC, Jl. Merdeka No.1" required />
    </div>
    <div>
      <label for="noTelp">No. Telp./HP Toko:</label>
      <input type="text" id="noTelp" placeholder="08123456789" required />
    </div>
    <div>
      <label for="namaBarang">Nama Barang:</label>
      <input type="text" id="namaBarang" required />
    </div>
    <div>
      <label for="volume">Volume:</label>
      <input type="number" id="volume" min="0" step="any" required />
    </div>
    <div>
      <label for="satuan">Satuan:</label>
      <input type="text" id="satuan" placeholder="Contoh: kg, liter, pcs" required />
    </div>
    <div>
      <label for="hargaSatuan">Harga Satuan (Rp):</label>
      <input type="number" id="hargaSatuan" min="0" step="any" required />
    </div>
    <button type="submit">Tambah Data Pembelian</button>
  </form>

  <div id="filterSection">
    <label for="filterBulan">Filter Bulan:</label>
    <select id="filterBulan">
      <option value="">Semua Bulan</option>
      <option value="1">Januari</option>
      <option value="2">Februari</option>
      <option value="3">Maret</option>
      <option value="4">April</option>
      <option value="5">Mei</option>
      <option value="6">Juni</option>
      <option value="7">Juli</option>
      <option value="8">Agustus</option>
      <option value="9">September</option>
      <option value="10">Oktober</option>
      <option value="11">November</option>
      <option value="12">Desember</option>
    </select>

    <label for="filterTahun">Filter Tahun:</label>
    <select id="filterTahun">
      <option value="">Semua Tahun</option>
    </select>

    <button class="printBtn" id="printBtn">Print Data</button>
  </div>

  <div id="printArea">
    <table id="dataTable">
      <thead>
        <tr>
          <th>No.</th>
          <th>Tanggal</th>
          <th>Nama dan Alamat Toko</th>
          <th>No. Telp./HP Toko</th>
          <th>Nama Barang</th>
          <th>Volume</th>
          <th>Satuan</th>
          <th>Harga Satuan (Rp)</th>
          <th>Jumlah Harga (Rp)</th>
        </tr>
      </thead>
      <tbody>
        <!-- Data akan muncul di sini -->
      </tbody>
    </table>
  </div>
</div>

<script>
  const loginScreen = document.getElementById('loginScreen');
  const app = document.getElementById('app');
  const loginBtn = document.getElementById('loginBtn');
  const usernameInput = document.getElementById('username');
  const passwordInput = document.getElementById('password');
  const loginError = document.getElementById('loginError');
  const logoutBtn = document.getElementById('logoutBtn');

  const purchaseForm = document.getElementById('purchaseForm');
  const dataTableBody = document.querySelector('#dataTable tbody');
  const filterBulan = document.getElementById('filterBulan');
  const filterTahun = document.getElementById('filterTahun');
  const printBtn = document.getElementById('printBtn');

  const STORAGE_KEY = 'trakaNusaAbadiData';

  // Cek login status
  function checkLogin() {
    if(localStorage.getItem('loggedIn') === 'true') {
      loginScreen.style.display = 'none';
      app.style.display = 'block';
      loadData();
      populateYearFilter();
    } else {
      loginScreen.style.display = 'flex';
      app.style.display = 'none';
    }
  }

  // Login handler
  loginBtn.addEventListener('click', () => {
    const username = usernameInput.value.trim();
    const password = passwordInput.value.trim();
    if(username === 'admin' && password === 'trakanusaabadi611') {
      localStorage.setItem('loggedIn', 'true');
      loginError.style.display = 'none';
      usernameInput.value = '';
      passwordInput.value = '';
      checkLogin();
    } else {
      loginError.style.display = 'block';
    }
  });

  // Logout handler
  logoutBtn.addEventListener('click', () => {
    localStorage.removeItem('loggedIn');
    checkLogin();
  });

  // Simpan data pembelian ke localStorage
  function saveData(data) {
    localStorage.setItem(STORAGE_KEY, JSON.stringify(data));
  }

  // Ambil data pembelian dari localStorage
  function getData() {
    const data = localStorage.getItem(STORAGE_KEY);
    return data ? JSON.parse(data) : [];
  }

  // Tambah data baru
  purchaseForm.addEventListener('submit', e => {
    e.preventDefault();
    const tanggal = document.getElementById('tanggal').value;
    const namaToko = document.getElementById('namaToko').value.trim();
    const noTelp = document.getElementById('noTelp').value.trim();
    const namaBarang = document.getElementById('namaBarang').value.trim();
    const volume = parseFloat(document.getElementById('volume').value);
    const satuan = document.getElementById('satuan').value.trim();
    const hargaSatuan = parseFloat(document.getElementById('hargaSatuan').value);
    if(!tanggal || !namaToko || !noTelp || !namaBarang || isNaN(volume) || !satuan || isNaN(hargaSatuan)) {
      alert('Mohon isi semua data dengan benar.');
      return;
    }
    const jumlahHarga = volume * hargaSatuan;
    const data = getData();
    data.push({ tanggal, namaToko, noTelp, namaBarang, volume, satuan, hargaSatuan, jumlahHarga });
    saveData(data);
    purchaseForm.reset();
    loadData();
    populateYearFilter();
  });

  // Tampilkan data di tabel sesuai filter
  function loadData() {
    const data = getData();
    const bulanFilter = filterBulan.value;
    const tahunFilter = filterTahun.value;
    let filteredData = data;

    if(bulanFilter) {
      filteredData = filteredData.filter(item => {
        const bulan = new Date(item.tanggal).getMonth() + 1;
        return bulan == bulanFilter;
      });
    }
    if(tahunFilter) {
      filteredData = filteredData.filter(item => {
        const tahun = new Date(item.tanggal).getFullYear();
        return tahun == tahunFilter;
      });
    }

    dataTableBody.innerHTML = '';
    if(filteredData.length === 0) {
      dataTableBody.innerHTML = '<tr><td colspan="9">Tidak ada data pembelian.</td></tr>';
      return;
    }
    filteredData.forEach((item, index) => {
      const tr = document.createElement('tr');
      tr.innerHTML = `
        <td>${index + 1}</td>
        <td>${item.tanggal}</td>
        <td>${item.namaToko}</td>
        <td>${item.noTelp}</td>
        <td>${item.namaBarang}</td>
        <td>${item.volume}</td>
        <td>${item.satuan}</td>
        <td>${item.hargaSatuan.toLocaleString('id-ID')}</td>
        <td>${item.jumlahHarga.toLocaleString('id-ID')}</td>
      `;
      dataTableBody.appendChild(tr);
    });
  }

  // Isi pilihan tahun di filter berdasarkan data
  function populateYearFilter() {
    const data = getData();
    const years = new Set(data.map(item => new Date(item.tanggal).getFullYear()));
    const currentOptions = Array.from(filterTahun.options).map(opt => opt.value);
    years.forEach(year => {
      if(!currentOptions.includes(year.toString())) {
        const option = document.createElement('option');
        option.value = year;
        option.textContent = year;
        filterTahun.appendChild(option);
      }
    });
  }

  // Event filter
  filterBulan.addEventListener('change', loadData);
  filterTahun.addEventListener('change', loadData);

  // Print data
  printBtn.addEventListener('click', () => {
    window.print();
  });

  // Inisialisasi
  checkLogin();
</script>

</body>
</html>
