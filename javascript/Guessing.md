# Guessing.js - Program

```javascript
const readline = require("readline");

const rl = readline.createInterface({
    input: process.stdin,
    output: process.stdout,
    terminal: false,
});

const phrases = [
    "Fruit of life",
    "Life is art",
    "Spread love",
    "Do justice",
    "Love mercy",
    "Be the change",
    "Heart of Texas",
    "Computer science",
    "Photo journalism",
    "Political activism",
];

function game() {

    const x = phrases[Math.floor(Math.random() * phrases.length)].split("");
    var y = [], attempts = 7;
    for (i of x)
        y.push(i == " " ? i : "*");

    function over() {
        rl.question("Play again? (y/n) :: ", (ans) => {
            if (ans === "y")
                game();
            else process.exit(0);
        });
    }
        
    function guess() {
        console.info(y.join("") + "  |  " + attempts + " attempts left");
        rl.question("Guess a letter :: ", (ans) => {
            var change = false;
            for (i in x) {
                if (x[i].toLowerCase() === ans.toLowerCase()) {
                    y[i] = x[i];
                    change = true;
                }
            }
            if (!change) {
                attempts -= 1;
                if (attempts <= 0) {
                    console.info("You lose!");
                    over();
                }
                else guess();
            }
            else if (!y.includes("*")) {
                console.info(y.join(""));
                console.info("You win!");
                over();
            }
            else guess();
        });
    }

    guess();

}

game();
```

## Phrase Guessing Game
A simple, text based guessing game using Node. 

Once the phrase is randomly selected it should display the phrase, with all character replaced with `*` symbols. For example, if the phrase is `Hello World` the game would start like this.

Once the player has entered a letter, check if exists in the selected phrase and then display the currently solved phrase. For example, if they enter an `L`. Comparisons should be case insensitive and you should only consider the first letter of whatever the user enters. 

If the letter guessed is not part of the phrase display a message that the letter is not part of phrase.

The game is won when the user guesses the entire phrase. The game is lost if they guess 7 times without completing the phrase. 
