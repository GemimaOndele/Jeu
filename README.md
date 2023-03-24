# Jeu
#Jeu de carré au curseur aléatoirement 


console.log('Jeu démarré');

const box = document.querySelector('.box');
const scoreElement = document.querySelector('#score');
let click = 0;
let chrono = 30;
const chronoElement = document.querySelector('#chrono');
chronoElement.innerHTML = chrono;

// Récupération du score précédent depuis Local Storage
const previousScore = localStorage.getItem('score');
if (previousScore) {
  click = parseInt(previousScore);
  scoreElement.innerHTML = click;
}

box.addEventListener("click", () => {
  console.log('click sur la box !');
  click += 1;
  scoreElement.innerHTML = click;

  // Stockage du score actuel dans Local Storage
  localStorage.setItem('score', click);

  let top = Math.floor(Math.random() * window.innerHeight);
  let left = Math.floor(Math.random() * window.innerWidth);

  box.style.top = `${top}px`;
  box.style.left = `${left}px`;
});

const intervalId = setInterval(() => {
  console.log("timer");
  if (chrono !== 0) {
    chrono--;
    chronoElement.innerHTML = chrono;
  } else {
    clearInterval(intervalId);
  }
}, 1000);
