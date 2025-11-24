
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pangsit coii 12H - Pedasnya Bikin Nagih!</title>
    
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    
    <!-- Font Awesome (untuk ikon) -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">
    
    <!-- Google Font (Poppins) -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">
    
    <script>
        // Konfigurasi Tailwind CSS
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        // Ini adalah palet "Rough Red Pastel"
                        'brand-red': '#F87171',   // Merah muda/coral cerah (CTA)
                        'brand-light': '#FEF2F2', // Latar belakang pastel (Sangat muda)
                        'brand-dark': '#B91C1C',   // Merah tua untuk aksen/judul
                        'brand-text': '#441C1C',  // Teks coklat/merah tua
                    },
                    fontFamily: {
                        'poppins': ['Poppins', 'sans-serif']
                    }
                }
            }
        }
    </script>
    
    <style>
        /* Gaya kustom */
        body {
            font-family: 'Poppins', sans-serif;
            background-color: #FEF2F2; /* Latar belakang brand-light */
            color: #441C1C; /* Teks brand-text */
        }
        html {
            scroll-behavior: smooth;
        }
        /* Animasi untuk modal */
        .modal-fade-in {
            animation: fadeIn 0.3s ease-out;
        }
        .modal-fade-out {
            animation: fadeOut 0.3s ease-out;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: scale(0.95); }
            to { opacity: 1; transform: scale(1); }
        }
        @keyframes fadeOut {
            from { opacity: 1; transform: scale(1); }
            to { opacity: 0; transform: scale(0.95); }
        }
        /* Sembunyikan scrollbar untuk keranjang */
        #cart-items::-webkit-scrollbar {
            width: 8px;
        }
        #cart-items::-webkit-scrollbar-thumb {
            background: #F87171;
            border-radius: 4px;
        }
        #cart-items::-webkit-scrollbar-track {
            background: #FEF2F2;
        }
    </style>
