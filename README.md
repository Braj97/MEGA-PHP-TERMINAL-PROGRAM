# MEGA-PHP-TERMINAL-PROGRAM
PHP
<?php
// MEGA TERMINAL PROGRAM IN PHP

function quizGame() {
    $score = 0;
    $questions = [
        ["PHP stands for?", "Hypertext Preprocessor"],
        ["Symbol for variable in PHP?", "$"],
        ["Function to output data?", "echo"]
    ];

    echo "\n--- QUIZ GAME ---\n";
    foreach ($questions as $q) {
        echo $q[0] . "\nAnswer: ";
        $ans = trim(fgets(STDIN));
        if (strtolower($ans) == strtolower($q[1])) {
            echo "Correct!\n";
            $score++;
        } else {
            echo "Wrong! Correct Answer: {$q[1]}\n";
        }
    }
    echo "Your Score: $score / " . count($questions) . "\n";
}

function calculator() {
    echo "\n--- SCIENTIFIC CALCULATOR ---\n";
    echo "1. Add\n2. Subtract\n3. Multiply\n4. Divide\n";
    echo "Choose: ";
    $ch = trim(fgets(STDIN));

    echo "Enter First Number: ";
    $a = trim(fgets(STDIN));
    echo "Enter Second Number: ";
    $b = trim(fgets(STDIN));

    switch ($ch) {
        case 1: echo "Result: " . ($a + $b) . "\n"; break;
        case 2: echo "Result: " . ($a - $b) . "\n"; break;
        case 3: echo "Result: " . ($a * $b) . "\n"; break;
        case 4:
            if ($b == 0) echo "Cannot divide by zero!\n";
            else echo "Result: " . ($a / $b) . "\n";
            break;
        default: echo "Invalid option!\n";
    }
}

function numberGuessGame() {
    $num = rand(1, 10);
    echo "\n--- NUMBER GUESS GAME (1-10) ---\n";

    for ($i = 1; $i <= 3; $i++) {
        echo "Attempt $i: ";
        $guess = trim(fgets(STDIN));
        if ($guess == $num) {
            echo "🎉 Correct Guess!\n";
            return;
        }
        echo "Wrong guess!\n";
    }
    echo "Correct Number was: $num\n";
}

function patternGenerator() {
    echo "\n--- PATTERN GENERATOR ---\n";
    echo "Enter number of rows: ";
    $rows = trim(fgets(STDIN));

    for ($i = 1; $i <= $rows; $i++) {
        for ($j = 1; $j <= $i; $j++) {
            echo "* ";
        }
        echo "\n";
    }
}

function numberCheck() {
    echo "\nEnter a number: ";
    $n = trim(fgets(STDIN));

    // Prime
    $prime = true;
    if ($n < 2) $prime = false;
    for ($i = 2; $i <= sqrt($n); $i++) {
        if ($n % $i == 0) $prime = false;
    }

    // Palindrome
    $rev = strrev($n);
    $pal = ($n == $rev);

    // Armstrong
    $sum = 0;
    foreach (str_split($n) as $d) {
        $sum += $d * $d * $d;
    }
    $arm = ($sum == $n);

    echo "Prime: " . ($prime ? "Yes" : "No") . "\n";
    echo "Palindrome: " . ($pal ? "Yes" : "No") . "\n";
    echo "Armstrong: " . ($arm ? "Yes" : "No") . "\n";
}

// MAIN MENU
while (true) {
    echo "\n===============================\n";
    echo " MEGA PHP TERMINAL PROGRAM\n";
    echo "===============================\n";
    echo "1. Quiz Game\n";
    echo "2. Calculator\n";
    echo "3. Number Guess Game\n";
    echo "4. Pattern Generator\n";
    echo "5. Number Checker\n";
    echo "6. Exit\n";
    echo "Choose option: ";

    $choice = trim(fgets(STDIN));

    switch ($choice) {
        case 1: quizGame(); break;
        case 2: calculator(); break;
        case 3: numberGuessGame(); break;
        case 4: patternGenerator(); break;
        case 5: numberCheck(); break;
        case 6: exit("Program Ended.\n");
        default: echo "Invalid Choice!\n";
    }
}
?>
#OUTPUT
