<!DOCTYPE html>
<html lang="id" style="scroll-behavior: smooth;">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Selamat Datang di Gacoan</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <style>
    /* Transisi untuk keranjang pop-up */
    .cart-drawer {
      transition: transform 0.3s cubic-bezier(0.4, 0, 0.2, 1);
    }

    /* Keyframe untuk animasi slide-in pada item keranjang */
    @keyframes slideInFromTop {
      0% {
        transform: translateY(-20px);
        opacity: 0;
      }
      100% {
        transform: translateY(0);
        opacity: 1;
      }
    }

    .cart-item-animate {
      animation: slideInFromTop 0.3s ease-out;
    }

    /* Keyframe untuk animasi shake pada ikon keranjang */
    @keyframes shake {
      0%, 100% { transform: translateX(0) scale(1); }
      20%, 60% { transform: translateX(-5px) scale(1.1); }
      40%, 80% { transform: translateX(5px) scale(1.1); }
    }
    .shake-animation {
      animation: shake 0.5s cubic-bezier(.36,.07,.19,.97) both;
    }
  
  @keyframes popIn {
  0% { transform: scale(0); opacity: 0; }
  80% { transform: scale(1.1); opacity: 1; }
  100% { transform: scale(1); }
}

.qty-btn {
  animation: popIn 0.2s ease-out;
}
  </style>
</head>
<body class="bg-gray-100 min-h-screen flex flex-col font-sans">

  <header class="bg-blue-600 text-white p-4 shadow-lg sticky top-0 z-50">
    <div class="container mx-auto flex justify-between items-center">
      <h1 class="text-2xl font-bold tracking-wide">Gacoan Jakarta</h1>
      <button id="cart-toggle" class="relative transform transition-transform duration-150 active:scale-95">
        <svg id="cart-icon" xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-white" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 3h2l.4 2M7 13h10l4-8H5.4M7 13L5.4 5M7 13l-2.293 2.293c-.63.63-.102 1.743.707 1.743H18a2 2 0 002-2V7.786" />
        </svg>
        <span id="cart-item-count" class="absolute -top-1 -right-1 bg-white text-pink-600 rounded-full text-xs w-4 h-4 flex items-center justify-center font-bold" style="display:none;">0</span>
      </button>
    </div>
  </header>

  <nav class="bg-white sticky top-16 z-40 shadow-sm md:shadow-md p-4">
    <div class="container mx-auto">
      <ul class="flex justify-around items-center space-x-4 overflow-x-auto whitespace-nowrap md:justify-center">
        <li><a href="#noodle-section" class="text-gray-800 font-semibold px-4 py-2 rounded-full hover:bg-gray-200 transition-colors duration-200">🍜 Noodle</a></li>
        <li><a href="#dimsum-section" class="text-gray-800 font-semibold px-4 py-2 rounded-full hover:bg-gray-200 transition-colors duration-200">🥟 Dimsum</a></li>
        <li><a href="#beverage-section" class="text-gray-800 font-semibold px-4 py-2 rounded-full hover:bg-gray-200 transition-colors duration-200">🥤 Beverage</a></li>
      </ul>
    </div>
  </nav>

  <main class="flex-1 container mx-auto p-4 flex flex-col md:flex-row gap-8">
    <section class="flex-1">
      <h2 class="text-3xl font-bold mb-6 text-gray-800 border-b-2 border-pink-500 pb-2">SELAMAT DATANG DI GACOAN</h2>

      <div class="bg-white rounded-xl shadow-md p-6 mb-8 border-t-4 border-blue-600">
        <h3 class="text-xl font-bold mb-4 text-gray-800">Detail Pesanan</h3>
        <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
            <div>
                <label class="block text-sm font-semibold mb-2">Nama Pelanggan:</label>
                <input id="customerName" type="text" placeholder="Masukkan nama Anda" class="w-full border border-gray-300 rounded-lg p-3 focus:outline-none focus:border-blue-500 transition-colors" />
            </div>
            <div>
                <label class="block text-sm font-semibold mb-2">Pilih Tipe Pesanan:</label>
                <select id="orderType" class="w-full border border-gray-300 rounded-lg p-3 focus:outline-none focus:border-blue-500 transition-colors">
                    <option value="Dine In">Dine In</option>
                    <option value="Take Away">Take Away</option>
                </select>
            </div>
        </div>
      </div>

      <h3 id="noodle-section" class="text-2xl font-bold mb-4 mt-8 text-gray-700">🍜 Noodle</h3>
      <div class="grid grid-cols-2 lg:grid-cols-3 gap-6">
        <div class="bg-white rounded-2xl shadow-lg p-4 flex flex-col transform transition-transform duration-300 hover:scale-[1.02]">
          <h4 class="font-bold text-lg text-gray-900 mt-2">Mie Suit</h4>
          <p class="text-pink-500 text-sm font-semibold">NOODLE</p>
          <p class="font-bold text-lg mt-1 text-pink-600">Rp 11.000</p>
          <button class="add-to-cart mt-auto bg-blue-600 text-white rounded-full py-1 px-2 font-sm hover:bg-blue-700 transition-colors duration-300 transform active:scale-95 relative">
  Tambah
  <span class="qty-btn absolute -top-1 -right-1 bg-pink-500 text-white-600 rounded-full text-xs w-5 h-5 flex items-center justify-center font-bold" style="display:none;">0</span>
