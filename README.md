# CSS3 Transitions, Animations, and Advanced JavaScript Functions

## Objectives

Create smooth CSS transitions and animations.
Use JavaScript functions for dynamic behavior.
Implement local storage for data persistence.

## Instructions
Add CSS animations to elements like buttons or images.

>[!NOTE]
> - Write a JavaScript function that:
> - Stores and retrieves user preferences using localStorage.
> - Implements an animation triggered by user actions.

## Tasks

Create a CSS animation.
Store data in localStorage.
Apply JavaScript to trigger animations.

Happy Coding! 💻✨


<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>CSS Transitions and Local Storage</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <div class="container">
    <h1>Welcome to CSS3 Animations!</h1>
    <button id="animate-btn">Click Me</button>
    <p id="message"></p>
  </div>

  <script src="script.js"></script>
</body>
</html>



body {
  font-family: Arial, sans-serif;
  text-align: center;
  margin: 0;
  padding: 0;
  background-color: #f4f4f4;
}

.container {
  padding: 50px;
}

button {
  padding: 10px 20px;
  font-size: 16px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease, transform 0.2s ease;
}

button:hover {
  background-color: #0056b3;
  transform: scale(1.1);
}

@keyframes button-click {
  0% {
    transform: scale(1);
    background-color: #007bff;
  }
  50% {
    transform: scale(1.2);
    background-color: #28a745;
  }
  100% {
    transform: scale(1);
    background-color: #007bff;
  }
}




// Function to animate the button
function triggerAnimation(button) {
  button.style.animation = "button-click 0.5s ease";
  
  // Remove animation after it completes
  button.addEventListener("animationend", () => {
    button.style.animation = "";
  });
}

// Function to store user preference
function storePreference(key, value) {
  localStorage.setItem(key, value);
}

// Function to retrieve user preference
function getPreference(key) {
  return localStorage.getItem(key);
}

// Add event listener to button
const button = document.getElementById("animate-btn");
const message = document.getElementById("message");

button.addEventListener("click", () => {
  // Trigger the animation
  triggerAnimation(button);
  
  // Store user action
  storePreference("lastAction", "Button clicked!");
  
  // Display the retrieved message
  const storedMessage = getPreference("lastAction");
  message.textContent = storedMessage;
});
