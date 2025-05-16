<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Graduation Thoughts 2025</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f8f9fa;
      padding: 20px;
    }
    h1 {
      text-align: center;
    }
    #messageForm {
      max-width: 500px;
      margin: 0 auto 20px;
      background: white;
      padding: 15px;
      border-radius: 10px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.1);
    }
    textarea {
      width: 100%;
      height: 100px;
      padding: 10px;
      margin-bottom: 10px;
      resize: none;
    }
    button {
      width: 100%;
      padding: 10px;
      background: #007BFF;
      color: white;
      border: none;
      border-radius: 5px;
    }
    #messages {
      max-width: 600px;
      margin: 0 auto;
    }
    .message {
      background: white;
      padding: 15px;
      margin: 10px 0;
      border-radius: 10px;
      box-shadow: 0 1px 5px rgba(0,0,0,0.1);
    }
  </style>
</head>
<body>

  <h1>🎓 Graduation Thoughts 2025 🎉</h1>

  <div id="messageForm">
    <textarea id="messageInput" placeholder="Write your message here..."></textarea>
    <button onclick="addMessage()">Submit Message</button>
  </div>

  <div id="messages"></div>

  <script>
    const messagesDiv = document.getElementById('messages');

    function addMessage() {
      const text = document.getElementById('messageInput').value.trim();
      if (text === '') return;

      const message = document.createElement('div');
      message.className = 'message';
      message.textContent = text;
      messagesDiv.prepend(message);

      document.getElementById('messageInput').value = '';
    }
  </script>

</body>
</html>
