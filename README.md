<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>FabrIA</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            background-color: #f4f4f4;
        }
        .chat-container {
            width: 300px;
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            text-align: center;
        }
        .chat-box {
            height: 200px;
            overflow-y: auto;
            border-bottom: 1px solid #ccc;
            margin-bottom: 10px;
            padding: 5px;
            text-align: left;
        }
        .input-container {
            display: flex;
            gap: 5px;
        }
        .user-input {
            flex: 1;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        .send-button {
            padding: 10px;
            background-color: #007bff;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        .send-button:hover {
            background-color: #0056b3;
        }
        h1 {
            margin: 0;
        }
        h2 {
            margin: 5px 0 15px;
            font-size: 14px;
            color: gray;
        }
    </style>
</head>
<body>
    <div class="chat-container">
        <h1>FabrIA</h1>
        <h2>versión 0.0.1.F1</h2>
        <div class="chat-box" id="chat-box"></div>
        <div class="input-container">
            <input type="text" id="user-input" class="user-input" placeholder="Escribe un mensaje...">
            <button class="send-button" onclick="sendMessage()">Enviar</button>
        </div>
    </div>
    <script>
        function sendMessage() {
            let userInput = document.getElementById("user-input").value;
            let chatBox = document.getElementById("chat-box");
            if (userInput.trim() === "") return;
            
            chatBox.innerHTML += `<div><strong>Tu:</strong> ${userInput}</div>`;
            document.getElementById("user-input").value = "";
            
            setTimeout(() => {
                let botResponse = getBotResponse(userInput);
                chatBox.innerHTML += `<div><strong>FabrIA:</strong> ${botResponse}</div>`;
                chatBox.scrollTop = chatBox.scrollHeight;
            }, 500);
        }
        
        function getBotResponse(input) {
            let responses = {
                "hola": "¡Hola! ¿Cómo puedo ayudarte?",
                "¿cómo estás?": "Estoy bien, gracias por preguntar.",
                "adiós": "Hasta luego. ¡Que tengas un buen día!",
                "quien es la novia de fabrix": "Su novia es norgelis, una venezolana ¿puedo ayudarte en algo más?",
                "fabri me quiere": "Mija, él te quiere como no te lo imaginas.",
                "¿quien es mi pastelito?": "Es Fabri."
            };
            return responses[input.toLowerCase()] || "Lo siento, no entiendo esa pregunta.espera a que fabrix me actualice";
        }
    </script>
</body>
</html>
