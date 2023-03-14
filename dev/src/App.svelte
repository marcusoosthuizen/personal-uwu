<script>
  import mouth from "./assets/images/mouth.png"
  import cheeks from "./assets/images/cheeks.png"
  import eye from "./assets/images/eyes.png"
  import ball from "./assets/images/eyeballs.png"
  import uwuAudio from './assets/audio/uwu.mp3'
  import uwuEarape from './assets/audio/uwuloud.mp3'
  var m = { x: 0, y: 0};
  var diffLeft = { x: 0, y: 0};
  var diffRight = { x: 0, y: 0};
  var blush = 203;
  //console.log(Math.atan(45) * 180/Math.PI)
  
  function uwuSound(event) {
    var avolume = (100 - (blush - 123)) / 100;
    console.log(avolume);

    if (blush < 125) {
      var audio = new Audio(uwuEarape);
      avolume -= 0.5
    } else {
      var audio = new Audio(uwuAudio);
    }
    
    audio.loop = false;
    audio.volume = avolume;
    audio.play();
    blush = 203
  }

  function nothing(event) {
    // nothing to see here
  }


  function eyes(event) {
      m.x = event.clientX;
      m.y = event.clientY;
      diffLeft.x = -200 + m.x;
      diffLeft.y = 210 - m.y;
      diffRight.x = -400 + m.x;
      diffRight.y = 210 - m.y;
      
      const canvas = document.getElementById('canvas');
      const ctx = canvas.getContext('2d');
      ctx.strokeStyle = 'red';
      ctx.lineWidth = 5;

      var leftie = document.getElementById("leftBall")

      if (diffLeft.x > 0 && diffLeft.y > 0) {
        var angle = Math.atan(diffLeft.x / diffLeft.y) * 180 / Math.PI
        leftie.style.transform = 'rotate(' + angle + 'deg)'
      } else if (diffLeft.x > 0 && diffLeft.y < 0) {
        var angle = 180 - Math.atan(diffLeft.x / (diffLeft.y * -1)) * 180 / Math.PI
        leftie.style.transform = 'rotate(' + angle + 'deg)'
      } else if (diffLeft.x < 0 && diffLeft.y < 0) {
        var angle = 180 + Math.atan((diffLeft.x * -1) / (diffLeft.y * -1)) * 180 / Math.PI
        leftie.style.transform = 'rotate(' + angle + 'deg)'
      } else if (diffLeft.x < 0 && diffLeft.y > 0) {
        var angle = 360 - Math.atan((diffLeft.x * -1) / diffLeft.y) * 180 / Math.PI
        leftie.style.transform = 'rotate(' + angle + 'deg)'
      }

      var rightie = document.getElementById("rightBall")

      if (diffRight.x > 0 && diffRight.y > 0) {
        var angle = Math.atan(diffRight.x / diffRight.y) * 180 / Math.PI
        rightie.style.transform = 'rotate(' + angle + 'deg)'
      } else if (diffRight.x > 0 && diffRight.y < 0) {
        var angle = 180 - Math.atan(diffRight.x / (diffRight.y * -1)) * 180 / Math.PI
        rightie.style.transform = 'rotate(' + angle + 'deg)'
      } else if (diffRight.x < 0 && diffRight.y < 0) {
        var angle = 180 + Math.atan((diffRight.x * -1) / (diffRight.y * -1)) * 180 / Math.PI
        rightie.style.transform = 'rotate(' + angle + 'deg)'
      } else if (diffRight.x < 0 && diffRight.y > 0) {
        var angle = 360 - Math.atan((diffRight.x * -1) / diffRight.y) * 180 / Math.PI
        rightie.style.transform = 'rotate(' + angle + 'deg)'
      }

      if (m.x >= 100 && m.y >= 135 && m.x <= 500 && m.y <= 350) {
        blush -= 0.2;
        if (blush < 100) {
          blush = 100;
        }
      } else {
        blush += 1;
        if (blush > 203) {
          blush = 203
        }
      }

      /*ctx.clearRect(0, 0, 600, 600)

      ctx.beginPath();
      ctx.moveTo(m.x, m.y);
      ctx.lineTo(400, 210)
      ctx.stroke();

      ctx.beginPath();
      ctx.moveTo(m.x, m.y);
      ctx.lineTo(400, m.y)
      ctx.stroke();

      ctx.beginPath();
      ctx.moveTo(400, m.y);
      ctx.lineTo(400, 210)
      ctx.stroke(); */

      /*ctx.beginPath();
      ctx.moveTo(m.x, m.y);
      ctx.lineTo(400, 210)
      ctx.stroke();*/
  }
  
</script>

<main>
  <body style="background-color: rgb(255, {blush}, 45);" on:mousemove="{eyes}" on:click="{uwuSound}" on:keydown="{nothing}">
    
    <img id="uwu" src="{mouth}" alt="">
    <img id="uwu" src="{cheeks}" alt="">
    <img id="leftEye" src="{eye}" alt="">
    <img id="leftBall" src="{ball}" alt="">
    <img id="rightEye" src="{eye}" alt="">
    <img id="rightBall" src="{ball}" alt="">
    <!--<button type="button" id="daBut">press me uwu</button>
    <audio controls id="daaudio">
        <source src="./assets/audio/uwu.mp3" type="audio/mp3">
      </audio> -->
    <!--<div><h4 id="X">{m.x}, {m.y}<br>{diffLeft.x}, {diffLeft.y}<br>{blush}</h4></div>-->
    <canvas id="canvas" style="position: absolute; left: 0px; top: 0px; --border:1px solid #000000;" height="600" width="600">
    </canvas>
</body>
</main>

<style>
  body {
      position: absolute;
      left: 0;
      top: 0;
      min-width: 600px;
      min-height: 600px;
      max-width: 100%;
      max-height: 100%;
  }
  #uwu {
      position: absolute;
      width: 500px;
      height: 500px;
      top: 0px;
      left: calc(300px - 250px);
  }

  #leftEye {
      position: absolute;
      width: 100px;
      height: 100px;
      top: 150px;
      left: 155px;
  }

  #leftBall {
      position: absolute;
      width: 100px;
      height: 100px;
      top: 150px;
      left: 155px;
  }

  #rightEye {
      position: absolute;
      width: 100px;
      height: 100px;
      top: 150px;
      left: 355px;
  }

  #rightBall {
      position: absolute;
      width: 100px;
      height: 100px;
      top: 150px;
      left: 355px;
  }

  button {
      position: absolute;
      width: 150px;
      height: 70px;
      font-size: 17px;
      background-color: orange;
      border-width: 1vh;
      border-color: orange;
      border-radius: 2vh;
      border-style: none;
      left: calc(50vw - 10vh);
      top: 80vh;
  }

  audio {
      --visibility: hidden;
  }

  div {
      position: absolute;
      bottom: 1px;
      width: 100vw;
  }

  h4 {
      text-align: center;
  }
</style>
