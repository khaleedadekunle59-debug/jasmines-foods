<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Jasmine's Food</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f4;
            color: #333;
        }
        header {
            background-color: #ff6347;
            color: white;
            text-align: center;
            padding: 20px;
            position: relative;
        }
        h1 {
            margin: 0;
        }
        #admin-link {
            position: absolute;
            top: 20px;
            right: 20px;
            color: white;
            text-decoration: none;
            font-weight: bold;
        }
        #menu {
            max-width: 1200px;
            margin: 20px auto;
            padding: 20px;
            display: flex;
            flex-wrap: wrap;
            justify-content: space-around;
        }
        .dish {
            background-color: white;
            border: 1px solid #ddd;
            border-radius: 8px;
            padding: 15px;
            margin: 10px;
            width: 300px;
            text-align: center;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }
        .dish img {
            max-width: 100%;
            height: auto;
            border-radius: 8px;
        }
        .dish .quantity {
            width: 50px;
            padding: 5px;
            margin: 10px 5px;
            text-align: center;
        }
        .dish button.add-to-cart {
            background-color: #2196F3;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 5px;
            cursor: pointer;
        }
        .dish button.add-to-cart:hover {
            background-color: #1E88E5;
        }
        .dish button.order-now {
            background-color: #4CAF50;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 5px;
            cursor: pointer;
            margin-top: 10px;
        }
        .dish button.order-now:hover {
            background-color: #45a049;
        }
        #cart {
            max-width: 1200px;
            margin: 20px auto;
            padding: 20px;
            background-color: white;
            border: 1px solid #ddd;
            border-radius: 8px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }
        #cart-items {
            list-style-type: none;
            padding: 0;
        }
        #cart-items li {
            margin-bottom: 10px;
            border-bottom: 1px solid #eee;
            padding-bottom: 10px;
        }
        #total {
            font-weight: bold;
            margin-top: 20px;
        }
        #checkout {
            background-color: #FF9800;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 5px;
            cursor: pointer;
            margin-top: 10px;
        }
        #checkout:hover {
            background-color: #F57C00;
        }
        #admin-dashboard {
            display: none;
            max-width: 1200px;
            margin: 20px auto;
            padding: 20px;
            background-color: white;
            border: 1px solid #ddd;
            border-radius: 8px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }
        #admin-login {
            max-width: 400px;
            margin: 20px auto;
            padding: 20px;
            background-color: white;
            border: 1px solid #ddd;
            border-radius: 8px;
            text-align: center;
        }
        #admin-form {
            margin-top: 20px;
        }
        #admin-form input {
            display: block;
            width: 100%;
            margin: 10px 0;
            padding: 10px;
        }
        #dish-list {
            margin-top: 20px;
        }
        .admin-dish {
            border-bottom: 1px solid #eee;
            padding: 10px 0;
        }
        .admin-dish input {
            width: 80%;
            margin: 5px 0;
        }
    </style>
