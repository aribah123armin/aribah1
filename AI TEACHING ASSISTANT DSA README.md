<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AI Teaching Assistant for DSA</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f9;
            margin: 0;
            padding: 20px;
        }

        .container {
            width: 100%;
            max-width: 800px;
            margin: 0 auto;
            background-color: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }

        h1 {
            text-align: center;
            color: #333;
        }

        .chat-box {
            border: 1px solid #ddd;
            padding: 10px;
            height: 400px;
            overflow-y: auto;
            background-color: #f9f9f9;
            border-radius: 8px;
        }

        .message {
            margin: 10px 0;
            padding: 10px;
            border-radius: 8px;
            width: fit-content;
        }

        .assistant {
            background-color: #d1ecf1;
            align-self: flex-start;
        }

        .student {
            background-color: #f1d1d1;
            align-self: flex-end;
        }

        .input-section {
            margin-top: 20px;
            display: flex;
            justify-content: space-between;
        }

        input[type="text"] {
            width: 80%;
            padding: 10px;
            border-radius: 8px;
            border: 1px solid #ddd;
        }

        button {
            padding: 10px 20px;
            border: none;
            background-color: #007bff;
            color: white;
            border-radius: 8px;
            cursor: pointer;
        }

        button:hover {
            background-color: #0056b3;
        }

        .question {
            font-weight: bold;
        }
    </style>
</head>
<body>

    <div class="container">
        <h1>AI Teaching Assistant for DSA</h1>
        <div class="chat-box" id="chatBox">
            <div class="message assistant">
                <div class="question">Assistant:</div> 
                <p>Welcome! Let's learn about Data Structures and Algorithms. What do you want to focus on today?</p>
            </div>
        </div>
        
        <div class="input-section">
            <input type="text" id="studentInput" placeholder="Type your message here...">
            <button onclick="handleStudentMessage()">Send</button>
        </div>
    </div>

    <script>
        const chatBox = document.getElementById('chatBox');
        const studentInput = document.getElementById('studentInput');

        // Array of sample Socratic questions to guide the learning process
        const socraticQuestions = [
            "What do you think is different about this test case compared to others that passed?",
            "Can you explain how your algorithm processes this input?",
            "What part of the code do you think is responsible for the timeout?",
            "Have you considered the time complexity of your algorithm?",
            "How does your data structure affect the efficiency of your solution?",
            "What could be optimized in the section of the code you identified?"
        ];

        // Function to handle student message and respond with a Socratic question
        function handleStudentMessage() {
            const studentMessage = studentInput.value;
            if (studentMessage.trim() === "") return;

            // Add student's message to the chat box
            const studentMessageElement = document.createElement('div');
            studentMessageElement.classList.add('message', 'student');
            studentMessageElement.innerHTML = `<div class="question">Student:</div><p>${studentMessage}</p>`;
            chatBox.appendChild(studentMessageElement);

            // Scroll to the bottom of the chat box
            chatBox.scrollTop = chatBox.scrollHeight;

            // Clear the input field
            studentInput.value = "";

            // Get a random Socratic question from the array
            const assistantQuestion = socraticQuestions[Math.floor(Math.random() * socraticQuestions.length)];

            // Respond with a Socratic question
            setTimeout(() => {
                const assistantMessageElement = document.createElement('div');
                assistantMessageElement.classList.add('message', 'assistant');
                assistantMessageElement.innerHTML = `<div class="question">Assistant:</div><p>${assistantQuestion}</p>`;
                chatBox.appendChild(assistantMessageElement);

                // Scroll to the bottom of the chat box
                chatBox.scrollTop = chatBox.scrollHeight;
            }, 1000);  // Simulate a 1-second delay for the AI response
        }
    </script>

</body>
</html>
