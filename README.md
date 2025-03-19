<?php
session_start();

// Initialize game variables
if (!isset($_SESSION['pies'])) {
    $_SESSION['pies'] = 10; // Total pies to pop
    $_SESSION['turns'] = 5; // Total turns
    $_SESSION['popped'] = 0; // Pies popped
}

// Handle form submission
if ($_SERVER['REQUEST_METHOD'] === 'POST') {
    if ($_SESSION['turns'] > 0) {
        // Randomly determine if the pie is popped
        $popSuccess = rand(0, 1); // 50% chance to pop a pie
        if ($popSuccess && $_SESSION['pies'] > 0) {
            $_SESSION['popped']++;
            $_SESSION['pies']--;
            $message = "🎉 You popped a pie!";
        } else {
            $message = "😢 No pie popped this turn.";
        }
        $_SESSION['turns']--;
    } else {
        $message = "⏰ No turns left! Game over.";
    }
}

// Check if the game is over
if ($_SESSION['turns'] === 0 || $_SESSION['pies'] === 0) {
    $gameOver = true;
    $finalMessage = "Game Over! You popped {$_SESSION['popped']} pies.";
    // Reset the game
    session_destroy();
} else {
    $gameOver = false;
}
?>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pop Pies Game</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f0f8ff;
            color: #333;
            text-align: center;
            padding: 20px;
        }
        h1 {
            color: #ff6347;
        }
        .game-container {
            border: 2px solid #ff6347;
            border-radius: 10px;
            padding: 20px;
            background-color: #fff;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            display: inline-block;
        }
        button {
            background-color: #ff6347;
            color: white;
            border: none;
            border-radius: 5px;
            padding: 10px 20px;
            cursor: pointer;
            font-size: 16px;
        }
        button:hover {
            background-color: #ff4500;
        }
        .message {
            margin-top: 20px;
            font-size: 18px;
        }
        .final-message {
            font-size: 20px;
            font-weight: bold;
            color: #ff6347;
        }
        a {
            display: inline-block;
            margin-top: 20px;
            text-decoration: none;
            color: #ff6347;
            font-weight: bold;
        }
    </style>
</head>
<body>
    <h1>Pop Pies Game</h1>
    <div class="game-container">
        <?php if ($gameOver): ?>
            <div class="final-message"><?php echo $finalMessage; ?></div>
            <a href="index.php">Play Again</a>
        <?php else: ?>
            <p>Pies left to pop: <strong><?php echo $_SESSION['pies']; ?></strong></p>
            <p>Turns left: <strong><?php echo $_SESSION['turns']; ?></strong></p>
            <p>Pies popped: <strong><?php echo $_SESSION['popped']; ?></strong></p>
            <form method="post">
                <button type="submit">Pop a Pie!</button>
            </form>
            <?php if (isset($message)): ?>
                <div class="message"><?php echo $message; ?></div>
            <?php endif; ?>
        <?php endif; ?>
    </div>
</body>
</html><?php
session_start();

// Initialize game variables
if (!isset($_SESSION['pies'])) {
    $_SESSION['pies'] = 10; // Total pies to pop
    $_SESSION['turns'] = 5; // Total turns
    $_SESSION['popped'] = 0; // Pies popped
}

// Handle form submission
if ($_SERVER['REQUEST_METHOD'] === 'POST') {
    if ($_SESSION['turns'] > 0) {
        // Randomly determine if the pie is popped
        $popSuccess = rand(0, 1); // 50% chance to pop a pie
        if ($popSuccess && $_SESSION['pies'] > 0) {
            $_SESSION['popped']++;
            $_SESSION['pies']--;
            $message = "🎉 You popped a pie!";
        } else {
            $message = "😢 No pie popped this turn.";
        }
        $_SESSION['turns']--;
    } else {
        $message = "⏰ No turns left! Game over.";
    }
}

// Check if the game is over
if ($_SESSION['turns'] === 0 || $_SESSION['pies'] === 0) {
    $gameOver = true;
    $finalMessage = "Game Over! You popped {$_SESSION['popped']} pies.";
    // Reset the game
    session_destroy();
} else {
    $gameOver = false;
}
?>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pop Pies Game</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f0f8ff;
            color: #333;
            text-align: center;
            padding: 20px;
        }
        h1 {
            color: #ff6347;
        }
        .game-container {
            border: 2px solid #ff6347;
            border-radius: 10px;
            padding: 20px;
            background-color: #fff;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            display: inline-block;
        }
        button {
            background-color: #ff6347;
            color: white;
            border: none;
            border-radius: 5px;
            padding: 10px 20px;
            cursor: pointer;
            font-size: 16px;
        }
        button:hover {
            background-color: #ff4500;
        }
        .message {
            margin-top: 20px;
            font-size: 18px;
        }
        .final-message {
            font-size: 20px;
            font-weight: bold;
            color: #ff6347;
        }
        a {
            display: inline-block;
            margin-top: 20px;
            text-decoration: none;
            color: #ff6347;
            font-weight: bold;
        }
    </style>
</head>
<body>
    <h1>Pop Pies Game</h1>
    <div class="game-container">
        <?php if ($gameOver): ?>
            <div class="final-message"><?php echo $finalMessage; ?></div>
            <a href="index.php">Play Again</a>
        <?php else: ?>
            <p>Pies left to pop: <strong><?php echo $_SESSION['pies']; ?></strong></p>
            <p>Turns left: <strong><?php echo $_SESSION['turns']; ?></strong></p>
            <p>Pies popped: <strong><?php echo $_SESSION['popped']; ?></strong></p>
            <form method="post">
                <button type="submit">Pop a Pie!</button>
            </form>
            <?php if (isset($message)): ?>
                <div class="message"><?php echo $message; ?></div>
            <?php endif; ?>
        <?php endif; ?>
    </div>
</body>
</html>
