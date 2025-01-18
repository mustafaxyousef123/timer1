<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Web Timer</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
      background-color: #f4f4f9;
    }
    .timer {
      text-align: center;
      background: #fff;
      padding: 20px 40px;
      border-radius: 10px;
      box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
    }
    .timer-display {
      font-size: 3em;
      font-weight: bold;
      margin-bottom: 20px;
      color: #333;
    }
    .timer-buttons {
      display: flex;
      gap: 10px;
    }
    button {
      padding: 10px 20px;
      font-size: 1em;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      color: white;
    }
    button.start {
      background-color: #28a745;
    }
    button.pause {
      background-color: #dc3545;
    }
    button.reset {
      background-color: #007bff;
    }
  </style>
</head>
<body>
  <div class="timer">
    <div id="display" class="timer-display">00:00:00</div>
    <div class="timer-buttons">
      <button class="start" id="startButton">Start</button>
      <button class="pause" id="pauseButton">Pause</button>
      <button class="reset" id="resetButton">Reset</button>
    </div>
  </div>

  <script>
    let timerInterval;
    let seconds = 0;

    const display = document.getElementById('display');
    const startButton = document.getElementById('startButton');
    const pauseButton = document.getElementById('pauseButton');
    const resetButton = document.getElementById('resetButton');

    function formatTime(sec) {
      const hrs = Math.floor(sec / 3600).toString().padStart(2, '0');
      const mins = Math.floor((sec % 3600) / 60).toString().padStart(2, '0');
      const secs = (sec % 60).toString().padStart(2, '0');
      return `${hrs}:${mins}:${secs}`;
    }

    function updateDisplay() {
      display.textContent = formatTime(seconds);
    }

    startButton.addEventListener('click', () => {
      if (!timerInterval) {
        timerInterval = setInterval(() => {
          seconds++;
          updateDisplay();
        }, 1000);
      }
    });

    pauseButton.addEventListener('click', () => {
      clearInterval(timerInterval);
      timerInterval = null;
    });

    resetButton.addEventListener('click', () => {
      clearInterval(timerInterval);
      timerInterval = null;
      seconds = 0;
      updateDisplay();
    });

    // Initialize display
    updateDisplay();
  </script>
</body>
</html>
# timer1
