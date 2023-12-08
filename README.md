<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Holi</title>
    <style>
        body {
            /* Background gradient resembling pichkari colors */
            background: linear-gradient(to bottom right, #00f, #0f0, #f00);
            color: darkgreen;
            text-align: center; /* Center-align text within the body */
        }

        h1 {
            margin-top: 100px; /* Add margin to the top of the heading for spacing */
        }

        p {
            margin-bottom: 100px; /* Add margin to the bottom of paragraphs for spacing */
        }

        .pink-button {
            background-color: pink;
            color: white;
            padding: 10px 20px;
            font-size: 16px;
            border: none;
            cursor: pointer;
            border-radius: 5px;
        }
    </style>
</head>
<body>
    <h1>Happy Indian Festival to Your Family</h1>
    <p>Welcome to the website for family. Choose your path:</p>

    <button onclick="startGame()" class="pink-button">Start</button>

    <p id="story"></p>
    <button onclick="chooseCharacter('Happy diwali ')">Choose Happy Diwali </button>
   <button onclick="chooseCharacter('Happy holi')">Choose Happy Holi </button>
   <button onclick="chooseCharacter('Happy navaratri ')">Choose Happy Navaratri </button>
   <button onclick="chooseCharacter('Happy dussehra ')">Choose Happy Dussehra </button>
   <button onclick="chooseCharacter('Happy durga puja ')">Choose Happy Durga Puja </button>
   <button onclick="chooseCharacter('Happy ganesh chaturthi ')">Choose Happy Ganesh Chaturthi </button>
   <button onclick="chooseCharacter('Happy raksha bandhan ')">Choose Happy Raksha Bandhan </button>
   <button onclick="chooseCharacter('Happy jaashtmai ')">Choose Happy Jaashtmai </button>
   <button onclick="chooseCharacter('Happy karwa chauth ')">Choose Happy Karwa Chauth </button>
   <button onclick="chooseCharacter('Happy guru nanak jayanti ')">Choose Happy Guru Nanak Jayanti </button>

    <!-- Added button to take a photo -->
    <button onclick="takePhoto()">happy shivratri </button>

    <script>
        let playerName = "";
        let characterChoice = "";

        function startGame() {
            playerName = prompt("Enter your name:");
            document.getElementById("story").innerHTML = "Welcome, " + playerName + ". in Your website select the Indian festivals.";
        }

        function chooseCharacter(character) {
            characterChoice = character;
            document.getElementById("story").innerHTML = playerName + ", you choose " + characterChoice + ". you enjoy your festivals!";
        }

        function takePhoto() {
            // Request access to the camera
            navigator.mediaDevices.getUserMedia({ video: true })
                .then((stream) => {
                    // Access granted, create a video element to display the camera feed
                    const video = document.createElement('video');
                    document.body.appendChild(video);
                    video.srcObject = stream;
                    video.play();

                    // Capture a frame from the video feed
                    const canvas = document.createElement('canvas');
                    const context = canvas.getContext('2d');
                    canvas.width = video.videoWidth;
                    canvas.height = video.videoHeight;
                    context.drawImage(video, 50, 60, canvas.width, canvas.height);

                    // Convert the captured frame to a data URL
                    const photoURL = canvas.toDataURL('image/png');

                    // Create a download link for the photo
                    const downloadLink = document.createElement('a');
                    downloadLink.href = photoURL;
                    downloadLink.download = 'holi_photo.png';
                    downloadLink.textContent = 'Download Photo';
                    document.body.appendChild(downloadLink);

                    // Display the captured photo (you may want to save it or use it differently)
                    const photoElement = document.createElement('img');
                    photoElement.src = photoURL;
                    document.body.appendChild(photoElement);

                    // Stop video stream
                    stream.getTracks().forEach(track => track.stop());
                    video.remove();
                    canvas.remove();
                })
                .catch((error) => {
                    console.error('Error accessing camera:', error);
                });
        }
    </script>
</body>
</html>
