<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Sign Up - KANTO CLOSET</title>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <style>
    body { font-family: Arial, sans-serif; background: #f4f4f4; padding: 20px; }
    form { max-width: 400px; margin: auto; background: #fff; padding: 20px; border-radius: 10px; box-shadow: 0 0 10px #ccc; }
    input, button { width: 100%; padding: 10px; margin-top: 10px; border-radius: 6px; border: 1px solid #ccc; }
    button { background: green; color: white; border: none; cursor: pointer; }
    h2 { text-align: center; }
  </style>
</head>
<body>
  <form id="signupForm">
    <h2>Create Account</h2>
    <input type="text" id="name" placeholder="Full Name" required>
    <input type="email" id="email" placeholder="Email Address" required>
    <input type="password" id="password" placeholder="Password" required>
    <button type="submit">Sign Up</button>
    <p style="text-align:center;"><a href="login.html">Already have an account? Log in</a></p>
  </form>

  <script>
    document.getElementById('signupForm').addEventListener('submit', function(e) {
      e.preventDefault();
      const name = document.getElementById('name').value;
      const email = document.getElementById('email').value;
      const password = document.getElementById('password').value;

      const users = JSON.parse(localStorage.getItem('users') || '[]');
      const exists = users.find(u => u.email === email);
      if (exists) {
        alert("Email already registered!");
        return;
      }

      users.push({ name, email, password });
      localStorage.setItem('users', JSON.stringify(users));
      alert("Signup successful! Please login.");
      window.location.href = 'login.html';
    });
  </script>
</body>
</html>
