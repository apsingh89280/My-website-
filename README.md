<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0">
<title>Anurag — UI/UX Designer</title>
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Cormorant+Garamond:ital,wght@0,300;0,400;0,700;1,300;1,700&family=Syne:wght@300;400;500;700;800&display=swap" rel="stylesheet">
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.2/css/all.min.css">
<style>
:root{
  --bg:#050505; --s1:#0c0c0c; --s2:#111;
  --gold:#d4a843; --gold2:#f5cc6a; --gold3:rgba(212,168,67,0.12);
  --w:#f0ece3; --g:#5a5a5a; --g2:#2a2a2a;
  --serif:'Cormorant Garamond',serif;
  --display:'Bebas Neue',sans-serif;
  --sans:'Syne',sans-serif;
  --ease:cubic-bezier(.25,.46,.45,.94);
  --out:cubic-bezier(.16,1,.3,1);
}
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth}
body{font-family:var(--sans);background:var(--bg);color:var(--w);overflow-x:hidden;cursor:none}
::-webkit-scrollbar{width:2px}
::-webkit-scrollbar-track{background:var(--bg)}
::-webkit-scrollbar-thumb{background:var(--gold)}

/* ─── CURSOR ─── */
#cur,#cur2{position:fixed;pointer-events:none;z-index:99999;border-radius:50%;transform:translate(-50%,-50%)}
#cur{width:6px;height:6px;background:var(--gold);transition:width .2s,height .2s,opacity .2s}
#cur2{width:28px;height:28px;border:1px solid rgba(212,168,67,.5);transition:width .3s var(--out),height .3s var(--out)}
body.hov #cur{width:0;height:0;opacity:0}
body.hov #cur2{width:60px;height:60px;border-color:var(--gold);background:rgba(212,168,67,.06)}
@media(max-width:768px){#cur,#cur2{display:none}body{cursor:auto}}

/* ─── NOISE ─── */
body::before{content:'';position:fixed;inset:0;z-index:99990;pointer-events:none;
  background:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='200' height='200'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='.85' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='200' height='200' filter='url(%23n)' opacity='.05'/%3E%3C/svg%3E");
  opacity:.5;mix-blend-mode:overlay}

/* ─── KEYFRAMES ─── */
@keyframes fadeUp{from{opacity:0;transform:translateY(40px)}to{opacity:1;transform:translateY(0)}}
@keyframes fadeIn{from{opacity:0}to{opacity:1}}
@keyframes scaleUp{from{opacity:0;transform:scale(.9)}to{opacity:1;transform:scale(1)}}
@keyframes float{0%,100%{transform:translateY(0)}50%{transform:translateY(-18px)}}
@keyframes floatR{0%,100%{transform:translateY(0) rotate(0deg)}50%{transform:translateY(-12px) rotate(3deg)}}
@keyframes spin{from{transform:rotate(0)}to{transform:rotate(360deg)}}
@keyframes spinR{from{transform:rotate(360deg)}to{transform:rotate(0)}}
@keyframes pulse{0%,100%{opacity:1}50%{opacity:.3}}
@keyframes marquee{from{transform:translateX(0)}to{transform:translateX(-50%)}}
@keyframes shimmer{0%{background-position:200% center}100%{background-position:-200% center}}
@keyframes borderPulse{0%,100%{border-color:rgba(212,168,67,.3)}50%{border-color:rgba(212,168,67,.8)}}
@keyframes ripple{0%{transform:translate(-50%,-50%) scale(0);opacity:1}100%{transform:translate(-50%,-50%) scale(4);opacity:0}}
@keyframes slideInLeft{from{opacity:0;transform:translateX(-60px)}to{opacity:1;transform:translateX(0)}}
@keyframes slideInRight{from{opacity:0;transform:translateX(60px)}to{opacity:1;transform:translateX(0)}}
@keyframes drawLine{from{width:0}to{width:100%}}
@keyframes countUp{from{opacity:0}to{opacity:1}}
@keyframes bgShift{0%,100%{background-position:0% 50%}50%{background-position:100% 50%}}
@keyframes glitch1{0%{clip-path:polygon(0 20%,100% 20%,100% 30%,0 30%)}20%{clip-path:polygon(0 60%,100% 60%,100% 65%,0 65%)}40%{clip-path:polygon(0 10%,100% 10%,100% 20%,0 20%)}60%{clip-path:polygon(0 80%,100% 80%,100% 90%,0 90%)}80%,100%{clip-path:none}}

/* ─── REVEAL ─── */
.rev{opacity:0;transform:translateY(50px);transition:opacity 1s var(--out),transform 1s var(--out)}
.rev.on{opacity:1;transform:none}
.rev-l{opacity:0;transform:translateX(-60px);transition:opacity 1s var(--out),transform 1s var(--out)}
.rev-l.on{opacity:1;transform:none}
.rev-r{opacity:0;transform:translateX(60px);transition:opacity 1s var(--out),transform 1s var(--out)}
.rev-r.on{opacity:1;transform:none}
.d1{transition-delay:.1s}.d2{transition-delay:.22s}.d3{transition-delay:.35s}.d4{transition-delay:.48s}

/* ─── LOADING SCREEN ─── */
#loader{
  position:fixed;inset:0;z-index:99999;
  background:var(--bg);display:flex;flex-direction:column;
  align-items:center;justify-content:center;gap:2rem;
  transition:opacity .8s var(--out),transform .8s var(--out);
}
#loader.gone{opacity:0;transform:scale(1.05);pointer-events:none}
.loader-name{
  font-family:var(--display);font-size:clamp(3rem,8vw,7rem);
  letter-spacing:.1em;color:var(--gold);
  background:linear-gradient(90deg,var(--gold),var(--gold2),var(--gold));
  background-size:200%;
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;
  animation:shimmer 2s linear infinite;
}
.loader-bar{width:200px;height:1px;background:var(--g2);position:relative;overflow:hidden}
.loader-bar::after{
  content:'';position:absolute;left:0;top:0;height:100%;
  background:var(--gold);animation:drawLine 2s var(--ease) forwards;
}
.loader-pct{font-size:.7rem;letter-spacing:.3em;text-transform:uppercase;color:var(--g)}

