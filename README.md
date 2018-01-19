var randomCircle = 0;

var randomColorCircle = "";

var scoreCount = 0;

var scoreCountString = "";

var enable = true;

var seconds = 11;

var timer = "";

function startGameMain(){
    setTimeout(startGame, 3000);
    setTimeout(stopGame, 13000);
    setTimeout(countDownMain, 2000);
    threeToOneCountDown();
    scoreCount = 0;
};

function startGame(){
    randomizeCircle();
    randomizerRect();
    scoreCountString = scoreCount.toString();
    document.getElementById("scoreCount").innerHTML = scoreCountString;
    enable = true;
};

function stopGame(){
    enable = false;
};

function score(){
    scoreCount += 1;
    scoreCountString = scoreCount.toString();
    document.getElementById("scoreCount").innerHTML = scoreCountString;
};

function randomizeCircle(){
    
    var colors = ["blue", "red", "yellow", "green"];
    
    randomCircle = Math.floor((Math.random() * 4));
    
    colorCircle = colors[randomCircle];
    
    $("#mainCircle").css("fill", colorCircle);
};

function randomizerRect(){
  const COLORS = ['red', 'blue', 'green', 'yellow'];
  Array.from(document.querySelectorAll('rect')).forEach((rect) => {
    const idx = Math.floor(Math.random() * COLORS.length);
    rect.style.fill = COLORS[idx];
    COLORS.splice(idx, 1);
  });
}

function moveCircle(event){

  if (enable == true){
      var button = event.keyCode;
    
  rightRectColor = $("#rightRect").css("fill");
    
  topRectColor = $("#topRect").css("fill");
    
  bottomRectColor = $("#bottomRect").css("fill");
    
  leftRectColor = $("#leftRect").css("fill");
      
  circleColor = $("#mainCircle").css("fill");
  
  if (button == 65){
      if (leftRectColor == circleColor){
          startGame();
          score();
      } else {
          stopGame();
          console.log("dog");
      };
  };
  if (button == 87){
      if (topRectColor == circleColor){
          startGame();
          score();
      } else {
          stopGame();
          console.log("dog");
      };
  };
  if (button == 68){
      if (rightRectColor == circleColor){
          startGame();
          score();
      } else {
          stopGame();
          console.log("dog");
      };
  };
  if (button == 83){
      if (bottomRectColor == circleColor){
          startGame();
          score();
      } else {
          stopGame();
          console.log("dog");
      };
  };
  } else {
      console.log("off");
  };
  
};

function countDown(){    
    seconds--;
    
    document.getElementById("countDown").innerHTML = seconds;
    
    if (seconds == 0){
        clearInterval(timer);
        stopGame();
    };
};

function countDownMain(){
    timer = setInterval(countDown, 1000);
};
