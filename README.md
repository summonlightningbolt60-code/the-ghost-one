# the-ghost-one
ไม่รู้

<!DOCTYPE html>
<html lang="th">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>THE GHOST ONE | FAN ART</title>
<style>
*{box-sizing:border-box}
body{
 margin:0;background:#080808;color:#fff;
 font-family:Arial,"Noto Sans Thai",sans-serif;
}
header{
 padding:20px 7%;border-bottom:1px solid #333;
 display:flex;justify-content:space-between;
 align-items:center;background:#080808;
}
.logo{font-size:18px;font-weight:900;letter-spacing:3px}
nav a{color:#aaa;text-decoration:none;margin-left:18px}
nav a:hover{color:white}
.hero{
 min-height:350px;display:flex;flex-direction:column;
 justify-content:center;align-items:center;text-align:center;
 padding:50px 20px;
 background:radial-gradient(ellipse,#292929,#080808 70%);
}
.hero h1{font-size:clamp(35px,8vw,75px);margin:15px 0;letter-spacing:5px}
.hero p{color:#aaa}
.universe{border:1px solid #777;padding:10px 20px;letter-spacing:4px}
main{max-width:1150px;margin:auto;padding:45px 20px}
.heading{display:flex;justify-content:space-between;gap:15px;flex-wrap:wrap}
.heading h2{letter-spacing:3px}
input,select{
 background:#151515;color:white;border:1px solid #444;
 padding:12px;border-radius:3px;
}
.gallery{
 display:grid;grid-template-columns:repeat(3,1fr);
 gap:18px;margin-top:25px;
}
.card{background:#121212;border:1px solid #333;overflow:hidden}
.card img{width:100%;aspect-ratio:4/3;object-fit:cover;display:block}
.info{padding:15px}
.info p{color:#aaa;font-size:13px}
.tag{font-size:11px;color:#aaa;border:1px solid #555;padding:5px}
.empty{grid-column:1/-1;text-align:center;color:#888;padding:60px 10px;border:1px dashed #444}
.about{border-top:1px solid #333;margin-top:60px;padding-top:35px;color:#aaa;line-height:1.8}
footer{padding:30px;text-align:center;border-top:1px solid #333;color:#777;font-size:12px}
@media(max-width:700px){.gallery{grid-template-columns:repeat(2,1fr)}}
@media(max-width:420px){.gallery{grid-template-columns:1fr}header{padding:18px 15px}nav a{margin-left:8px;font-size:12px}}
</style>
</head>
<body>

<header>
 <div class="logo">THE GHOST ONE</div>
 <nav>
  <a href="#home">หน้าแรก</a>
  <a href="#gallery">แกลเลอรี</a>
  <a href="#about">เกี่ยวกับ</a>
 </nav>
</header>

<section class="hero" id="home">
 <p>OFFICIAL FAN ART ARCHIVE</p>
 <h1>THE GHOST ONE</h1>
 <p>พื้นที่จัดแสดงผลงานแฟนอาร์ต</p>
 <div class="universe">UNIVERSE 1789</div>
</section>

<main>
 <section id="gallery">
  <div class="heading">
   <div>
    <h2>แกลเลอรีผลงาน</h2>
    <small style="color:#888">THE GHOST ONE FAN ART COLLECTION</small>
   </div>
   <div>
    <input id="search" placeholder="ค้นหาผลงาน...">
    <select id="sort">
     <option value="new">ใหม่ล่าสุด</option>
     <option value="old">เก่าที่สุด</option>
    </select>
   </div>
  </div>
  <div class="gallery" id="galleryList">
   <div class="empty">ยังไม่มีผลงานในแกลเลอรี</div>
  </div>
 </section>

 <section class="about" id="about">
  <h2>ABOUT THE GALLERY</h2>
  <p>
   THE GHOST ONE FAN ART GALLERY
   คือพื้นที่รวบรวมผลงานแฟนอาร์ตจากจักรวาล
   Universe 1789
  </p>
  <p>ผู้เข้าชมสามารถรับชมผลงานได้ โดยการเผยแพร่ภาพสงวนไว้สำหรับเจ้าของเว็บไซต์</p>
 </section>
</main>

<footer>
 © THE GHOST ONE — UNIVERSE 1789
</footer>

<script>
const artworks = [];

function render(){
 const q=document.getElementById("search").value.toLowerCase();
 const sort=document.getElementById("sort").value;
 let list=artworks.filter(a=>a.title.toLowerCase().includes(q));
 list.sort((a,b)=>sort==="new"?b.date-a.date:a.date-b.date);

 const gallery=document.getElementById("galleryList");
 gallery.innerHTML=list.length?list.map(a=>`
  <article class="card">
   <img src="${a.image}" alt="">
   <div class="info">
    <h3>${a.title}</h3>
    <p>${a.description}</p>
    <span class="tag">${a.category}</span>
   </div>
  </article>
 `).join(""):'<div class="empty">ยังไม่มีผลงานในแกลเลอรี</div>';
}

document.getElementById("search").addEventListener("input",render);
document.getElementById("sort").addEventListener("change",render);
render();
</script>

</body>
</html>