/* ─── CANVAS ─── */
#particles{position:fixed;inset:0;z-index:0;pointer-events:none}

/* ─── NAV ─── */
nav{
  position:fixed;top:0;left:0;right:0;z-index:1000;
  display:flex;justify-content:space-between;align-items:center;
  padding:1.5rem 5%;
  transition:background .5s,border-color .5s,backdrop-filter .5s;
  border-bottom:1px solid transparent;
}
nav.s{background:rgba(5,5,5,.92);backdrop-filter:blur(20px);border-color:rgba(255,255,255,.06)}
.nav-logo{
  font-family:var(--display);font-size:1.5rem;letter-spacing:.08em;
  color:var(--w);text-decoration:none;position:relative;z-index:1;
}
.nav-logo span{color:var(--gold)}
.nav-links{display:flex;gap:2.5rem;list-style:none}
.nav-links a{
  font-size:.68rem;font-weight:500;letter-spacing:.2em;
  text-transform:uppercase;color:var(--g);text-decoration:none;
  position:relative;padding-bottom:4px;transition:color .3s;
}
.nav-links a::after{
  content:'';position:absolute;bottom:0;left:0;
  width:0;height:1px;background:var(--gold);
  transition:width .4s var(--ease);
}
.nav-links a:hover{color:var(--w)}
.nav-links a:hover::after{width:100%}
.nav-hire{
  background:transparent;border:1px solid rgba(212,168,67,.4);
  color:var(--gold);padding:.55rem 1.4rem;
  font-family:var(--sans);font-size:.68rem;font-weight:500;
  letter-spacing:.15em;text-transform:uppercase;
  border-radius:100px;text-decoration:none;
  transition:background .3s,border-color .3s,color .3s,transform .3s;
  animation:borderPulse 3s infinite;
}
.nav-hire:hover{background:var(--gold);border-color:var(--gold);color:var(--bg);transform:translateY(-2px);animation:none}
.ham{display:none;flex-direction:column;gap:5px;background:none;border:none;cursor:pointer;padding:4px;z-index:1001}
.ham span{display:block;width:22px;height:1.5px;background:var(--w);border-radius:2px;transition:all .4s var(--ease)}
.ham.open span:nth-child(1){transform:rotate(45deg) translate(4px,4px)}
.ham.open span:nth-child(2){opacity:0;width:0}
.ham.open span:nth-child(3){transform:rotate(-45deg) translate(4px,-4px)}