</button>
        </div>
        <div class="bg-white rounded-2xl shadow-lg p-4 flex flex-col transform transition-transform duration-300 hover:scale-[1.02]">
          <h4 class="font-bold text-lg text-gray-900 mt-2">Mie Gacoan Lv.0</h4>
          <p class="text-yellow-500 text-sm font-semibold">NOODLE</p>
          <p class="font-bold text-lg mt-1 text-pink-600">Rp 11.000</p>
         <button class="add-to-cart mt-auto bg-blue-600 text-white rounded-full py-1 px-2 font-sm hover:bg-blue-700 transition-colors duration-300 transform active:scale-95 relative">
  Tambah
  <span class="qty-btn absolute -top-1 -right-1 bg-pink-500 text-white-600 rounded-full text-xs w-5 h-5 flex items-center justify-center font-bold" style="display:none;">0</span>
</button>
        </div>
        <div class="bg-white rounded-2xl shadow-lg p-4 flex flex-col transform transition-transform duration-300 hover:scale-[1.02]">
          <h4 class="font-bold text-lg text-gray-900 mt-2">Mie gacoan Lv. 1</h4>
          <p class="text-yellow-500 text-sm font-semibold">NOODLE</p>
          <p class="font-bold text-lg mt-1 text-pink-600">Rp 11.000</p>
       <button class="add-to-cart mt-auto bg-blue-600 text-white rounded-full py-1 px-2 font-sm hover:bg-blue-700 transition-colors duration-300 transform active:scale-95 relative">
  Tambah
  <span class="qty-btn absolute -top-1 -right-1 bg-pink-500 text-white-600 rounded-full text-xs w-5 h-5 flex items-center justify-center font-bold" style="display:none;">0</span>
</button> </div>
        <div class="bg-white rounded-2xl shadow-lg p-4 flex flex-col transform transition-transform duration-300 hover:scale-[1.02]">
          <h4 class="font-bold text-lg text-gray-900 mt-0">Mie Gacoan Lv. 2</h4>
          <p class="text-yellow-500 text-sm font-semibold">NOODLE</p>
          <p class="font-bold text-lg mt-1 text-pink-600">Rp 11.000</p>
    <button class="add-to-cart mt-auto bg-blue-600 text-white rounded-full py-1 px-2 font-sm hover:bg-blue-700 transition-colors duration-300 transform active:scale-95 relative">
  Tambah
  <span class="qty-btn absolute -top-1 -right-1 bg-pink-500 text-white-600 rounded-full text-xs w-5 h-5 flex items-center justify-center font-bold" style="display:none;">0</span>
</button>
        </div>
        <div class="bg-white rounded-2xl shadow-lg p-4 flex flex-col transform transition-transform duration-300 hover:scale-[1.02]">
          <h4 class="font-bold text-lg text-gray-900 mt-2">Mie Gacoan Lv. 3</h4>
             <p class="text-yellow-500 text-sm font-semibold">NOODLE</p>
          <p class="font-bold text-lg mt-1 text-pink-600">Rp 11.000</p>
<button class="add-to-cart mt-auto bg-blue-600 text-white rounded-full py-1 px-2 font-sm hover:bg-blue-700 transition-colors duration-300 transform active:scale-95 relative">
  Tambah
  <span class="qty-btn absolute -top-1 -right-1 bg-pink-500 text-white-600 rounded-full text-xs w-5 h-5 flex items-center justify-center font-bold" style="display:none;">0</span>
</button>
        </div>
        <div class="bg-white rounded-2xl shadow-lg p-4 flex flex-col transform transition-transform duration-300 hover:scale-[1.02]">
          <h4 class="font-bold text-lg text-gray-900 mt-2">Mie Gacoan Lv. 4</h4>
         <p class="text-yellow-500 text-sm font-semibold">NOODLE</p>
          <p class="font-bold text-lg mt-1 text-pink-600">Rp 11.000</p>
<button class="add-to-cart mt-auto bg-blue-600 text-white rounded-full py-1 px-2 font-sm hover:bg-blue-700 transition-colors duration-300 transform active:scale-95 relative">
  Tambah
  <span class="qty-btn absolute -top-1 -right-1 bg-pink-500 text-white-600 rounded-full text-xs w-5 h-5 flex items-center justify-center font-bold" style="display:none;">0</span>
</button>
        </div>
        <div class="bg-white rounded-2xl shadow-lg p-4 flex flex-col transform transition-transform duration-300 hover:scale-[1.02]">
          <h4 class="font-bold text-lg text-gray-900 mt-2">Mie Gacoan Lv. 6</h4>
          <p class="text-yellow-500 text-sm font-semibold">NOODLE</p>
          <p class="font-bold text-lg mt-1 text-pink-600">Rp 12.000</p>
