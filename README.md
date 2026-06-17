# It4ka.github.io
<!DOCTYPE html>
<html lang="bg">
<head>
<meta charset="UTF-8">
<title>🛡️ Cyber Guardian Ultra</title>

<style>
body{
    margin:0;
    background:#050014;
    color:white;
    font-family:Arial;
    height:100vh;
    display:flex;
    align-items:center;
    justify-content:center;
}

.game{
    width:900px;
    background:#111827;
    border:3px solid #00ffff;
    border-radius:25px;
    padding:30px;
    box-shadow:0 0 30px #00ffff;
}

h1{
    color:#00ffff;
    text-align:center;
}

#score{
    color:#ffd700;
    font-size:22px;
}

#text{
    font-size:22px;
    min-height:180px;
    line-height:1.5;
}

button{
    width:45%;
    padding:20px;
    margin:10px;
    border:0;
    border-radius:15px;
    font-size:18px;
    cursor:pointer;
}

.red{
    background:#e74c3c;
    color:white;
}

.green{
    background:#2ecc71;
    color:white;
}

</style>
</head>

<body>

<div class="game">

<div id="score">
Точки: 0
</div>

<h1 id="title">
🛡️ CYBER GUARDIAN ULTRA
</h1>

<div id="text">
Добре дошъл в мисията срещу кибертормоза.
<br><br>
Готов ли си?
</div>

<button class="red" onclick="A()" id="btnA">
🚀 START GAME
</button>

<button class="green" onclick="B()" id="btnB">
ИЗХОД
</button>

</div>


<script>

let stage="menu";
let points=0;
let q=0;


let quiz=[
["Кибертормозът е само когато има директни обиди.","НЕ"],
["Трябва да пазиш доказателства от тормоз.","ДА"],
["Най-доброто решение е да отговориш с обиди.","НЕ"],
["Трябва да докладваш профил на насилник.","ДА"],
["Трябва да плащаш на изнудвач.","НЕ"],
["Блокиране и докладване помага.","ДА"]
];


function update(){

document.getElementById("score").innerHTML=
"Точки: "+points;


let title=document.getElementById("title");
let text=document.getElementById("text");
let a=document.getElementById("btnA");
let b=document.getElementById("btnB");


if(stage=="menu"){

title.innerHTML="🛡️ CYBER GUARDIAN ULTRA";

text.innerHTML=
"Добре дошъл в играта срещу кибертормоза.<br><br>Готов ли си за мисията?";

a.innerHTML="🚀 START GAME";
b.innerHTML="Изход";

}


if(stage=="one"){

title.innerHTML="ФАЗА 1: Чат атака";

text.innerHTML=
"Някой качва подигравателни мемета за София.<br><br>Какво правиш?";

a.innerHTML="Споделям мемето";
b.innerHTML="Помагам и докладвам";

}


if(stage=="two"){

title.innerHTML="ФАЗА 2: Фалшив профил";

text.innerHTML=
"Създаден е фалшив профил със снимки на жертвата.";

a.innerHTML="Следвам профила";
b.innerHTML="Докладвам";

}


if(stage=="three"){

title.innerHTML="ФАЗА 3: Изнудване";

text.innerHTML=
"Някой заплашва да публикува фалшиви снимки.";

a.innerHTML="Плащам";
b.innerHTML="Пазя доказателства";

}


if(stage=="quiz"){

title.innerHTML=
"Въпрос "+(q+1)+" от 6";

text.innerHTML=quiz[q][0];

a.innerHTML="ДА";
b.innerHTML="НЕ";

}


if(stage=="win"){

title.innerHTML="🏆 ПОБЕДА!";

text.innerHTML=
"Ти си истински Cyber Guardian!<br>Точки: "+points;

a.innerHTML="Нова игра";
b.innerHTML="Изход";

}

}



function A(){

if(stage=="menu")
stage="one";

else if(stage=="one"||stage=="two"||stage=="three")
stage="menu";

else if(stage=="quiz")
answer("ДА");

else if(stage=="win"){
points=0;
q=0;
stage="menu";
}

update();

}



function B(){

if(stage=="one"){
points+=50;
stage="two";
}

else if(stage=="two"){
points+=50;
stage="three";
}

else if(stage=="three"){
points+=50;
stage="quiz";
}

else if(stage=="quiz")
answer("НЕ");

else{
stage="menu";
}

update();

}



function answer(x){

if(x==quiz[q][1]){

points+=25;
q++;

if(q==6)
stage="win";

}else{

alert("Грешен отговор!");
q=0;

}

update();

}


update();

</script>

</body>
</html>