/* Mobile overlay */
.mob{
  position:fixed;inset:0;z-index:999;
  background:rgba(5,5,5,.97);backdrop-filter:blur(24px);
  display:flex;flex-direction:column;align-items:center;justify-content:center;gap:2.5rem;
  opacity:0;pointer-events:none;transition:opacity .5s var(--out);
}
.mob.open{opacity:1;pointer-events:all}
.mob a{
  font-family:var(--display);font-size:clamp(2rem,8vw,4rem);
  letter-spacing:.05em;color:var(--w);text-decoration:none;
  opacity:0;transform:translateY(30px);
  transition:opacity .5s,transform .5s var(--out),color .3s;
}
.mob.open a{opacity:1;transform:none}
.mob.open a:nth-child(1){transition-delay:.1s}
.mob.open a:nth-child(2){transition-delay:.18s}
.mob.open a:nth-child(3){transition-delay:.26s}
.mob.open a:nth-child(4){transition-delay:.34s}
.mob.open a:nth-child(5){transition-delay:.42s}
.mob a:hover{color:var(--gold)}
.mob-social{display:flex;gap:1.5rem;margin-top:1rem}
.mob-social a{font-size:1.2rem;color:var(--g);transition:color .3s;text-decoration:none;opacity:1;transform:none}
.mob-social a:hover{color:var(--gold)}

/* ─── HERO ─── */
#hero{
  min-height:100svh;display:grid;
  grid-template-columns:1fr 1fr;
  align-items:center;gap:3rem;
  padding:9rem 5% 6rem;
  position:relative;z-index:1;overflow:hidden;
}
.hero-l{position:relative;z-index:2}
.h-tag{
  display:inline-flex;align-items:center;gap:.7rem;
  background:rgba(212,168,67,.08);border:1px solid rgba(212,168,67,.2);
  border-radius:100px;padding:.4rem 1rem .4rem .5rem;
  font-size:.65rem;letter-spacing:.18em;text-transform:uppercase;color:var(--gold);
  margin-bottom:1.8rem;
  animation:fadeUp .6s .5s both;
}
.h-dot{width:7px;height:7px;border-radius:50%;background:var(--gold);animation:pulse 2s infinite}
.h1{
  font-family:var(--display);
  font-size:clamp(3.5rem,7vw,8.5rem);
  line-height:.95;letter-spacing:.02em;color:var(--w);
  animation:fadeUp .8s .7s both;
}
.h1 .gold-word{
  -webkit-text-stroke:1px var(--gold);color:transparent;
  transition:color .4s,-webkit-text-stroke .4s;
}
.h1 .gold-word:hover{color:var(--gold);-webkit-text-stroke:0px transparent}
.h-sub{
  font-family:var(--serif);font-style:italic;
  font-size:clamp(1.2rem,2.5vw,1.8rem);
  color:rgba(240,236,227,.5);margin-top:.8rem;
  animation:fadeUp .8s .9s both;
}
.h-desc{
  margin-top:2rem;max-width:420px;
  font-size:.88rem;line-height:1.9;color:var(--g);font-weight:300;
  animation:fadeUp .8s 1.1s both;
}
.h-btns{display:flex;gap:1.2rem;flex-wrap:wrap;margin-top:2.5rem;animation:fadeUp .8s 1.3s both}
.btn-gld{
  display:inline-flex;align-items:center;gap:.8rem;
  background:var(--gold);color:var(--bg);
  padding:.9rem 2rem;border-radius:100px;
  font-family:var(--sans);font-size:.72rem;font-weight:700;
  letter-spacing:.12em;text-transform:uppercase;
  text-decoration:none;border:none;cursor:none;
  transition:background .3s,transform .3s,box-shadow .3s;
  position:relative;overflow:hidden;
}
.btn-gld::before{
  content:'';position:absolute;inset:0;
  background:radial-gradient(circle at var(--mx,50%) var(--my,50%),rgba(255,255,255,.25),transparent 60%);
  opacity:0;transition:opacity .3s;
}
.btn-gld:hover::before{opacity:1}
.btn-gld:hover{background:var(--gold2);transform:translateY(-3px);box-shadow:0 16px 50px rgba(212,168,67,.35)}
.btn-out{
  display:inline-flex;align-items:center;gap:.8rem;
  background:transparent;color:var(--w);
  padding:.9rem 2rem;border-radius:100px;
  border:1px solid rgba(255,255,255,.12);
  font-family:var(--sans);font-size:.72rem;font-weight:500;
  letter-spacing:.12em;text-transform:uppercase;
  text-decoration:none;cursor:none;
  transition:border-color .3s,background .3s,transform .3s;
}
.btn-out:hover{border-color:var(--gold);background:rgba(212,168,67,.06);transform:translateY(-3px)}