<button class="add-to-cart mt-auto bg-blue-600 text-white rounded-full py-1 px-2 font-sm hover:bg-blue-700 transition-colors duration-300 transform active:scale-95 relative">
  Tambah
  <span class="qty-btn absolute -top-1 -right-1 bg-pink-500 text-white-600 rounded-full text-xs w-5 h-5 flex items-center justify-center font-bold" style="display:none;">0</span>
</button>
        </div>
        <div class="bg-white rounded-2xl shadow-lg p-4 flex flex-col transform transition-transform duration-300 hover:scale-[1.02]">
          <h4 class="font-bold text-lg text-gray-900 mt-2">Mie Gacoan Lv. 8</h4>
          <p class="text-yellow-500 text-sm font-semibold">NOODLE</p>
          <p class="font-bold text-lg mt-2 text-pink-600">Rp 12.000</p>
        <button class="add-to-cart mt-auto bg-blue-600 text-white rounded-full py-1 px-2 font-sm hover:bg-blue-700 transition-colors duration-300 transform active:scale-95 relative">
  Tambah
  <span class="qty-btn absolute -top-1 -right-1 bg-pink-500 text-white-600 rounded-full text-xs w-5 h-5 flex items-center justify-center font-bold" style="display:none;">0</span>
        </button>
        </div>
        <div class="bg-white rounded-2xl shadow-lg p-4 flex flex-col transform transition-transform duration-300 hover:scale-[1.02]">
          <h4 class="font-bold text-l text-gray-900 mt-1">Mie Hompimpa Lv.1</h4>
          <p class="text-blue-400 text-sm font-semibold">NOODLE</p>
          <p class="font-bold text-lg mt-2 text-pink-600">Rp 11.000</p>
        <button class="add-to-cart mt-auto bg-blue-600 text-white rounded-full py-1 px-2 font-sm hover:bg-blue-700 transition-colors duration-300 transform active:scale-95 relative">
  Tambah
  <span class="qty-btn absolute -top-1 -right-1 bg-pink-500 text-white-600 rounded-full text-xs w-5 h-5 flex items-center justify-center font-bold" style="display:none;">0</span>
        </button>
        </div>
         <div class="bg-white rounded-2xl shadow-lg p-4 flex flex-col transform transition-transform duration-300 hover:scale-[1.02]">
          <h4 class="font-bold text-l text-gray-900 mt-2">Mie Hompimpa Lv.2</h4>
          <p class="text-blue-400 text-sm font-semibold">NOODLE</p>
          <p class="font-bold text-lg mt-2 text-pink-600">Rp 11.000</p>
        <button class="add-to-cart mt-auto bg-blue-600 text-white rounded-full py-1 px-2 font-sm hover:bg-blue-700 transition-colors duration-300 transform active:scale-95 relative">
  Tambah
  <span class="qty-btn absolute -top-1 -right-1 bg-pink-500 text-white-600 rounded-full text-xs w-5 h-5 flex items-center justify-center font-bold" style="display:none;">0</span>
        </button>
         </div>
         <div class="bg-white rounded-2xl shadow-lg p-4 flex flex-col transform transition-transform duration-300 hover:scale-[1.02]">
          <h4 class="font-bold text-l text-gray-900 mt-2">Mie Hompimpa Lv. 3</h4>
          <p class="text-blue-400 text-sm font-semibold">NOODLE</p>
          <p class="font-bold text-lg mt-2 text-pink-600">Rp 11.000</p>
        <button class="add-to-cart mt-auto bg-blue-600 text-white rounded-full py-1 px-2 font-sm hover:bg-blue-700 transition-colors duration-300 transform active:scale-95 relative">
  Tambah
  <span class="qty-btn absolute -top-1 -right-1 bg-pink-500 text-white-600 rounded-full text-xs w-5 h-5 flex items-center justify-center font-bold" style="display:none;">0</span>
        </button>
         </div>
         <div class="bg-white rounded-2xl shadow-lg p-4 flex flex-col transform transition-transform duration-300 hover:scale-[1.02]">
          <h4 class="font-bold text-l text-gray-900 mt-2">Mie Hompimpa Lv. 4</h4>
          <p class="text-blue-400 text-sm font-semibold">NOODLE</p>
          <p class="font-bold text-lg mt-2 text-pink-600">Rp 11.000</p>
        <button class="add-to-cart mt-auto bg-blue-600 text-white rounded-full py-1 px-2 font-sm hover:bg-blue-700 transition-colors duration-300 transform active:scale-95 relative">
  Tambah
  <span class="qty-btn absolute -top-1 -right-1 bg-pink-500 text-white-600 rounded-full text-xs w-5 h-5 flex items-center justify-center font-bold" style="display:none;">0</span>
        </button>
         </div>
        <div class="bg-white rounded-2xl shadow-lg p-4 flex flex-col transform transition-transform duration-300 hover:scale-[1.02]">
          <h4 class="font-bold text-l text-gray-900 mt-2">Mie Hompimpa Lv. 6</h4>
       <p class="text-blue-400 text-sm font-semibold">NOODLE</p>
          <p class="font-bold text-lg mt-2 text-pink-600">Rp 12.000</p>
          <button class="add-to-cart mt-auto bg-blue-600 text-white rounded-full py-1 px-2 font-sm hover:bg-blue-700 transition-colors duration-300 transform active:scale-95 relative">Tambah
  <span class="qty-btn absolute -top-1 -right-1 bg-pink-500 text-white-600 rounded-full text-xs w-5 h-5 flex items-center justify-center font-bold" style="display:none;">0</span>
        </button>
        </div><div class="bg-white rounded-2xl shadow-lg p-4 flex flex-col transform transition-transform duration-300 hover:scale-[1.02]">
          <h4 class="font-bold text-l text-gray-900 mt-2">Mie Hompimpa Lv. 8</h4>
           <p class="text-blue-400 text-sm font-semibold">NOODLE</p>
          <p class="font-bold text-lg mt-2 text-pink-600">Rp 12.000</p>
          <button class="add-to-cart mt-auto bg-blue-600 text-white rounded-full py-1 px-2 font-sm hover:bg-blue-700 transition-colors duration-300 transform active:scale-95 relative">
  Tambah
  <span class="qty-btn absolute -top-1 -right-1 bg-pink-500 text-white-600 rounded-full text-xs w-5 h-5 flex items-center justify-center font-bold" style="display:none;">0</span>
        </button>
        </div>
      </div>
      
      <h3 id="dimsum-section" class="text-2xl font-bold mb-4 mt-8 text-gray-700">🥟 Dimsum</h3>
      <div class="grid grid-cols-2 lg:grid-cols-3 gap-6">
        <div class="bg-white rounded-2xl shadow-lg p-4 flex flex-col transform transition-transform duration-300 hover:scale-[1.02]">
          <h4 class="font-bold text-lg text-gray-900 mt-2">Udang Keju</h4>
          <p class="text-blue-600 text-sm font-semibold">DIMSUM.</p>
          <p class="font-bold text-lg mt-2 text-pink-600">Rp 10.000</p>
        <button class="add-to-cart mt-auto bg-blue-600 text-white rounded-full py-1 px-2 font-sm hover:bg-blue-700 transition-colors duration-300 transform active:scale-95 relative">
  Tambah
  <span class="qty-btn absolute -top-1 -right-1 bg-pink-500 text-white-600 rounded-full text-xs w-5 h-5 flex items-center justify-center font-bold" style="display:none;">0</span>
        </button>
        </div>
        <div class="bg-white rounded-2xl shadow-lg p-4 flex flex-col transform transition-transform duration-300 hover:scale-[1.02]">
          <h4 class="font-bold text-lg text-gray-900 mt-2">Udang Rambutan</h4>
          <p class="text-blue-600 text-sm font-semibold">DIMSUM.</p>
          <p class="font-bold text-lg mt-2 text-pink-600">Rp 10.000</p>
        <button class="add-to-cart mt-auto bg-blue-600 text-white rounded-full py-1 px-2 font-sm hover:bg-blue-700 transition-colors duration-300 transform active:scale-95 relative">
  Tambah
  <span class="qty-btn absolute -top-1 -right-1 bg-pink-500 text-white-600 rounded-full text-xs w-5 h-5 flex items-center justify-center font-bold" style="display:none;">0</span>
        </button>
        </div>
        <div class="bg-white rounded-2xl shadow-lg p-4 flex flex-col transform transition-transform duration-300 hover:scale-[1.02]">
          <h4 class="font-bold text-lg text-gray-900 mt-2">Lumpia Udang</h4>
          <p class="text-blue-600 text-sm font-semibold">DIMSUM.</p>
          <p class="font-bold text-lg mt-2 text-pink-600">Rp 10.000</p>
        <button class="add-to-cart mt-auto bg-blue-600 text-white rounded-full py-1 px-2 font-sm hover:bg-blue-700 transition-colors duration-300 transform active:scale-95 relative">
  Tambah
  <span class="qty-btn absolute -top-1 -right-1 bg-pink-500 text-white-600 rounded-full text-xs w-5 h-5 flex items-center justify-center font-bold" style="display:none;">0</span>
        </button>
        </div>
        <div class="bg-white rounded-2xl shadow-lg p-4 flex flex-col transform transition-transform duration-300 hover:scale-[1.02]">
          <h4 class="font-bold text-lg text-gray-900 mt-2">Siomay Ayam</h4>
          <p class="text-blue-600 text-sm font-semibold">DIMSUM.</p>
          <p class="font-bold text-lg mt-2 text-pink-600">Rp 10.000</p>
        <button class="add-to-cart mt-auto bg-blue-600 text-white rounded-full py-1 px-2 font-sm hover:bg-blue-700 transition-colors duration-300 transform active:scale-95 relative">
  Tambah
  <span class="qty-btn absolute -top-1 -right-1 bg-pink-500 text-white-600 rounded-full text-xs w-5 h-5 flex items-center justify-center font-bold" style="display:none;">0</span>
        </button>
        </div>
        <div class="bg-white rounded-2xl shadow-lg p-4 flex flex-col transform transition-transform duration-300 hover:scale-[1.02]">
          <h4 class="font-bold text-lg text-gray-900 mt-2">Pangsit Goreng</h4>
          <p class="text-blue-600 text-sm font-semibold">DIMSUM.</p>
          <p class="font-bold text-lg mt-2 text-pink-600">Rp 11.000</p>
        <button class="add-to-cart mt-auto bg-blue-600 text-white rounded-full py-1 px-2 font-sm hover:bg-blue-700 transition-colors duration-300 transform active:scale-95 relative">
  Tambah
  <span class="qty-btn absolute -top-1 -right-1 bg-pink-500 text-white-600 rounded-full text-xs w-5 h-5 flex items-center justify-center font-bold" style="display:none;">0</span>
        </button>
        </div>
      </div>

      <h3 id="beverage-section" class="text-2xl font-bold mb-4 mt-8 text-gray-700">🥤 Beverage</h3>
      <div class="grid grid-cols-2 lg:grid-cols-3 gap-6">
        <div class="bg-white rounded-2xl shadow-lg p-4 flex flex-col transform transition-transform duration-300 hover:scale-[1.02]">
           <h4 class="font-bold text-lg text-gray-900 mt-2">Es Gobak Sodor</h4>
          <p class="text-gray-600 text-sm font-semibold">BAR.</p>
          <p class="font-bold text-lg mt-2 text-pink-600">Rp 10.000</p>
        <button class="add-to-cart mt-auto bg-blue-600 text-white rounded-full py-1 px-2 font-sm hover:bg-blue-700 transition-colors duration-300 transform active:scale-95 relative">
  Tambah
  <span class="qty-btn absolute -top-1 -right-1 bg-pink-500 text-white-600 rounded-full text-xs w-5 h-5 flex items-center justify-center font-bold" style="display:none;">0</span>
        </button>
        </div>
        <div class="bg-white rounded-2xl shadow-lg p-4 flex flex-col transform transition-transform duration-300 hover:scale-[1.02]">
           <h4 class="font-bold text-lg text-gray-900 mt-2">Es Petak Umpet</h4>
          <p class="text-gray-600 text-sm font-semibold">BAR.</p>
          <p class="font-bold text-lg mt-2 text-pink-600">Rp 10.000</p>
        <button class="add-to-cart mt-auto bg-blue-600 text-white rounded-full py-1 px-2 font-sm hover:bg-blue-700 transition-colors duration-300 transform active:scale-95 relative">
  Tambah
  <span class="qty-btn absolute -top-1 -right-1 bg-pink-500 text-white-600 rounded-full text-xs w-5 h-5 flex items-center justify-center font-bold" style="display:none;">0</span>
        </button>
        </div>
        <div class="bg-white rounded-2xl shadow-lg p-4 flex flex-col transform transition-transform duration-300 hover:scale-[1.02]">
           <h4 class="font-bold text-lg text-gray-900 mt-2">Es Teklek</h4>
          <p class="text-gray-600 text-sm font-semibold">BAR.</p>
          <p class="font-bold text-lg mt-2 text-pink-600">Rp 10.000</p>
        <button class="add-to-cart mt-auto bg-blue-600 text-white rounded-full py-1 px-2 font-sm hover:bg-blue-700 transition-colors duration-300 transform active:scale-95 relative">
  Tambah
  <span class="qty-btn absolute -top-1 -right-1 bg-pink-500 text-white-600 rounded-full text-xs w-5 h-5 flex items-center justify-center font-bold" style="display:none;">0</span>
        </button>
        </div>
        <div class="bg-white rounded-2xl shadow-lg p-4 flex flex-col transform transition-transform duration-300 hover:scale-[1.02]">
           <h4 class="font-bold text-lg text-gray-900 mt-2">Es Sluku Bathok</h4>
          <p class="text-gray-600 text-sm font-semibold">BAR.</p>
          <p class="font-bold text-lg mt-2 text-pink-600">Rp 10.000</p>
        <button class="add-to-cart mt-auto bg-blue-600 text-white rounded-full py-1 px-2 font-sm hover:bg-blue-700 transition-colors duration-300 transform active:scale-95 relative">
  Tambah
  <span class="qty-btn absolute -top-1 -right-1 bg-pink-500 text-white-600 rounded-full text-xs w-5 h-5 flex items-center justify-center font-bold" style="display:none;">0</span>
        </button>
        </div>
        <div class="bg-white rounded-2xl shadow-lg p-4 flex flex-col transform transition-transform duration-300 hover:scale-[1.02]">
           <h4 class="font-bold text-lg text-gray-900 mt-2">Green Thai Tea</h4>
          <p class="text-gray-600 text-sm font-semibold">BAR.</p>
          <p class="font-bold text-lg mt-2 text-pink-600">Rp 10.000</p>
        <button class="add-to-cart mt-auto bg-blue-600 text-white rounded-full py-1 px-2 font-sm hover:bg-blue-700 transition-colors duration-300 transform active:scale-95 relative">
  Tambah
  <span class="qty-btn absolute -top-1 -right-1 bg-pink-500 text-white-600 rounded-full text-xs w-5 h-5 flex items-center justify-center font-bold" style="display:none;">0</span>
        </button>
        </div>
        <div class="bg-white rounded-2xl shadow-lg p-4 flex flex-col transform transition-transform duration-300 hover:scale-[1.02]">
           <h4 class="font-bold text-lg text-gray-900 mt-2">Thai Tea</h4>
          <p class="text-gray-600 text-sm font-semibold">BAR.</p>
          <p class="font-bold text-lg mt-2 text-pink-600">Rp 10.000</p>
        <button class="add-to-cart mt-auto bg-blue-600 text-white rounded-full py-1 px-2 font-sm hover:bg-blue-700 transition-colors duration-300 transform active:scale-95 relative">
  Tambah
  <span class="qty-btn absolute -top-1 -right-1 bg-pink-500 text-white-600 rounded-full text-xs w-5 h-5 flex items-center justify-center font-bold" style="display:none;">0</span>
        </button>
        </div>
        <div class="bg-white rounded-2xl shadow-lg p-4 flex flex-col transform transition-transform duration-300 hover:scale-[1.02]">
           <h4 class="font-bold text-lg text-gray-900 mt-2">Lemon Tea</h4>
          <p class="text-gray-600 text-sm font-semibold">BAR.</p>
          <p class="font-bold text-lg mt-2 text-pink-600">Rp 10.000</p>
        <button class="add-to-cart mt-auto bg-blue-600 text-white rounded-full py-1 px-2 font-sm hover:bg-blue-700 transition-colors duration-300 transform active:scale-95 relative">
  Tambah
  <span class="qty-btn absolute -top-1 -right-1 bg-pink-500 text-white-600 rounded-full text-xs w-5 h-5 flex items-center justify-center font-bold" style="display:none;">0</span>
        </button>
        </div>
        <div class="bg-white rounded-2xl shadow-lg p-4 flex flex-col transform transition-transform duration-300 hover:scale-[1.02]">
           <h4 class="font-bold text-lg text-gray-900 mt-2">Tea</h4>
          <p class="text-gray-600 text-sm font-semibold">BAR.</p>
          <p class="font-bold text-lg mt-2 text-pink-600">Rp 10.000</p>
        <button class="add-to-cart mt-auto bg-blue-600 text-white rounded-full py-1 px-2 font-sm hover:bg-blue-700 transition-colors duration-300 transform active:scale-95 relative">
  Tambah
  <span class="qty-btn absolute -top-1 -right-1 bg-pink-500 text-white-600 rounded-full text-xs w-5 h-5 flex items-center justify-center font-bold" style="display:none;">0</span>
        </button>
        </div>
        <div class="bg-white rounded-2xl shadow-lg p-4 flex flex-col transform transition-transform duration-300 hover:scale-[1.02]">
           <h4 class="font-bold text-lg text-gray-900 mt-2">Coklat</h4>
          <p class="text-gray-600 text-sm font-semibold">BAR.</p>
          <p class="font-bold text-lg mt-2 text-pink-600">Rp 10.000</p>
        <button class="add-to-cart mt-auto bg-blue-600 text-white rounded-full py-1 px-2 font-sm hover:bg-blue-700 transition-colors duration-300 transform active:scale-95 relative">
  Tambah
  <span class="qty-btn absolute -top-1 -right-1 bg-pink-500 text-white-600 rounded-full text-xs w-5 h-5 flex items-center justify-center font-bold" style="display:none;">0</span>
        </button>
        </div>
        <div class="bg-white rounded-2xl shadow-lg p-4 flex flex-col transform transition-transform duration-300 hover:scale-[1.02]">
           <h4 class="font-bold text-lg text-gray-900 mt-2">Vanilla Late</h4>
          <p class="text-gray-600 text-sm font-semibold">BAR.</p>
          <p class="font-bold text-lg mt-2 text-pink-600">Rp 10.000</p>
        <button class="add-to-cart mt-auto bg-blue-600 text-white rounded-full py-1 px-2 font-sm hover:bg-blue-700 transition-colors duration-300 transform active:scale-95 relative">
  Tambah
  <span class="qty-btn absolute -top-1 -right-1 bg-pink-500 text-white-600 rounded-full text-xs w-5 h-5 flex items-center justify-center font-bold" style="display:none;">0</span>
        </button>
        </div>
        <div class="bg-white rounded-2xl shadow-lg p-4 flex flex-col transform transition-transform duration-300 hover:scale-[1.02]">
           <h4 class="font-bold text-lg text-gray-900 mt-2">Teh Tarik</h4>
          <p class="text-gray-600 text-sm font-semibold">BAR.</p>
          <p class="font-bold text-lg mt-2 text-pink-600">Rp 10.000</p>
        <button class="add-to-cart mt-auto bg-blue-600 text-white rounded-full py-1 px-2 font-sm hover:bg-blue-700 transition-colors duration-300 transform active:scale-95 relative">
  Tambah
  <span class="qty-btn absolute -top-1 -right-1 bg-pink-500 text-white-600 rounded-full text-xs w-5 h-5 flex items-center justify-center font-bold" style="display:none;">0</span>
        </button>
        </div>
        <div class="bg-white rounded-2xl shadow-lg p-4 flex flex-col transform transition-transform duration-300 hover:scale-[1.02]">
           <h4 class="font-bold text-lg text-gray-900 mt-2">Air Mineral</h4>
          <p class="text-gray-600 text-sm font-semibold">BAR.</p>
          <p class="font-bold text-lg mt-2 text-pink-600">Rp 10.000</p>
        <button class="add-to-cart mt-auto bg-blue-600 text-white rounded-full py-1 px-2 font-sm hover:bg-blue-700 transition-colors duration-300 transform active:scale-95 relative">
  Tambah
  <span class="qty-btn absolute -top-1 -right-1 bg-pink-500 text-white-600 rounded-full text-xs w-5 h-5 flex items-center justify-center font-bold" style="display:none;">0</span>
        </button>
        </div>
      </div>
    </section>

    <div id="cart-overlay" class="fixed inset-0 bg-black bg-opacity-50 z-40 hidden md:hidden"></div>

    <aside id="cart-section" class="fixed inset-0 z-50 h-full w-full bg-white cart-drawer transform translate-x-full md:relative md:h-fit md:w-1/3 md:translate-x-0 rounded-l-2xl shadow-xl flex flex-col p-6">
      
      <div class="flex justify-between items-center mb-4">
        <h2 class="text-xl font-bold text-gray-800">🛒 Keranjang Belanja</h2>
        <button id="cart-close" class="text-gray-600 hover:text-gray-900 md:hidden">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
          </svg>
        </button>
      </div>

      <div class="flex-grow overflow-y-auto pr-2">
          <ul id="cart" class="space-y-4 text-sm text-gray-700">
            <li class="text-gray-400 italic text-center py-4">Keranjang Anda kosong</li>
          </ul>
      </div>

      <div class="border-t-2 border-gray-200 mt-6 pt-6">
        <div class="flex justify-between items-center font-bold text-lg">
            <span>Total:</span>
            <span id="total" class="text-green-600">Rp 0</span>
        </div>
        <button id="checkout" class="w-full mt-6 bg-blue-600 text-white rounded-lg py-3 font-semibold hover:bg-blue-700 transition-colors duration-300 shadow-md transform active:scale-95">Checkout via WhatsApp</button>
      </div>
    </aside>

  </main>

  <footer class="bg-gray-200 text-center p-4 text-sm text-gray-600 mt-8">
    © 2025 Pilih Menu Online
  </footer>

  <script>
  const cart = document.getElementById("cart");
