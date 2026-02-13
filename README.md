# mi-beso-en-las-escaleras
san-valentin-jazmin
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Para Jazmín ❤️</title>

<style>
body{
    margin:0;
    height:100vh;
    display:flex;
    flex-direction:column;
    justify-content:center;
    align-items:center;
    background:linear-gradient(135deg,#ff4e8a,#ff9ecf);
    font-family:Arial, Helvetica, sans-serif;
    text-align:center;
    overflow:hidden;
    position:relative;
}

h1{
    color:white;
    font-size:2.2em;
    margin-bottom:40px;
}

button{
    padding:15px 30px;
    font-size:18px;
    border:none;
    border-radius:30px;
    cursor:pointer;
    transition:0.2s;
}

#si{
    background:#ffffff;
    color:#ff2f7d;
    margin-top:10px;
}

#no{
    background:#ff2f7d;
    color:white;
    position:absolute;
}

.mensajeNo{
    position:absolute;
    color:white;
    font-weight:bold;
    animation:desaparecer 1.5s forwards;
}

.destino{
    position:absolute;
    top:20%;
    color:white;
    font-size:1.8em;
    font-weight:bold;
    animation:aparecer 1s ease-in-out;
}

@keyframes desaparecer{
    0%{opacity:1;}
    100%{opacity:0; transform:translateY(-25px);}
}

@keyframes aparecer{
    0%{opacity:0; transform:scale(0.8);}
    100%{opacity:1; transform:scale(1);}
}

.heart, .loveText{
    position:absolute;
    animation:fall linear infinite;
}

@keyframes fall{
    0%{transform:translateY(-10vh);}
    100%{transform:translateY(110vh);}
}

.final-message{
    position:absolute;
    bottom:40px;
    color:white;
    font-size:1.4em;
    font-weight:bold;
}
</style>
</head>

<body>

<h1>¿Quieres ser mi San Valentín, Jazmín? 💘</h1>

<button id="si">Sí ❤️</button>
<button id="no">No 😢</button>

<script>
let noBtn = document.getElementById("no");
let siBtn = document.getElementById("si");
let intentos = 0;

let niveles = [
    ["¿Segura? 😳","Piénsalo bien 🥺"],
    ["No seas así 😢","Marco se pondrá triste 💔"],
    ["Mira que te amo mucho 😭","No me hagas sufrir así 💕"],
    ["Te prometo hacerte feliz 😩","Por favor di que sí ❤️"],
    ["Jasmin… eres lo mejor que me pasó 😔","No me rompas el corazón 💘"],
    ["Está bien… pero el destino ya decidió 😌"]
];

function moverBoton(){
    intentos++;

    if(intentos > 10){
        noBtn.remove();
        mostrarDestino();
        return;
    }

    let ancho = window.innerWidth - noBtn.offsetWidth;
    let alto = window.innerHeight - noBtn.offsetHeight;

    let randomX = Math.random() * ancho;
    let randomY = Math.random() * alto;

    noBtn.style.left = randomX + "px";
    noBtn.style.top = randomY + "px";

    mostrarFrase(randomX, randomY);
}

function mostrarFrase(x,y){
    let nivel = Math.min(Math.floor(intentos/2), niveles.length-1);
    let frases = niveles[nivel];

    let mensaje = document.createElement("div");
    mensaje.classList.add("mensajeNo");
    mensaje.innerText = frases[Math.floor(Math.random()*frases.length)];
    mensaje.style.left = x + "px";
    mensaje.style.top = (y - 30) + "px";
    document.body.appendChild(mensaje);

    setTimeout(()=>{ mensaje.remove(); },1500);
}

function mostrarDestino(){
    let destino = document.createElement("div");
    destino.classList.add("destino");
    destino.innerText = "El destino ya decidió 😌💘";
    document.body.appendChild(destino);
}

noBtn.addEventListener("mouseover", moverBoton);
noBtn.addEventListener("touchstart", moverBoton);

siBtn.addEventListener("click", function(){
    document.body.innerHTML = "";
    lluviaCorazones();
});

function lluviaCorazones(){
    for(let i=0;i<120;i++){
        let heart = document.createElement("div");
        heart.classList.add("heart");
        heart.innerHTML = "❤️";
        heart.style.left = Math.random()*100 + "vw";
        heart.style.fontSize = Math.random()*25+20+"px";
        heart.style.animationDuration = (Math.random()*3+2)+"s";
        document.body.appendChild(heart);

        let text = document.createElement("div");
        text.classList.add("loveText");
        text.innerHTML = "Te amo 💕";
        text.style.left = Math.random()*100 + "vw";
        text.style.fontSize = Math.random()*20+15+"px";
        text.style.animationDuration = (Math.random()*3+2)+"s";
        document.body.appendChild(text);
    }

    let mensaje = document.createElement("div");
    mensaje.classList.add("final-message");
    mensaje.innerHTML = "Me hiciste muy feliz. No olvidaré ese beso en las escaleras del taller ❤️";
    document.body.appendChild(mensaje);
}
</script>

</body>
</html>
