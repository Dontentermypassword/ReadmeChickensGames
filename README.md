<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Dino Game</title>
  <style>
    body {
      background: #f7f7f7;
      font-family: Arial, sans-serif;
    }
    #game {
      width: 800px;
      height: 200px;
      background: #ffffff;
      border: 2px solid #000000;
      margin: 40px auto;
      position: relative;
      overflow: hidden;
    }
    #dino {
      width: 40px;
      height: 40px;
      background: #000000;
      position: absolute;
      bottom: 0;
      left: 50px;
    }
    #cactus {
      width: 20px;
      height: 50px;
      background: #008000;
      position: absolute;
      bottom: 0;
      left: 800px;
    }
    #score {
      text-align: center;
      font-size: 24px;
      margin-top: 10px;
    }
  </style>
</head>
<body>

<div id="score">Score: 0</div>
<div id="game">
  <div id="dino"></div>
  <div id="cactus"></div>
</div>

<script>
  const dino = document.getElementById("dino");
  const cactus = document.getElementById("cactus");
  const scoreText = document.getElementById("score");

  let isJumping = false;
  let score = 0;
  let speed = 6;

  function jump() {
    if (isJumping) return;
    isJumping = true;

    let position = 0;
    const upInterval = setInterval(() => {
      if (position >= 120) {
        clearInterval(upInterval);
        const downInterval = setInterval(() => {
          if (position