</head>
<body>
    <header>
        <h1>Jasmine's Food</h1>
        <p>Delicious African Dishes | Phone: 09168877122</p>
        <a id="admin-link" href="#" onclick="showAdminLogin()">Admin</a>
    </header>
    <section id="menu">
        <h2 style="width: 100%; text-align: center;">Our Menu - African Dishes</h2>
        <!-- Dishes will be rendered here dynamically -->
    </section>
    <section id="cart">
        <h2>Your Cart</h2>
        <ul id="cart-items"></ul>
        <p id="total">Total: ₦0</p>
        <button id="checkout" onclick="window.location.href='tel:09168877122'">Checkout</button>
    </section>

    <section id="admin-login">
        <h2>Admin Login</h2>
        <input type="password" id="admin-password" placeholder="Enter password">
        <button onclick="loginAdmin()">Login</button>
    </section>

    <section id="admin-dashboard">
        <h2>Admin Dashboard</h2>
        <button onclick="logoutAdmin()">Logout</button>
        <h3>Add New Dish</h3>
        <form id="add-dish-form">
            <input type="text" id="new-name" placeholder="Dish Name" required>
            <input type="text" id="new-desc" placeholder="Description" required>
            <input type="number" id="new-price" placeholder="Price (₦)" required>
            <input type="text" id="new-img" placeholder="Image URL" required>
            <button type="submit">Add Dish</button>
        </form>
        <h3>Edit/Remove Dishes</h3>
        <div id="dish-list">
            <!-- Admin dish list will be rendered here -->
        </div>
    </section>

    <script>
        // Default dishes with improved high-quality images
        let dishes = [
            {
                name: "Jollof Rice",
                desc: "A flavorful West African classic made with rice, tomatoes, spices, and often served with chicken and plantains.",
                price: 1500,
                img: "https://thumbs.dreamstime.com/b/delicious-jollof-rice-grilled-chicken-fried-plantains-vibrant-appetizing-close-up-traditional-west-african-420300260.jpg"
            },
            {
                name: "Egusi Soup",
                desc: "Rich and hearty melon seed soup with leafy greens, meat, and spices. Best enjoyed with fufu or pounded yam.",
                price: 1200,
                img: "https://www.preciouscore.com/wp-content/uploads/2018/10/Egusi-Soup-Nigerian-Egusi-Soup.jpg"
            },
            {
                name: "Suya",
                desc: "Spicy grilled meat skewers (beef or chicken) coated in peanut spice mix – a popular Nigerian street food.",
                price: 1000,
                img: "https://appetizing-cactus-7139e93734.media.strapiapp.com/Suya_Satay_Skewer_Nigerian_Street_Food_C_24_16591_1200x800_6a45073_1_bd22702f7d.jpeg"
            },
            {
                name: "Fufu",
                desc: "Soft pounded dough made from cassava or yam, perfect for swallowing with your favorite soup.",
                price: 800,
                img: "https://media.istockphoto.com/id/498310978/photo/egusi-soup-and-pounded-yam-nigerian-cuisine.jpg?s=612x612&w=0&k=20&c=7TmkO_7Nx12PpXqWQpPUUWEuxjY6qX4ITdBVBFxfHuA="
            },
            {
                name: "Moin-Moin",
                desc: "Steamed bean pudding made from peeled beans, peppers, and spices – nutritious and delicious.",
                price: 500,
                img: "https://sisijemimah.com/wp-content/uploads/2015/12/moimoi-3.jpg"
            },
            {
                name: "Pounded Yam",
                desc: "Smooth, stretchy dough made from boiled yams, traditionally paired with soups like egusi or okra.",
                price: 1000,
                img: "https://media.istockphoto.com/id/498310978/photo/egusi-soup-and-pounded-yam-nigerian-cuisine.jpg?s=612x612&w=0&k=20&c=7TmkO_7Nx12PpXqWQpPUUWEuxjY6qX4ITdBVBFxfHuA="
            },
            {
                name: "Okra Soup",
                desc: "Slimy yet delicious soup made with okra, meat, fish, and spices. A West African favorite.",
                price: 1100,
                img: "https://lookaside.fbsbx.com/lookaside/crawler/media/?media_id=1249541363854993"
            },
            {
                name: "Akara",
                desc: "Deep-fried bean cakes made from black-eyed peas, onions, and peppers. Great for breakfast or snacks.",
                price: 600,
                img: "https://media.istockphoto.com/id/975572398/photo/nigerian-akara-bean-cake-ready-to-serve.jpg?s=612x612&w=0&k=20&c=vOkP0kBsD_8g2ztbNfGd75zML-CXwE48pn3x-fmJ-hg="
            },
            {
                name: "Fried Plantain (Dodo)",
                desc: "Sweet, crispy fried ripe plantains – a versatile side dish or snack in Nigerian cuisine.",
                price: 700,
                img: "https://previews.123rf.com/images/osarieme/osarieme1805/osarieme180500064/101067843-nigerian-fried-plantain-dodo-in-plastic-container.jpg"
            },
            {
                name: "Pepper Soup",
                desc: "Spicy, aromatic soup made with goat meat, herbs, and hot peppers. Known for its medicinal qualities.",
                price: 1300,
                img: "https://thumbs.dreamstime.com/b/nigerian-pepper-soup-goat-meat-spicy-aromatic-broth-image-depicts-close-up-shot-showcasing-its-clear-flavorful-359973253.jpg"
            }
        ];

        // Load dishes from localStorage if available
        if (localStorage.getItem('dishes')) {
            dishes = JSON.parse(localStorage.getItem('dishes'));
        }

        let cart = [];
        
        function findItemInCart(name) {
            return cart.find(item => item.name === name);
        }

        function updateCart() {
            const cartItems = document.getElementById('cart-items');
            cartItems.innerHTML = '';
            let total = 0;
            cart.forEach(item => {
                const li = document.createElement('li');
                li.textContent = `${item.name} - ${item.quantity} x ₦${item.price} = ₦${item.quantity * item.price}`;
                cartItems.appendChild(li);
                total += item.quantity * item.price;
            });
            document.getElementById('total').textContent = `Total: ₦${total}`;
        }

        function renderDishes() {
            const menu = document.getElementById('menu');
            menu.innerHTML = '<h2 style="width: 100%; text-align: center;">Our Menu - African Dishes</h2>';
            dishes.forEach(dish => {
                const div = document.createElement('div');
                div.className = 'dish';
                div.innerHTML = `
                    <img src="${dish.img}" alt="${dish.name}">
                    <h3>${dish.name}</h3>
                    <p>${dish.desc}</p>
                    <p><strong>Price: ₦${dish.price}</strong></p>
                    <label>Quantity: </label><input type="number" class="quantity" min="1" value="1">
                    <button class="add-to-cart" data-name="${dish.name}" data-price="${dish.price}">Add to Cart</button>
                    <button class="order-now" onclick="window.location.href='tel:09168877122'">Order Now</button>
                `;
                menu.appendChild(div);
            });

            // Add event listeners to new buttons
            document.querySelectorAll('.add-to-cart').forEach(button => {
                button.addEventListener('click', () => {
                    const name = button.getAttribute('data-name');
                    const price = parseInt(button.getAttribute('data-price'));
                    const quantityInput = button.previousElementSibling;
                    const quantity = parseInt(quantityInput.value);
                    
                    if (quantity > 0) {
                        const existingItem = findItemInCart(name);
                        if (existingItem) {
                            existingItem.quantity += quantity;
                        } else {
                            cart.push({ name, price, quantity });
                        }
                        updateCart();
                        alert(`${quantity} x ${name} added to cart!`);
                        quantityInput.value = 1;
                    } else {
                        alert('Please select a valid quantity.');
                    }
                });
            });
        }

        // Admin functions
        function showAdminLogin() {
            document.getElementById('admin-login').style.display = 'block';
            document.getElementById('menu').style.display = 'none';
            document.getElementById('cart').style.display = 'none';
        }

        function loginAdmin() {
            const password = document.getElementById('admin-password').value;
            if (password === 'Odunlade1') { // Updated password
                document.getElementById('admin-login').style.display = 'none';
                document.getElementById('admin-dashboard').style.display = 'block';
                renderAdminDishes();
            } else {
                alert('Incorrect password');
            }
        }

        function logoutAdmin() {
            document.getElementById('admin-dashboard').style.display = 'none';
            document.getElementById('menu').style.display = 'block';
            document.getElementById('cart').style.display = 'block';
            renderDishes();
        }

        function renderAdminDishes() {
            const dishList = document.getElementById('dish-list');
            dishList.innerHTML = '';
            dishes.forEach((dish, index) => {
                const div = document.createElement('div');
                div.className = 'admin-dish';
                div.innerHTML = `
                    <input type="text" value="${dish.name}" data-index="${index}" class="edit-name">
                    <input type="text" value="${dish.desc}" data-index="${index}" class="edit-desc">
                    <input type="number" value="${dish.price}" data-index="${index}" class="edit-price">
                    <input type="text" value="${dish.img}" data-index="${index}" class="edit-img">
                    <button onclick="updateDish(${index})">Update</button>
                    <button onclick="removeDish(${index})">Remove</button>
                `;
                dishList.appendChild(div);
            });
        }

        function updateDish(index) {
            const name = document.querySelector(`.edit-name[data-index="${index}"]`).value;
            const desc = document.querySelector(`.edit-desc[data-index="${index}"]`).value;
            const price = parseInt(document.querySelector(`.edit-price[data-index="${index}"]`).value);
            const img = document.querySelector(`.edit-img[data-index="${index}"]`).value;
            
            dishes[index] = { name, desc, price, img };
            saveDishes();
            renderAdminDishes();
            alert('Dish updated!');
        }

        function removeDish(index) {
            if (confirm('Are you sure you want to remove this dish?')) {
                dishes.splice(index, 1);
                saveDishes();
                renderAdminDishes();
            }
        }

        function saveDishes() {
            localStorage.setItem('dishes', JSON.stringify(dishes));
        }

        // Add new dish
        document.getElementById('add-dish-form').addEventListener('submit', (e) => {
            e.preventDefault();
            const name = document.getElementById('new-name').value;
            const desc = document.getElementById('new-desc').value;
            const price = parseInt(document.getElementById('new-price').value);
            const img = document.getElementById('new-img').value;
            
            dishes.push({ name, desc, price, img });
            saveDishes();
            renderAdminDishes();
            alert('New dish added!');
            e.target.reset();
        });

        // Initial render
        renderDishes();
    </script>
</body>
</html>
