
75cheonyo511
/
Musicplayer-
Public template
Code
Issues
1
Pull requests
Actions
Projects
Wiki
Security
Insights
Settings
Musicplayer-/document_1000002401.html
@75cheonyo511
75cheonyo511 Add files via upload
 1 contributor
209 lines (204 sloc)  4.22 KB
<html lang="en">
  <head>
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Record Player</title>
    <!-- Stylesheet -->
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <div class="player">
      <div class="record">
        <div class="label"></div>
      </div>
      <div class="tone-arm">
        <div class="control"></div>
      </div>
      <button class="btn"></button>
      <div class="slider-container">
        <input
          type="range"
          class="slider"
          min="0"
          max="1"
          step="0.1"
          value="0.7"
        />
      </div>
    </div>
    <audio loop class="my-song" src="https://drive.google.com/uc?export=download&id=17zkmTYl2K3xh9-n6VIxBLCG4hdtgAblx" preload="auto"></audio>
    <!-- Script -->
    <script src="script.js"></script>
  </body>
</html>
 
 <style>
 * {
  padding: 0;
  margin: 0;
}
body {
  background-color: #f8d76e;
}
.player {
  background-color: #d52f31;
  width: 330px;
  height: 190px;
  position: absolute;
  transform: translate(-50%, -50%);
  left: 50%;
  top: 50%;
  border-radius: 8px;
  box-shadow: 0 8px 0 0 #be272a;
}
.record {
  height: 175px;
  width: 175px;
  background-color: #181312;
  border-radius: 50%;
  position: absolute;
  top: 10px;
  left: 20px;
  display: flex;
  align-items: center;
  justify-content: center;
}
.record:before,
.record:after {
  position: absolute;
  content: "";
  border: 5px solid transparent;
  border-top-color: #2c2424;
  border-bottom-color: #2c2424;
  border-radius: 50%;
}
.record:before {
  height: 135px;
  width: 135px;
}
.record:after {
  height: 95px;
  width: 95px;
}
.label {
  background-color: #181312;
  height: 15px;
  width: 15px;
  border: 20px solid #ff8e00;
  border-radius: 50%;
}
.tone-arm {
  height: 90px;
  width: 6px;
  background-color: #ffffff;
  position: absolute;
  top: 25px;
  right: 95px;
  transition: 1s;
  transform-origin: top;
}
.control {
  background-color: #181312;
  height: 17px;
  width: 17px;
  border: 10px solid #2c2c2c;
  border-radius: 50%;
  position: absolute;
  top: -16px;
  left: -16px;
}
.tone-arm:before {
  content: "";
  height: 40px;
  width: 6px;
  background-color: #ffffff;
  position: absolute;
  transform: rotate(30deg);
  bottom: -36px;
  right: 10px;
}
.tone-arm:after {
  content: "";
  position: absolute;
  height: 0;
  width: 10px;
  border-top: 18px solid #b2aea6;
  border-left: 2px solid transparent;
  border-right: 2px solid transparent;
  top: 108px;
  right: 12.5px;
  transform: rotate(30deg);
}
.btn {
  height: 28px;
  width: 28px;
  background-color: #ed5650;
  border-radius: 50%;
  position: absolute;
  bottom: 20px;
  right: 30px;
  border: none;
  border: 3.5px solid #be272a;
  outline: none;
  cursor: pointer;
}
.slider {
  -webkit-appearance: none;
  appearance: none;
  transform: rotate(-90deg);
  width: 90px;
  height: 7px;
  position: absolute;
  left: 233px;
  top: 60px;
  background-color: #be272a;
  outline: none;
  border-radius: 3px;
  border: 6px solid #ed5650;
}
.slider::-webkit-slider-thumb {
  -webkit-appearance: none;
  appearance: none;
  width: 10px;
  height: 12px;
  background-color: #ffffff;
  cursor: pointer;
}
.play {
  transform: rotate(30deg);
  transform-origin: top;
  transition: 1s;
}
.on {
  animation: spin 3s 1s linear infinite;
}
@keyframes spin {
  100% {
    transform: rotate(360deg);
  }
}
 </style> 
 
 <script> 
 let state = false;
let btn = document.querySelector(".btn");
let record = document.querySelector(".record");
let toneArm = document.querySelector(".tone-arm");
let song = document.querySelector(".my-song");
let slider = document.querySelector(".slider");

btn.addEventListener("click", () => {
  if (state == false) {
    record.classList.add("on");
    toneArm.classList.add("play");
    setTimeout(() => {
      song.play();
    }, 1000);
  } else {
    record.classList.remove("on");
    toneArm.classList.remove("play");
    song.pause();
  }
  state = !state;
});

slider.addEventListener("input", (e) => {
  song.volume = Number(e.target.value);
});
 </script> 
 
</html>
