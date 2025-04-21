# Salon-Urody-Kobiet
from flask import Flask, render_template, request, redirect, url_for

app = Flask(__name__)

@app.route("/")
def home():
    return render_template("index.html")

@app.route("/kontakt", methods=["POST"])
def kontakt():
    name = request.form.get("name")
    email = request.form.get("email")
    message = request.form.get("message")
    print(f"Nowa wiadomość od {name} <{email}>: {message}")
    return redirect(url_for("home"))

if __name__ == "__main__":
    app.run(debug=True)
<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <title>Studio Urody Kobiet</title>
    <link rel="stylesheet" href="{{ url_for('static', filename='style.css') }}">
</head>
<body>
    <header class="hero">
        <h1>Studio Urody Kobiet</h1>
        <p>Luksus w każdym dotyku</p>
        <button onclick="scrollToSection('services')">Poznaj ofertę</button>
    </header>

    <section id="services">
        <h2>Nasze Usługi</h2>
        <div class="service">
            <h3>Pielęgnacja twarzy</h3>
            <p>Profesjonalne zabiegi na każdą cerę.</p>
        </div>
        <div class="service">
            <h3>Stylizacja paznokci</h3>
            <p>Klasa, trwałość i estetyka.</p>
        </div>
        <div class="service">
            <h3>Masaże relaksacyjne</h3>
            <p>Odzyskaj harmonię ciała i ducha.</p>
        </div>
    </section>

    <section id="contact">
        <h2>Kontakt</h2>
        <form action="/kontakt" method="post" class="contact-form">
            <input type="text" name="name" placeholder="Twoje imię" required>
            <input type="email" name="email" placeholder="Twój email" required>
            <textarea name="message" rows="5" placeholder="Wiadomość..." required></textarea>
            <button type="submit">Wyślij</button>
        </form>
    </section>

    <footer>
        <p>&copy; 2025 Studio Urody Kobiet. Wszystkie prawa zastrzeżone.</p>
    </footer>

    <script>
        function scrollToSection(id) {
            document.getElementById(id).scrollIntoView({ behavior: \"smooth\" });
        }
    </script>
</body>
</html>
body {
    margin: 0;
    font-family: 'Helvetica Neue', sans-serif;
    background-color: #fff;
    color: #000;
}

.hero {
    background-color: #000;
    color: #fff;
    text-align: center;
    padding: 100px 20px;
}

.hero h1 {
    font-size: 3rem;
    margin-bottom: 10px;
    letter-spacing: 2px;
}

.hero p {
    font-size: 1.5rem;
    margin-bottom: 30px;
}

.hero button {
    padding: 12px 30px;
    font-size: 1rem;
    background: #fff;
    color: #000;
    border: none;
    cursor: pointer;
    transition: background 0.3s ease;
    border-radius: 6px;
}

.hero button:hover {
    background: #ddd;
}

section {
    padding: 80px 20px;
    text-align: center;
}

section h2 {
    font-size: 2rem;
    margin-bottom: 40px;
}

.service {
    margin: 30px auto;
    max-width: 600px;
    padding: 20px;
    border-bottom: 1px solid #ccc;
}

.contact-form {
    max-width: 600px;
    margin: 0 auto;
    display: flex;
    flex-direction: column;
    gap: 15px;
}

.contact-form input,
.contact-form textarea {
    padding: 12px;
    font-size: 1rem;
    border: 1px solid #000;
    border-radius: 4px;
    background: #fff;
    color: #000;
}

.contact-form button {
    padding: 12px;
    font-size: 1rem;
    background: #000;
    color: #fff;
    border: none;
    cursor: pointer;
    border-radius: 6px;
    transition: background 0.3s ease;
}

.contact-form button:hover {
    background: #333;
}

footer {
    background-color: #000;
    color: #fff;
    text-align: center;
    padding: 20px;
    font-size: 0.9rem;
}
