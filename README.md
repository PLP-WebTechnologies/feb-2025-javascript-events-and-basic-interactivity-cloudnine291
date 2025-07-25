index.html

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>JS Event Playground</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>
  <header>
    <h1>Interactive Page</h1>
  </header>

  <section>
    <button id="changeBtn">Click Me</button>
    <p id="textChange">This text will change</p>
  </section>

  <section id="gallery">
    <img src="https://via.placeholder.com/200" alt="Image 1" id="galleryImg" />
    <button id="nextImg">Next Image</button>
  </section>

  <section>
    <form id="userForm">
      <input type="text" id="name" placeholder="Name" required />
      <input type="email" id="email" placeholder="Email" required />
      <input type="password" id="password" placeholder="Password" required />
      <button type="submit">Submit</button>
      <p id="formMsg"></p>
    </form>
  </section>

  <script src="script.js"></script>
</body>
</html>

styles.css
body {
  font-family: sans-serif;
  padding: 20px;
}

button {
  margin: 10px 0;
  padding: 8px 16px;
  cursor: pointer;
}

img {
  width: 200px;
  height: auto;
  display: block;
  margin-bottom: 10px;
}


script.js
// Button click to change text
document.getElementById("changeBtn").addEventListener("click", () => {
  const text = document.getElementById("textChange");
  text.textContent = "You clicked the button!";
  text.style.color = "blue";
});

// Hover effect
const changeBtn = document.getElementById("changeBtn");
changeBtn.addEventListener("mouseover", () => {
  changeBtn.style.backgroundColor = "lightgreen";
});
changeBtn.addEventListener("mouseout", () => {
  changeBtn.style.backgroundColor = "";
});

// Keypress detection
document.addEventListener("keydown", (e) => {
  if (e.key === "Enter") {
    alert("Enter key pressed");
  }
});

// Double-click secret action
changeBtn.addEventListener("dblclick", () => {
  alert("🎉 Secret double-click unlocked!");
});

// Image gallery
const galleryImages = [
  "https://via.placeholder.com/200?text=Image+1",
  "https://via.placeholder.com/200?text=Image+2",
  "https://via.placeholder.com/200?text=Image+3",
];
let currentImg = 0;

document.getElementById("nextImg").addEventListener("click", () => {
  currentImg = (currentImg + 1) % galleryImages.length;
  document.getElementById("galleryImg").src = galleryImages[currentImg];
});

// Form validation
document.getElementById("userForm").addEventListener("submit", function (e) {
  e.preventDefault();

  const email = document.getElementById("email").value;
  const password = document.getElementById("password").value;
  const msg = document.getElementById("formMsg");

  if (!email.includes("@")) {
    msg.textContent = "Please enter a valid email.";
    msg.style.color = "red";
    return;
  }

  if (password.length < 8) {
    msg.textContent = "Password must be at least 8 characters.";
    msg.style.color = "red";
    return;
  }

  msg.textContent = "Form submitted successfully!";
  msg.style.color = "green";
});



