<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>FarmLife 🌱</title>

<style>

/* =====================================================
   DASAR
===================================================== */

*{
    box-sizing:border-box;
    margin:0;
    padding:0;
}

:root{
    --green:#22c55e;
    --dark-green:#15803d;
    --light-green:#dcfce7;
    --yellow:#facc15;
    --brown:#92400e;
    --blue:#3b82f6;
    --red:#ef4444;
    --purple:#8b5cf6;
    --bg:#f0fdf4;
    --card:#ffffff;
    --text:#172033;
    --muted:#64748b;
}

body{
    font-family:Arial,Helvetica,sans-serif;
    background:var(--bg);
    color:var(--text);
    min-height:100vh;
}

/* DARK MODE */

body.dark{
    --bg:#0f172a;
    --card:#1e293b;
    --text:#f8fafc;
    --muted:#cbd5e1;
}

/* =====================================================
   HEADER
===================================================== */

header{
    background:var(--card);
    padding:15px 5%;
    display:flex;
    justify-content:space-between;
    align-items:center;
    gap:15px;
    position:sticky;
    top:0;
    z-index:1000;
    box-shadow:0 3px 15px #00000015;
}

.logo{
    font-size:24px;
    font-weight:bold;
    color:var(--green);
}

.logo span{
    color:var(--text);
}

.player-info{
    display:flex;
    gap:10px;
    align-items:center;
    flex-wrap:wrap;
}

.stat{
    background:var(--bg);
    padding:8px 12px;
    border-radius:12px;
    font-weight:bold;
    font-size:14px;
}

/* =====================================================
   SIDEBAR
===================================================== */

.layout{
    display:flex;
    min-height:calc(100vh - 70px);
}

.sidebar{
    width:230px;
    background:#166534;
    padding:20px 12px;
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
    font-size:14px;
    font-weight:bold;
}

.sidebar button:hover,
.sidebar button.active{
    background:#22c55e;
}

.main{
    flex:1;
    padding:25px;
    overflow:hidden;
}

/* =====================================================
   PAGE
===================================================== */

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

/* =====================================================
   CARD
===================================================== */

.card{
    background:var(--card);
    border-radius:18px;
    padding:20px;
    box-shadow:0 7px 20px #0000000d;
}

.grid{
    display:grid;
    grid-template-columns:repeat(3,1fr);
    gap:20px;
}

/* =====================================================
   HOME
===================================================== */

.welcome{
    background:linear-gradient(135deg,#16a34a,#4ade80);
    color:white;
    border-radius:25px;
    padding:35px;
    margin-bottom:25px;
    display:flex;
    justify-content:space-between;
    align-items:center;
    gap:20px;
}

.welcome h1{
    font-size:40px;
    margin-bottom:10px;
}

.welcome-art{
    font-size:100px;
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
    box-shadow:0 5px 15px #0000000c;
}

.quick:hover{
    transform:translateY(-4px);
}

.quick .emoji{
    font-size:40px;
    margin-bottom:8px;
}

/* =====================================================
   KEBUN
===================================================== */

.weather{
    background:linear-gradient(135deg,#60a5fa,#38bdf8);
    color:white;
    border-radius:18px;
    padding:20px;
    margin-bottom:20px;
    display:flex;
    justify-content:space-between;
    align-items:center;
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
    position:relative;
    overflow:hidden;
}

.plot:hover{
    filter:brightness(1.15);
}

.plot .plant{
    font-size:48px;
}

.plot .timer{
    font-size:12px;
    margin-top:5px;
    color:#fef3c7;
}

.empty{
    color:#fde68a;
    font-size:14px;
}

/* =====================================================
   SHOP
===================================================== */

.item{
    background:var(--card);
    border-radius:18px;
    padding:20px;
    box-shadow:0 6px 18px #0000000d;
}

.item .item-icon{
    font-size:55px;
    margin-bottom:10px;
}

.item h3{
    margin-bottom:5px;
}

.item p{
    color:var(--muted);
    margin-bottom:10px;
}

.price{
    color:#ca8a04;
    font-weight:bold;
}

button.primary{
    background:var(--green);
    color:white;
}

button.secondary{
    background:var(--blue);
    color:white;
}

button.danger{
    background:var(--red);
    color:white;
}

.action{
    border:0;
    padding:10px 15px;
    border-radius:10px;
    cursor:pointer;
    font-weight:bold;
}

/* =====================================================
   INVENTORI
===================================================== */

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
}

/* =====================================================
   MARKET
===================================================== */

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

/* =====================================================
   PETERNakan
===================================================== */

.animal{
    text-align:center;
}

.animal-icon{
    font-size:70px;
    margin-bottom:10px;
}

/* =====================================================
   KOLAM
===================================================== */

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
    margin-bottom:15px;
}

