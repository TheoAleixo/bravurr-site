<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Bravurr | Moda com Atitude</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;700&display=swap" rel="stylesheet">
  <style>
    body { font-family: 'Montserrat', sans-serif; }
  </style>
</head>
<body class="bg-white text-gray-800">
  <!-- Header -->
  <header class="bg-black text-white p-6 flex justify-between items-center">
    <h1 class="text-3xl font-bold">Bravurr</h1>
    <nav>
      <ul class="flex space-x-6">
        <li><a href="#produtos" class="hover:text-yellow-400">Produtos</a></li>
        <li><a href="#sobre" class="hover:text-yellow-400">Sobre</a></li>
        <li><a href="#contato" class="hover:text-yellow-400">Contato</a></li>
        <li><button onclick="toggleCart()" class="hover:text-yellow-400">🛒 Carrinho (<span id="cart-count">0</span>)</button></li>
      </ul>
    </nav>
  </header>

  <!-- Hero Section -->
  <section class="bg-[url('https://images.unsplash.com/photo-1521334884684-d80222895322')] bg-cover bg-center text-white h-[80vh] flex items-center justify-center">
    <div class="bg-black bg-opacity-50 p-10 rounded-xl text-center">
      <h2 class="text-4xl md:text-6xl font-bold mb-4">Moda com Atitude</h2>
      <p class="text-xl mb-6">Vista-se com personalidade. Vista Bravurr.</p>
      <a href="#produtos" class="bg-yellow-400 text-black px-6 py-3 rounded-full font-bold hover:bg-yellow-300">Ver Coleção</a>
    </div>
  </section>

  <!-- Produtos -->
  <section id="produtos" class="p-10 bg-gray-100">
    <h3 class="text-3xl font-bold text-center mb-8">Nossos Produtos</h3>
    <div class="grid md:grid-cols-3 gap-8">
      <!-- Produto 1 -->
      <div class="bg-white p-6 rounded-lg shadow">
        <img src="https://source.unsplash.com/300x300/?tshirt" alt="Camiseta" class="w-full rounded mb-4">
        <h4 class="text-xl font-bold mb-2">Camiseta Bravurr</h4>
        <p class="mb-2">Estilo urbano e confortável.</p>
        <span class="font-bold text-yellow-500 block mb-2">R$ 89,90</span>
        <button onclick="addToCart('Camiseta Bravurr', 89.90)" class="bg-black text-white px-4 py-2 rounded hover:bg-yellow-400 hover:text-black">Adicionar ao Carrinho</button>
      </div>
      <!-- Produto 2 -->
      <div class="bg-white p-6 rounded-lg shadow">
        <img src="https://source.unsplash.com/300x300/?hoodie" alt="Moletom" class="w-full rounded mb-4">
        <h4 class="text-xl font-bold mb-2">Moletom Bravurr</h4>
        <p class="mb-2">Perfeito para dias frios com estilo.</p>
        <span class="font-bold text-yellow-500 block mb-2">R$ 149,90</span>
        <button onclick="addToCart('Moletom Bravurr', 149.90)" class="bg-black text-white px-4 py-2 rounded hover:bg-yellow-400 hover:text-black">Adicionar ao Carrinho</button>
      </div>
      <!-- Produto 3 -->
      <div class="bg-white p-6 rounded-lg shadow">
        <img src="https://source.unsplash.com/300x300/?jeans" alt="Calça" class="w-full rounded mb-4">
        <h4 class="text-xl font-bold mb-2">Calça Bravurr</h4>
        <p class="mb-2">Conforto e resistência para o dia a dia.</p>
        <span class="font-bold text-yellow-500 block mb-2">R$ 129,90</span>
        <button onclick="addToCart('Calça Bravurr', 129.90)" class="bg-black text-white px-4 py-2 rounded hover:bg-yellow-400 hover:text-black">Adicionar ao Carrinho</button>
      </div>
    </div>
  </section>

  <!-- Carrinho -->
  <section id="cart" class="fixed top-0 right-0 w-80 h-full bg-white border-l border-gray-300 shadow-xl p-6 overflow-y-auto hidden z-50">
    <h3 class="text-2xl font-bold mb-4">Seu Carrinho</h3>
    <ul id="cart-items" class="mb-4"></ul>
    <p class="font-bold text-lg">Total: R$ <span id="cart-total">0.00</span></p>
    <button class="mt-4 bg-yellow-400 text-black px-4 py-2 rounded w-full font-bold hover:bg-yellow-300">Finalizar Compra</button>
  </section>

  <!-- Sobre -->
  <section id="sobre" class="p-10">
    <h3 class="text-3xl font-bold text-center mb-6">Sobre a Bravurr</h3>
    <p class="max-w-3xl mx-auto text-center text-lg">A Bravurr nasceu para vestir pessoas ousadas, autênticas e que não têm medo de se expressar. Unimos design moderno com qualidade e conforto para criar roupas que inspiram atitude todos os dias.</p>
  </section>

  <!-- Contato -->
  <footer id="contato" class="bg-black text-white p-8 mt-10">
    <div class="max-w-4xl mx-auto text-center">
      <h4 class="text-xl font-bold mb-2">Fale Conosco</h4>
      <p>Email: contato@bravurr.com</p>
      <p>Instagram: @bravurr.oficial</p>
      <p class="mt-4 text-sm">&copy; 2025 Bravurr. Todos os direitos reservados.</p>
    </div>
  </footer>

  <script>
    const cart = [];

    function addToCart(product, price) {
      cart.push({ product, price });
      updateCart();
    }

    function updateCart() {
      const cartItems = document.getElementById('cart-items');
      const cartCount = document.getElementById('cart-count');
      const cartTotal = document.getElementById('cart-total');

      cartItems.innerHTML = '';
      let total = 0;

      cart.forEach((item, index) => {
        total += item.price;
        const li = document.createElement('li');
        li.className = 'mb-2 flex justify-between';
        li.innerHTML = `${item.product} <span>R$ ${item.price.toFixed(2)}</span>`;
        cartItems.appendChild(li);
      });

      cartCount.textContent = cart.length;
      cartTotal.textContent = total.toFixed(2);
    }

    function toggleCart() {
      const cartEl = document.getElementById('cart');
      cartEl.classList.toggle('hidden');
    }
  </script>
</body>
</html>