const totalEl = document.getElementById("total");
const checkoutBtn = document.getElementById("checkout");
const orderType = document.getElementById("orderType");
const customerName = document.getElementById("customerName");
const addButtons = document.querySelectorAll(".add-to-cart");
const cartToggleBtn = document.getElementById("cart-toggle");
const cartSection = document.getElementById("cart-section");
const cartCloseBtn = document.getElementById("cart-close");
const cartItemCount = document.getElementById("cart-item-count");
const cartOverlay = document.getElementById("cart-overlay");

let totalHarga = 0;
let totalItems = 0;

function updateTotalDisplay() {
  totalEl.innerText = "Rp " + totalHarga.toLocaleString("id-ID");
  cartItemCount.innerText = totalItems;
  cartItemCount.style.display = totalItems > 0 ? 'flex' : 'none';
}

function ensureEmptyTextRemoved() {
  if (cart.children.length === 1 && cart.children[0].classList.contains("text-gray-400")) {
    cart.innerHTML = "";
  }
}

// Fungsi baru untuk mencari tombol yang sesuai dengan item di keranjang
function findButtonForCartItem(itemName) {
  const allCards = document.querySelectorAll(".bg-white.rounded-2xl");
  for (const card of allCards) {
    const cardItemName = card.querySelector("h4").innerText.trim();
    if (cardItemName === itemName) {
      return card.querySelector(".add-to-cart");
    }
  }
  return null;
}