/* =====================================================
   QUEST
===================================================== */

.quest{
    background:var(--card);
    padding:20px;
    border-radius:18px;
    margin-bottom:15px;
    box-shadow:0 5px 15px #0000000b;
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
    background:var(--green);
}

/* =====================================================
   PROFILE
===================================================== */

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

.level{
    font-size:20px;
    font-weight:bold;
    color:var(--green);
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
    background:linear-gradient(90deg,#22c55e,#84cc16);
}

/* =====================================================
   SETTINGS
===================================================== */

.setting{
    display:flex;
    justify-content:space-between;
    align-items:center;
    background:var(--card);
    padding:20px;
    border-radius:15px;
    margin-bottom:12px;
}

.switch{
    width:50px;
    height:28px;
    border-radius:20px;
    background:#cbd5e1;
    cursor:pointer;
}

.switch.on{
    background:var(--green);
}

/* =====================================================
   MODAL
===================================================== */

.modal{
    position:fixed;
    inset:0;
    background:#00000088;
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

.modal-box h2{
    margin-bottom:15px;
}

.modal-buttons{
    display:flex;
    gap:10px;
    margin-top:20px;
}

.modal-buttons button{
    flex:1;
}

/* =====================================================
   TOAST
===================================================== */

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

/* =====================================================
   MOBILE
===================================================== */

@media(max-width:900px){

    .layout{
        display:block;
    }

    .sidebar{
        width:100%;
        display:flex;
        overflow-x:auto;
        gap:5px;
        padding:10px;
    }

    .sidebar button{
        min-width:max-content;
        margin:0;
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

    .welcome-art{
        display:none;
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

    .welcome h1{
        font-size:30px;
    }

    .main{
        padding:15px;
    }

}

</style>
</head>

<body>

<!-- =====================================================
     HEADER
===================================================== -->

<header>

    <div class="logo">
        🌱 Farm<span>Life</span>
    </div>

    <div class="player-info">

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

<!-- =====================================================
     SIDEBAR
===================================================== -->

<aside class="sidebar">

    <button class="active" onclick="page('home',this)">
        🏡 Beranda
    </button>

    <button onclick="page('farm',this)">
        🌾 Kebun
    </button>

    <button onclick="page('shop',this)">
        🛒 Toko
    </button>

    <button onclick="page('inventory',this)">
        🎒 Inventori
    </button>

    <button onclick="page('market',this)">
        💰 Pasar
    </button>

    <button onclick="page('animals',this)">
        🐄 Peternakan
    </button>

    <button onclick="page('pond',this)">
        🐟 Kolam
    </button>

    <button onclick="page('quests',this)">
        🏆 Misi
    </button>

    <button onclick="page('daily',this)">
        🎁 Hadiah
    </button>

    <button onclick="page('profile',this)">
        👤 Profil
    </button>

    <button onclick="page('settings',this)">
        ⚙️ Pengaturan
    </button>

    <button onclick="page('about',this)">
        ℹ️ Tentang
    </button>

</aside>


<!-- =====================================================
     MAIN
===================================================== -->

<main class="main">


<!-- =====================================================
     1. HOME
===================================================== -->

<section id="home" class="page active">

    <div class="welcome">

        <div>

            <h1>Selamat datang, Petani! 🌱</h1>

            <p>
                Bangun perkebunan impianmu,
                tanam tanaman, rawat hewan,
                dan jadilah petani terbaik!
            </p>

        </div>

        <div class="welcome-art">
            🌻
        </div>

    </div>


    <div class="quick-grid">

        <div class="quick"
             onclick="page('farm')">
            <div class="emoji">🌾</div>
            <b>Kelola Kebun</b>
        </div>

        <div class="quick"
             onclick="page('shop')">
            <div class="emoji">🛒</div>
            <b>Belanja Bibit</b>
        </div>

        <div class="quick"
             onclick="page('market')">
            <div class="emoji">💰</div>
            <b>Jual Panen</b>
        </div>

        <div class="quick"
             onclick="page('quests')">
            <div class="emoji">🏆</div>
            <b>Lihat Misi</b>
        </div>

    </div>


    <br>


    <div class="grid">

        <div class="card">

            <h2>☀️ Cuaca Hari Ini</h2>

            <br>

            <h1 id="homeWeather">
                Cerah ☀️
            </h1>

            <p>
                Tanaman tumbuh dengan baik hari ini.
            </p>

        </div>


        <div class="card">

            <h2>📈 Statistik</h2>

            <br>

            <p>
                🌾 Tanaman dipanen:
                <b id="totalHarvest">0</b>
            </p>

            <p>
                🐟 Ikan ditangkap:
                <b id="totalFish">0</b>
            </p>

            <p>
                🐄 Hewan:
                <b id="animalCount">2</b>
            </p>

        </div>


        <div class="card">

            <h2>💡 Tips Petani</h2>

            <br>

            <p id="tip">
                Jangan lupa menyiram tanamanmu!
            </p>

        </div>

    </div>

</section>


<!-- =====================================================
     2. FARM
===================================================== -->

<section id="farm" class="page">

    <div class="page-title">

        <h1>🌾 Kebun Saya</h1>

        <p>
            Klik petak kosong untuk menanam.
            Klik tanaman siap panen untuk memanen.
        </p>

    </div>


    <div class="weather">

        <div>
            <h2 id="weather">
                ☀️ Cerah
            </h2>

            <p>
                Cuaca mempengaruhi pertumbuhan tanaman.
            </p>
        </div>

        <div style="font-size:50px">
            🌤️
        </div>

    </div>


    <div class="farm" id="farmGrid"></div>

</section>


<!-- =====================================================
     3. SHOP
===================================================== -->

<section id="shop" class="page">

    <div class="page-title">

        <h1>🛒 Toko Bibit</h1>

        <p>
            Beli bibit untuk menanam tanaman baru.
        </p>

    </div>


    <div class="grid" id="shopGrid"></div>

</section>


<!-- =====================================================
     4. INVENTORY
===================================================== -->

<section id="inventory" class="page">

    <div class="page-title">

        <h1>🎒 Inventori</h1>

        <p>
            Semua barang yang kamu miliki.
        </p>

    </div>


    <div class="inventory-grid" id="inventoryGrid"></div>

</section>


<!-- =====================================================
     5. MARKET
===================================================== -->

<section id="market" class="page">

    <div class="page-title">

        <h1>💰 Pasar</h1>

        <p>
            Jual hasil panenmu dan dapatkan uang.
        </p>

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


<!-- =====================================================
     6. ANIMALS
===================================================== -->

<section id="animals" class="page">

    <div class="page-title">

        <h1>🐄 Peternakan</h1>

        <p>
            Rawat hewanmu untuk mendapatkan produk.
        </p>

    </div>


    <div class="grid">

        <div class="card animal">

            <div class="animal-icon">
                🐄
            </div>

            <h2>Sapi</h2>

            <p>
                Menghasilkan susu.
            </p>

            <br>

            <button class="action primary"
                    onclick="collectAnimal('sapi')">
                🥛 Ambil Susu
            </button>

        </div>


        <div class="card animal">

            <div class="animal-icon">
                🐔
            </div>

            <h2>Ayam</h2>

            <p>
                Menghasilkan telur.
            </p>

            <br>

            <button class="action primary"
                    onclick="collectAnimal('ayam')">
                🥚 Ambil Telur
            </button>

        </div>


        <div class="card animal">

            <div class="animal-icon">
                🐑
            </div>

            <h2>Domba</h2>

            <p>
                Menghasilkan wol.
            </p>

            <br>

            <button class="action primary"
                    onclick="collectAnimal('domba')">
                🧶 Ambil Wol
            </button>

        </div>

    </div>

</section>


<!-- =====================================================
     7. POND
===================================================== -->

<section id="pond" class="page">

    <div class="page-title">

        <h1>🐟 Kolam Pemancingan</h1>

        <p>
            Gunakan energi untuk memancing ikan.
        </p>

    </div>


    <div class="pond">

        <div class="fish">
            🐟
        </div>

        <h2>
            Kolam Tenang
        </h2>

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


<!-- =====================================================
     8. QUEST
===================================================== -->

<section id="quests" class="page">

    <div class="page-title">

        <h1>🏆 Misi & Pencapaian</h1>

        <p>
            Selesaikan misi untuk mendapatkan hadiah.
        </p>

    </div>


    <div id="questList"></div>

</section>


<!-- =====================================================
     9. DAILY
===================================================== -->

<section id="daily" class="page">

    <div class="page-title">

        <h1>🎁 Hadiah Harian</h1>

        <p>
            Login setiap hari untuk mendapatkan hadiah.
        </p>

    </div>


    <div class="card"
         style="text-align:center">

        <div style="font-size:100px">
            🎁
        </div>

        <h2>
            Hadiah Hari Ini
        </h2>

        <p>
            Kamu bisa mendapatkan
            <b>💰 250</b> koin gratis.
        </p>

        <br>

        <button
            class="action primary"
            onclick="dailyReward()">

            🎁 Ambil Hadiah

        </button>

    </div>

</section>


<!-- =====================================================
     10. PROFILE
===================================================== -->

<section id="profile" class="page">

    <div class="page-title">

        <h1>👤 Profil Petani</h1>

    </div>


    <div class="card profile">

        <div class="avatar">
            👨‍🌾
        </div>

        <h2>
            Petani Hebat
        </h2>

        <div class="level">
            Level <span id="profileLevel">1</span>
        </div>

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
            💰 Total Uang:
            <b id="profileMoney">500</b>
        </p>

        <p>
            🌾 Total Panen:
            <b id="profileHarvest">0</b>
        </p>

    </div>

</section>


<!-- =====================================================
     11. SETTINGS
===================================================== -->

<section id="settings" class="page">

    <div class="page-title">

        <h1>⚙️ Pengaturan</h1>

        <p>
            Atur pengalaman bermainmu.
        </p>

    </div>


    <div class="setting">

        <div>
            <h3>🌙 Mode Gelap</h3>
            <p>Gunakan tema gelap.</p>
        </div>

        <button
            class="action"
            onclick="darkMode()">

            Toggle

        </button>

    </div>


    <div class="setting">

        <div>
            <h3>🔊 Suara</h3>
            <p>Aktifkan atau matikan suara.</p>
        </div>

        <button
            class="action"
            onclick="toggleSound()">

            <span id="soundText">
                ON
            </span>

        </button>

    </div>


    <div class="setting">

        <div>
            <h3>💾 Data Game</h3>
            <p>Hapus semua progress.</p>
        </div>

        <button
            class="action danger"
            onclick="resetGame()">

            Reset

        </button>

    </div>

</section>


<!-- =====================================================
     12. ABOUT
===================================================== -->

<section id="about" class="page">

    <div class="page-title">

        <h1>ℹ️ Tentang FarmLife</h1>

    </div>


    <div class="card">

        <h2>🌱 FarmLife</h2>

        <br>

        <p>
            FarmLife adalah game simulasi perkebunan
            sederhana berbasis web.
        </p>

        <br>

        <p>
            Kamu dapat menanam tanaman, memanen,
            berdagang, merawat hewan, memancing,
            menyelesaikan misi dan meningkatkan level.
        </p>

        <br>

        <h3>🎮 Tujuan Game</h3>

        <br>

        <p>
            Jadilah petani terkaya dan bangun
            perkebunan impianmu!
        </p>

        <br>

        <p>
            Versi: 1.0
        </p>

    </div>

</section>


</main>
</div>


<!-- =====================================================
     MODAL
===================================================== -->

<div class="modal" id="plantModal">

    <div class="modal-box">

        <h2>🌱 Tanam Tanaman</h2>

        <p>
            Pilih bibit yang ingin ditanam.
        </p>

        <div id="plantOptions"></div>

        <div class="modal-buttons">

            <button
                class="action danger"
                onclick="closeModal()">

                Batal

            </button>

        </div>

    </div>

</div>


<!-- =====================================================
     TOAST
===================================================== -->

<div class="toast" id="toast">
    Berhasil!
</div>


<script>

/* =====================================================
   DATA GAME
===================================================== */

let game = JSON.parse(
    localStorage.getItem("farmlife")
) || {

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

    sound:true,

    daily:false,

    quests:{
        harvest:false,
        money:false,
        fish:false
    }

};


/* =====================================================
   TANAMAN
===================================================== */

const crops = {

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


/* =====================================================
   SAVE
===================================================== */

function save(){

    localStorage.setItem(
        "farmlife",
        JSON.stringify(game)
    );

    updateUI();

}


/* =====================================================
   TOAST
===================================================== */

function toast(message){

    let t=
        document.getElementById("toast");

    t.innerText=message;

    t.classList.add("show");

    setTimeout(()=>{
        t.classList.remove("show");
    },2500);

}


/* =====================================================
   NAVIGATION
===================================================== */

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

    if(button){

        button.classList.add("active");

    }

    if(id==="farm") renderFarm();

    if(id==="shop") renderShop();

    if(id==="inventory") renderInventory();

    if(id==="market") renderMarket();

    if(id==="quests") renderQuests();

    updateUI();

    window.scrollTo({
        top:0,
        behavior:"smooth"
    });

}


/* =====================================================
   UI
===================================================== */

function updateUI(){

    document.getElementById("money").innerText=
        game.money;

    document.getElementById("level").innerText=
        game.level;

    document.getElementById("energy").innerText=
        game.energy;

    document.getElementById("profileLevel").innerText=
        game.level;

    document.getElementById("profileMoney").innerText=
        game.money;

    document.getElementById("profileHarvest").innerText=
        game.totalHarvest;

    document.getElementById("totalHarvest").innerText=
        game.totalHarvest;

    document.getElementById("totalFish").innerText=
        game.totalFish;

    document.getElementById("animalCount").innerText=
        game.animals;

    let xpNeeded=
        game.level*100;

    document.getElementById("xpText").innerText=
        game.xp+" / "+xpNeeded;

    document.getElementById("xpBar").style.width=
        Math.min(
            100,
            game.xp/xpNeeded*100
        )+"%";

}


/* =====================================================
   XP
===================================================== */

function addXP(amount){

    game.xp+=amount;

    let needed=
        game.level*100;

    if(game.xp>=needed){

        game.xp-=needed;

        game.level++;

        game.money+=100;

        toast(
            "🎉 LEVEL UP! Kamu sekarang level "+
            game.level+
            "! Bonus 💰100"
        );

    }

}


/* =====================================================
   FARM
===================================================== */

function renderFarm(){

    let grid=
        document.getElementById("farmGrid");

    grid.innerHTML="";

    game.plots.forEach(
        (plot,index)=>{

        let div=
            document.createElement("div");

        div.className="plot";

        if(!plot){

            div.innerHTML=`

                <div class="plant">
                    🌱
                </div>

                <div class="empty">
                    Tanam
                </div>

            `;

            div.onclick=()=>openPlant(index);

        }else{

            let crop=
                crops[plot.type];

            let elapsed=
                (Date.now()-plot.planted)/1000;

            let ready=
                elapsed>=crop.time;

            let remaining=
                Math.max(
                    0,
                    Math.ceil(
                        crop.time-elapsed
                    )
                );

            div.innerHTML=`

                <div class="plant">
                    ${ready ? crop.emoji : "🌱"}
                </div>

                <b>
                    ${crop.name}
                </b>

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

                if(ready){

                    harvest(index);

                }else{

                    toast(
                        "⏳ Tanaman belum siap dipanen!"
                    );

                }

            };

        }

        grid.appendChild(div);

    });

}


/* =====================================================
   PLANT MODAL
===================================================== */

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

        button.onclick=()=>plant(type);

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

        toast(
            "❌ Kamu tidak punya bibit "+crops[type].name
        );

        return;

    }

    if(game.energy<5){

        toast(
            "⚡ Energi tidak cukup!"
        );

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


/* =====================================================
   HARVEST
===================================================== */

function harvest(index){

    let plot=
        game.plots[index];

    if(!plot)return;

    let crop=
        crops[plot.type];

    game.crops[plot.type]++;

    game.totalHarvest++;

    addXP(crop.xp);

    game.plots[index]=null;

    save();

    renderFarm();

    toast(
        "🌾 Panen "+crop.name+
        "! +"+crop.xp+" XP"
    );

}


/* =====================================================
   SHOP
===================================================== */

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
                Waktu tumbuh:
                ${c.time} detik
            </p>

            <p class="price">
                💰 ${c.seedPrice} / bibit
            </p>

            <button
                class="action primary"
                style="width:100%"
                onclick="buySeed('${type}')">

                Beli Bibit

            </button>

        `;

        grid.appendChild(div);

    });

}


function buySeed(type){

    let c=crops[type];

    if(game.money<c.seedPrice){

        toast(
            "❌ Uang tidak cukup!"
        );

        return;

    }

    game.money-=c.seedPrice;

    game.seeds[type]++;

    save();

    toast(
        "🌱 Membeli 1 bibit "+c.name
    );

}


/* =====================================================
   INVENTORY
===================================================== */

function renderInventory(){

    let grid=
        document.getElementById("inventoryGrid");

    grid.innerHTML="";

    Object.keys(crops).forEach(type=>{

        let c=crops[type];

        let div=
            document.createElement("div");

        div.className="inventory-item";

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


/* =====================================================
   MARKET
===================================================== */

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
                ${c.emoji}
                ${c.name}
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

                    Jual 1

                </button>

            </td>

        `;

        table.appendChild(tr);

    });

}


function sell(type){

    if(game.crops[type]<=0){

        toast(
            "❌ Kamu tidak punya hasil panen."
        );

        return;

    }

    let c=crops[type];

    game.crops[type]--;

    game.money+=c.price;

    addXP(5);

    if(game.money>=1000){

        game.quests.money=true;

    }

    save();

    renderMarket();

    toast(
        "💰 "+c.name+
        " terjual seharga "+
        c.price
    );

}


/* =====================================================
   ANIMAL
===================================================== */

function collectAnimal(type){

    if(game.energy<5){

        toast(
            "⚡ Energi tidak cukup!"
        );

        return;

    }

    game.energy-=5;

    if(type==="sapi"){

        game.money+=30;

        toast(
            "🥛 Mendapatkan susu! +💰30"
        );

    }

    if(type==="ayam"){

        game.money+=20;

        toast(
            "🥚 Mendapatkan telur! +💰20"
        );

    }

    if(type==="domba"){

        game.money+=40;

        toast(
            "🧶 Mendapatkan wol! +💰40"
        );

    }

    addXP(5);

    save();

}


/* =====================================================
   FISHING
===================================================== */

function fish(){

    if(game.energy<10){

        toast(
            "⚡ Energi tidak cukup!"
        );

        return;

    }

    game.energy-=10;

    let chance=
        Math.random();

    if(chance<0.1){

        game.money+=200;

        toast(
            "🐠 IKAN LANGKA! +💰200"
        );

    }else if(chance<0.4){

        game.money+=80;

        toast(
            "🐟 Mendapat ikan besar! +💰80"
        );

    }else{

        game.money+=30;

        toast(
            "🐟 Mendapat ikan! +💰30"
        );

    }

    game.totalFish++;

    addXP(10);

    game.quests.fish=true;

    save();

}


/* =====================================================
   QUEST
===================================================== */

function renderQuests(){

    let list=
        document.getElementById("questList");

    list.innerHTML="";


    let quests=[

        {
            title:"🌾 Petani Pemula",
            desc:"Panen 5 tanaman.",
            current:game.totalHarvest,
            target:5,
            done:game.totalHarvest>=5,
            reward:100
        },

        {
            title:"💰 Pedagang Sukses",
            desc:"Kumpulkan 1.000 koin.",
            current:game.money,
            target:1000,
            done:game.money>=1000,
            reward:250
        },

        {
            title:"🎣 Nelayan",
            desc:"Tangkap 3 ikan.",
            current:game.totalFish,
            target:3,
            done:game.totalFish>=3,
            reward:150
        }

    ];


    quests.forEach(q=>{

        let percent=
            Math.min(
                100,
                q.current/q.target*100
            );

        let div=
            document.createElement("div");

        div.className="quest";

        div.innerHTML=`

            <h3>${q.title}</h3>

            <p>${q.desc}</p>

            <div class="progress">

                <div style="width:${percent}%"></div>

            </div>

            <p>
                ${Math.min(q.current,q.target)}
                / ${q.target}
            </p>

            <br>

            ${
                q.done
                ?
                `<span style="color:#16a34a;font-weight:bold">
                    ✅ Misi Selesai! Hadiah 💰${q.reward}
                </span>`
                :
                `<span style="color:#64748b">
                    🔒 Belum selesai
                </span>`
            }

        `;

        list.appendChild(div);

    });

}


/* =====================================================
   DAILY REWARD
===================================================== */

function dailyReward(){

    if(game.daily){

        toast(
            "🎁 Hadiah hari ini sudah diambil!"
        );

        return;

    }

    game.money+=250;

    game.daily=true;

    addXP(20);

    save();

    toast(
        "🎁 Mendapat hadiah harian 💰250!"
    );

}


/* =====================================================
   SETTINGS
===================================================== */

function darkMode(){

    document.body.classList.toggle("dark");

}


function toggleSound(){

    game.sound=!game.sound;

    document.getElementById("soundText")
        .innerText=
        game.sound
        ?
        "ON"
        :
        "OFF";

    save();

}


function resetGame(){

    let confirmReset=
        confirm(
            "Yakin ingin menghapus semua progress?"
        );

    if(!confirmReset)return;

    localStorage.removeItem("farmlife");

    location.reload();

}


/* =====================================================
   RANDOM WEATHER
===================================================== */

function changeWeather(){

    let weatherList=[

        "☀️ Cerah",

        "🌤️ Berawan",

        "🌧️ Hujan",

        "🌈 Pelangi"

    ];

    let weather=
        weatherList[
            Math.floor(
                Math.random()*
                weatherList.length
            )
        ];

    document.getElementById("weather")
        .innerText=weather;

    document.getElementById("homeWeather")
        .innerText=weather;

}


/* =====================================================
   TIPS
===================================================== */

let tips=[

    "🌱 Tanam tanaman sebanyak mungkin untuk mendapatkan XP.",

    "💰 Jual hasil panen di pasar untuk mendapatkan uang.",

    "⚡ Gunakan energi dengan bijak.",

    "🎁 Jangan lupa mengambil hadiah harian.",

    "🎣 Memancing bisa memberikan ikan langka!",

    "🏆 Selesaikan misi untuk mendapatkan hadiah."

];

document.getElementById("tip").innerText=
    tips[
        Math.floor(
            Math.random()*tips.length
        )
    ];


/* =====================================================
   AUTO UPDATE TANAMAN
===================================================== */

setInterval(()=>{

    if(
        document.getElementById("farm")
        .classList.contains("active")
    ){

        renderFarm();

    }

},1000);


/* =====================================================
   ENERGI REGEN
===================================================== */

setInterval(()=>{

    if(game.energy<100){

        game.energy+=1;

        save();

    }

},10000);


/* =====================================================
   INIT
===================================================== */

renderFarm();

renderShop();

renderInventory();

renderMarket();

renderQuests();

updateUI();

changeWeather();

</script>

</body>
</html>

