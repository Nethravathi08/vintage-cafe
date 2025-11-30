<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>The Vintage Cafe</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Georgia', serif;
            background: #f4e8d8;
            color: #3e2723;
        }

        .page {
            display: none;
        }

        .page.active {
            display: block;
        }

        /* Login Page */
        .login-container {
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            background: linear-gradient(rgba(62, 39, 35, 0.7), rgba(62, 39, 35, 0.7)),
                        url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><text y="50" font-size="60">☕</text></svg>');
            background-size: 100px;
        }

        .login-box {
            background: #fff9f0;
            padding: 50px 40px;
            border-radius: 10px;
            box-shadow: 0 10px 40px rgba(0,0,0,0.3);
            border: 3px solid #8b6f47;
            max-width: 400px;
            width: 90%;
        }

        .login-box h1 {
            text-align: center;
            color: #5d4037;
            margin-bottom: 10px;
            font-size: 2.5em;
            font-style: italic;
        }

        .login-box p {
            text-align: center;
            color: #8b6f47;
            margin-bottom: 30px;
            font-style: italic;
        }

        .form-group {
            margin-bottom: 25px;
        }

        .form-group label {
            display: block;
            margin-bottom: 8px;
            color: #5d4037;
            font-weight: bold;
        }

        .form-group input {
            width: 100%;
            padding: 12px;
            border: 2px solid #8b6f47;
            border-radius: 5px;
            background: #fff;
            font-size: 16px;
            font-family: 'Georgia', serif;
        }

        .btn {
            width: 100%;
            padding: 15px;
            background: #5d4037;
            color: #fff;
            border: none;
            border-radius: 5px;
            font-size: 18px;
            cursor: pointer;
            font-family: 'Georgia', serif;
            transition: background 0.3s;
        }

        .btn:hover {
            background: #3e2723;
        }

        /* Header */
        header {
            background: #5d4037;
            color: #fff;
            padding: 20px 0;
            box-shadow: 0 2px 10px rgba(0,0,0,0.3);
        }

        nav {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0 20px;
        }

        .logo {
            font-size: 2em;
            font-style: italic;
            font-weight: bold;
        }

        .nav-links {
            display: flex;
            gap: 30px;
            list-style: none;
        }

        .nav-links a {
            color: #fff;
            text-decoration: none;
            font-size: 1.1em;
            transition: color 0.3s;
            cursor: pointer;
        }

        .nav-links a:hover {
            color: #d7ccc8;
        }

        .cart-icon {
            position: relative;
        }

        .cart-count {
            position: absolute;
            top: -10px;
            right: -10px;
            background: #ff6f00;
            color: #fff;
            border-radius: 50%;
            width: 20px;
            height: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 12px;
        }

        /* Home Page */
        .home-hero {
            background: linear-gradient(rgba(62, 39, 35, 0.5), rgba(62, 39, 35, 0.5)),
                        url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 200 200"><circle cx="100" cy="100" r="80" fill="%238b6f47"/></svg>');
            background-size: cover;
            height: 500px;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            color: #fff;
        }

        .hero-content h1 {
            font-size: 4em;
            margin-bottom: 20px;
            font-style: italic;
        }

        .hero-content p {
            font-size: 1.5em;
            margin-bottom: 30px;
        }

        .hero-btn {
            padding: 15px 40px;
            background: #ff6f00;
            color: #fff;
            text-decoration: none;
            border-radius: 5px;
            font-size: 1.2em;
            transition: background 0.3s;
            cursor: pointer;
            display: inline-block;
        }

        .hero-btn:hover {
            background: #e65100;
        }

        .features {
            max-width: 1200px;
            margin: 80px auto;
            padding: 0 20px;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 40px;
        }

        .feature {
            text-align: center;
            padding: 30px;
            background: #fff;
            border-radius: 10px;
            border: 2px solid #8b6f47;
        }

        .feature h3 {
            font-size: 1.8em;
            margin: 20px 0 10px;
            color: #5d4037;
        }

        /* Menu Page */
        .menu-container {
            max-width: 1200px;
            margin: 50px auto;
            padding: 0 20px;
        }

        .menu-header {
            text-align: center;
            margin-bottom: 50px;
        }

        .menu-header h1 {
            font-size: 3em;
            color: #5d4037;
            margin-bottom: 10px;
            font-style: italic;
        }

        .menu-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 30px;
        }

        .menu-item {
            background: #fff;
            border-radius: 10px;
            overflow: hidden;
            border: 3px solid #8b6f47;
            transition: transform 0.3s;
        }

        .menu-item:hover {
            transform: translateY(-5px);
        }

        .item-image {
            height: 200px;
            background: linear-gradient(135deg, #8b6f47, #d7ccc8);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 4em;
        }

        .item-details {
            padding: 20px;
        }

        .item-details h3 {
            color: #5d4037;
            margin-bottom: 10px;
            font-size: 1.5em;
        }

        .item-details p {
            color: #8b6f47;
            margin-bottom: 15px;
        }

        .item-footer {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .price {
            font-size: 1.5em;
            color: #ff6f00;
            font-weight: bold;
        }

        .add-to-cart {
            padding: 10px 20px;
            background: #5d4037;
            color: #fff;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: background 0.3s;
        }

        .add-to-cart:hover {
            background: #3e2723;
        }

        /* Cart Page */
        .cart-container {
            max-width: 900px;
            margin: 50px auto;
            padding: 0 20px;
        }

        .cart-header {
            text-align: center;
            margin-bottom: 40px;
        }

        .cart-header h1 {
            font-size: 3em;
            color: #5d4037;
            font-style: italic;
        }

        .cart-items {
            background: #fff;
            border-radius: 10px;
            padding: 30px;
            border: 3px solid #8b6f47;
            margin-bottom: 30px;
        }

        .cart-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 0;
            border-bottom: 2px solid #e0e0e0;
        }

        .cart-item:last-child {
            border-bottom: none;
        }

        .item-info h3 {
            color: #5d4037;
            margin-bottom: 5px;
        }

        .item-controls {
            display: flex;
            align-items: center;
            gap: 20px;
        }

        .quantity-controls {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .qty-btn {
            width: 30px;
            height: 30px;
            background: #8b6f47;
            color: #fff;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 18px;
        }

        .remove-btn {
            padding: 8px 15px;
            background: #d32f2f;
            color: #fff;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }

        .cart-summary {
            background: #fff;
            border-radius: 10px;
            padding: 30px;
            border: 3px solid #8b6f47;
        }

        .summary-row {
            display: flex;
            justify-content: space-between;
            padding: 15px 0;
            border-bottom: 1px solid #e0e0e0;
        }

        .summary-row.total {
            border-bottom: none;
            font-size: 1.5em;
            font-weight: bold;
            color: #5d4037;
        }

        .checkout-btn {
            width: 100%;
            padding: 15px;
            margin-top: 20px;
            background: #ff6f00;
            color: #fff;
            border: none;
            border-radius: 5px;
            font-size: 1.3em;
            cursor: pointer;
            transition: background 0.3s;
        }

        .checkout-btn:hover {
            background: #e65100;
        }

        .empty-cart {
            text-align: center;
            padding: 60px 20px;
        }

        .empty-cart h2 {
            color: #8b6f47;
            margin-bottom: 20px;
        }

        /* Payment Page */
        .payment-container {
            max-width: 600px;
            margin: 50px auto;
            padding: 0 20px;
        }

        .payment-box {
            background: #fff;
            border-radius: 10px;
            padding: 40px;
            border: 3px solid #8b6f47;
        }

        .payment-box h1 {
            text-align: center;
            color: #5d4037;
            margin-bottom: 30px;
            font-style: italic;
        }

        .order-summary {
            background: #f4e8d8;
            padding: 20px;
            border-radius: 5px;
            margin-bottom: 30px;
        }

        .order-summary h3 {
            color: #5d4037;
            margin-bottom: 15px;
        }

        .success-message {
            background: #4caf50;
            color: #fff;
            padding: 20px;
            border-radius: 5px;
            text-align: center;
            margin-bottom: 20px;
            display: none;
        }

        .success-message.show {
            display: block;
        }
    </style>
</head>
<body>
    <!-- Login Page -->
    <div id="loginPage" class="page active">
        <div class="login-container">
            <div class="login-box">
                <h1>The Vintage Cafe</h1>
                <p>Est. 1965</p>
                <form id="loginForm">
                    <div class="form-group">
                        <label for="username">Username</label>
                        <input type="text" id="username" required>
                    </div>
                    <div class="form-group">
                        <label for="password">Password</label>
                        <input type="password" id="password" required>
                    </div>
                    <button type="submit" class="btn">Enter Cafe</button>
                </form>
            </div>
        </div>
    </div>

    <!-- Home Page -->
    <div id="homePage" class="page">
        <header>
            <nav>
                <div class="logo">The Vintage Cafe</div>
                <ul class="nav-links">
                    <li><a onclick="showPage('homePage')">Home</a></li>
                    <li><a onclick="showPage('menuPage')">Menu</a></li>
                    <li class="cart-icon">
                        <a onclick="showPage('cartPage')">Cart <span class="cart-count" id="cartCount">0</span></a>
                    </li>
                    <li><a onclick="logout()">Logout</a></li>
                </ul>
            </nav>
        </header>

        <div class="home-hero">
            <div class="hero-content">
                <h1>Welcome to The Vintage Cafe</h1>
                <p>Where memories brew since 1965</p>
                <a class="hero-btn" onclick="showPage('menuPage')">Explore Menu</a>
            </div>
        </div>

        <div class="features">
            <div class="feature">
                <div style="font-size: 3em;">☕</div>
                <h3>Premium Coffee</h3>
                <p>Handcrafted with the finest beans</p>
            </div>
            <div class="feature">
                <div style="font-size: 3em;">🍰</div>
                <h3>Fresh Pastries</h3>
                <p>Baked daily with love</p>
            </div>
            <div class="feature">
                <div style="font-size: 3em;">🏛️</div>
                <h3>Vintage Ambiance</h3>
                <p>Step back in time</p>
            </div>
        </div>
    </div>

    <!-- Menu Page -->
    <div id="menuPage" class="page">
        <header>
            <nav>
                <div class="logo">The Vintage Cafe</div>
                <ul class="nav-links">
                    <li><a onclick="showPage('homePage')">Home</a></li>
                    <li><a onclick="showPage('menuPage')">Menu</a></li>
                    <li class="cart-icon">
                        <a onclick="showPage('cartPage')">Cart <span class="cart-count" id="cartCount2">0</span></a>
                    </li>
                    <li><a onclick="logout()">Logout</a></li>
                </ul>
            </nav>
        </header>

        <div class="menu-container">
            <div class="menu-header">
                <h1>Our Menu</h1>
                <p style="color: #8b6f47; font-style: italic;">Timeless flavors for every palate</p>
            </div>

            <div class="menu-grid" id="menuGrid"></div>
        </div>
    </div>

    <!-- Cart Page -->
    <div id="cartPage" class="page">
        <header>
            <nav>
                <div class="logo">The Vintage Cafe</div>
                <ul class="nav-links">
                    <li><a onclick="showPage('homePage')">Home</a></li>
                    <li><a onclick="showPage('menuPage')">Menu</a></li>
                    <li class="cart-icon">
                        <a onclick="showPage('cartPage')">Cart <span class="cart-count" id="cartCount3">0</span></a>
                    </li>
                    <li><a onclick="logout()">Logout</a></li>
                </ul>
            </nav>
        </header>

        <div class="cart-container">
            <div class="cart-header">
                <h1>Your Cart</h1>
            </div>

            <div id="cartContent"></div>
        </div>
    </div>

    <!-- Payment Page -->
    <div id="paymentPage" class="page">
        <header>
            <nav>
                <div class="logo">The Vintage Cafe</div>
                <ul class="nav-links">
                    <li><a onclick="showPage('homePage')">Home</a></li>
                    <li><a onclick="showPage('menuPage')">Menu</a></li>
                    <li class="cart-icon">
                        <a onclick="showPage('cartPage')">Cart <span class="cart-count" id="cartCount4">0</span></a>
                    </li>
                    <li><a onclick="logout()">Logout</a></li>
                </ul>
            </nav>
        </header>

        <div class="payment-container">
            <div class="payment-box">
                <h1>Payment Details</h1>
                
                <div class="success-message" id="successMessage">
                    <h2>✓ Payment Successful!</h2>
                    <p>Thank you for your order. Enjoy your meal!</p>
                </div>

                <div class="order-summary" id="orderSummary"></div>

                <form id="paymentForm">
                    <div class="form-group">
                        <label for="cardName">Cardholder Name</label>
                        <input type="text" id="cardName" required>
                    </div>
                    <div class="form-group">
                        <label for="cardNumber">Card Number</label>
                        <input type="text" id="cardNumber" placeholder="1234 5678 9012 3456" maxlength="19" required>
                    </div>
                    <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 20px;">
                        <div class="form-group">
                            <label for="expiry">Expiry Date</label>
                            <input type="text" id="expiry" placeholder="MM/YY" maxlength="5" required>
                        </div>
                        <div class="form-group">
                            <label for="cvv">CVV</label>
                            <input type="text" id="cvv" placeholder="123" maxlength="3" required>
                        </div>
                    </div>
                    <button type="submit" class="btn" style="margin-top: 20px;">Complete Payment</button>
                </form>
            </div>
        </div>
    </div>

    <script>
        // Menu Items
        const menuItems = [
            { id: 1, name: 'Espresso', price: 120, emoji: '☕', desc: 'Rich and bold Italian espresso' },
            { id: 2, name: 'Cappuccino', price: 150, emoji: '☕', desc: 'Creamy espresso with steamed milk' },
            { id: 3, name: 'Cafe Latte', price: 160, emoji: '☕', desc: 'Smooth espresso with milk foam' },
            { id: 4, name: 'Cold Coffee', price: 180, emoji: '🥤', desc: 'Refreshing iced coffee blend' },
            { id: 5, name: 'Chocolate Cake', price: 140, emoji: '🍰', desc: 'Decadent chocolate sponge' },
            { id: 6, name: 'Blueberry Muffin', price: 90, emoji: '🧁', desc: 'Fresh baked with real blueberries' },
            { id: 7, name: 'Croissant', price: 80, emoji: '🥐', desc: 'Buttery French pastry' },
            { id: 8, name: 'Club Sandwich', price: 220, emoji: '🥪', desc: 'Triple-decker classic' },
            { id: 9, name: 'Pasta Alfredo', price: 280, emoji: '🍝', desc: 'Creamy parmesan pasta' },
            { id: 10, name: 'Margherita Pizza', price: 320, emoji: '🍕', desc: 'Classic tomato and mozzarella' },
            { id: 11, name: 'Green Tea', price: 100, emoji: '🍵', desc: 'Soothing herbal blend' },
            { id: 12, name: 'Tiramisu', price: 180, emoji: '🍰', desc: 'Italian coffee-flavored dessert' }
        ];

        let cart = [];

        // Login
        document.getElementById('loginForm').addEventListener('submit', (e) => {
            e.preventDefault();
            const username = document.getElementById('username').value;
            const password = document.getElementById('password').value;
            
            if (username && password) {
                showPage('homePage');
            }
        });

        // Show page
        function showPage(pageId) {
            document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
            document.getElementById(pageId).classList.add('active');
            
            if (pageId === 'menuPage') {
                renderMenu();
            } else if (pageId === 'cartPage') {
                renderCart();
            } else if (pageId === 'paymentPage') {
                renderPaymentSummary();
            }
            
            updateCartCount();
        }

        // Render Menu
        function renderMenu() {
            const menuGrid = document.getElementById('menuGrid');
            menuGrid.innerHTML = menuItems.map(item => `
                <div class="menu-item">
                    <div class="item-image">${item.emoji}</div>
                    <div class="item-details">
                        <h3>${item.name}</h3>
                        <p>${item.desc}</p>
                        <div class="item-footer">
                            <span class="price">₹${item.price}</span>
                            <button class="add-to-cart" onclick="addToCart(${item.id})">Add to Cart</button>
                        </div>
                    </div>
                </div>
            `).join('');
        }

        // Add to Cart
        function addToCart(itemId) {
            const item = menuItems.find(i => i.id === itemId);
            const existingItem = cart.find(i => i.id === itemId);
            
            if (existingItem) {
                existingItem.quantity++;
            } else {
                cart.push({ ...item, quantity: 1 });
            }
            
            updateCartCount();
            alert(`${item.name} added to cart!`);
        }

        // Update cart count
        function updateCartCount() {
            const count = cart.reduce((sum, item) => sum + item.quantity, 0);
            document.querySelectorAll('[id^="cartCount"]').forEach(el => {
                el.textContent = count;
            });
        }

        // Render Cart
        function renderCart() {
            const cartContent = document.getElementById('cartContent');
            
            if (cart.length === 0) {
                cartContent.innerHTML = `
                    <div class="empty-cart">
                        <h2>Your cart is empty</h2>
                        <p style="color: #8b6f47;">Add some delicious items from our menu!</p>
                        <a class="hero-btn" onclick="showPage('menuPage')" style="margin-top: 20px;">Browse Menu</a>
                    </div>
                `;
                return;
            }

            const subtotal = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
            const tax = subtotal * 0.05;
            const total = subtotal + tax;

            cartContent.innerHTML = `
                <div class="cart-items">
                    ${cart.map(item => `
                        <div class="cart-item">
                            <div class="item-info">
                                <h3>${item.emoji} ${item.name}</h3>
                                <p style="color: #8b6f47;">₹${item.price} each</p>
                            </div>
                            <div class="item-controls">
                                <div class="quantity-controls">
                                    <button class="qty-btn" onclick="updateQuantity(${item.id}, -1)">-</button>
                                    <span style="font-size: 1.2em; font-weight: bold;">${item.quantity}</span>
                                    <button class="qty-btn" onclick="updateQuantity(${item.id}, 1)">+</button>
                                </div>
                                <span class="price">₹${item.price * item.quantity}</span>
                                <button class="remove-btn" onclick="removeFromCart(${item.id})">Remove</button>
                            </div>
                        </div>
                    `).join('')}
                </div>
                
                <div class="cart-summary">
                    <div class="summary-row">
                        <span>Subtotal:</span>
                        <span>₹${subtotal.toFixed(2)}</span>
                    </div>
                    <div class="summary-row">
                        <span>Tax (5%):</span>
                        <span>₹${tax.toFixed(2)}</span>
                    </div>
                    <div class="summary-row total">
                        <span>Total:</span>
                        <span>₹${total.toFixed(2)}</span>
                    </div>
                    <button class="checkout-btn" onclick="showPage('paymentPage')">Proceed to Payment</button>
                </div>
            `;
        }

        // Update quantity
        function updateQuantity(itemId, change) {
            const item = cart.find(i => i.id === itemId);
            if (item) {
                item.quantity += change;
                if (item.quantity <= 0) {
                    removeFromCart(itemId);
                } else {
                    renderCart();
                    updateCartCount();
                }
            }
        }

        // Remove from cart
        function removeFromCart(itemId) {
            cart = cart.filter(i => i.id !== itemId);
            renderCart();
            updateCartCount();
        }

        // Render Payment Summary
        function renderPaymentSummary() {
            const subtotal = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
            const tax = subtotal * 0.05;
            const total = subtotal + tax;

            document.getElementById('orderSummary').innerHTML = `
                <h3>Order Summary</h3>
                ${cart.map(item => `
                    <div style="display: flex; justify-content: space-between; padding: 5px 0;">
                        <span>${item.name} x ${item.quantity}</span>
                        <span>₹${(item.price * item.quantity).toFixed(2)}</span>
                    </div>
                `).join('')}
                <hr style="margin: 15px 0; border: none; border-top: 2px solid #8b6f47;">
                <div style="display: flex; justify-content: space-between; font-weight: bold; font-size: 1.2em; color: #5d4037;">
                    <span>Total Amount:</span>
                    <span>₹${total.toFixed(2)}</span>
                </div>
            `;
        }

        // Payment Form
        document.getElementById('paymentForm').addEventListener('submit', (e) => {
            e.preventDefault();
            
            document.getElementById('successMessage').classList.add('show');
            document.getElementById('paymentForm').style.display = 'none';
            
            setTimeout(() => {
                cart = [];
                updateCartCount();
                showPage('homePage');
                document.getElementById('successMessage').classList.remove('show');
                document.getElementById('paymentForm').style.display = 'block';
                document.getElementById('paymentForm').reset();
            }, 3000);
        });

        // Format card number
        document.getElementById('cardNumber').addEventListener('input', (e) => {
            let value = e.target.value.replace(/\s/g, '');
            let formattedValue = value.match(/.{1,4}/g)?.join(' ') || value;
            e.target.value = formattedValue;
        });

        // Format expiry
        document.getElementById('expiry').addEventListener('input', (e) => {
            let value = e.target.value.replace(/\D/g, '');
            if (value.length >= 2) {
                value = value.slice(0, 2) + '/' + value.slice(2, 4);
            }
            e.target.value = value;
        });

        // Logout
        function logout() {
            cart = [];
            updateCartCount();
            showPage('loginPage');
            document.getElementById('loginForm').reset();
        }
    </script>
</body>
</html>