/* Hero right - Cinematic image stack */
.hero-r{position:relative;z-index:2;animation:fadeIn .8s 1s both}
.img-stack{position:relative;width:100%;max-width:440px;margin:0 auto;height:580px}
.img-stack .card{
  position:absolute;border-radius:1.5rem;overflow:hidden;
  box-shadow:0 40px 100px rgba(0,0,0,.7);
  transition:transform .6s var(--out);
}
.img-stack .card img{width:100%;height:100%;object-fit:cover;display:block;transition:transform 8s ease}
.img-stack:hover .card img{transform:scale(1.08)}
.card-main{
  width:100%;height:100%;top:0;left:0;
  animation:float 6s ease-in-out infinite;
}
.card-sm1{
  width:48%;height:46%;bottom:10%;right:-8%;
  border:2px solid rgba(212,168,67,.3);
  animation:floatR 5s 1s ease-in-out infinite;
}
.card-sm2{
  width:40%;height:36%;top:8%;left:-6%;
  border:2px solid rgba(212,168,67,.2);
  animation:floatR 7s .5s ease-in-out infinite;
}
.img-badge{
  position:absolute;bottom:-1.5rem;right:1rem;
  background:var(--gold);color:var(--bg);
  border-radius:1rem;padding:1.2rem 1.4rem;
  text-align:center;box-shadow:0 8px 40px rgba(212,168,67,.4);
  animation:float 4s 2s ease-in-out infinite;
  z-index:10;
}
.img-badge strong{
  font-family:var(--display);font-size:2.5rem;
  display:block;line-height:1;
}
.img-badge span{font-size:.6rem;letter-spacing:.12em;text-transform:uppercase}

/* rotating ring */
.spin-ring{
  position:absolute;top:-20px;right:-20px;
  width:120px;height:120px;z-index:10;
}
.spin-ring svg{animation:spin 12s linear infinite}
.spin-ring-inner{
  position:absolute;inset:20px;border-radius:50%;
  background:var(--gold);opacity:.15;
  animation:pulse 3s infinite;
}

/* hero scroll */
.h-scroll{
  position:absolute;bottom:2rem;left:50%;transform:translateX(-50%);
  display:flex;flex-direction:column;align-items:center;gap:.6rem;
  font-size:.58rem;letter-spacing:.25em;text-transform:uppercase;color:var(--g);
  animation:fadeIn 1s 2s both;z-index:5;
}
.h-scroll-bar{width:1px;height:55px;background:linear-gradient(var(--gold),transparent);animation:pulse 2s infinite}

