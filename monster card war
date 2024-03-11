
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Yu-Gi-Oh! Life Point Battle</title>
<style>
body {
    font-family: Arial, sans-serif;
    background-color: #f2f2f2;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
}
#game-container {
    text-align: center;
}
.card {
    width: 150px;
    height: 200px;
    border: 2px solid #000;
    border-radius: 10px;
    background-color: #fff;
    margin: 10px;
    display: inline-block;
    cursor: pointer;
}
.selected {
    border-color: red;
}
#result {
    font-size: 24px;
    font-weight: bold;
    margin-top: 20px;
}
#player-lp, #computer-lp {
    font-size: 18px;
    font-weight: bold;
    margin-top: 10px;
}
</style>
</head>
<body>
<div id="game-container">
    <div id="player-card" class="card"></div>
    <div id="computer-card" class="card"></div>
    <div id="result"></div>
    <div id="player-lp">Player LP: 8000</div>
    <div id="computer-lp">Computer LP: 8000</div>
    <button onclick="startTurn()">Start Turn</button>
    <button onclick="checkCard()">Check Card</button>
    <div id="card-info"></div>
</div>
<script>
const cards = [
    { name: 'Dark Magician', attack: 2500, defense: 2100 },
    { name: 'Blue-Eyes White Dragon', attack: 3000, defense: 2500 },
    { name: 'Red-Eyes Black Dragon', attack: 2400, defense: 2000 },
    { name: 'moon wizard', attack: 1200, defense: 1700 },
    { name: 'artillery', attack: 1800, defense: 1700 },
    { name: 'kiss goochi', attack: 400, defense: 300 },
    { name: 'lanky', attack: 400, defense: 300 },
    { name: 'Shrine maiden who can see strange shapes', attack: 1200, defense: 1000 },
    { name: 'ruins exploration team', attack: 1500, defense: 1600 },
    { name: 'Ruins grave robbery squad', attack: 1700, defense: 1500 },
    { name: 'Medaka', attack: 100, defense: 500 },
    { name: 'Ghost of Sugar Loaf', attack: 2000, defense: 1800 },
    { name: 'lanky soldier', attack: 1000, defense: 1000 },
    { name: 'wriggling arms', attack: 1100, defense: 1200 },
    { name: 'lucky Star', attack: 700, defense: 700 },
    { name: 'combat medic', attack: 300, defense: 1000 },
    { name: 'invaders from space', attack: 800, defense: 700 },
    { name: 'insect human', attack: 700, defense: 800 },
    { name: 'Monster Rat', attack: 500, defense: 400 },
    { name: 'zombie worm', attack: 1300, defense: 1600 },
    // Add other card data here
];

let playerLP = 8000;
let computerLP = 8000;

// 追加のカードリスト
const additionalCards = [
    { name: 'Master of the Pond', attack: 2100, defense: 2000 },
    { name: 'Killer Worm', attack: 500, defense: 100 },
    { name: 'Water Spirit Aquan', attack: 1200, defense: 1600 },
    { name: 'Insect Plane', attack: 1600, defense: 1000 },
    { name: 'Wretched One', attack: 1300, defense: 500 },
    { name: 'Wind Spirit Windy', attack: 1900, defense: 1300 },
    { name: 'Prisoner', attack: 300, defense: 1800 },
    { name: 'Guardian of the Den', attack: 600, defense: 100 },
    { name: 'Chain of Hope', attack: 700, defense: 1700 },
    { name: 'Cursed Pot', attack: 500, defense: 800 },
    { name: 'Keel Cave', attack: 2100, defense: 1800 },
    { name: 'Smaller', attack: 300, defense: 200 },
    { name: 'The Underground Dweller', attack: 1200, defense: 300 },
    { name: 'Volks', attack: 700, defense: 800 },
    { name: 'Hyoronaga-go', attack: 1700, defense: 1300 },
    { name: 'forest adventurer', attack: 2000, defense: 1600 },
    { name: 'blue-eyed demon tamer', attack: 500, defense: 2100 },
    { name: 'puppet doll', attack: 800, defense: 900 },
    { name: 'battleship machine gun', attack: 1800, defense: 1000 },
    { name: 'spin water', attack: 1400, defense: 1000 },
    { name: 'bat', attack: 1400, defense: 100 },
    { name: 'spin water', attack: 1900, defense: 200 },
    { name: 'shadow man', attack: 1300, defense: 1700 },
    { name: 'dark trial', attack: 1500, defense: 1500 }
];

