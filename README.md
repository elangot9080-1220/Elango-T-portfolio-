<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Elango T — Mage's Grimoire Portfolio</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<style>
@import url('https://fonts.googleapis.com/css2?family=Cinzel:wght@600;700;900&family=MedievalSharp&family=EB+Garamond:ital,wght@0,400;0,600;1,400&display=swap');

:root{
  --night:#0b0a14;
  --night2:#15101f;
  --gold:#d4a948;
  --gold-bright:#f3d27a;
  --clover-green:#2fae6a;
  --blood:#7a1f2b;
  --parchment:#ece2c7;
  --mist:#8d86a8;
}

*{box-sizing:border-box; margin:0; padding:0;}

html{scroll-behavior:smooth;}

body{
  background:
    radial-gradient(ellipse at 20% 0%, rgba(122,31,43,0.18), transparent 55%),
    radial-gradient(ellipse at 80% 10%, rgba(47,174,106,0.10), transparent 50%),
    linear-gradient(180deg, var(--night) 0%, var(--night2) 60%, #090812 100%);
  color:var(--parchment);
  font-family:'EB Garamond', serif;
  overflow-x:hidden;
  position:relative;
  min-height:100vh;
}

/* ---- Ambient floating mana particles ---- */
.mana{
  position:fixed; inset:0; pointer-events:none; z-index:1; overflow:hidden;
}
.mana span{
  position:absolute; bottom:-20px;
  width:4px; height:4px; border-radius:50%;
  background:var(--gold-bright);
  box-shadow:0 0 8px 2px var(--gold-bright);
  animation:rise linear infinite;
  opacity:0.7;
}
@keyframes rise{
  0%{transform:translateY(0) translateX(0); opacity:0;}
  10%{opacity:0.8;}
  100%{transform:translateY(-110vh) translateX(20px); opacity:0;}
}

/* ---- Silhouette training scene (Asta-inspired, generic figure, no IP likeness) ---- */
.training-scene{
  position:fixed; bottom:0; left:0; width:100%; height:38vh;
  z-index:0; pointer-events:none;
  background:
    linear-gradient(180deg, transparent 0%, rgba(5,4,10,0.9) 90%);
}
.training-scene svg{position:absolute; bottom:0; left:0; width:100%; height:100%;}
.tree{fill:#0a0812; opacity:0.85;}
.swordsman{
  transform-origin:bottom center;
  animation:swing 3.2s ease-in-out infinite;
}
@keyframes swing{
  0%,100%{transform:rotate(-3deg);}
  45%{transform:rotate(14deg);}
  55%{transform:rotate(14deg);}
}
.slash-mark{
  opacity:0; animation:flash 3.2s ease-in-out infinite;
}
@keyframes flash{
  0%,40%{opacity:0;}
  48%{opacity:1;}
  60%{opacity:0;}
  100%{opacity:0;}
}

/* ---- Layout shell ---- */
.wrap{position:relative; z-index:2; max-width:980px; margin:0 auto; padding:60px 24px 160px;}

/* ---- Hero / portrait photo ---- */
.hero{text-align:center; margin-bottom:70px;}
.hex-frame{
  position:relative; width:170px; height:260px; margin:0 auto 22px;
  filter:drop-shadow(0 0 22px rgba(212,169,72,0.55));
}
.hex-clip{
  width:100%; height:100%;
  overflow:hidden;
  background:#000;
  position:relative;
  border-radius:4px;
}
.hex-clip img{
  width:100%; height:100%; object-fit:cover; display:block;
  filter:contrast(1.05) saturate(1.05);
}
.hex-ring{
  position:absolute; inset:-10px;
  border-radius:6px;
  background:conic-gradient(from 0deg, var(--gold), var(--clover-green), var(--gold-bright), var(--blood), var(--gold));
  z-index:-1;
  animation:spin 9s linear infinite;
}
@keyframes spin{to{transform:rotate(360deg);}}
.hex-runes{
  position:absolute; inset:-26px; z-index:-2;
  border:1px dashed rgba(212,169,72,0.35); border-radius:10px;
  animation:spin 30s linear infinite reverse;
}

.eyebrow{
  font-family:'MedievalSharp', cursive; letter-spacing:3px; text-transform:uppercase;
  color:var(--clover-green); font-size:.85rem; margin-bottom:8px;
}
h1.name{
  font-family:'Cinzel', serif; font-weight:900; font-size:clamp(2.4rem,6vw,3.6rem);
  color:var(--gold-bright);
  text-shadow:0 0 18px rgba(243,210,122,0.35);
  letter-spacing:1px;
}
.title-sub{
  font-family:'MedievalSharp', cursive; color:var(--mist); font-size:1.05rem; margin-top:10px;
}

/* ---- Section heading ---- */
.section{margin-bottom:64px; position:relative;}
.section-head{
  display:flex; align-items:center; gap:14px; margin-bottom:24px;
}
.section-head .sigil{
  width:26px; height:26px; flex:none;
  clip-path:polygon(50% 0%, 95% 25%, 95% 75%, 50% 100%, 5% 75%, 5% 25%);
  background:linear-gradient(135deg,var(--gold),var(--clover-green));
}
.section-head h2{
  font-family:'Cinzel', serif; font-size:1.5rem; color:var(--gold);
  letter-spacing:1px; text-transform:uppercase;
}
.section-head::after{
  content:''; flex:1; height:1px;
  background:linear-gradient(90deg, rgba(212,169,72,0.6), transparent);
}

.card{
  background:rgba(20,16,30,0.72);
  border:1px solid rgba(212,169,72,0.25);
  border-radius:6px;
  padding:28px 30px;
  backdrop-filter:blur(3px);
  position:relative;
}
.card::before{
  content:''; position:absolute; inset:0; border-radius:6px; padding:1px;
  background:linear-gradient(135deg, rgba(212,169,72,0.5), transparent 40%, rgba(47,174,106,0.3));
  -webkit-mask:linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
  -webkit-mask-composite:xor; mask-composite:exclude; pointer-events:none;
}
.bio p{line-height:1.75; font-size:1.08rem; color:#e9e1c8;}
.bio strong{color:var(--gold-bright);}

.info-grid{display:grid; grid-template-columns:repeat(auto-fit,minmax(220px,1fr)); gap:18px;}
.info-grid .card{padding:20px 22px;}
.info-grid .label{font-family:'MedievalSharp',cursive; color:var(--clover-green); font-size:.8rem; text-transform:uppercase; letter-spacing:1.5px; margin-bottom:6px;}
.info-grid .value{font-size:1.15rem; color:var(--parchment);}

/* ---- Achievements ---- */
.ach-grid{display:grid; grid-template-columns:repeat(auto-fit,minmax(230px,1fr)); gap:20px;}
.ach-card{
  text-align:center;
}
.medal-img{
  width:120px; height:auto; margin:0 auto 14px; display:block;
  filter:drop-shadow(0 0 14px rgba(212,169,72,0.45));
  transition:transform .35s ease;
}
.ach-card:hover .medal-img{transform:scale(1.08) rotate(-3deg);}
.ach-card h3{font-family:'Cinzel',serif; color:var(--gold-bright); font-size:1.05rem; margin-bottom:8px;}
.ach-card p{font-size:.95rem; color:var(--mist); line-height:1.5;}

/* ---- Marks ---- */
.marks-table{width:100%; border-collapse:collapse;}
.marks-table th, .marks-table td{padding:14px 16px; text-align:left; font-size:1rem;}
.marks-table thead th{
  font-family:'MedievalSharp',cursive; color:var(--clover-green); text-transform:uppercase; letter-spacing:1px; font-size:.85rem;
  border-bottom:1px solid rgba(212,169,72,0.3);
}
.marks-table tbody tr{border-bottom:1px solid rgba(212,169,72,0.12);}
.marks-table tbody tr:last-child{border-bottom:none;}
.marks-table td.score{color:var(--gold-bright); font-family:'Cinzel',serif;}
.bar-bg{background:rgba(255,255,255,0.06); border-radius:4px; height:8px; overflow:hidden; margin-top:6px;}
.bar-fill{height:100%; background:linear-gradient(90deg,var(--clover-green),var(--gold-bright)); border-radius:4px;}

/* ---- Contact ---- */
.contact-grid{display:grid; grid-template-columns:repeat(auto-fit,minmax(240px,1fr)); gap:18px;}
.contact-card{display:flex; align-items:center; gap:14px;}
.contact-icon{
  width:42px; height:42px; flex:none; display:flex; align-items:center; justify-content:center;
  clip-path:polygon(50% 0%, 95% 25%, 95% 75%, 50% 100%, 5% 75%, 5% 25%);
  background:linear-gradient(135deg,var(--blood),var(--gold));
  font-size:1.1rem;
}
.contact-card a{color:var(--parchment); text-decoration:none; font-size:1.05rem;}
.contact-card a:hover{color:var(--gold-bright);}

/* ---- Floating Grimoire Button ---- */
.grimoire-pointer{
  position:fixed; bottom:130px; right:30px; z-index:50;
  font-family:'MedievalSharp', cursive; color:var(--gold-bright);
  text-align:right; pointer-events:none;
  text-shadow:0 0 10px rgba(0,0,0,0.8);
  animation:bob 2.2s ease-in-out infinite;
}
.grimoire-pointer .msg{font-size:1rem; display:block; margin-bottom:4px;}
.grimoire-pointer svg{width:46px; height:46px;}
@keyframes bob{0%,100%{transform:translateY(0);} 50%{transform:translateY(8px);}}

.grimoire-btn{
  position:fixed; bottom:30px; right:30px; z-index:50;
  width:84px; height:84px; border:none; cursor:pointer;
  background:radial-gradient(circle at 35% 30%, #3a2a18, #120d08 70%);
  border-radius:50%;
  box-shadow:0 0 0 2px var(--gold), 0 0 24px 6px rgba(212,169,72,0.55), inset 0 0 14px rgba(0,0,0,0.8);
  display:flex; align-items:center; justify-content:center;
  animation:pulse 2.6s ease-in-out infinite;
}
.grimoire-btn:hover{box-shadow:0 0 0 2px var(--gold-bright), 0 0 36px 10px rgba(243,210,122,0.75), inset 0 0 14px rgba(0,0,0,0.8);}
@keyframes pulse{0%,100%{transform:scale(1);} 50%{transform:scale(1.06);}}
.grimoire-btn svg{width:46px; height:46px;}

/* ---- Modal ---- */
.modal-overlay{
  position:fixed; inset:0; background:rgba(4,3,8,0.86); backdrop-filter:blur(4px);
  z-index:100; display:none; align-items:center; justify-content:center; padding:24px;
}
.modal-overlay.open{display:flex;}
.modal{
  max-width:560px; width:100%; max-height:80vh; overflow-y:auto;
  background:linear-gradient(180deg, #1a1426, #0d0a16);
  border:1px solid var(--gold); border-radius:8px; padding:34px 30px;
  box-shadow:0 0 60px rgba(212,169,72,0.25);
  position:relative;
  animation:open-book .5s ease;
}
@keyframes open-book{
  from{transform:scale(0.8) rotateY(40deg); opacity:0;}
  to{transform:scale(1) rotateY(0); opacity:1;}
}
.modal h2{font-family:'Cinzel',serif; color:var(--gold-bright); margin-bottom:18px; font-size:1.4rem;}
.modal p{line-height:1.7; margin-bottom:12px; color:#e6dcc0;}
.modal-close{
  position:absolute; top:14px; right:16px; background:none; border:none; color:var(--gold);
  font-size:1.4rem; cursor:pointer; font-family:'Cinzel',serif;
}
.modal ul{margin:10px 0 10px 20px; color:#e6dcc0; line-height:1.8;}

footer.signoff{
  text-align:center; margin-top:60px; font-family:'MedievalSharp',cursive; color:var(--mist); font-size:.9rem;
}

/* ---- Certificate scroll (Achievements) ---- */
.cert-card{grid-column:1 / -1;}
.cert-frame{
  margin-top:16px; border-radius:6px; overflow:hidden; cursor:pointer;
  border:1px solid rgba(212,169,72,0.4);
  box-shadow:0 0 0 1px rgba(0,0,0,0.4), 0 0 26px rgba(212,169,72,0.22);
  position:relative;
}
.cert-frame img{
  width:100%; display:block; filter:sepia(.18) saturate(1.08) contrast(1.05);
  transition:transform .5s ease, filter .5s ease;
}
.cert-frame:hover img{transform:scale(1.035); filter:sepia(.05) saturate(1.15) contrast(1.08);}
.cert-frame::after{
  content:'✦ tap the scroll to enlarge ✦'; position:absolute; left:0; right:0; bottom:0;
  padding:8px 12px; text-align:center; font-family:'MedievalSharp',cursive; font-size:.72rem;
  color:var(--gold-bright); background:linear-gradient(0deg, rgba(6,5,10,0.88), transparent);
  opacity:0; transition:opacity .3s ease;
}
.cert-frame:hover::after, .cert-frame.touched::after{opacity:1;}

/* ---- Spellbook (text pages) ---- */
.spellbook{display:flex; flex-direction:column; align-items:center; gap:16px;}
.book-shell{width:100%; max-width:660px; display:flex; align-items:stretch; gap:12px;}
.book-nav{
  flex:none; align-self:center; width:44px; height:44px; border-radius:50%;
  border:1px solid rgba(212,169,72,.5); background:rgba(20,16,30,.75); color:var(--gold-bright);
  font-size:1.1rem; cursor:pointer; display:flex; align-items:center; justify-content:center;
  transition:background .25s ease, transform .25s ease, box-shadow .25s ease;
}
.book-nav:hover{background:rgba(212,169,72,.2); transform:scale(1.08); box-shadow:0 0 14px rgba(212,169,72,.4);}
.book-nav:active{transform:scale(0.94);}
.book-pages{
  position:relative; flex:1; min-height:380px;
  background:linear-gradient(180deg,#efe6cb,#ddd0a8);
  border-radius:4px; border:1px solid rgba(212,169,72,.55);
  box-shadow:0 16px 40px rgba(0,0,0,.55), inset 0 0 46px rgba(122,31,43,0.10), 0 0 22px rgba(212,169,72,.15);
  overflow:hidden; perspective:1400px;
}
.book-pages::before{
  content:''; position:absolute; left:50%; top:0; bottom:0; width:18px; margin-left:-9px; z-index:3;
  background:linear-gradient(90deg, transparent, rgba(0,0,0,.20), transparent); pointer-events:none;
}
.book-pages::after{
  content:''; position:absolute; inset:0; z-index:3; pointer-events:none; border-radius:4px;
  box-shadow:inset 0 0 60px rgba(60,40,10,0.18);
}
.book-page{
  position:absolute; inset:0; padding:32px 36px; overflow-y:auto;
  color:#241a10; opacity:0; transform:rotateY(-95deg); transform-origin:left center;
  transition:opacity .5s ease, transform .55s ease; pointer-events:none;
}
.book-page.active{opacity:1; transform:rotateY(0deg); pointer-events:auto; z-index:2;}
.book-page h3{font-family:'Cinzel',serif; color:var(--blood); font-size:1.3rem; margin-bottom:16px; letter-spacing:.5px;}
.book-page h4{font-family:'MedievalSharp',cursive; color:#5c3d1c; font-size:1rem; margin:16px 0 8px;}
.book-page p{font-family:'EB Garamond',serif; line-height:1.75; font-size:1.05rem; margin-bottom:10px; color:#2c2013;}
.book-page ul{margin:0 0 4px 20px; line-height:1.9; font-family:'EB Garamond',serif; font-size:1.02rem; color:#2c2013;}
.book-page dl div{
  display:flex; justify-content:space-between; align-items:baseline; gap:14px; padding:9px 0;
  border-bottom:1px dashed rgba(122,31,43,.28);
}
.book-page dt{font-family:'MedievalSharp',cursive; color:var(--blood); font-size:.85rem; flex:none;}
.book-page dd{font-family:'EB Garamond',serif; font-size:1.02rem; text-align:right; color:#2c2013;}
.book-lead{font-family:'Cinzel',serif; font-weight:700; color:#5c3d1c; margin-bottom:12px;}
.motto-head{margin-top:24px;}
.motto-text{font-style:italic; color:#5c3d1c; font-size:1.08rem;}
.book-dots{display:flex; gap:9px;}
.book-dots .dot{
  width:9px; height:9px; border-radius:50%; border:1px solid var(--gold); background:transparent;
  cursor:pointer; padding:0; transition:background .25s ease, box-shadow .25s ease;
}
.book-dots .dot.active{background:var(--gold-bright); box-shadow:0 0 8px rgba(243,210,122,.75);}
.book-hint{font-family:'MedievalSharp',cursive; color:var(--mist); font-size:.78rem;}
@media (max-width:560px){
  .book-pages{min-height:440px;}
  .book-page{padding:26px 22px;}
}

/* ---- Contact: instagram / linkedin ---- */
.contact-icon svg{width:20px; height:20px;}

/* ================= MAGIC BOOK LOADER ================= */
#bookLoader{
  position:fixed; inset:0; z-index:9999;
  display:flex; flex-direction:column; align-items:center; justify-content:center; gap:26px;
  background:
    radial-gradient(ellipse at 50% 42%, rgba(122,31,43,0.22), transparent 60%),
    radial-gradient(ellipse at 50% 55%, #180f24 0%, #050409 75%);
  transition:opacity .85s ease, visibility .85s ease;
}
#bookLoader.hide{opacity:0; visibility:hidden; pointer-events:none;}
.loader-circle{
  position:absolute; width:340px; height:340px; border-radius:50%;
  border:1px solid rgba(212,169,72,0.28);
  animation:spin 14s linear infinite;
}
.loader-circle::before{
  content:''; position:absolute; inset:18px; border-radius:50%;
  border:1px dashed rgba(47,174,106,0.3);
}
.loader-circle::after{
  content:''; position:absolute; inset:0; border-radius:50%;
  box-shadow:0 0 40px 6px rgba(212,169,72,0.12) inset;
}
.book-stage{position:relative; width:180px; height:130px; perspective:1200px;}
.book-base{
  position:absolute; inset:0; margin:auto; width:150px; height:104px; top:10px;
  background:linear-gradient(180deg,#4a3419,#2a1c0d);
  border-radius:3px 8px 8px 3px;
  box-shadow:0 10px 30px rgba(0,0,0,0.6), 0 0 26px rgba(212,169,72,0.25);
}
.book-base::before{
  content:''; position:absolute; left:0; top:0; bottom:0; width:8px;
  background:linear-gradient(90deg,#1b1108,#4a3419);
}
.page{
  position:absolute; top:10px; left:75px; width:75px; height:104px;
  background:linear-gradient(120deg,#ece2c7,#d8caa3);
  border-radius:1px 8px 8px 1px;
  transform-origin:left center;
  box-shadow:1px 0 6px rgba(0,0,0,0.35);
  animation:pageTurn 2.4s ease-in-out infinite;
}
.page.p2{animation-delay:.18s; background:linear-gradient(120deg,#e6dab8,#cfbd90);}
.page.p3{animation-delay:.36s; background:linear-gradient(120deg,#e0d3ab,#c7b384);}
@keyframes pageTurn{
  0%{transform:rotateY(0deg);}
  35%{transform:rotateY(-165deg);}
  55%{transform:rotateY(-165deg);}
  90%{transform:rotateY(0deg);}
  100%{transform:rotateY(0deg);}
}
.book-sigil{
  position:absolute; left:50%; top:50%; width:34px; height:34px; margin:-17px 0 0 -17px;
  border:1.5px solid var(--gold-bright); border-radius:50%; z-index:5;
  box-shadow:0 0 16px 4px rgba(243,210,122,0.55);
  animation:sigilPulse 2.4s ease-in-out infinite;
}
@keyframes sigilPulse{
  0%,100%{opacity:.55; transform:translate(-50%,-50%) scale(1);}
  50%{opacity:1; transform:translate(-50%,-50%) scale(1.25);}
}
.loader-title{
  font-family:'Cinzel',serif; color:var(--gold-bright); letter-spacing:2px;
  font-size:1.15rem; text-shadow:0 0 14px rgba(243,210,122,0.4); text-align:center;
}
.loader-sub{
  font-family:'MedievalSharp',cursive; color:var(--mist); font-size:.85rem; text-align:center;
}
.loader-sub .dots::after{content:''; animation:dots 1.4s steps(4,end) infinite;}
@keyframes dots{0%{content:'';} 25%{content:'.';} 50%{content:'..';} 75%{content:'...';} 100%{content:'';}}
.loader-bar{width:220px; height:5px; border-radius:4px; background:rgba(255,255,255,0.08); overflow:hidden; box-shadow:0 0 8px rgba(0,0,0,0.5) inset;}
.loader-bar-fill{
  height:100%; width:0%; border-radius:4px;
  background:linear-gradient(90deg,var(--blood),var(--gold),var(--gold-bright));
}

/* ---- Touch interaction feedback: spark particles ---- */
.spark-burst{
  position:fixed; z-index:9998; pointer-events:none;
  width:6px; height:6px; border-radius:50%;
  background:var(--gold-bright);
  box-shadow:0 0 10px 3px rgba(243,210,122,0.85);
  animation:sparkOut .6s ease-out forwards;
}
@keyframes sparkOut{
  0%{transform:translate(0,0) scale(1); opacity:1;}
  100%{transform:translate(var(--dx),var(--dy)) scale(0); opacity:0;}
}

/* ---- Touch interaction: summoned magic circle ---- */
.magic-circle{
  position:fixed; top:0; left:0; z-index:9997; pointer-events:none;
  width:150px; height:150px;
  transform:translate(-50%,-50%) scale(0.1) rotate(0deg);
  opacity:0;
  transition:transform .32s cubic-bezier(.22,.9,.28,1.35), opacity .22s ease;
  will-change:transform, opacity;
}
.magic-circle.charging{
  opacity:1;
  transform:translate(-50%,-50%) scale(1) rotate(0deg);
}
.magic-circle.release{
  transition:transform .5s cubic-bezier(.3,0,.6,1), opacity .5s ease .05s;
  transform:translate(-50%,-50%) scale(1.55) rotate(25deg);
  opacity:0;
}
.magic-circle svg{
  width:100%; height:100%; overflow:visible;
  filter:
    drop-shadow(0 0 8px rgba(243,210,122,0.7))
    drop-shadow(0 0 20px rgba(47,174,106,0.35));
}
.magic-circle .mc-ring, .magic-circle .mc-star, .magic-circle .mc-tick{
  transform-box:fill-box; transform-origin:center;
}
.mc-ring{fill:none; stroke:var(--gold-bright);}
.mc-ring-outer{stroke-width:1.1; stroke-dasharray:3 5; opacity:.9; animation:mc-spin-cw 3.4s linear infinite;}
.mc-ring-mid{stroke:var(--clover-green); stroke-width:1; stroke-dasharray:1.5 4; opacity:.85; animation:mc-spin-ccw 4.8s linear infinite;}
.mc-ring-inner{stroke-width:1; opacity:.9; animation:mc-spin-cw 2.3s linear infinite;}
.mc-ticks{animation:mc-spin-ccw 9s linear infinite;}
.mc-tick{stroke:var(--gold-bright); stroke-width:1.4; opacity:.55;}
.mc-star{fill:none; stroke:var(--gold-bright); stroke-width:1; opacity:.85; animation:mc-spin-ccw 6.5s linear infinite;}
.mc-star.alt{stroke:var(--clover-green); opacity:.65; animation:mc-spin-cw 6.5s linear infinite;}
.mc-core{fill:var(--gold-bright); opacity:.95; animation:mc-core-pulse 1.1s ease-in-out infinite;}
@keyframes mc-spin-cw{to{transform:rotate(360deg);}}
@keyframes mc-spin-ccw{to{transform:rotate(-360deg);}}
@keyframes mc-core-pulse{0%,100%{opacity:.6; transform:scale(1);} 50%{opacity:1; transform:scale(1.5);}}

.card, .book-page, .cert-frame{ touch-action:manipulation; }
.card.touched{
  box-shadow:0 0 0 1px rgba(212,169,72,0.6), 0 0 22px rgba(212,169,72,0.4) !important;
  transition:box-shadow .25s ease, transform .25s ease;
}
.hex-frame.dragging{transition:none;}
.hex