/* ─── MARQUEE ─── */
.mqwrap{
  overflow:hidden;border-top:1px solid rgba(255,255,255,.05);
  border-bottom:1px solid rgba(255,255,255,.05);
  background:var(--s1);padding:1rem 0;position:relative;z-index:1;
}
.mq{display:flex;white-space:nowrap;animation:marquee 18s linear infinite}
.mq:hover{animation-play-state:paused}
.mq-item{
  display:inline-flex;align-items:center;gap:1.5rem;padding:0 2rem;
  font-family:var(--display);font-size:1.1rem;letter-spacing:.05em;color:var(--g2);
}
.mq-item .dot{color:var(--gold);font-family:var(--sans)}

/* ─── ABOUT ─── */
#about{
  padding:9rem 5%;display:grid;
  grid-template-columns:1fr 1fr;
  gap:6rem;align-items:center;
  position:relative;z-index:1;
}
.a-img-col{position:relative}
.a-img-grid{
  display:grid;grid-template-columns:1fr 1fr;gap:.8rem;
  grid-template-rows:auto auto;
}
.a-img-grid .gi{
  overflow:hidden;border-radius:1rem;cursor:none;
  position:relative;
}
.a-img-grid .gi::after{
  content:'';position:absolute;inset:0;
  background:linear-gradient(to top,rgba(5,5,5,.6),transparent 50%);
  opacity:0;transition:opacity .4s;
}
.a-img-grid .gi:hover::after{opacity:1}
.a-img-grid .gi .zoom-icon{
  position:absolute;bottom:1rem;right:1rem;z-index:2;
  width:36px;height:36px;border-radius:50%;
  background:var(--gold);color:var(--bg);
  display:flex;align-items:center;justify-content:center;
  font-size:.75rem;opacity:0;transform:scale(.6);
  transition:opacity .3s,transform .4s var(--out);
}
.a-img-grid .gi:hover .zoom-icon{opacity:1;transform:scale(1)}
.a-img-grid img{
  width:100%;height:100%;object-fit:cover;display:block;
  transition:transform .7s var(--ease);
}
.a-img-grid .gi:hover img{transform:scale(1.07)}
.a-img-grid .gi:nth-child(1){grid-row:span 2;aspect-ratio:2/3;cursor:none}
.a-img-grid .gi:nth-child(2){aspect-ratio:1/1}
.a-img-grid .gi:nth-child(3){aspect-ratio:1/1}
.a-badge{
  position:absolute;top:50%;left:-2rem;
  transform:translateY(-50%);
  background:var(--gold);color:var(--bg);
  padding:1.5rem 1.2rem;border-radius:1rem;
  text-align:center;box-shadow:0 8px 50px rgba(212,168,67,.4);
  animation:float 5s ease-in-out infinite;
}
.a-badge strong{font-family:var(--display);font-size:2.8rem;display:block;line-height:1}
.a-badge span{font-size:.58rem;letter-spacing:.12em;text-transform:uppercase}
.lbl{
  display:inline-flex;align-items:center;gap:.7rem;
  font-size:.65rem;letter-spacing:.25em;text-transform:uppercase;color:var(--gold);
  margin-bottom:1.2rem;
}
.lbl::before{content:'';width:24px;height:1px;background:var(--gold)}
.stitle{
  font-family:var(--serif);
  font-size:clamp(1.8rem,3vw,3rem);
  font-weight:700;line-height:1.15;margin-bottom:1.5rem;
}
.stitle em{font-style:italic;color:var(--gold)}
.atxt{font-size:.88rem;line-height:1.9;color:var(--g);font-weight:300;margin-bottom:2rem}
.sk-grid{display:grid;grid-template-columns:1fr 1fr;gap:.7rem;margin-bottom:2rem}
.sk-pill{
  display:flex;align-items:center;gap:.7rem;
  background:var(--s2);border:1px solid rgba(255,255,255,.06);
  border-radius:.7rem;padding:.7rem 1rem;
  font-size:.78rem;color:var(--w);
  transition:border-color .3s,background .3s,transform .3s;
}
.sk-pill:hover{border-color:rgba(212,168,67,.4);background:var(--gold3);transform:translateX(4px)}
.sk-pill i{color:var(--gold);width:14px;font-size:.72rem}

