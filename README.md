# website

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/css/bootstrap.min.css" rel="stylesheet">
    <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
    <title>TasteBud Express</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background-color: #f8f9fa;
        }
        .section { display: none; }
        .active { display: block; }
        .hero {
            background-image: url('https://example.com/hero-image.jpg'); /* Replace with a real image URL */
            background-size: cover;
            background-position: center;
            height: 400px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.7);
        }
        footer {
            background-color: #343a40;
            color: white;
        }
        .navbar-brand {
            font-size: 1.5rem;
        }
        .card img {
            height: 200px;
            object-fit: cover;
        }
    </style>
    <script>
        function showSection(sectionId) {
            const sections = document.querySelectorAll('.section');
            sections.forEach(section => section.classList.remove('active'));
            document.getElementById(sectionId).classList.add('active');
        }

        function saveData(event) {
            event.preventDefault();
            const name = document.getElementById('name').value;
            const email = document.getElementById('email').value;
            const message = document.getElementById('message').value;

            let contactData = JSON.parse(localStorage.getItem('contactData')) || [];
            contactData.push({ name, email, message });
            localStorage.setItem('contactData', JSON.stringify(contactData));
            alert('Your query has been submitted!');
            document.getElementById('contactForm').reset();
        }

        window.onload = function() {
            const data = JSON.parse(localStorage.getItem('contactData')) || [];
            const tableBody = document.getElementById('data-table-body');
            data.forEach(item => {
                const row = `<tr>
                    <td>${item.name}</td>
                    <td>${item.email}</td>
                    <td>${item.message}</td>
                </tr>`;
                tableBody.innerHTML += row;
            });
            showSection('home'); // Show home section on load
        };
    </script>
</head>
<body>
    <header class="bg-light p-3">
        <nav class="navbar navbar-expand-lg">
            <a class="navbar-brand" href="javascript:void(0);" onclick="showSection('home')">TasteBud Express</a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarNav">
                <ul class="navbar-nav ml-auto">
                    <li class="nav-item"><a class="nav-link" href="javascript:void(0);" onclick="showSection('home')">Home</a></li>
                    <li class="nav-item"><a class="nav-link" href="javascript:void(0);" onclick="showSection('about')">About</a></li>
                    <li class="nav-item"><a class="nav-link" href="javascript:void(0);" onclick="showSection('contact')">Contact</a></li>
                    <li class="nav-item"><a class="nav-link" href="javascript:void(0);" onclick="showSection('queries')">Queries</a></li>
                </ul>
            </div>
        </nav>
    </header>

    <!-- Home Section -->
    <section id="home" class="section active">
        <div class="hero">
            <div class="text-center">
                <h1 class="display-4">Welcome to TasteBud Express</h1>
                <p class="lead">Delicious meals delivered fast to your doorstep!</p>
                <a href="javascript:void(0);" onclick="showSection('contact')" class="btn btn-primary btn-lg">Order Now</a>
            </div>
        </div>
        <div class="container mt-5">
            <h2>Our Popular Dishes</h2>
            <div class="row">
                <div class="col-md-4">
                    <div class="card mb-4">
                        <img src="https://example.com/dish1.jpg" class="card-img-top" alt="Dish 1"> <!-- Replace with real image URL -->
                        <div class="card-body">
                            <h5 class="card-title">Spaghetti Carbonara</h5>
                            <p class="card-text">Creamy pasta with pancetta and parmesan.</p>
                        </div>
                    </div>
                </div>
                <div class="col-md-4">
                    <div class="card mb-4">
                        <img src="https://example.com/dish2.jpg" class="card-img-top" alt="Dish 2"> <!-- Replace with real image URL -->
                        <div class="card-body">
                            <h5 class="card-title">Margherita Pizza</h5>
                            <p class="card-text">Classic pizza topped with fresh basil and mozzarella.</p>
                        </div>
                    </div>
                </div>
                <div class="col-md-4">
                    <div class="card mb-4">
                        <img src="https://example.com/dish3.jpg" class="card-img-top" alt="Dish 3"> <!-- Replace with real image URL -->
                        <div class="card-body">
                            <h5 class="card-title">Caesar Salad</h5>
                            <p class="card-text">Crisp romaine lettuce with Caesar dressing.</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- About Section -->
    <section id="about" class="section">
        <div class="container mt-5">
            <h2>About Us</h2>
            <p>TasteBud Express is your go-to solution for quick and tasty meals. We partner with local restaurants to bring you a variety of dishes right to your door, ensuring freshness and quality. Our mission is to satisfy your cravings and make meal times delightful.</p>
        </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="section">
        <div class="container mt-5">
            <h2>Contact Us</h2>
            <form id="contactForm" onsubmit="saveData(event)">
                <div class="mb-3">
                    <label for="name" class="form-label">Name</label>
                    <input type="text" class="form-control" id="name" required>
                </div>
                <div class="mb-3">
                    <label for="email" class="form-label">Email</label>
                    <input type="email" class="form-control" id="email" required>
                </div>
                <div class="mb-3">
                    <label for="message" class="form-label">Message</label>
                    <textarea class="form-control" id="message" rows="3" required></textarea>
                </div>
                <button type="submit" class="btn btn-primary">Submit</button>
            </form>
        </div>
    </section>

    <!-- Queries Section -->
    <section id="queries" class="section">
        <div class="container mt-5">
            <h2>Saved Queries</h2>
            <table class="table table-bordered">
                <thead>
                    <tr>
                        <th>Name</th>
                        <th>Email</th>
                        <th>Message</th>
                    </tr>
                </thead>
                <tbody id="data-table-body">
                    <!-- Data will be populated here -->
                </tbody>
            </table>
        </div>
    </section>

    <footer class="p-3 text-center">
        <p>&copy; 2024 TasteBud Express</p>
    </footer>
</body>
</html>
