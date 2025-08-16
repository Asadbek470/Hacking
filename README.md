# Hacking
Hacking
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Hacking </title>
  <style>
    body {
      font-family: Arial, sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      background: #f3f3f3;
    }
    .container {
      background: #fff;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0px 4px 10px rgba(0,0,0,0.2);
      width: 300px;
      text-align: center;
    }
    input {
      width: 90%;
      padding: 10px;
      margin: 8px 0;
      border: 1px solid #ccc;
      border-radius: 5px;
    }
    button {
      width: 90%;
      padding: 10px;
      margin: 8px 0;
      border: none;
      border-radius: 5px;
      background: #007BFF;
      color: #fff;
      font-size: 16px;
      cursor: pointer;
    }
    button:hover {
      background: #0056b3;
    }
    .hidden {
      display: none;
    }
  </style>
</head>
<body>  
  <h1></h1>
  <div class="container" id="authContainer">
    <h2 id="title">Register</h2>
    <input type="text" id="username" placeholder="Username">
    <input type="password" id="password" placeholder="Password">
    <button onclick="register()" id="registerBtn">Register</button>
    <button onclick="login()" id="loginBtn" class="hidden">Login</button>
  </div>

  <div class="container hidden" id="mainContainer">
    <h2>Welcome, <span id="userDisplay"></span>!</h2>
    <button onclick="openTelegramDelete()">Open Telegram Delete</button>
    <button onclick="logout()">Logout</button>
  </div>

  <script>
    const authContainer = document.getElementById("authContainer");
    const mainContainer = document.getElementById("mainContainer");
    const userDisplay = document.getElementById("userDisplay");

    // Check if already registered
    window.onload = () => {
      const user = localStorage.getItem("username");
      if (user) {
        showMain(user);
      } else {
        showAuth();
      }
    };

    function register() {
      const username = document.getElementById("username").value;
      const password = document.getElementById("password").value;

      if (!username || !password) {
        alert("Please fill in both fields!");
        return;
      }

      localStorage.setItem("username", username);
      localStorage.setItem("password", password);
      showMain(username);
    }

    function login() {
      const username = document.getElementById("username").value;
      const password = document.getElementById("password").value;

      if (
        username === localStorage.getItem("username") &&
        password === localStorage.getItem("password")
      ) {
        showMain(username);
      } else {
        alert("Incorrect username or password!");
      }
    }

    function showMain(username) {
      authContainer.classList.add("hidden");
      mainContainer.classList.remove("hidden");
      userDisplay.textContent = username;
    }

    function showAuth() {
      authContainer.classList.remove("hidden");
      mainContainer.classList.add("hidden");
    }

    function openTelegramDelete() {
      // Открывает официальную страницу удаления аккаунта Telegram
      window.open("https://my.telegram.org/auth?to=delete", "_blank");
    }

    function logout() {
      localStorage.removeItem("username");
      localStorage.removeItem("password");
      showAuth();
    }
  </script>
</body>
</html>