/* stats row */
.stats-row{
  display:flex;gap:2.5rem;flex-wrap:wrap;margin-top:2.5rem;
  padding-top:2rem;border-top:1px solid rgba(255,255,255,.06);
}
.stat{}
.stat-n{
  font-family:var(--display);font-size:3rem;line-height:1;
  background:linear-gradient(135deg,var(--gold),var(--gold2));
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;
}
.stat-l{font-size:.62rem;letter-spacing:.18em;text-transform:uppercase;color:var(--g)}

/* ─── PARALLAX SECTION ─── */
.parallax-section{
  position:relative;height:500px;overflow:hidden;z-index:1;
  display:flex;align-items:center;justify-content:center;
}
.par-bg{
  position:absolute;inset:-15%;
  background-size:cover;background-position:center;
  will-change:transform;
}
.par-overlay{
  position:absolute;inset:0;
  background:linear-gradient(to bottom,rgba(5,5,5,.7),rgba(5,5,5,.5),rgba(5,5,5,.7));
}
.par-content{
  position:relative;z-index:2;text-align:center;
  font-family:var(--display);
  font-size:clamp(3rem,8vw,8rem);
  letter-spacing:.05em;color:var(--w);
  text-shadow:0 10px 50px rgba(0,0,0,.5);
}
.par-content span{color:var(--gold)}

/* ─── CLIENTS ─── */
.clients{
  padding:5rem 5%;background:var(--s1);
  border-top:1px solid rgba(255,255,255,.04);
  border-bottom:1px solid rgba(255,255,255,.04);
  position:relative;z-index:1;
}
.c-lbl{text-align:center;font-size:.62rem;letter-spacing:.3em;text-transform:uppercase;color:var(--g);margin-bottom:2.5rem}
.c-logos{display:flex;justify-content:center;align-items:center;gap:4rem;flex-wrap:wrap}
.c-logos img{height:20px;opacity:.15;filter:invert(1) grayscale(1);transition:opacity .4s,filter .4s,transform .4s}
.c-logos img:hover{opacity:.6;filter:invert(1) grayscale(0);transform:scale(1.1)}

/* ─── PROCESS ─── */
#process{padding:9rem 5%;background:var(--bg);position:relative;z-index:1;overflow:hidden}
#process::after{
  content:'DESIGN';position:absolute;right:-3rem;top:50%;
  transform:translateY(-50%) rotate(90deg);
  font-family:var(--display);font-size:14rem;letter-spacing:.05em;
  color:rgba(255,255,255,.02);pointer-events:none;white-space:nowrap;
}
.proc-hd{display:flex;justify-content:space-between;align-items:flex-end;margin-bottom:5rem;gap:2rem;flex-wrap:wrap}
.proc-desc{max-width:300px;font-size:.85rem;line-height:1.8;color:var(--g)}
.proc-cards{display:grid;grid-template-columns:repeat(4,1fr);gap:1px;background:rgba(255,255,255,.04);border-radius:1.2rem;overflow:hidden}
.pc{
  background:var(--s1);padding:2.5rem 2rem;
  position:relative;overflow:hidden;
  transition:background .4s;
}
.pc::after{
  content:'';position:absolute;bottom:0;left:0;right:0;height:2px;
  background:linear-gradient(90deg,var(--gold),var(--gold2));
  transform:scaleX(0);transform-origin:left;
  transition:transform .6s var(--ease);
}
.pc:hover{background:rgba(212,168,67,.04)}
.pc:hover::after{transform:scaleX(1)}
.pc-num{
  font-family:var(--display);font-size:5rem;letter-spacing:.02em;
  color:rgba(255,255,255,.03);line-height:1;margin-bottom:1.5rem;
  transition:color .4s;
}
.pc:hover .pc-num{color:rgba(212,168,67,.07)}
.pc-icon{
  width:44px;height:44px;border:1px solid rgba(212,168,67,.2);
  border-radius:.75rem;display:flex;align-items:center;justify-content:center;
  color:var(--gold);margin-bottom:1.2rem;font-size:.95rem;
  transition:background .3s,border-color .3s,transform .4s var(--out);
}
.pc:hover .pc-icon{background:rgba(212,168,67,.12);border-color:var(-
