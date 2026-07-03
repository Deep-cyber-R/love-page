<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>For Happy 💜</title>

<style>
*{
margin:0;
padding:0;
box-sizing:border-box;
font-family:Arial,sans-serif;
}

body{
height:100vh;
display:flex;
justify-content:center;
align-items:center;
background:linear-gradient(135deg,#6a11cb,#8e44ad,#c471ed);
overflow:hidden;
color:white;
text-align:center;
}

.container{
max-width:700px;
padding:30px;
z-index:2;
}

h1{
font-size:3rem;
margin-bottom:20px;
}

p{
font-size:1.2rem;
line-height:1.8;
margin-bottom:25px;
}

button{
padding:14px 28px;
font-size:18px;
border:none;
border-radius:50px;
cursor:pointer;
margin:10px;
transition:.3s;
}

#yes{
background:#ff4fa3;
color:white;
}

#yes:hover{
transform:scale(1.1);
}

#no{
background:white;
color:#8e44ad;
position:relative;
}

.heart{
position:absolute;
color:#ff69b4;
font-size:24px;
animation:float 8s linear infinite;
}

@keyframes float{
0%{
transform:translateY(100vh);
opacity:0;
}
100%{
transform:translateY(-120vh);
opacity:1;
}
}
</style>
</head>

<body>

<div class="container">

<h1>💜 Dear Happy 💜</h1>

<p>
Every time I think of you, my heart smiles.<br><br>

You make ordinary moments feel special, and I'd love the chance to create beautiful memories together.
</p>

<h2 style="margin-bottom:25px;">Will you go on a date with me? 💜</h2>

<button id="yes">💖 Yes</button>
<button id="no">🙈 No</button>

</div>

<script>

const no=document.getElementById("no");

no.addEventListener("mouseover",()=>{
no.style.position="absolute";
no.style.left=Math.random()*80+"%";
no.style.top=Math.random()*80+"%";
});

document.getElementById("yes").onclick=function(){
document.body.innerHTML=`
<div style="display:flex;height:100vh;justify-content:center;align-items:center;flex-direction:column;background:linear-gradient(135deg,#6a11cb,#c471ed);color:white;text-align:center;">
<h1 style="font-size:60px;">💜 Thank You Happy 💜</h1>
<h2>You've made my day! 😊</h2>
<p style="font-size:22px;margin-top:20px;">
Can't wait to spend some wonderful time together.
</p>
</div>`;
};

function createHeart(){
const heart=document.createElement("div");
heart.classList.add("heart");
heart.innerHTML="💜";
heart.style.left=Math.random()*100+"vw";
heart.style.fontSize=(20+Math.random()*25)+"px";
heart.style.animationDuration=(5+Math.random()*5)+"s";
document.body.appendChild(heart);

setTimeout(()=>{
heart.remove();
},9000);
}

setInterval(createHeart,300);

</script>

</body>
</html>
