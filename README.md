<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Health AI Assistant</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background: #f0f8ff;
      margin: 0;
      padding: 0;
    }
    .container {
      max-width: 700px;
      margin: 40px auto;
      background: white;
      border-radius: 10px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
    }
    .header {
      background: #28a745;
      color: white;
      text-align: center;
      padding: 20px;
      font-size: 1.6em;
      font-weight: bold;
    }
    .chat-box {
      height: 500px;
      overflow-y: auto;
      padding: 20px;
      border-bottom: 1px solid #ccc;
    }
    .message {
      margin: 12px 0;
      padding: 10px;
      border-radius: 10px;
      max-width: 80%;
    }
    .user {
      background: #d1ecf1;
      text-align: right;
      margin-left: auto;
    }
    .bot {
      background: #e2f0cb;
      text-align: left;
      margin-right: auto;
    }
    .input-area {
      display: flex;
      border-top: 1px solid #ccc;
    }
    .input-area input {
      flex: 1;
      padding: 15px;
      border: none;
      font-size: 1em;
    }
    .input-area button {
      padding: 15px 20px;
      background: #28a745;
      color: white;
      border: none;
      cursor: pointer;
    }
    .input-area button:hover {
      background: #218838;
    }
  </style>
</head>
<body>

<div class="container">
  <div class="header">Health AI Assistant</div>
  <div class="chat-box" id="chatBox"></div>
  <div class="input-area">
    <input type="text" id="userInput" placeholder="Ask me any health-related question..." />
    <button onclick="sendMessage()">Send</button>
  </div>
</div>

<script>
  function sendMessage() {
    const input = document.getElementById("userInput");
    const message = input.value.trim();
    if (!message) return;

    appendMessage("You", message, "user");

    const reply = getBotReply(message);
    setTimeout(() => {
      appendMessage("Assistant", reply, "bot");
      document.getElementById("chatBox").scrollTop = chatBox.scrollHeight;
    }, 500);

    input.value = "";
  }

  function appendMessage(sender, message, type) {
    const chatBox = document.getElementById("chatBox");
    const msgDiv = document.createElement("div");
    msgDiv.className = `message ${type}`;
    msgDiv.innerHTML = `<strong>${sender}:</strong> ${message}`;
    chatBox.appendChild(msgDiv);
  }

  function getBotReply(message) {
    const msg = message.toLowerCase();
    if (msg.includes("fever")) return "You may have a viral infection. Stay hydrated, rest, and monitor your temperature. Consult a doctor if it persists.";
    if (msg.includes("headache")) return "A headache can have many causes. Try resting, drinking water, and reducing screen time.";
    if (msg.includes("covid")) return "For COVID-19, isolate, monitor symptoms, and get tested. Contact local health services if needed.";
    if (msg.includes("cold") || msg.includes("cough")) return "Rest, drink warm fluids, and use a humidifier. Seek medical help if symptoms get worse.";
    if (msg.includes("diabetes")) return "Manage blood sugar with a healthy diet, regular exercise, and medication if prescribed.";
    if (msg.includes("heart")) return "Heart issues require professional care. Monitor symptoms like chest pain or shortness of breath and seek immediate help if needed.";
    if (msg.includes("mental health") || msg.includes("depression")) return "You're not alone. Reach out to a mental health professional or talk to someone you trust.";
    return "I'm here to assist with general health questions. Please provide more details.";
  }
</script>

</body>
</html>