function getRandomCard() {
    return cards[Math.floor(Math.random() * cards.length)];
}

function displayCard(elementId, card) {
    const cardElement = document.getElementById(elementId);
    cardElement.innerHTML = `
        <p>${card.name}</p>
        <p>Attack: ${card.attack}</p>
        <p>Defense: ${card.defense}</p>
    `;
}

function startTurn() {
    if (playerLP <= 0 || computerLP <= 0) {
        resetGame();
        return;
    }

    const playerCard = getRandomCard();
    const computerCard = getRandomCard();

    displayCard('player-card', playerCard);
    displayCard('computer-card', computerCard);

    setTimeout(() => battle(playerCard, computerCard), 1000);
}

function battle(playerCard, computerCard) {
    let result = '';
    let playerDamage = Math.max(playerCard.attack - computerCard.defense, 0);
    let computerDamage = Math.max(computerCard.attack - playerCard.defense, 0);

    if (playerDamage > computerDamage) {
        result = 'Player Wins!';
        computerLP -= playerDamage;
    } else if (playerDamage < computerDamage) {
        result = 'Computer Wins!';
        playerLP -= computerDamage;
    } else {
        result = 'It\'s a Draw!';
    }

    document.getElementById('result').textContent = `Result: ${result}`;
    document.getElementById('player-lp').textContent = `Player LP: ${playerLP}`;
    document.getElementById('computer-lp').textContent = `Computer LP: ${computerLP}`;

    if (playerLP <= 0 || computerLP <= 0) {
        endGame();
    }
}

function resetGame() {
    playerLP = 8000;
    computerLP = 8000;
    document.getElementById('player-lp').textContent = `Player LP: ${playerLP}`;
    document.getElementById('computer-lp').textContent = `Computer LP: ${computerLP}`;
}

function endGame() {
    let message = '';
    if (playerLP <= 0 && computerLP <= 0) {
        message = 'Draw!';
    } else if (playerLP <= 0) {
        message = 'Computer Wins!';
    } else {
        message = 'Player Wins!';
        offerCard();
    }
    alert(`Game Over! ${message}`);
}

function checkCard() {
    const randomIndex = Math.floor(Math.random() * cards.length);
    const card = cards[randomIndex];
    document.getElementById('card-info').innerHTML = `
        <p>Name: ${card.name}</p>
        <p>Attack: ${card.attack}</p>
        <p>Defense: ${card.defense}</p>
    `;
}

function offerCard() {
    const choice = confirm('Congratulations! You won the game! Would you like to add one of the additional cards to your deck?');
    if (choice) {
        const randomIndex = Math.floor(Math.random() * additionalCards.length);
        const cardToAdd = additionalCards[randomIndex];
        alert(`You have obtained ${cardToAdd.name}!`);

        // 新しいカードをデッキに追加
        cards.push(cardToAdd);

        // デッキに追加したことを確認
        console.log(`Added ${cardToAdd.name} to your deck:`, cards);

        // カードを表示
        displayCard('card-info', cardToAdd);
    }
}

function displayCardInfo(card) {
    document.getElementById('card-info').innerHTML = `
        <p>Name: ${card.name}</p>
        <p>Attack: ${card.attack}</p>
        <p>Defense: ${card.defense}</p>
    `;
}
</script>
</body>
</html>
