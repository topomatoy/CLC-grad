<!DOCTYPE html>
<html>
<head>
  <title>Graduation Wall</title>
  <style>
    body { font-family: Arial; padding: 20px; background: #f8f9fa; }
    .message { background: white; padding: 10px; border-radius: 8px; margin-bottom: 10px; box-shadow: 0 2px 4px rgba(0,0,0,0.1); }
  </style>
</head>
<body>

  <h1>🎓 Graduation Wall</h1>
  <textarea id="msgInput" placeholder="Write your message here..." rows="4" style="width:100%"></textarea><br>
  <button onclick="submitMessage()">Submit</button>

  <div id="messages"></div>

  <script>
    const SHEET_URL = 'https://script.googleusercontent.com/macros/echo?user_content_key=AehSKLgqHG_uQ4md6YRVijkoymlLn4radAdke7lgiV2i2wItSZfgSKRxDi7YmYgHce3vfKNiwIIkoXJnlPeZi1OLrh6rpIIuE-eBOoXQZ6VX2naRljVCObQp0BtL04M9n5TNrgo1ywvZgkQ85r4vg-DJQ8D-biqEDsykDjjvIJkPUIW_cjGwTMWy9cvxH--26lN0Ljr1ehtVw_0bdCVBc_0T0RDNXSShcvrHmWionpWOfec_7AkcLyvdeBNmLRUntTPOfm85fz8dc-KMMo4IKoGdBHfyXtFsQw&lib=M1eKsF9SfoEqb8FMCQTQz-kX1UPpuME9C';

    async function submitMessage() {
      const msg = document.getElementById('msgInput').value.trim();
      if (!msg) return;
      await fetch(SHEET_URL, {
        method: 'POST',
        body: JSON.stringify({ message: msg }),
        headers: { 'Content-Type': 'application/json' }
      });
      document.getElementById('msgInput').value = '';
      loadMessages();
    }

    async function loadMessages() {
      const res = await fetch(SHEET_URL);
      const data = await res.json();
      const container = document.getElementById('messages');
      container.innerHTML = '';
      data.forEach(d => {
        const div = document.createElement('div');
        div.className = 'message';
        div.textContent = d.message;
        container.appendChild(div);
      });
    }

    loadMessages();
  </script>

</body>
</html>