</head>
<body class="bg-brand-light text-brand-text">

    <!-- ===== HEADER & NAVIGASI ===== -->
    <header class="bg-white shadow-md sticky top-0 z-50">
        <nav class="container mx-auto px-4 py-3 flex justify-between items-center">
            <!-- Brand -->
            <a href="#beranda" class="text-2xl font-bold text-brand-dark">
                Pangsit coii <span class="text-brand-red">12H</span>
            </a>
            
            <!-- Nav Links (Desktop) -->
            <div class="hidden md:flex space-x-6">
                <a href="#beranda" class="hover:text-brand-red">Beranda</a>
                <a href="#tentang" class="hover:text-brand-red">Tentang Kami</a>
                <a href="#menu" class="hover:text-brand-red">Menu</a>
                <a href="#testimoni" class="hover:text-brand-red">Testimoni</a>
                <a href="#pesan" class="hover:text-brand-red">Pesan</a>
            </div>
            
            <!-- Ikon Keranjang -->
            <button id="cart-button" class="relative text-2xl hover:text-brand-red transition-colors">
                <i class="fa-solid fa-cart-shopping"></i>
                <span id="cart-count" class="absolute -top-2 -right-3 bg-brand-red text-white text-xs font-bold w-5 h-5 rounded-full flex items-center justify-center">0</span>
            </button>
        </nav>
    </header>

    <!-- ===== MODAL KERANJANG (Hidden by default) ===== -->
    <div id="cart-modal" class="fixed inset-0 bg-black bg-opacity-50 z-[99] flex justify-center items-center hidden">
        <div id="cart-modal-content" class="bg-white w-11/12 md:w-1/2 lg:w-1/3 rounded-lg shadow-xl modal-fade-in">
            <!-- Header Modal -->
            <div class="flex justify-between items-center p-4 border-b">
                <h3 class="text-xl font-semibold text-brand-dark">🛒 Keranjang Anda</h3>
                <button id="close-modal-btn" class="text-2xl">&times;</button>
            </div>
            
            <!-- Isi Keranjang -->
            <div id="cart-items" class="p-4 max-h-[40vh] overflow-y-auto">
                <!-- Item keranjang akan ditambahkan oleh JavaScript -->
                <p id="cart-empty-msg" class="text-center text-gray-500">Keranjang masih kosong...</p>
            </div>
            
            <!-- Footer Modal -->
            <div class="p-4 border-t">
                <div class="flex justify-between items-center mb-4">
                    <span class="text-lg font-semibold">Total:</span>
                    <span id="cart-total" class="text-xl font-bold text-brand-red">Rp 0</span>
                </div>
                <button id="checkout-btn" class="w-full bg-brand-red text-white py-3 rounded-lg font-semibold hover:bg-brand-dark transition-colors">
                    Lanjut ke Pemesanan
                </button>
            </div>
        </div>
    </div>

    <!-- ===== MAIN CONTENT ===== -->
    <main>
        
        <!-- 1. BERANDA (HERO SECTION) -->
        <section id="beranda" class="container mx-auto px-4 py-16 md:py-24 flex flex-col md:flex-row items-center min-h-[calc(100vh-68px)]">
            <!-- Teks Hero -->
            <div class="md:w-1/2 text-center md:text-left mb-8 md:mb-0">
                <h1 class="text-4xl md:text-6xl font-bold text-brand-dark leading-tight">
                    Pangsit <span class="text-brand-red">coii 12H</span>
                </h1>
                <p class="text-xl md:text-2xl mt-4 mb-6">
                    Pedasnya Juara, Harganya Bersahaja!
                </p>
                <p class="text-lg mb-4">
                    Rasakan sensasi pangsit chili oil kekinian yang pedas, gurih, dan menggugah selera. Dibuat dari bahan pilihan, 100% Halal!
                </p>
                <p class="text-xl font-bold text-brand-red mb-8">
                    Mulai dari Rp 10.000 - Rp 20.000
                </p>
                <a href="#menu" class="bg-brand-red text-white font-semibold px-8 py-3 rounded-full text-lg hover:bg-brand-dark transition-colors shadow-lg">
                    Lihat Menu
                </a>
            </div>
            <!-- Gambar Hero -->
            <div class="md:w-1/2 flex justify-center">
                <!-- GANTI 'src' DENGAN URL GAMBAR PANGSIT ANDA -->
                <img src="https://assets.pikiran-rakyat.com/crop/0x0:0x0/720x0/webp/photo/2024/08/31/283435587.png" alt="Pangsit Chili Oil" class="rounded-2xl shadow-xl w-full max-w-md">
            </div>
        </section>
        
        <!-- 2. TENTANG KAMI -->
        <section id="tentang" class="py-16 bg-white">
            <div class="container mx-auto px-4 text-center">
                <h2 class="text-3xl font-bold text-brand-dark mb-6">Tentang Kami</h2>
                <p class="text-lg max-w-3xl mx-auto mb-8">
                    "Pangsit coii 12H" lahir dari tugas dan semangat kami untuk menyajikan makanan kekinian yang lezat dengan harga terjangkau. Kami percaya bahwa rasa enak tidak harus mahal.
                </p>
                <div class="bg-brand-light p-6 rounded-lg max-w-lg mx-auto shadow-inner">
                    <h3 class="text-2xl font-semibold text-brand-red">Kelompok 2 - 12 H</h3>
                    <p class="text-xl mt-2">
                        Adinda, Fachrezi, dan Eza
                    </p>
                </div>
            </div>
        </section>
        
        <!-- 3. DAFTAR MENU -->
        <section id="menu" class="py-16">
            <div class="container mx-auto px-4">
                <h2 class="text-3xl font-bold text-brand-dark text-center mb-10">🌶️ Menu Pilihan Kami 🌶️</h2>
                <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8">
                    
                    <!-- Produk 1 -->
                    <div class="bg-white rounded-xl shadow-lg overflow-hidden flex flex-col">
                        <img src="https://i.gojekapi.com/darkroom/gofood-indonesia/v2/images/uploads/2328e486-541e-4208-86f8-eec037529bb7_Go-Biz_20241007_074401.jpeg" alt="Pangsit Original" class="w-full h-48 object-cover">
                        <div class="p-6 flex flex-col flex-grow">
                            <h3 class="text-2xl font-semibold text-brand-dark mb-2">Pangsit Original</h3>
                            <p class="text-lg font-bold text-brand-red mb-3">Rp 10.000</p>
                            <p class="mb-4 flex-grow">Isi 5 pangsit ayam gurih dengan chili oil khas racikan kami. Klasik tapi asik!</p>
                            <button class="add-to-cart-btn mt-auto w-full bg-brand-red text-white py-2 px-4 rounded-lg font-semibold hover:bg-brand-dark transition-colors" data-id="1" data-name="Pangsit Original" data-price="10000">
                                <i class="fa-solid fa-cart-plus mr-2"></i>Tambah
                            </button>
                        </div>
                    </div>
                    
                    <!-- Produk 2 -->
                    <div class="bg-white rounded-xl shadow-lg overflow-hidden flex flex-col">
                        <img src="https://down-id.img.susercontent.com/file/id-11134233-7r98r-lzv36egl5val8d" alt="Pangsit Mozzarella" class="w-full h-48 object-cover">
                        <div class="p-6 flex flex-col flex-grow">
                            <h3 class="text-2xl font-semibold text-brand-dark mb-2">Pangsit Mozzarella</h3>
                            <p class="text-lg font-bold text-brand-red mb-3">Rp 15.000</p>
                            <p class="mb-4 flex-grow">Isi 5 pangsit ayam dengan lelehan keju mozzarella. Pedas, gurih, lumer di mulut!</p>
                            <button class="add-to-cart-btn mt-auto w-full bg-brand-red text-white py-2 px-4 rounded-lg font-semibold hover:bg-brand-dark transition-colors" data-id="2" data-name="Pangsit Mozzarella" data-price="15000">
                                <i class="fa-solid fa-cart-plus mr-2"></i>Tambah
                            </button>
                        </div>
                    </div>
                    
                    <!-- Produk 3 -->
                    <div class="bg-white rounded-xl shadow-lg overflow-hidden flex flex-col">
                        <img src="https://i.gojekapi.com/darkroom/gofood-indonesia/v2/images/uploads/41804a8b-0338-414c-8484-449096ddf1e8_Go-Biz_20240516_094912.jpeg" alt="Pangsit Komplit" class="w-full h-48 object-cover">
                        <div class="p-6 flex flex-col flex-grow">
                            <h3 class="text-2xl font-semibold text-brand-dark mb-2">Pangsit Sultan</h3>
                            <p class="text-lg font-bold text-brand-red mb-3">Rp 20.000</p>
                            <p class="mb-4 flex-grow">Isi 8 (campur Ori & Mozza). Porsi sultan, harga kawan. Dijamin kenyang!</p>
                            <button class="add-to-cart-btn mt-auto w-full bg-brand-red text-white py-2 px-4 rounded-lg font-semibold hover:bg-brand-dark transition-colors" data-id="3" data-name="Pangsit Sultan" data-price="20000">
                                <i class="fa-solid fa-cart-plus mr-2"></i>Tambah
                            </button>
                        </div>
                    </div>
                    
                </div>
            </div>
        </section>

        <!-- 4. TESTIMONI -->
        <section id="testimoni" class="py-16 bg-white">
            <div class="container mx-auto px-4">
                <h2 class="text-3xl font-bold text-brand-dark text-center mb-10">💬 Apa Kata Mereka? 💬</h2>
                <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                    <!-- Testi 1 -->
                    <div class="bg-brand-light p-6 rounded-lg shadow-md border-l-4 border-brand-red">
                        <p class="italic text-lg mb-4">"Gila sih, chili oil-nya beda banget! Pedesnya nampol tapi bikin nagih. Pangsitnya juga lembut. Fix langganan!"</p>
                        <p class="font-bold text-right text-brand-dark">- Kak Amanda, Siswi SMA</p>
                    </div>
                    <!-- Testi 2 -->
                    <div class="bg-brand-light p-6 rounded-lg shadow-md border-l-4 border-brand-red">
                        <p class="italic text-lg mb-4">"Harganya pas banget buat kantong pelajar. Yang mozza juaraaa, lumer banget di mulut. Sukses terus Pangsit coii!"</p>
                        <p class="font-bold text-right text-brand-dark">- Budi, Anak SMP</p>
                    </div>
                    <!-- Testi 3 -->
                    <div class="bg-brand-light p-6 rounded-lg shadow-md border-l-4 border-brand-red">
                        <p class="italic text-lg mb-4">"Porsinya pas, rasanya mantap. Cocok buat nemenin nugas atau nonton drakor. Recommended!"</p>
                        <p class="font-bold text-right text-brand-dark">- Kak Citra, Mahasiswi</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- 5. FORMULIR PEMESANAN -->
        <section id="pesan" class="py-16">
            <div class="container mx-auto px-4">
                <h2 class="text-3xl font-bold text-brand-dark text-center mb-10">📝 Yuk, Pesan Sekarang! 📝</h2>
                <div class="grid grid-cols-1 md:grid-cols-2 gap-10">
                    
                    <!-- Kolom Kiri: Form -->
                    <div class="bg-white p-6 md:p-8 rounded-xl shadow-lg">
                        <h3 class="text-2xl font-semibold text-brand-dark mb-6">Langkah 1: Isi Data Diri</h3>
                        <form id="order-form" class="space-y-4">
                            <div>
                                <label for="nama" class="block text-sm font-medium mb-1">Nama Lengkap:</label>
                                <input type="text" id="nama" name="nama" class="w-full p-3 border border-gray-300 rounded-lg focus:ring-brand-red focus:border-brand-red" placeholder="cth: Adinda" required>
                            </div>
                            <div>
                                <label for="alamat" class="block text-sm font-medium mb-1">Alamat Lengkap:</label>
                                <textarea id="alamat" name="alamat" rows="3" class="w-full p-3 border border-gray-300 rounded-lg focus:ring-brand-red focus:border-brand-red" placeholder="cth: Jl. Merdeka No. 123, atau Sekolah SMAN 1" required></textarea>
                            </div>
                            <div>
                                <label for="nomor" class="block text-sm font-medium mb-1">Nomor WhatsApp:</label>
                                <input type="tel" id="nomor" name="nomor" class="w-full p-3 border border-gray-300 rounded-lg focus:ring-brand-red focus:border-brand-red" placeholder="cth: 08123456789" required>
                            </div>
                            <div>
                                <label for="payment" class="block text-sm font-medium mb-1">Pilihan Pembayaran:</label>
                                <select id="payment" name="payment" class="w-full p-3 border border-gray-300 rounded-lg bg-white focus:ring-brand-red focus:border-brand-red">
                                    <option value="QRIS">Bayar dengan QRIS</option>
                                    <option value="DANA">Bayar ke DANA</option>
                                    <option value="COD">Bayar di Tempat (COD)</option>
                                </select>
                            </div>
                            
                            <!-- Pesan Error -->
                            <div id="form-error" class="text-red-600 text-sm hidden"></div>

                            <button type="button" id="order-btn" class="w-full bg-green-500 text-white py-3 px-6 rounded-lg font-semibold text-lg hover:bg-green-600 transition-colors">
                                <i class="fa-brands fa-whatsapp mr-2"></i>Pesan via WhatsApp
                            </button>
                        </form>
                    </div>
                    
                    <!-- Kolom Kanan: Info Pembayaran -->
                    <div class="bg-white p-6 md:p-8 rounded-xl shadow-lg">
                        <h3 class="text-2xl font-semibold text-brand-dark mb-6">Langkah 2: Pembayaran</h3>
                        <p class="mb-4">Selesaikan pembayaran setelah pesanan Anda dikonfirmasi oleh kami melalui WhatsApp.</p>
                        
                        <!-- Opsi QRIS -->
                        <div class="mb-6">
                            <h4 class="text-xl font-semibold text-brand-red mb-2">Via QRIS (All E-Wallet/Bank)</h4>
                            <p class="mb-2">Scan kode di bawah ini:</p>
                            <!-- GANTI 'src' DENGAN URL GAMBAR QRIS ANDA -->
                            <img src="blob:https://web.whatsapp.com/d50594a5-8c55-4ab7-b344-40ae0419ba9c" alt="QRIS Pembayaran" class="rounded-lg border border-gray-300 w-2/3 max-w-[250px]">
                        </div>
                        
                        <!-- Opsi DANA -->
                        <div>
                            <h4 class="text-xl font-semibold text-brand-red mb-2">Via DANA</h4>
                            <p class="mb-3">Bisa juga langsung transfer atau klik link Minta Bayar DANA:</p>
                            <a href="https://link.dana.id/minta?full_url=https://qr.dana.id/v1/281012012024092780081600" target="_blank" class="inline-block bg-blue-500 text-white py-2 px-4 rounded-lg font-semibold hover:bg-blue-600 transition-colors mb-3">
                                <i class="fa-solid fa-link mr-2"></i>Link Minta Bayar DANA
                            </a>
                            <p class="text-lg">Atau transfer manual ke DANA:</p>
                            <p class="text-xl font-bold text-brand-dark">085691507261</p>
                        </div>
                    </div>
                </div>
            </div>
        </section>
        
    </main>
    
    <!-- ===== TOMBOL WHATSAPP MELAYANG ===== -->
    <a href="https://wa.me/6285691507261?text=Halo%20Pangsit%20coii%2012H%2C%20saya%20mau%20tanya-tanya%20dong..." target="_blank" class="fixed bottom-5 right-5 w-16 h-16 bg-green-500 text-white rounded-full flex items-center justify-center shadow-lg text-3xl hover:bg-green-600 transition-transform hover:scale-110 z-40">
        <i class="fa-brands fa-whatsapp"></i>
    </a>

    <!-- ===== FOOTER ===== -->
    <footer class="bg-brand-dark text-white p-6 text-center">
        <p>&copy; 2025 Pangsit coii 12H.</p>
        <p>Dibuat oleh: <strong>Kelompok 2 (12 H)</strong> - Adinda, Fachrezi, dan Eza.</p>
    </footer>

    <!-- ===== JAVASCRIPT ===== -->
    <script>
        document.addEventListener('DOMContentLoaded', () => {
            
            // --- Variabel Global ---
            let cart = []; // Array untuk menyimpan item keranjang
            const WA_NUMBER = "6285691507261"; // Nomor WA (ganti 08 menjadi 62)

            // --- Elemen DOM ---
            const cartButton = document.getElementById('cart-button');
            const cartModal = document.getElementById('cart-modal');
            const cartModalContent = document.getElementById('cart-modal-content');
            const closeModalBtn = document.getElementById('close-modal-btn');
            const cartCount = document.getElementById('car