// Fungsi baru untuk memperbarui kuantitas di tombol
function updateButtonQty(item, qty) {
  const targetButton = findButtonForCartItem(item);
  if (targetButton) {
    const qtyBtnSpan = targetButton.querySelector(".qty-btn");
    if (qty > 0) {
      qtyBtnSpan.innerText = qty;
      qtyBtnSpan.style.display = 'flex';
    } else {
      qtyBtnSpan.innerText = '0';
      qtyBtnSpan.style.display = 'none';
    }
  }
}

function tambahKeKeranjang(item, harga) {
  ensureEmptyTextRemoved();

  let existing = [...cart.children].find(li => li.dataset.item === item);
  let newQty;

  if (existing) {
    let qtySpan = existing.querySelector(".qty");
    let qty = parseInt(qtySpan.innerText, 10);
    qty++;
    newQty = qty;
    qtySpan.innerText = qty;
    totalHarga += harga;
    totalItems++;
  } else {
    const li = document.createElement("li");
    li.dataset.item = item;
    li.dataset.harga = harga;
    li.classList.add("flex", "justify-between", "items-center", "gap-2", "cart-item-animate");

    li.innerHTML = `
      <span class="text-sm">${item}</span>
      <div class="flex items-center gap-2">
        <button class="minus bg-gray-200 px-2 rounded transform transition-transform duration-150 active:scale-95">-</button>
        <span class="qty px-2">1</span>
        <button class="plus bg-gray-200 px-2 rounded transform transition-transform duration-150 active:scale-95">+</button>
        <span class="harga text-sm">Rp ${harga.toLocaleString("id-ID")}</span>
        <button class="hapus text-pink-500 hover:text-pink-700 transform transition-transform duration-150 active:scale-95">❌</button>
      </div>
    `;

    li.querySelector(".plus").addEventListener("click", () => {
      let qtySpan = li.querySelector(".qty");
      let qty = parseInt(qtySpan.innerText, 10);
      qty++;
      qtySpan.innerText = qty;
      totalHarga += harga;
      totalItems++;
      updateTotalDisplay();
      updateButtonQty(item, qty);
    });

    li.querySelector(".minus").addEventListener("click", () => {
      let qtySpan = li.querySelector(".qty");
      let qty = parseInt(qtySpan.innerText, 10);
      if (qty > 1) {
        qty--;
        qtySpan.innerText = qty;
        totalHarga -= harga;
        totalItems--;
        updateTotalDisplay();
        updateButtonQty(item, qty);
      }
    });

    li.querySelector(".hapus").addEventListener("click", () => {
      li.style.transition = 'opacity 0.3s ease-out, transform 0.3s ease-out';
      li.style.opacity = '0';
      li.style.transform = 'translateX(20px)';
      
      li.addEventListener('transitionend', () => {
          let qty = parseInt(li.querySelector(".qty").innerText, 10);
          totalHarga -= harga * qty;
          totalItems -= qty;
          if (totalHarga < 0) totalHarga = 0;
          if (totalItems < 0) totalItems = 0;
          li.remove();
          updateTotalDisplay();
          updateButtonQty(item, 0); // Reset kuantitas di tombol

          if (cart.children.length === 0) {
            cart.innerHTML = `<li class="text-gray-400 italic text-center py-4">Keranjang Anda kosong</li>`;
          }
      });
    });

    cart.appendChild(li);
    totalHarga += harga;
    totalItems++;
    newQty = 1;
  }
  
  updateTotalDisplay();
  updateButtonQty(item, newQty);
}

