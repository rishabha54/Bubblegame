# Bubblegame

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <div id="main">
      <div id="panel">
        <div id="ptop">
          <div class="elem">
            <h2>Hit</h2>
            <div id= "hitval" class="box">5</div>
          </div>
          <div class="elem">
            <h2>Timer</h2>
            <div id ="timervalue" class="box">60</div>
          </div>
          <div class="elem">
            <h2>Score</h2>
            <div id="scoreval" class="box">0</div>
          </div>
        </div>
        <div id="pbtm">
         
        </div>
      </div>
    </div>


    <script src="script.js"></script>
  </body>
</html>



<!!Javascript code!! >>
var timer =60;
var score =0;
var hitrn = 0;

function increasescore(){
    score += 10;
    document.querySelector("#scoreval").textContent = score;
}



function getHit(){
    hitrn = Math.floor(Math.random()*10);
    document.querySelector("#hitval").textContent = hitrn;
}


function makebubble(){
    var clutter = " ";
    for(var i =1; i<=68; i++){
        var rn = Math.floor(Math.random()*10);
        clutter += `<div class="bubble">${rn}</div>`;
    }
    document.querySelector("#pbtm").innerHTML = clutter;
}


function runTimer(){

    var timerint= setInterval(function(){
     if(timer>0) {
    timer--;
    document.querySelector("#timervalue").textContent = timer;
    }else{
        clearInterval(timerint);
    }
    },1000);
     
}

document.querySelector("#pbtm").addEventListener("click",function(dets){
    var clickednum = Number(dets.target.textContent); 
    if(clickednum === hitrn){
        increasescore();
        makebubble();
        getHit();
    }
});



getHit();
makebubble();
runTimer();



<<!!CSS Code!! >>

*{
    margin: 0;
    padding: 0;
    font-family: "Gilroy";
    box-sizing: border-box;

}

html,body{
   width: 100%;
   height: 100%;
}

#main{
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    height: 100%;
    background-color: #c1bc22;
}

#panel{
    overflow: hidden;
    width:80%;
    height:80%;
    border-radius: 10px;
    background-color: #fff;
}

#ptop{
    display: flex;
    align-items:center;
    justify-content: space-between;
    padding: 0px 70px;
    color:#fff ;
    width:100%;
    height: 100px;
    background-color: rgb(236, 228, 17);
}

.elem{
    display:flex;
   align-items: center;
   gap: 10px;
   
}
.elem h2{
    font-size: 20px;
    font-weight: 100;
}


.box{
  font-weight: 700;
  font-size: 20px;
  color: #000;
  padding: 10px 20px;
  background-color: #fff;
  border-radius: 5px;
}

#pbtm{
    display:flex;
    gap:10px;
    flex-wrap: wrap;
    padding :20px;
    width: 100%;
    height:calc(100% - 100px);
    
}

.bubble{
    display: flex;
    align-items: center;
    justify-content: center;
    height:60px;
    width:60px;
    border-radius: 50%;
    background-color: #7f8340;
    color: #fff;
    font-weight: 500;
}
.bubble:hover{
    cursor:pointer;
    background-color: #616429;
}
