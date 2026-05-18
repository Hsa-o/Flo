# Flo
<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Flores Amarillas</title>

<style>
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

body{
    height:100vh;
    display:flex;
    justify-content:center;
    align-items:center;
    background:#f5f5f5;
    font-family:Arial, sans-serif;
}

.Flores_Amarillas{
    position: relative;
    width: 90%;
    max-width: 900px;
    height: 500px;
    background: #efe6dc;
    border-radius: 30px;
    overflow: hidden;
    padding: 40px;
}

/* TEXTO */
.texto{
    width:45%;
    color:#444;
    z-index:2;
    position:relative;
}

.texto h1{
    font-size:2rem;
    margin-bottom:20px;
}

.texto p{
    font-size:1.4rem;
    line-height:1.6;
    margin-bottom:20px;
}

.assinatura{
    font-size:1.5rem;
    margin-top:20px;
}

/* CONTADOR */
.contador{
    position:absolute;
    bottom:30px;
    left:40px;
    font-size:1.2rem;
    color:#333;
}

/* ÁRVORE */
.arvore{
    position:absolute;
    right:70px;
    bottom:0;
    width:300px;
    height:400px;
}

/* TRONCO */
.tronco{
    position:absolute;
    bottom:0;
    left:50%;
    transform:translateX(-50%);
    width:40px;
    height:160px;
    background:#8b5a2b;
    border-radius:10px;
}

/* COPA */
.copa{
    position:absolute;
    top:20px;
    left:50%;
    transform:translateX(-50%);
    width:260px;
    height:260px;
}

/* FLORES */
.flor{
    position:absolute;
    width:22px;
    height:22px;
    background:yellow;
    border-radius:50%;
    box-shadow:
        0 0 0 6px rgba(255,255,0,0.6),
        inset 0 0 0 6px #5c3b00;
}
</style>
</head>
<body>

<div class="Flores_Amarillas">

    <div class="texto">
        <h1>Flores Amarillas para el amor de mi vida:</h1>

        <p>
            Si pudiera elegir un lugar seguro, sería a tu lado.
        </p>

        <p>
            Cuanto más tiempo estoy contigo más te amo.
        </p>

        <div class="assinatura">— I Love You 💛</div>
    </div>

    <!-- ÁRVORE -->
    <div class="arvore">
        <div class="tronco"></div>
        <div class="copa" id="copa"></div>
    </div>

    <!-- CONTADOR -->
    <div class="contador">
        Mi amor por ti comenzó hace...<br><br>

        <span id="dias">0</span> días
        <span id="horas">00</span> horas
        <span id="minutos">00</span> minutos
        <span id="segundos">00</span> segundos
    </div>

</div>

<script>
// CRIAR FLORES AUTOMATICAMENTE
const copa = document.getElementById("copa");

for(let i = 0; i < 180; i++){

    const flor = document.createElement("div");
    flor.classList.add("flor");

    // posição aleatória em formato coração
    let t = Math.random() * Math.PI * 2;

    let x = 16 * Math.pow(Math.sin(t), 3);
    let y = 13 * Math.cos(t)
            - 5 * Math.cos(2*t)
            - 2 * Math.cos(3*t)
            - Math.cos(4*t);

    x *= 8;
    y *= 8;

    flor.style.left = (120 + x + (Math.random()*20-10)) + "px";
    flor.style.top = (120 - y + (Math.random()*20-10)) + "px";

    copa.appendChild(flor);
}

// CONTADOR
const dataInicio = new Date("2024-01-01 00:00:00");

function atualizarContador(){

    const agora = new Date();
    const diferenca = agora - dataInicio;

    const segundos = Math.floor(diferenca / 1000) % 60;
    const minutos = Math.floor(diferenca / (1000 * 60)) % 60;
    const horas = Math.floor(diferenca / (1000 * 60 * 60)) % 24;
    const dias = Math.floor(diferenca / (1000 * 60 * 60 * 24));

    document.getElementById("dias").innerText = dias;
    document.getElementById("horas").innerText = String(horas).padStart(2,'0');
    document.getElementById("minutos").innerText = String(minutos).padStart(2,'0');
    document.getElementById("segundos").innerText = String(segundos).padStart(2,'0');
}

setInterval(atualizarContador, 1000);
atualizarContador();
</script>

</body>
</html>
