<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>FarmLife 🌱</title>

<style>
*{
    box-sizing:border-box;
    margin:0;
    padding:0;
}

:root{
    --green:#22c55e;
    --dark-green:#15803d;
    --bg:#f0fdf4;
    --card:#ffffff;
    --text:#172033;
    --muted:#64748b;
}

body{
    font-family:Arial,sans-serif;
    background:var(--bg);
    color:var(--text);
    min-height:100vh;
}

body.dark{
    --bg:#0f172a;
    --card:#1e293b;
    --text:#f8fafc;
    --muted:#cbd5e1;
}

header{
    background:var(--card);
    padding:15px 5%;
    display:flex;
    justify-content:space-between;
    align-items:center;
    position:sticky;
    top:0;
    z-index:1000;
    box-shadow:0 3px 15px #0002;
}

.logo{
    font-size:25px;
    font-weight:bold;
    color:#22c55e;
}

.logo span{
    color:var(--text);
}

.player-info{
    display:flex;
    gap:10px;
    flex-wrap:wrap;
}

.stat{
    background:var(--bg);
    padding:8px 12px;
    border-radius:12px;
    font-weight:bold;
}

.layout{
    display:flex;
    min-height:calc(100vh - 70px);
}

.sidebar{
    width:230px;
    background:#166534;
    padding:15px;
    flex-shrink:0;
}

.sidebar button{
    width:100%;
    background:transparent;
    border:0;
    color:white;
    text-align:left;
    padding:12px;
    margin-bottom:5px;
    border-radius:10px;
    cursor:pointer;
    font-weight:bold;
}

.sidebar button:hover,
.sidebar button.active{
    background:#22c55e;
}

.main{
    flex:1;
    padding:25px;
}

.page{
    display:none;
}

.page.active{
    display:block;
}

.page-title{
    margin-bottom:25px;
}

.page-title h1{
    font-size:32px;
    margin-bottom:7px;
}

.page-title p{
    color:var(--muted);
}

.card{
    background:var(--card);
    border-radius:18px;
    padding:20px;
    box-shadow:0 7px 20px #0001;
}

.grid{
    display:grid;
    grid-template-columns:repeat(3,1fr);
    gap:20px;
}