// Event listener untuk tombol 'Tambah'
addButtons.forEach(btn => {
  btn.addEventListener("click", () => {
    const card = btn.closest(".flex.flex-col");
    const item = card.querySelector("h4").innerText.trim();
    const hargaText = card.querySelector("p.font-bold").innerText;
    const harga = parseInt(hargaText.replace(/[^\d]/g, ""), 10);
    tambahKeKeranjang(item, harga);
  });
});

// Event listener untuk tombol pop-up keranjang
cartToggleBtn.addEventListener("click", () => {
  cartSection.classList.remove("translate-x-full");
  cartOverlay.classList.remove("hidden");
});

// Event listener untuk tombol tutup pop-up
cartCloseBtn.addEventListener("click", () => {
  cartSection.classList.add("translate-x-full");
  cartOverlay.classList.add("hidden");
});

// Event listener untuk menutup keranjang saat overlay diklik
cartOverlay.addEventListener("click", () => {
  cartSection.classList.add("translate-x-full");
  cartOverlay.classList.add("hidden");
});

checkoutBtn.addEventListener("click", () => {
  if (cart.children.length === 1 && cart.children[0].classList.contains("text-gray-400")) {
    alert("Keranjang masih kosong!");
    return;
  }

  const nama = customerName.value.trim();
  if (!nama) {
    alert("Silakan isi Nama Pelanggan terlebih dahulu.");
    customerName.focus();
    return;
  }

  let pesan = `Halo Gacoan Jl. Jakarta, saya mau pesan.%0A`;
  pesan += `Tipe Pesanan: ${*orderType.value*}%0A%0A`;
  pesan += `Nama: ${nama}%0A%0A`;
  pesan += `Daftar pesanan:%0A`;

  [...cart.children].forEach(li => {
    const item = li.dataset.item;
    const qty = Number(li.querySelector(".qty").innerText);
    const subtotal = hargaPerItem * qty;
    pesan += `- ${item} x${qty} = Rp ${subtotal.toLocaleString("id-ID")}%0A`;
  });

  pesan += `%0ATotal: ${totalEl.innerText}%0A`;
  pesan += `Terima kasih 🙏`;

  const noWA = "628991190404";
  const url = `https://api.whatsapp.com/send?phone=${noWA}&text=${pesan}`;

  window.open(url, "_blank", "noopener,noreferrer");
});
     </script>

</body>
</html>
