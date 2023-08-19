# code_alpha_captcha_generator
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>CAPTCHA Validator</title>
<style>
  body {
    font-family: Arial, sans-serif;
    text-align: center;
    background-color: rgb(49, 43, 43);
  }
  #captcha-box {
    margin: 20px auto;
    padding: 10px;
    border: 1px solid #d19494;
    max-width: 300px;
    background-color: rgb(111, 111, 192);
  }
</style>
</head>
<body>
  <h1 aria-setsize="bold" style="color: aliceblue;">CAPTCHA Validator</h1>
  <div id="captcha-box">
    <p style="color:rgb(247, 244, 245) ;" aria-setsize="bold">Prove you're not a robot:</p>
    <p><span id="captcha-text"></span></p>
    <input type="text" id="captcha-input" placeholder="Enter CAPTCHA" >
    <button id="verify-btn" style="color: rgb(4, 71, 71);" aria-setsize="bold">Verify</button>
    <p id="result"></p>
  </div>

  <script>
    // Generate a random CAPTCHA string
    function generateCaptcha() {
      const chars = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789';
      let captcha = '';
      for (let i = 0; i < 6; i++) {
        captcha += chars[Math.floor(Math.random() * chars.length)];
      }
      return captcha;
    }

    // Initialize CAPTCHA and set the text
    function initializeCaptcha() {
      const captchaText = generateCaptcha();
      document.getElementById('captcha-text').textContent = captchaText;
    }

    // Verify the entered CAPTCHA
    function verifyCaptcha() {
      const captchaInput = document.getElementById('captcha-input').value;
      const captchaText = document.getElementById('captcha-text').textContent;
      const resultElement = document.getElementById('result');
      
      if (captchaInput === captchaText) {
        resultElement.textContent = 'CAPTCHA verified!';
        resultElement.style.color = ' yellow';
      } else {
        resultElement.textContent = 'CAPTCHA incorrect. Please try again.';
        resultElement.style.color = 'brown';
      }
      
      // Refresh CAPTCHA after verification
      initializeCaptcha();
    }

    // Initialize CAPTCHA when the page loads
    window.onload = function() {
      initializeCaptcha();
      const verifyButton = document.getElementById('verify-btn');
      verifyButton.addEventListener('click', verifyCaptcha);
    };
  </script>
</body>
</html>