.welcome{
    background:linear-gradient(135deg,#16a34a,#4ade80);
    color:white;
    border-radius:25px;
    padding:35px;
    margin-bottom:25px;
}

.welcome h1{
    font-size:38px;
    margin-bottom:10px;
}

.quick-grid{
    display:grid;
    grid-template-columns:repeat(4,1fr);
    gap:15px;
}

.quick{
    background:var(--card);
    border-radius:18px;
    padding:20px;
    text-align:center;
    cursor:pointer;
    box-shadow:0 5px 15px #0001;
}

.quick:hover{
    transform:translateY(-4px);
}

.quick .emoji{
    font-size:40px;
    margin-bottom:8px;
}

.weather{
    background:linear-gradient(135deg,#60a5fa,#38bdf8);
    color:white;
    border-radius:18px;
    padding:20px;
    margin-bottom:20px;
}

.farm{
    background:#a16207;
    padding:20px;
    border-radius:20px;
    display:grid;
    grid-template-columns:repeat(4,1fr);
    gap:15px;
}

.plot{
    height:150px;
    background:#78350f;
    border:4px solid #92400e;
    border-radius:15px;
    display:flex;
    align-items:center;
    justify-content:center;
    flex-direction:column;
    color:white;
    cursor:pointer;
}

.plot:hover{
    filter:brightness(1.15);
}

.plot .plant{
    font-size:48px;
}

.timer{
    font-size:12px;
    margin-top:5px;
}

.item{
    background:var(--card);
    border-radius:18px;
    padding:20px;
    box-shadow:0 6px 18px #0001;
}

.item-icon{
    font-size:55px;
    margin-bottom:10px;
}

.item p{
    color:var(--muted);
    margin:8px 0;
}

.action{
    border:0;
    padding:10px 15px;
    border-radius:10px;
    cursor:pointer;
    font-weight:bold;
}

.primary{
    background:#22c55e;
    color:white;
}

.danger{
    background:#ef4444;
    color:white;
}

.inventory-grid{
    display:grid;
    grid-template-columns:repeat(5,1fr);
    gap:15px;
}

.inventory-item{
    background:var(--card);
    border-radius:15px;
    padding:20px;
    text-align:center;
}

.inventory-item .emoji{
    font-size:45px;
}

.inventory-item strong{
    display:block;
    margin-top:8px;
    font-size:22px;
}

.market-table{
    width:100%;
    border-collapse:collapse;
}

.market-table th,
.market-table td{
    padding:14px;
    border-bottom:1px solid #cbd5e1;
    text-align:left;
}

.animal{
    text-align:center;
}

.animal-icon{
    font-size:70px;
    margin-bottom:10px;
}

.pond{
    min-height:350px;
    background:linear-gradient(#38bdf8,#0284c7);
    border-radius:25px;
    display:flex;
    align-items:center;
    justify-content:center;
    flex-direction:column;
    color:white;
    text-align:center;
}

.fish{
    font-size:100px;
}

.quest{
    background:var(--card);
    padding:20px;
    border-radius:18px;
    margin-bottom:15px;
}

.progress{
    height:10px;
    background:#e2e8f0;
    border-radius:20px;
    overflow:hidden;
    margin:10px 0;
}

.progress div{
    height:100%;
    background:#22c55e;
}

.profile{
    text-align:center;
}

.avatar{
    width:120px;
    height:120px;
    border-radius:50%;
    background:#dcfce7;
    display:flex;
    justify-content:center;
    align-items:center;
    font-size:65px;
    margin:0 auto 15px;
}

.xpbar{
    height:15px;
    background:#e2e8f0;
    border-radius:20px;
    overflow:hidden;
    margin:15px 0;
}

.xpbar div{
    height:100%;
    background:#22c55e;
}

.setting{
    display:flex;
    justify-content:space-between;
    align-items:center;
    background:var(--card);
    padding:20px;
    border-radius:15px;
    margin-bottom:12px;
}

.modal{
    position:fixed;
    inset:0;
    background:#0009;
    display:none;
    align-items:center;
    justify-content:center;
    z-index:2000;
    padding:20px;
}

.modal.show{
    display:flex;
}

.modal-box{
    background:var(--card);
    width:420px;
    max-width:100%;
    border-radius:20px;
    padding:25px;
    text-align:center;
}

.toast{
    position:fixed;
    right:20px;
    bottom:20px;
    background:#172033;
    color:white;
    padding:15px 20px;
    border-radius:12px;
    display:none;
    z-index:3000;
}

.toast.show{
    display:block;
}

.name-input{
    padding:12px;
    border:2px solid #22c55e;
    border-radius:10px;
    width:100%;
    max-width:300px;
    font-size:16px;
}

@media(max-width:900px){

    .layout{
        display:block;
    }

    .sidebar{
        width:100%;
        display:flex;
        overflow-x:auto;
        gap:5px;
    }

    .sidebar button{
        min-width:max-content;
    }

    .grid{
        grid-template-columns:repeat(2,1fr);
    }

    .quick-grid{
        grid-template-columns:repeat(2,1fr);
    }

    .inventory-grid{
        grid-template-columns:repeat(3,1fr);
    }

    .farm{
        grid-template-columns:repeat(2,1fr);
    }
}

@media(max-width:600px){

    header{
        flex-direction:column;
        align-items:flex-start;
    }

    .grid{
        grid-template-columns:1fr;
    }

    .inventory-grid{
        grid-template-columns:repeat(2,1fr);
    }

    .main{
        padding:15px;
    }
}
</style>
</head>

<body>

<header>

    <div class="logo">
        🌱 Farm<span>Life</span>
    </div>

    <div class="player-info">

        <div class="stat">
            👤 <span id="headerName">Petani</span>
        </div>

        <div class="stat">
            💰 <span id="money">500</span>
        </div>

        <div class="stat">
            ⭐ Level <span id="level">1</span>
        </div>

        <div class="stat">
            ⚡ <span id="energy">100</span>
        </div>

    </div>

</header>


<div class="layout">

<aside class="sidebar">

<button class="active" onclick="page('home',this)">🏡 Beranda</button>
<button onclick="page('farm',this)">🌾 Kebun</button>
<button onclick="page('shop',this)">🛒 Toko</button>
<button onclick="page('inventory',this)">🎒 Inventori</button>
<button onclick="page('market',this)">💰 Pasar</button>
<button onclick="page('animals',this)">🐄 Peternakan</button>
<button onclick="page('pond',this)">🐟 Kolam</button>
<button onclick="page('quests',this)">🏆 Misi</button>
<button onclick="page('daily',this)">🎁 Hadiah</button>
<button onclick="page('profile',this)">👤 Profil</button>
<button onclick="page('settings',this)">⚙️ Pengaturan</button>
<button onclick="page('about',this)">ℹ️ Tentang</button>

</aside>


<main class="main">


<!-- BERANDA -->

<section id="home" class="page active">

<div class="welcome">

<h1>
Selamat datang,
<span id="welcomeName">Petani</span>! 🌱
</h1>

<p>
Bangun perkebunan impianmu,
tanam tanaman, rawat hewan,
dan jadilah petani terbaik!
</p>

</div>


<div class="quick-grid">

<div class="quick" onclick="page('farm')">
<div class="emoji">🌾</div>
<b>Kelola Kebun</b>
</div>

<div class="quick" onclick="page('shop')">
<div class="emoji">🛒</div>
<b>Belanja Bibit</b>
</div>

<div class="quick" onclick="page('market')">
<div class="emoji">💰</div>
<b>Jual Panen</b>
</div>

<div class="quick" onclick="page('quests')">
<div class="emoji">🏆</div>
<b>Lihat Misi</b>
</div>

</div>

<br>

<div class="grid">

<div class="card">

<h2>☀️ Cuaca</h2>
<br>
<h1 id="homeWeather">Cerah ☀️</h1>

</div>

<div class="card">

<h2>📊 Statistik</h2>
<br>

<p>
🌾 Panen:
<b id="totalHarvest">0</b>
</p>

<p>
🐟 Ikan:
<b id="totalFish">0</b>
</p>

<p>
🐄 Hewan:
<b id="animalCount">2</b>
</p>

</div>

<div class="card">

<h2>💡 Tips</h2>
<br>

<p id="tip">
Jangan lupa menyiram tanaman!
</p>

</div>

</div>

</section>


<!-- KEBUN -->

<section id="farm" class="page">

<div class="page-title">

<h1>🌾 Kebun Saya</h1>

<p>
Klik petak untuk menanam.
Klik tanaman siap panen untuk memanen.
</p>

</div>

<div class="weather">

<h2 id="weather">
☀️ Cerah
</h2>

<p>
Tanaman sedang tumbuh.
</p>

</div>

<div class="farm" id="farmGrid"></div>

</section>


<!-- TOKO -->

<section id="shop" class="page">

<div class="page-title">

<h1>🛒 Toko Bibit</h1>

<p>Beli bibit tanaman.</p>

</div>

<div class="grid" id="shopGrid"></div>

</section>


<!-- INVENTORI -->

<section id="inventory" class="page">

<div class="page-title">

<h1>🎒 Inventori</h1>

<p>Hasil panen yang kamu miliki.</p>

</div>

<div class="inventory-grid" id="inventoryGrid"></div>

</section>


<!-- PASAR -->

<section id="market" class="page">

<div class="page-title">

<h1>💰 Pasar</h1>

<p>Jual hasil panen.</p>

</div>

<div class="card">

<table class="market-table">

<thead>

<tr>
<th>Tanaman</th>
<th>Jumlah</th>
<th>Harga</th>
<th>Aksi</th>
</tr>

</thead>

<tbody id="marketTable"></tbody>

</table>

</div>

</section>


<!-- PETERNAKAN -->

<section id="animals" class="page">

<div class="page-title">

<h1>🐄 Peternakan</h1>

<p>Rawat hewanmu.</p>

</div>

<div class="grid">

<div class="card animal">

<div class="animal-icon">🐄</div>

<h2>Sapi</h2>

<p>Menghasilkan susu.</p>

<br>

<button class="action primary"
onclick="collectAnimal('sapi')">

🥛 Ambil Susu

</button>

</div>


<div class="card animal">

<div class="animal-icon">🐔</div>

<h2>Ayam</h2>

<p>Menghasilkan telur.</p>

<br>

<button class="action primary"
onclick="collectAnimal('ayam')">

🥚 Ambil Telur

</button>

</div>


<div class="card animal">

<div class="animal-icon">🐑</div>

<h2>Domba</h2>

<p>Menghasilkan wol.</p>

<br>

<button class="action primary"
onclick="collectAnimal('domba')">

🧶 Ambil Wol

</button>

</div>

</div>

</section>


<!-- KOLAM -->

<section id="pond" class="page">

<div class="page-title">

<h1>🐟 Kolam Pemancingan</h1>

<p>Gunakan energi untuk memancing.</p>

</div>

<div class="pond">

<div class="fish">🐟</div>

<h2>Kolam Tenang</h2>

<p>
Siapa tahu dapat ikan langka!
</p>

<br>

<button
class="action"
style="background:white;color:#0284c7"
onclick="fish()">

🎣 Memancing (-10 Energi)

</button>

</div>

</section>


<!-- MISI -->

<section id="quests" class="page">

<div class="page-title">

<h1>🏆 Misi</h1>

<p>Selesaikan misi.</p>

</div>

<div id="questList"></div>

</section>


<!-- HADIAH -->

<section id="daily" class="page">

<div class="page-title">

<h1>🎁 Hadiah Harian</h1>

<p>Ambil hadiah setiap hari.</p>

</div>

<div class="card" style="text-align:center">

<div style="font-size:100px">🎁</div>

<h2>Hadiah Hari Ini</h2>

<p>
Dapatkan 💰250 gratis.
</p>

<br>

<button
class="action primary"
onclick="dailyReward()">

🎁 Ambil Hadiah

</button>

</div>

</section>


<!-- PROFIL -->

<section id="profile" class="page">

<div class="page-title">

<h1>👤 Profil Petani</h1>

<p>Atur nama pemainmu.</p>

</div>

<div class="card profile">

<div class="avatar">
👨‍🌾
</div>

<h2 id="playerName">
Petani
</h2>

<br>

<input
id="nameInput"
class="name-input"
type="text"
placeholder="Masukkan nama kamu"
maxlength="20">

<br><br>

<button
class="action primary"
onclick="saveName()">

💾 Simpan Nama

</button>

<br><br>

<h3>
⭐ Level <span id="profileLevel">1</span>
</h3>

<br>

<p>
XP:
<span id="xpText">0 / 100</span>
</p>

<div class="xpbar">

<div id="xpBar"
style="width:0%">
</div>

</div>

<p>
💰 Uang:
<b id="profileMoney">500</b>
</p>

<br>

<p>
🌾 Total Panen:
<b id="profileHarvest">0</b>
</p>

</div>

</section>


<!-- PENGATURAN -->

<section id="settings" class="page">

<div class="page-title">

<h1>⚙️ Pengaturan</h1>

<p>Atur game.</p>

</div>

<div class="setting">

<div>
<h3>🌙 Mode Gelap</h3>
<p>Aktifkan tema gelap.</p>
</div>

<button
class="action primary"
onclick="darkMode()">

Toggle

</button>

</div>


<div class="setting">

<div>
<h3>💾 Reset Game</h3>
<p>Hapus semua progress.</p>
</div>

<button
class="action danger"
onclick="resetGame()">

Reset

</button>

</div>

</section>


<!-- TENTANG -->

<section id="about" class="page">

<div class="page-title">

<h1>ℹ️ Tentang FarmLife</h1>

</div>

<div class="card">

<h2>🌱 FarmLife</h2>

<br>

<p>
FarmLife adalah game simulasi perkebunan
berbasis web.
</p>

<br>

<p>
Tanam tanaman, panen, jual hasil,
rawat hewan, memancing, menyelesaikan
misi dan meningkatkan level.
</p>

<br>

<h3>
🎮 Tujuan
</h3>

<br>

<p>
Jadilah petani terkaya!
</p>

</div>

</section>

</main>

</div>


<!-- MODAL TANAM -->

<div class="modal" id="plantModal">

<div class="modal-box">

<h2>🌱 Tanam Tanaman</h2>

<p>Pilih bibit.</p>

<div id="plantOptions"></div>

<br>

<button
class="action danger"
onclick="closeModal()">

Batal

</button>

</div>

</div>


<div class="toast" id="toast">
Berhasil!
</div>


<script>

/* ================================
   DATA GAME
================================ */

let game =
JSON.parse(localStorage.getItem("farmlife"))
|| {

name:"Petani",

money:500,

energy:100,

level:1,

xp:0,

totalHarvest:0,

totalFish:0,

seeds:{
wheat:3,
carrot:2,
tomato:1,
corn:0
},

crops:{
wheat:0,
carrot:0,
tomato:0,
corn:0
},

plots:Array(12).fill(null),

animals:2,

daily:false

};


/* ================================
   TANAMAN
================================ */

const crops={

wheat:{
name:"Gandum",
emoji:"🌾",
price:35,
seedPrice:20,
time:15,
xp:10
},

carrot:{
name:"Wortel",
emoji:"🥕",
price:55,
seedPrice:30,
time:20,
xp:15
},

tomato:{
name:"Tomat",
emoji:"🍅",
price:80,
seedPrice:45,
time:30,
xp:20
},

corn:{
name:"Jagung",
emoji:"🌽",
price:110,
seedPrice:65,
time:40,
xp:25
}

};


/* ================================
   SAVE
================================ */

function save(){

localStorage.setItem(
"farmlife",
JSON.stringify(game)
);

updateUI();
updateName();

}


/* ================================
   TOAST
================================ */

function toast(message){

let t=document.getElementById("toast");

t.innerText=message;

t.classList.add("show");

setTimeout(()=>{
t.classList.remove("show");
},2500);

}


/* ================================
   NAVIGATION
================================ */

function page(id,button){

document
.querySelectorAll(".page")
.forEach(p=>p.classList.remove("active"));

document
.getElementById(id)
.classList.add("active");

document
.querySelectorAll(".sidebar button")
.forEach(b=>b.classList.remove("active"));

if(button)
button.classList.add("active");

if(id==="farm")
renderFarm();

if(id==="shop")
renderShop();

if(id==="inventory")
renderInventory();

if(id==="market")
renderMarket();

if(id==="quests")
renderQuests();

updateUI();
updateName();

}


/* ================================
   UPDATE UI
================================ */

function updateUI(){

document.getElementById("money")
.innerText=game.money;

document.getElementById("level")
.innerText=game.level;

document.getElementById("energy")
.innerText=game.energy;

document.getElementById("profileLevel")
.innerText=game.level;

document.getElementById("profileMoney")
.innerText=game.money;

document.getElementById("profileHarvest")
.innerText=game.totalHarvest;

document.getElementById("totalHarvest")
.innerText=game.totalHarvest;

document.getElementById("totalFish")
.innerText=game.totalFish;

document.getElementById("animalCount")
.innerText=game.animals;

let needed=game.level*100;

document.getElementById("xpText")
.innerText=
game.xp+" / "+needed;

document.getElementById("xpBar")
.style.width=
Math.min(100,game.xp/needed*100)+"%";

}


/* ================================
   NAMA PEMAIN
================================ */

function updateName(){

let name=game.name || "Petani";

document.getElementById("playerName")
.innerText=name;

document.getElementById("welcomeName")
.innerText=name;

document.getElementById("headerName")
.innerText=name;

let input=
document.getElementById("nameInput");

if(input)
input.value=name;

}


function saveName(){

let input=
document.getElementById("nameInput");

let name=
input.value.trim();

if(name===""){

toast("❌ Nama tidak boleh kosong!");

return;

}

game.name=name;

save();

updateName();

toast(
"✅ Nama berhasil disimpan!"
);

}


/* ================================
   XP
================================ */

function addXP(amount){

game.xp+=amount;

let needed=
game.level*100;

if(game.xp>=needed){

game.xp-=needed;

game.level++;

game.money+=100;

toast(
"🎉 LEVEL UP! Level "+
game.level+
"! Bonus 💰100"
);

}

}


/* ================================
   FARM
================================ */

function renderFarm(){

let grid=
document.getElementById("farmGrid");

grid.innerHTML="";

game.plots.forEach((plot,index)=>{

let div=
document.createElement("div");

div.className="plot";

if(!plot){

div.innerHTML=`

<div class="plant">🌱</div>

<div>Tanam</div>

`;

div.onclick=
()=>openPlant(index);

}else{

let crop=crops[plot.type];

let elapsed=
(Date.now()-plot.planted)/1000;

let ready=
elapsed>=crop.time;

let remaining=
Math.max(
0,
Math.ceil(crop.time-elapsed)
);

div.innerHTML=`

<div class="plant">

${ready ? crop.emoji : "🌱"}

</div>

<b>${crop.name}</b>

<div class="timer">

${
ready
?
"✨ SIAP PANEN!"
:
"⏳ "+remaining+" detik"
}

</div>

`;

div.onclick=()=>{

if(ready)
harvest(index);

else
toast("⏳ Belum siap dipanen!");

};

}

grid.appendChild(div);

});

}


/* ================================
   MODAL TANAM
================================ */

let selectedPlot=null;


function openPlant(index){

selectedPlot=index;

let options=
document.getElementById("plantOptions");

options.innerHTML="";

Object.keys(crops).forEach(type=>{

let c=crops[type];

let button=
document.createElement("button");

button.className=
"action primary";

button.style.width="100%";

button.style.marginTop="10px";

button.innerText=
c.emoji+
" "+
c.name+
" ("+
game.seeds[type]+
" bibit)";

button.onclick=
()=>plant(type);

options.appendChild(button);

});

document
.getElementById("plantModal")
.classList.add("show");

}


function closeModal(){

document
.getElementById("plantModal")
.classList.remove("show");

}


function plant(type){

if(game.seeds[type]<=0){

toast("❌ Bibit habis!");

return;

}

if(game.energy<5){

toast("⚡ Energi tidak cukup!");

return;

}

game.seeds[type]--;

game.energy-=5;

game.plots[selectedPlot]={

type:type,

planted:Date.now()

};

closeModal();

save();

renderFarm();

toast(
"🌱 "+crops[type].name+
" berhasil ditanam!"
);

}


/* ================================
   PANEN
================================ */

function harvest(index){

let plot=game.plots[index];

if(!plot)return;

let crop=crops[plot.type];

game.crops[plot.type]++;

game.totalHarvest++;

game.plots[index]=null;

addXP(crop.xp);

save();

renderFarm();

toast(
"🌾 Panen "+crop.name+
"! +"+crop.xp+" XP"
);

}


/* ================================
   SHOP
================================ */

function renderShop(){

let grid=
document.getElementById("shopGrid");

grid.innerHTML="";

Object.keys(crops).forEach(type=>{

let c=crops[type];

let div=
document.createElement("div");

div.className="item";

div.innerHTML=`

<div class="item-icon">
${c.emoji}
</div>

<h3>${c.name}</h3>

<p>
Tumbuh: ${c.time} detik
</p>

<p>
💰 ${c.seedPrice}
</p>

<button
class="action primary"
style="width:100%"
onclick="buySeed('${type}')">

🌱 Beli Bibit

</button>

`;

grid.appendChild(div);

});

}


function buySeed(type){

let c=crops[type];

if(game.money<c.seedPrice){

toast("❌ Uang tidak cukup!");

return;

}

game.money-=c.seedPrice;

game.seeds[type]++;

save();

toast(
"🌱 Membeli bibit "+c.name
);

}


/* ================================
   INVENTORY
================================ */

function renderInventory(){

let grid=
document.getElementById("inventoryGrid");

grid.innerHTML="";

Object.keys(crops).forEach(type=>{

let c=crops[type];

let div=
document.createElement("div");

div.className=
"inventory-item";

div.innerHTML=`

<div class="emoji">
${c.emoji}
</div>

<b>${c.name}</b>

<strong>
${game.crops[type]}
</strong>

<small>
hasil panen
</small>

`;

grid.appendChild(div);

});

}


/* ================================
   MARKET
================================ */

function renderMarket(){

let table=
document.getElementById("marketTable");

table.innerHTML="";

Object.keys(crops).forEach(type=>{

let c=crops[type];

let tr=
document.createElement("tr");

tr.innerHTML=`

<td>
${c.emoji} ${c.name}
</td>

<td>
${game.crops[type]}
</td>

<td>
💰 ${c.price}
</td>

<td>

<button
class="action primary"
onclick="sell('${type}')">

Jual

</button>

</td>

`;

table.appendChild(tr);

});

}


function sell(type){

if(game.crops[type]<=0){

toast("❌ Tidak punya hasil panen!");

return;

}

let c=crops[type];

game.crops[type]--;

game.money+=c.price;

addXP(5);

save();

renderMarket();

toast(
"💰 "+c.name+
" terjual!"
);

}


/* ================================
   HEWAN
================================ */

function collectAnimal(type){

if(game.energy<5){

toast("⚡ Energi tidak cukup!");

return;

}

game.energy-=5;

let reward=30;

let text="🥛 Susu";

if(type==="ayam"){

reward=20;

text="🥚 Telur";

}

if(type==="domba"){

reward=40;

text="🧶 Wol";

}

game.money+=reward;

addXP(5);

save();

toast(
text+
" diperoleh! +💰"+
reward
);

}


/* ================================
   MEMANCING
================================ */

function fish(){

if(game.energy<10){

toast("⚡ Energi tidak cukup!");

return;

}

game.energy-=10;

let chance=Math.random();

let reward;

if(chance<0.1){

reward=200;

toast("🐠 IKAN LANGKA! +💰200");

}else if(chance<0.4){

reward=80;

toast("🐟 Ikan besar! +💰80");

}else{

reward=30;

toast("🐟 Mendapat ikan! +💰30");

}

game.money+=reward;

game.totalFish++;

addXP(10);

save();

}


/* ================================
   MISI
================================ */

function renderQuests(){

let list=
document.getElementById("questList");

list.innerHTML="";

let quests=[

[
"🌾 Petani Pemula",
"Panen 5 tanaman.",
game.totalHarvest,
5
],

[
"💰 Pedagang Sukses",
"Kumpulkan 1.000 koin.",
game.money,
1000
],

[
"🎣 Nelayan",
"Tangkap 3 ikan.",
game.totalFish,
3
]

];

quests.forEach(q=>{

let current=q[2];

let target=q[3];

let percent=
Math.min(
100,
current/target*100
);

let div=
document.createElement("div");

div.className="quest";

div.innerHTML=`

<h3>${q[0]}</h3>

<p>${q[1]}</p>

<div class="progress">

<div style="width:${percent}%"></div>

</div>

<p>
${Math.min(current,target)}
/
${target}
</p>

<br>

<b style="color:
${current>=target
?"#22c55e"
:"#64748b"}">

${
current>=target
?
"✅ Misi Selesai!"
:
"🔒 Belum selesai"
}

</b>

`;

list.appendChild(div);

});

}


/* ================================
   HADIAH
================================ */

function dailyReward(){

if(game.daily){

toast(
"🎁 Hadiah sudah diambil!"
);

return;

}

game.money+=250;

game.daily=true;

addXP(20);

save();

toast(
"🎁 Hadiah harian +💰250!"
);

}


/* ================================
   DARK MODE
================================ */

function darkMode(){

document.body.classList.toggle("dark");

}


/* ================================
   RESET
================================ */

function resetGame(){

if(
confirm(
"Yakin ingin menghapus semua progress?"
)
){

localStorage.removeItem("farmlife");

location.reload();

}

}


/* ================================
   CUACA
================================ */

function changeWeather(){

let list=[
"☀️ Cerah",
"🌤️ Berawan",
"🌧️ Hujan",
"🌈 Pelangi"
];

let weather=
list[
Math.floor(
Math.random()*list.length
)
];

document.getElementById("weather")
.innerText=weather;

document.getElementById("homeWeather")
.innerText=weather;

}


/* ================================
   TIPS
================================ */

let tips=[

"🌱 Tanam banyak tanaman untuk mendapatkan XP.",

"💰 Jual hasil panen di pasar.",

"⚡ Gunakan energi dengan bijak.",

"🎁 Jangan lupa hadiah harian.",

"🎣 Memancing bisa mendapatkan ikan langka."

];

document.getElementById("tip")
.innerText=
tips[
Math.floor(
Math.random()*tips.length
)
];


/* ================================
   UPDATE TANAMAN
================================ */

setInterval(()=>{

if(
document
.getElementById("farm")
.classList
.contains("active")
){

renderFarm();

}

},1000);


/* ================================
   REGEN ENERGI
================================ */

setInterval(()=>{

if(game.energy<100){

game.energy++;

save();

}

},10000);


/* ================================
   START
================================ */

renderFarm();

renderShop();

renderInventory();

renderMarket();

renderQuests();

updateUI();

updateName();

changeWeather();

</script>

</body>
</html>
