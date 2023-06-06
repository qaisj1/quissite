<!DOCTYPE html>
<html>
  <head>
    <style>
      body {
        font-family: Arial, sans-serif;
        text-align: center;
      }

      h1 {
        color: #333;
      }

      .container {
        margin-top: 50px;
      }

      .password-input {
        margin-bottom: 20px;
      }

      .button {
        padding: 10px 20px;
        background-color: #4CAF50;
        color: #fff;
        border: none;
        cursor: pointer;
      }

      .password-output {
        font-weight: bold;
        font-size: 20px;
      }
    </style>
  </head>
  <body>
    <h1>Random Password Generator</h1>
    <div class="container">
      <div class="password-input">
        <label for="length">Password Length:</label>
        <input type="number" id="length" min="1" max="20" value="8">
      </div>
      <button class="button" onclick="generatePassword()">Generate Password</button>
      <div class="password-output" id="passwordOutput"></div>
    </div>

    <script>
      function generatePassword() {
        var characters =
          'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789!@#$%^&*';
        var lengthInput = document.getElementById('length');
        var length = parseInt(lengthInput.value);
        var password = '';

        for (var i = 0; i < length; i++) {
          var randomIndex = Math.floor(Math.random() * characters.length);
          password += characters.charAt(randomIndex);
        }

        var passwordOutput = document.getElementById('passwordOutput');
        passwordOutput.textContent = 'Generated Password: ' + password;
      }
    </script>
  </body>
</html>
