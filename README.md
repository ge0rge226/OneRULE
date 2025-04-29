<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Thread Weavers</title>
  <style>
    body {
      height: 100vh;
      margin: 0;
      display: flex;
      justify-content: center;
      align-items: center;
      background: #f4f4f4;
      overflow: hidden;
      font-family: sans-serif;
    }

    .center {
      position: relative;
      text-align: center;
    }

    h1 {
      font-size: 1.5rem;
      margin-bottom: 10px;
    }

    form {
      margin-bottom: 20px;
    }

    input[type="text"] {
      padding: 8px;
      width: 250px;
      font-size: 1rem;
    }

    .responses {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
    }

    .bubble {
      position: absolute;
      background: #ffffff;
      border: 1px solid #ccc;
      padding: 8px 12px;
      border-radius: 20px;
      font-size: 0.9rem;
      max-width: 200px;
      word-break: break-word;
    }
  </style>
</head>
<body>

<div class="center">
  <h1>What thread would you add to the world?</h1>
  <form id="responseForm">
    <input type="text" id="responseInput" placeholder="Type your answer..." required>
  </form>
  <div class="responses" id="responsesContainer"></div>
</div>

<script>
  const form = document.getElementById('responseForm');
  const input = document.getElementById('responseInput');
  const container = document.getElementById('responsesContainer');

  form.addEventListener('submit', function(event) {
    event.preventDefault();
    const text = input.value.trim();
    if (text) {
      const bubble = document.createElement('div');
      bubble.className = 'bubble';
      bubble.innerText = text;

      // Random position around center
      const angle = Math.random() * 2 * Math.PI;
      const radius = 100 + Math.random() * 150; // distance from center
      bubble.style.top = `${Math.sin(angle) * radius}px`;
      bubble.style.left = `${Math.cos(angle) * radius}px`;

      container.appendChild(bubble);
      input.value = '';
    }
  });
</script>

</body>
</html>
