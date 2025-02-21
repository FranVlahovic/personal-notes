## 📜 Code Snippets

### Sample README File for GitHub

````Markdown
<a id="readme-top"></a>

<!-- PROJECT SHIELDS -->

[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![MIT License][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]

<!-- PROJECT LOGO -->
<br />

<div align="center">
  <img src="https://github.com/user-attachments/assets/5b8bc367-5cc4-4ade-8e7f-e9c27db12159" alt="Aeris Gif">

  <h3 align="center">Aeris</h3>

  <p align="center">
    A weather app delivering real-time updates and stunning visuals for a better user experience.
    <br />
    <a href="https://github.com/FranVlahovic/Aeris"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="https://franvlahovic.github.io/Aeris">Live</a>
    ·
    <a href="https://github.com/FranVlahovic/Aeris/issues/new?labels=bug&template=bug-report---.md">Report Bug</a>
    ·
    <a href="https://github.com/FranVlahovic/Aeris/issues/new?labels=enhancement&template=feature-request---.md">Request Feature</a>
  </p>
</div>

---

## Table of Contents

- [About The Project](#about-the-project)
- [Gallery](#gallery)
- [Built With](#built-with)
- [Getting Started](#getting-started)
    - [Prerequisites](#prerequisites)
    - [Installation](#installation)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)
- [Acknowledgments](#acknowledgments)

---

## About The Project

**Aeris** is a modern weather application providing users with detailed forecasts and interactive visuals. The app demonstrates a clean UI, responsive design, and real-time weather updates powered by robust API integrations.

## Gallery

<div align="center">
  <img src="https://github.com/user-attachments/assets/e7963d71-4e41-4e4b-8bf8-6778409c7291" alt="Image 1" width="400">
  <img src="https://github.com/user-attachments/assets/5264b96a-f55b-448c-b6e0-0ab8b44c7814" alt="Image 2" width="400">
  <img src="https://github.com/user-attachments/assets/43d5f1a7-cd5b-4b92-aedf-50a0942df8aa" alt="Image 3" width="400">
  <img src="https://github.com/user-attachments/assets/520b501c-b25e-41cf-91e7-f1de764c727c" alt="Image 3" width="400">
</div>

---

## Built With

- ![HTML5](https://img.shields.io/badge/-HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
- ![CSS3](https://img.shields.io/badge/-CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
- ![JavaScript](https://img.shields.io/badge/-JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)

---

## Getting Started

To set up a local copy, follow these steps:

### Prerequisites

- Ensure [Node.js](https://nodejs.org/) is installed.

### Installation

1. Clone the repository:
    ```sh
    git clone https://github.com/FranVlahovic/Aeris.git
    ```
2. Navigate to the directory:
    ```sh
    cd Aeris
    ```
3. Install dependencies:
    ```sh
    npm install
    ```

---

## Usage

To start the development environment:

```sh
npm start


Build for production:

```sh
npm run build


---

## Contributing

Contributions are welcome! To contribute:

1. Fork the repository.
2. Create your branch (`git checkout -b feature/YourFeature`).
3. Commit changes (`git commit -m 'Add your feature'`).
4. Push the branch (`git push origin feature/YourFeature`).
5. Open a pull request.

---

## License

Distributed under the MIT License. See `LICENSE.txt` for details.

---

## Contact

Fran Vlahovic - [LinkedIn](https://linkedin.com/in/franvlahovic)

Email: franvlahovic@proton.me

Project Link: [https://github.com/FranVlahovic/Aeris](https://github.com/FranVlahovic/Aeris)

---

## Acknowledgments

- [The Odin Project](https://www.theodinproject.com/)
- [MDN Web Docs](https://developer.mozilla.org/)
- [OpenWeather API](https://openweathermap.org/api)

<!-- MARKDOWN LINKS & IMAGES -->

[contributors-shield]: https://img.shields.io/github/contributors/FranVlahovic/Aeris.svg?style=for-the-badge
[contributors-url]: https://github.com/FranVlahovic/Aeris/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/FranVlahovic/Aeris.svg?style=for-the-badge
[forks-url]: https://github.com/FranVlahovic/Aeris/network/members
[stars-shield]: https://img.shields.io/github/stars/FranVlahovic/Aeris.svg?style=for-the-badge
[stars-url]: https://github.com/FranVlahovic/Aeris/stargazers
[issues-shield]: https://img.shields.io/github/issues/FranVlahovic/Aeris.svg?style=for-the-badge
[issues-url]: https://github.com/FranVlahovic/Aeris/issues
[license-shield]: https://img.shields.io/github/license/FranVlahovic/Aeris.svg?style=for-the-badge
[license-url]: https://github.com/FranVlahovic/Aeris/blob/main/LICENSE
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-blue.svg?style=for-the-badge&logo=linkedin&logoColor=white
[linkedin-url]: https://linkedin.com/in/franvlahovic

---

````

### Toggle Dark | Light Mode (System Preference & Local Storage)

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Toggling</title>
    <style>
        body {
            --text-color: #222;
            --bkg-color: #fff;
        }
        body.dark-theme {
            --text-color: #eee;
            --bkg-color: #121212;
        }

        @media (prefers-color-scheme: dark) {
            body.light-theme {
                --text-color: #222;
                --bkg-color: #fff;
            }
            body {
                --text-color: #eee;
                --bkg-color: #121212;
            }
        }

        body {
            background: var(--bkg-color);
        }
        h1, p {
            color: var(--text-color);
        }
    </style>
</head>

<body>
    <button class="btn-toggle">Dark Mode</button>
    <h1>Hey there im a sample text</h1>
    <p> Me too, dark mode is cool especially when you can toggle between dark and light mode. </p>

    <script>
      // Select the button
      const btn = document.querySelector(".btn-toggle");
      // Check for dark mode preference at the OS level
      const prefersDarkScheme = window.matchMedia("(prefers-color-scheme: dark)");

      // Get the user's theme preference from local storage, if it's available
      const currentTheme = localStorage.getItem("theme");
      // If the user's preference in localStorage is dark...
      if (currentTheme == "dark") {
        // ...let's toggle the .dark-theme class on the body
        document.body.classList.toggle("dark-theme");
      // Otherwise, if the user's preference in localStorage is light...
      } else if (currentTheme == "light") {
        // ...let's toggle the .light-theme class on the body
        document.body.classList.toggle("light-theme");
      }

      // Listen for a click on the button
      btn.addEventListener("click", function() {
        // If the user's OS setting is dark and matches our .dark-mode class...
        if (prefersDarkScheme.matches) {
          // ...then toggle the light mode class
          document.body.classList.toggle("light-theme");
          // ...but use .dark-mode if the .light-mode class is already on the body,
          theme = document.body.classList.contains("light-theme") ? "light" : "dark";
        } else {
          // Otherwise, let's do the same thing, but for .dark-mode
          document.body.classList.toggle("dark-theme");
          theme = document.body.classList.contains("dark-theme") ? "dark" : "light";
        }
        // Finally, let's save the current preference to localStorage to keep using it
        localStorage.setItem("theme", theme);
      });

    </script>
</body>
</html>
```

### Jonas Schmedtmann: Pig Game Project

```
'use strict';

// Selecting elements
const player0El = document.querySelector('.player--0');
const player1El = document.querySelector('.player--1');
const score0El = document.querySelector('#score--0');
const score1El = document.getElementById('score--1');
const current0El = document.getElementById('current--0');
const current1El = document.getElementById('current--1');

const diceEl = document.querySelector('.dice');
const btnNew = document.querySelector('.btn--new');
const btnRoll = document.querySelector('.btn--roll');
const btnHold = document.querySelector('.btn--hold');

let scores, currentScore, activePlayer, playing;

// Starting conditions
const init = function () {
  scores = [0, 0];
  currentScore = 0;
  activePlayer = 0;
  playing = true;

  score0El.textContent = 0;
  score1El.textContent = 0;
  current0El.textContent = 0;
  current1El.textContent = 0;

  diceEl.classList.add('hidden');
  player0El.classList.remove('player--winner');
  player1El.classList.remove('player--winner');
  player0El.classList.add('player--active');
  player1El.classList.remove('player--active');
};
init();

const switchPlayer = function () {
  document.getElementById(`current--${activePlayer}`).textContent = 0;
  currentScore = 0;
  activePlayer = activePlayer === 0 ? 1 : 0;
  player0El.classList.toggle('player--active');
  player1El.classList.toggle('player--active');
};

// Rolling dice functionality
btnRoll.addEventListener('click', function () {
  if (playing) {
    // 1. Generating a random dice roll
    const dice = Math.trunc(Math.random() * 6) + 1;

    // 2. Display dice
    diceEl.classList.remove('hidden');
    diceEl.src = `dice-${dice}.png`;

    // 3. Check for rolled 1
    if (dice !== 1) {
      // Add dice to current score
      currentScore += dice;
      document.getElementById(
        `current--${activePlayer}`
      ).textContent = currentScore;
    } else {
      // Switch to next player
      switchPlayer();
    }
  }
});

btnHold.addEventListener('click', function () {
  if (playing) {
    // 1. Add current score to active player's score
    scores[activePlayer] += currentScore;
    // scores[1] = scores[1] + currentScore

    document.getElementById(`score--${activePlayer}`).textContent =
      scores[activePlayer];

    // 2. Check if player's score is >= 100
    if (scores[activePlayer] >= 100) {
      // Finish the game
      playing = false;
      diceEl.classList.add('hidden');

      document
        .querySelector(`.player--${activePlayer}`)
        .classList.add('player--winner');
      document
        .querySelector(`.player--${activePlayer}`)
        .classList.remove('player--active');
    } else {
      // Switch to the next player
      switchPlayer();
    }
  }
});

btnNew.addEventListener('click', init);
```
