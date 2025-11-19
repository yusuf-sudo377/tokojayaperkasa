let keranjang = [];

function tambahKeranjang(namaProduk) {
    keranjang.push(namaProduk);
    tampilkanKeranjang();
    alert(`${namaProduk} telah ditambahkan ke keranjang!`);
}

function tampilkanKeranjang() {
    const daftar = document.getElementById('daftarKeranjang');
    daftar.innerHTML = "";

    if (keranjang.length === 0) {
        daftar.innerHTML = "<li>Keranjang masih kosong</li>";
        return;
    }

    keranjang.forEach((item, index) => {
        const li = document.createElement('li');
        li.textContent = item;
        const hapusBtn = document.createElement('button');
        hapusBtn.textContent = "Hapus";
        hapusBtn.onclick = () => hapusItem(index);
        li.appendChild(hapusBtn);
        daftar.appendChild(li);
    });
}

function hapusItem(index) {
    keranjang.splice(index, 1);
    tampilkanKeranjang();
}

function checkout() {
    if (keranjang.length === 0) {
        alert("Keranjang masih kosong!");
        return;
    }

    const nomorWA = "+6287738883008"; // ganti dengan nomor toko kamu
    const pesan = encodeURIComponent(
        `Halo, saya ingin memesan barang berikut dari Toko Jaya Perkasa:\n\n` +
        keranjang.map((item, i) => `${i + 1}. ${item}`).join("\n")
    );
    window.open(`https://wa.me/${nomorWA}?text=${pesan}`, "_blank");
}

body {
    font-family: "Poppins", sans-serif;
    margin: 0;
    padding: 0;
    background-image: url("pp.webp");
}

header {
    background-color: #e57dff;
    color: rgb(255, 255, 255);
    text-align: center;
    padding: 1.5em;
}

nav a {
    color: white;
    margin: 0 10px;
    text-decoration: none;
    font-weight: bold;
}

nav a:hover {
    text-decoration: underline;
}

section {
    padding: 20px;
    text-align: center;
}

.produk-list {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    gap: 20px;
}

.produk {
    background-color: white;
    border-radius: 8px;
    box-shadow: 0 0 5px rgba(0, 0, 0, 0.2);
    padding: 15px;
    width: 200px;
}

.produk img {
    width: 100%;
    border-radius: 5px;
}

button {
    background-color: #1e3d59;
    color: white;
    border: none;
    padding: 8px 12px;
    border-radius: 4px;
    cursor: pointer;
    margin-top: 10px;
}

button:hover {
    background-color: #16324f;
}

#checkoutBtn {
    margin-top: 15px;
    background-color: #28a745;
}

#checkoutBtn:hover {
    background-color: #218838;
}

footer {
    background-color: #1e3d59;
    color: white;
    text-align: center;
    padding: 10px;
}

<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Toko Jaya Perkasa</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

    <header>
        <h1>Toko Jaya Perkasa</h1>
        <nav>
            <a href="#tentang">Tentang</a>
            <a href="#produk">Produk</a>
            <a href="#keranjang">Keranjang</a>
            <a href="#kontak">Kontak</a>
        </nav>
    </header>

    <section id="tentang">
        <h2>Tentang Kami</h2>
        <p>
            <strong>Toko Jaya Perkasa</strong> 
            Selamat datang!
            Di sini, semua rasa punya cerita. Kami hadir untuk membawa kamu menjelajahi kelezatan jajanan khas Indonesia — dari yang tradisional sampai yang kekinian.
        </p>
    </section>

    <section id="produk">
        <h2>Produk Kami</h2>
        <div class="produk-list">

            <div class="produk">
                <img src="lbrn.jpg" alt="Roti Lebaran">
                <h3>Roti Lebaran</h3>
                <p>Rp 60.000 / toples</p>
                <button onclick="tambahKeranjang('Cat Tembok 5L')">Tambah ke Keranjang</button>
            </div>

            <div class="produk">
                <img src="uwh.jpg" alt="Wedang uwuh">
                <h3>Wedang uwuh</h3>
                <p>Rp 4.500</p>
                <button onclick="tambahKeranjang('Semen 50kg')">Tambah ke Keranjang</button>
            </div>

            <div class="produk">
                <img src="jjn.jpg" alt="aneka cemilan">
                <h3>Aneka cemilan</h3>
                <p>Rp 5.000</p>
                <button onclick="tambahKeranjang('aneka cemilan')">Tambah ke Keranjang</button>
            </div>

            <div class="produk">
                <img src="krpk.jpg" alt="kerupuk pedas">
                <h3>krupuk pedas</h3>
                <p>Rp 8.000 / 5ons</p>
                <button onclick="tambahKeranjang('aneka ciki')">Tambah ke Keranjang</button>
            </div>

           <div class="produk">
                <img src="mrh.jpg" alt="Gula">
                <h3>Gula</h3>
                <p>Rp 25.000 / 1kg</p>
                <button onclick="tambahKeranjang('Gula')">Tambah ke Keranjang</button>
            </div>
        </div>
    </section>

    <section id="keranjang">
        <h2>Keranjang Belanja</h2>
        <ul id="daftarKeranjang"></ul>
        <button id="checkoutBtn" onclick="checkout()">Checkout via WhatsApp</button>
    </section>

    <section id="kontak">
        <h2>Kontak Kami</h2>
        <p>Alamat: Jl.Greges Donotirto No. 55772, Kretek,Bantul</p>
        <p>Telepon: <a href="tel:+6287738883008">+6287738883008</a></p>
        <p>WhatsApp: <a href="https://wa.me/+6287738883008" target="_blank">Chat via WhatsApp</a></p>
    </section>

    <footer>
        <p>&copy; 2025 Toko Jaya Perkasa | Semua Hak Dilindungi</p>
    </footer>
    <!-- Tombol WhatsApp Melayang -->
<a href="https://wa.me/+6287738883008" 
   class="wa-float" 
   target="_blank" 
   aria-label="Chat via WhatsApp">
   <img src="https://upload.wikimedia.org/wikipedia/commons/6/6b/WhatsApp.svg" 
        alt="WhatsApp" class="wa-icon">
</a>

<style>
/* Tombol WhatsApp Melayang */
.wa-float {
  position: fixed;
  width: 60px;
  height: 60px;
  bottom: 20px;
  right: 20px;
  background-color: #25D366;
  color: #fff;
  border-radius: 50%;
  text-align: center;
  font-size: 30px;
  box-shadow: 2px 2px 5px rgba(0,0,0,0.3);
  z-index: 1000;
}

.wa-float:hover {
  background-color: #20ba5a;
}

.wa-icon {
  width: 35px;
  height: 35px;
  margin-top: 12px;
}
</style>
    <script src="script.js"></script>
</body>
</html>
