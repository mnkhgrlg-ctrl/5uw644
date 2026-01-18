# 5uw644
<!DOCTYPE html>
<html lang="mn">
<head>
<meta charset="UTF-8">
<title>For You</title>

<style>
body{
  margin:0;
  height:100vh;
  overflow:hidden;
  background:linear-gradient(120deg,#ff5f8a,#2b004f);
  animation:bg 15s infinite alternate;
  font-family:-apple-system;
  color:white;
}
@keyframes bg{
  0%{background:linear-gradient(120deg,#ff5f8a,#2b004f)}
  50%{background:linear-gradient(120deg,#4facfe,#00f2fe)}
  100%{background:linear-gradient(120deg,#ff0844,#ffb199)}
}

/* galaxy stars */
.star{
  position:fixed;
  width:2px;
  height:2px;
  background:white;
  opacity:.7;
  animation:twinkle 2s infinite;
}
@keyframes twinkle{
  50%{opacity:.2}
}

/* center */
.center{
  position:absolute;
  inset:0;
  display:flex;
  justify-content:center;
  align-items:center;
  flex-direction:column;
}

/* gift */
#gift{
  width:180px;
  height:130px;
  background:#c8002d;
  border-radius:14px;
  position:relative;
  cursor:pointer;
  box-shadow:0 25px 45px rgba(255,0,80,.6);
  animation:float 2.5s infinite ease-in-out;
}
#gift:before{
  content:"";
  position:absolute;
  width:36px;
  height:130px;
  background:#ffd1dc;
  left:72px;
}
#gift:after{
  content:"";
  position:absolute;
  width:180px;
  height:36px;
  background:#ffd1dc;
  top:47px;
}
#lid{
  width:200px;
  height:46px;
  background:#ff0033;
  position:absolute;
  top:-46px;
  left:-10px;
  border-radius:12px;
  transition:1s ease;
}
@keyframes float{
  50%{transform:translateY(-14px)}
}

/* message typing */
#msg{
  display:none;
  font-size:48px;
  font-weight:800;
  text-align:center;
  text-shadow:0 0 40px white;
  min-height:120px;
}

/* firework */
.fire{
  position:fixed;
  width:6px;
  height:6px;
  background:white;
  border-radius:50%;
  box-shadow:0 0 15px white;
  animation:fire 2.5s ease-out forwards;
}
@keyframes fire{
  to{
    transform:translate(
      calc(-260px + 520px * var(--x)),
      calc(-260px + 520px * var(--y))
    );
    opacity:0;
  }
}
</style>
</head>

<body>

<div class="center">
  <div id="gift">
    <div id="lid"></div>
  </div>

  <div id="msg"></div>
</div>

<script>
/* stars */
for(let i=0;i<150;i++){
  const s=document.createElement("div");
  s.className="star";
  s.style.left=Math.random()*100+"vw";
  s.style.top=Math.random()*100+"vh";
  document.body.appendChild(s);
}

/* click */
const text="Suwdaa\nби чамд хайртай ❤️";
let i=0, opened=false;

gift.onclick=()=>{
  if(opened) return;
  opened=true;

  lid.style.transform="rotateX(160deg) translateY(-80px)";
  gift.style.display="none";
  msg.style.display="block";

  type();

  for(let i=0;i<60;i++){
    firework();
  }
};

/* typing effect */
function type(){
  if(i<text.length){
    msg.innerHTML+=text[i]==="\n"?"<br>":text[i];
    i++;
    setTimeout(type,90);
  }
}

/* firework */
function firework(){
  const f=document.createElement("div");
  f.className="fire";
  f.style.left=innerWidth/2+"px";
  f.style.top=innerHeight/2+"px";
  f.style.setProperty("--x",Math.random());
  f.style.setProperty("--y",Math.random());
  document.body.appendChild(f);
  setTimeout(()=>f.remove(),2500);
}
</script>

</body>
</html>
