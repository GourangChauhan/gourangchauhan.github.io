<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Gourang Chauhan — Data Scientist & AI Engineer</title>
<link href="https://fonts.googleapis.com/css2?family=EB+Garamond:ital,wght@0,400;0,500;0,600;0,700;0,800;1,400;1,500;1,700&family=Libre+Baskerville:ital,wght@0,400;0,700;1,400&family=JetBrains+Mono:wght@300;400;500&display=swap" rel="stylesheet"/>
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
<style>
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
:root{
  --bg:#f7f5f0;
  --bg2:#efede8;
  --bg3:#e8e5de;
  --ink:#141210;
  --ink2:#2a2723;
  --ink3:#3d3a35;
  --muted:#7a756c;
  --accent:#1a1714;
  --green:#2d6a4f;
  --green-l:#52b788;
  --green-xl:#95d5b2;
  --border:rgba(20,18,16,0.1);
  --border-strong:rgba(20,18,16,0.18);
  --card:rgba(255,255,255,0.55);
  --shadow:rgba(20,18,16,0.07);
}
html{scroll-behavior:smooth}
body{background:var(--bg);color:var(--ink);font-family:'Libre Baskerville',Georgia,serif;overflow-x:hidden;cursor:none;font-size:15px}

/* CURSOR */
#cursor{position:fixed;width:10px;height:10px;background:var(--ink);border-radius:50%;pointer-events:none;z-index:9999;transform:translate(-50%,-50%);transition:transform 0.08s}
#cursor-ring{position:fixed;width:36px;height:36px;border:1.5px solid rgba(20,18,16,0.3);border-radius:50%;pointer-events:none;z-index:9998;transform:translate(-50%,-50%);transition:width 0.3s,height 0.3s}

/* NAV */
nav{
  position:fixed;top:0;left:0;right:0;z-index:100;
  padding:18px 64px;
  display:flex;justify-content:space-between;align-items:center;
  background:rgba(247,245,240,0.88);
  backdrop-filter:blur(24px);
  border-bottom:1px solid var(--border);
}
.nav-brand{
  font-family:'EB Garamond',Georgia,serif;font-size:1.35rem;font-weight:700;font-style:italic;
  color:var(--ink);letter-spacing:-0.02em;text-decoration:none;
}
.nav-brand span{color:var(--green)}
.nav-menu{display:flex;gap:32px}
.nav-menu a{
  color:var(--muted);text-decoration:none;font-size:0.82rem;
  font-weight:500;letter-spacing:0.04em;text-transform:uppercase;
  transition:color 0.2s;position:relative;
}
.nav-menu a::after{content:'';position:absolute;bottom:-3px;left:0;right:0;height:1px;background:var(--ink);transform:scaleX(0);transition:transform 0.2s}
.nav-menu a:hover{color:var(--ink)}
.nav-menu a:hover::after{transform:scaleX(1)}
.nav-cta{
  background:var(--ink);color:var(--bg);border:none;
  padding:10px 22px;border-radius:4px;
  font-family:'JetBrains Mono',monospace;font-weight:500;font-size:0.72rem;
  letter-spacing:0.1em;text-transform:uppercase;
  cursor:none;transition:all 0.2s;
}
.nav-cta:hover{background:var(--ink3);transform:translateY(-1px)}

/* ── HERO ── */
#hero{
  min-height:100vh;
  display:grid;grid-template-columns:1fr 1fr;
  align-items:center;
  padding:110px 64px 80px;
  position:relative;overflow:hidden;gap:60px;
}
#three-canvas{position:absolute;inset:0;z-index:0;opacity:0.4}
.hero-left{position:relative;z-index:2}

.hero-eyebrow{
  display:inline-flex;align-items:center;gap:8px;
  background:rgba(20,18,16,0.05);
  border:1px solid var(--border-strong);
  border-radius:3px;padding:7px 16px;
  font-family:'JetBrains Mono',monospace;font-size:0.7rem;
  color:var(--muted);margin-bottom:28px;
  letter-spacing:0.08em;text-transform:uppercase;
  animation:fadeUp 0.7s ease both;
}
.hero-eyebrow .dot{width:6px;height:6px;background:var(--green-l);border-radius:50%;animation:blink 2s infinite}
@keyframes blink{0%,100%{opacity:1}50%{opacity:0.2}}

.hero-title{
  font-family:'EB Garamond',Georgia,serif;
  font-size:clamp(3.2rem,5.5vw,6rem);
  font-weight:700;line-height:1.12;
  letter-spacing:-0.02em;margin-bottom:28px;
  color:var(--ink);font-style:normal;
  animation:fadeUp 0.7s 0.1s ease both;
}
.hero-title .italic{font-style:italic;color:var(--ink3);font-weight:300}
.hero-title .outline{
  -webkit-text-stroke:1.2px var(--ink);
  color:transparent;
  font-weight:700;font-style:italic;
}

.hero-sub{
  color:var(--muted);font-size:0.97rem;line-height:2;
  max-width:480px;margin-bottom:44px;
  animation:fadeUp 0.7s 0.2s ease both;
}
.hero-sub strong{color:var(--ink);font-weight:500}

.hero-buttons{display:flex;gap:14px;margin-bottom:60px;animation:fadeUp 0.7s 0.3s ease both}
.btn{
  display:inline-flex;align-items:center;gap:8px;
  padding:13px 26px;border-radius:4px;
  font-family:'JetBrains Mono',monospace;font-weight:400;
  font-size:0.78rem;letter-spacing:0.06em;
  text-decoration:none;transition:all 0.22s;cursor:none;
}
.btn.primary{background:var(--ink);color:var(--bg);box-shadow:0 4px 20px rgba(20,18,16,0.15)}
.btn.primary:hover{background:var(--ink3);transform:translateY(-2px);box-shadow:0 8px 32px rgba(20,18,16,0.2)}
.btn.secondary{background:transparent;border:1.5px solid var(--border-strong);color:var(--ink)}
.btn.secondary:hover{background:var(--bg2);transform:translateY(-2px)}

.hero-stats{display:flex;gap:44px;animation:fadeUp 0.7s 0.4s ease both}
.hstat .n{
  font-family:'EB Garamond',Georgia,serif;font-size:2.6rem;font-weight:700;
  color:var(--ink);line-height:1;letter-spacing:-0.01em;
}
.hstat .n span{color:var(--green);font-size:1.4rem}
.hstat .l{font-size:0.7rem;color:var(--muted);letter-spacing:0.1em;text-transform:uppercase;margin-top:4px}

/* HERO RIGHT — Profile Card */
.hero-right{position:relative;z-index:2;display:flex;justify-content:center;align-items:center}

.profile-card{
  background:var(--card);
  border:1px solid var(--border-strong);
  border-radius:16px;
  padding:36px;
  width:100%;max-width:380px;
  backdrop-filter:blur(20px);
  box-shadow:0 24px 80px var(--shadow),0 2px 8px var(--shadow);
  animation:float 7s ease-in-out infinite, fadeUp 0.7s 0.3s ease both;
  position:relative;overflow:hidden;
}
.profile-card::before{
  content:'';position:absolute;top:0;left:0;right:0;height:3px;
  background:linear-gradient(90deg,var(--green),var(--green-xl));
}
@keyframes float{0%,100%{transform:translateY(0) rotate(-0.5deg)}50%{transform:translateY(-14px) rotate(0.5deg)}}

.pc-photo-wrap{display:flex;justify-content:center;margin-bottom:20px}
.pc-photo{
  width:96px;height:96px;border-radius:50%;
  border:3px solid var(--bg3);
  object-fit:cover;object-position:top center;
  box-shadow:0 8px 28px rgba(20,18,16,0.12);
}
.pc-name{
  font-family:'EB Garamond',Georgia,serif;font-weight:700;font-size:1.3rem;
  text-align:center;letter-spacing:0em;color:var(--ink);margin-bottom:4px;
}
.pc-role{
  font-family:'JetBrains Mono',monospace;font-size:0.7rem;
  color:var(--green);text-align:center;margin-bottom:6px;
  letter-spacing:0.06em;
}
.pc-location{
  font-size:0.75rem;color:var(--muted);text-align:center;
  margin-bottom:24px;
}
.pc-divider{height:1px;background:var(--border);margin-bottom:20px}

.pc-tags{display:flex;flex-wrap:wrap;gap:7px;justify-content:center;margin-bottom:20px}
.pc-tag{
  background:rgba(20,18,16,0.05);border:1px solid var(--border-strong);
  border-radius:3px;padding:5px 11px;
  font-family:'JetBrains Mono',monospace;font-size:0.65rem;
  color:var(--ink3);letter-spacing:0.04em;
}
.pc-metrics{display:grid;grid-template-columns:1fr 1fr;gap:10px}
.pc-m{
  background:rgba(20,18,16,0.03);border:1px solid var(--border);
  border-radius:8px;padding:12px;text-align:center;
}
.pc-m .val{
  font-family:'EB Garamond',Georgia,serif;font-size:1.6rem;font-weight:700;
  color:var(--ink);line-height:1;letter-spacing:0em;
}
.pc-m .lbl{font-size:0.62rem;color:var(--muted);margin-top:4px;letter-spacing:0.06em;text-transform:uppercase}

/* SECTIONS */
section{padding:100px 64px;position:relative}
.s-tag{
  font-family:'JetBrains Mono',monospace;font-size:0.68rem;
  color:var(--muted);letter-spacing:0.18em;text-transform:uppercase;
  margin-bottom:14px;display:block;
}
.s-title{
  font-family:'EB Garamond',Georgia,serif;font-size:clamp(2.4rem,3.5vw,3.6rem);
  font-weight:700;letter-spacing:-0.01em;line-height:1.12;
  margin-bottom:16px;color:var(--ink);
}
.s-title .it{font-style:italic;font-weight:300;color:var(--ink3)}
.s-sub{color:var(--muted);font-size:0.98rem;margin-bottom:60px;max-width:500px;line-height:1.75}

/* ABOUT */
#about{background:var(--bg2);border-top:1px solid var(--border);border-bottom:1px solid var(--border)}
.about-grid{display:grid;grid-template-columns:1.15fr 0.85fr;gap:80px;align-items:start}
.about-text p{color:var(--muted);margin-bottom:20px;font-size:0.95rem;line-height:2}
.about-text p strong{color:var(--ink);font-weight:500}
.about-text p em{color:var(--green);font-style:normal;font-weight:500}

.about-sidebar{}
.sidebar-photo-wrap{margin-bottom:24px;display:flex;justify-content:center}
.sidebar-photo{
  width:160px;height:160px;border-radius:12px;
  object-fit:cover;object-position:top center;
  border:2px solid var(--border-strong);
  box-shadow:0 12px 40px var(--shadow);
}
.about-pills{display:flex;flex-direction:column;gap:12px}
.about-pill{
  display:flex;align-items:center;gap:14px;
  background:var(--card);border:1px solid var(--border-strong);
  border-radius:10px;padding:18px 20px;
  transition:all 0.22s;
  box-shadow:0 2px 8px var(--shadow);
}
.about-pill:hover{transform:translateX(6px);border-color:rgba(20,18,16,0.28);box-shadow:0 6px 20px var(--shadow)}
.ap-icon{
  width:38px;height:38px;background:var(--bg3);
  border-radius:8px;display:flex;align-items:center;
  justify-content:center;font-size:1.1rem;flex-shrink:0;
  border:1px solid var(--border);
}
.ap-title{font-family:'EB Garamond',Georgia,serif;font-weight:700;font-size:1rem;color:var(--ink);margin-bottom:2px}
.ap-sub{font-size:0.75rem;color:var(--muted)}

/* SKILLS */
#skills{background:var(--bg)}
.skills-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:18px}
.skill-card{
  background:var(--card);border:1px solid var(--border-strong);
  border-radius:12px;padding:26px;
  transition:all 0.25s;
  box-shadow:0 2px 8px var(--shadow);
  position:relative;overflow:hidden;
}
.skill-card::after{
  content:'';position:absolute;bottom:0;left:0;right:0;height:2px;
  background:var(--ink);opacity:0;transition:opacity 0.25s;
}
.skill-card:hover{transform:translateY(-6px);border-color:rgba(20,18,16,0.25);box-shadow:0 16px 48px var(--shadow)}
.skill-card:hover::after{opacity:1}
.sk-icon{font-size:1.6rem;margin-bottom:14px;display:block}
.sk-name{font-family:'EB Garamond',Georgia,serif;font-weight:700;font-size:1.05rem;margin-bottom:12px;color:var(--ink)}
.sk-tags{display:flex;flex-wrap:wrap;gap:6px}
.sk-tag{
  background:rgba(20,18,16,0.05);border:1px solid var(--border);
  color:var(--ink3);font-family:'JetBrains Mono',monospace;
  font-size:0.62rem;padding:3px 8px;border-radius:3px;
}
.sk-tag.hot{
  background:rgba(45,106,79,0.08);border-color:rgba(45,106,79,0.2);
  color:var(--green);font-weight:500;
}

/* EXPERIENCE */
#experience{background:var(--bg2);border-top:1px solid var(--border);border-bottom:1px solid var(--border)}
.exp-list{max-width:860px}
.exp-card{
  background:var(--card);border:1px solid var(--border-strong);
  border-radius:12px;padding:36px;margin-bottom:18px;
  transition:all 0.25s;position:relative;overflow:hidden;
  box-shadow:0 2px 8px var(--shadow);
}
.exp-card::before{
  content:'';position:absolute;left:0;top:0;bottom:0;width:3px;
  background:var(--ink);opacity:0;transition:opacity 0.25s;
}
.exp-card:hover{transform:translateX(5px);box-shadow:0 8px 32px var(--shadow)}
.exp-card:hover::before{opacity:1}
.ec-top{display:flex;justify-content:space-between;align-items:flex-start;margin-bottom:6px}
.ec-company{font-family:'EB Garamond',Georgia,serif;font-weight:700;font-size:1.4rem;color:var(--ink);letter-spacing:0em}
.ec-period{
  font-family:'JetBrains Mono',monospace;font-size:0.68rem;
  color:var(--muted);background:var(--bg3);
  border:1px solid var(--border);padding:4px 12px;border-radius:3px;
}
.ec-role{color:var(--green);font-size:0.82rem;font-family:'JetBrains Mono',monospace;margin-bottom:3px;letter-spacing:0.04em}
.ec-loc{font-size:0.75rem;color:var(--muted);margin-bottom:20px}
.ec-impact{
  background:rgba(20,18,16,0.03);border-left:2px solid var(--ink3);
  padding:11px 15px;border-radius:0 8px 8px 0;
  font-size:0.86rem;color:var(--muted);margin-bottom:16px;
}
.ec-impact strong{color:var(--ink)}
.ec-list{list-style:none}
.ec-list li{display:flex;gap:10px;padding:5px 0;font-size:0.85rem;color:var(--muted);line-height:1.85}
.ec-list li::before{content:'→';color:var(--green);flex-shrink:0}
.ec-list li strong{color:var(--ink);font-weight:500}
.ec-chips{display:flex;gap:8px;margin-top:18px;flex-wrap:wrap}
.chip{
  background:var(--bg3);border:1px solid var(--border-strong);
  color:var(--ink3);font-family:'JetBrains Mono',monospace;
  font-size:0.68rem;padding:4px 12px;border-radius:3px;
}

/* PROJECTS */
#projects{background:var(--bg)}
.projects-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:22px}
.proj-card{
  background:var(--card);border:1px solid var(--border-strong);
  border-radius:12px;padding:28px;
  transition:all 0.25s;display:flex;flex-direction:column;
  box-shadow:0 2px 8px var(--shadow);position:relative;overflow:hidden;
}
.proj-card::before{
  content:'';position:absolute;top:0;left:0;right:0;height:2px;
  background:linear-gradient(90deg,var(--ink),var(--ink3));
  opacity:0;transition:opacity 0.25s;
}
.proj-card:hover{transform:translateY(-8px);box-shadow:0 20px 56px var(--shadow);border-color:rgba(20,18,16,0.22)}
.proj-card:hover::before{opacity:1}
.proj-num{font-family:'JetBrains Mono',monospace;font-size:0.62rem;color:var(--muted);letter-spacing:0.12em;margin-bottom:8px}
.proj-title{font-family:'EB Garamond',Georgia,serif;font-weight:700;font-size:1.2rem;margin-bottom:5px;letter-spacing:0em;color:var(--ink)}
.proj-type{font-size:0.7rem;font-family:'JetBrains Mono',monospace;color:var(--green);margin-bottom:18px;letter-spacing:0.04em}
.proj-section{margin-bottom:12px}
.proj-label{font-family:'JetBrains Mono',monospace;font-size:0.58rem;color:var(--muted);letter-spacing:0.14em;text-transform:uppercase;margin-bottom:5px}
.proj-text{font-size:0.82rem;color:var(--muted);line-height:1.85}
.proj-text strong{color:var(--ink);font-weight:500}
.proj-metrics{display:flex;flex-wrap:wrap;gap:7px;margin:13px 0}
.pm{
  background:rgba(45,106,79,0.08);border:1px solid rgba(45,106,79,0.2);
  color:var(--green);font-family:'JetBrains Mono',monospace;
  font-size:0.65rem;padding:4px 9px;border-radius:3px;font-weight:500;
}
.proj-stack{display:flex;flex-wrap:wrap;gap:5px;margin-top:auto;padding-top:14px}
.ps{
  background:var(--bg3);border:1px solid var(--border);
  color:var(--muted);font-family:'JetBrains Mono',monospace;
  font-size:0.6rem;padding:2px 7px;border-radius:3px;
}
.proj-next{
  margin-top:14px;background:rgba(20,18,16,0.03);
  border:1px solid var(--border);border-radius:8px;padding:12px;
}
.pn-label{font-family:'JetBrains Mono',monospace;font-size:0.57rem;color:var(--green);letter-spacing:0.1em;text-transform:uppercase;margin-bottom:4px;font-weight:500}
.pn-text{font-size:0.79rem;color:var(--muted);line-height:1.65}

/* LLM SECTION */
#llm{background:var(--bg2);border-top:1px solid var(--border);border-bottom:1px solid var(--border)}
.llm-grid{display:grid;grid-template-columns:1fr 1fr;gap:60px;align-items:start}
.llm-text p{color:var(--muted);font-size:0.93rem;line-height:2;margin-bottom:16px}
.llm-text p strong{color:var(--ink);font-weight:500}
.llm-text p em{color:var(--green);font-style:normal}
.arch-box{
  background:var(--card);border:1px solid var(--border-strong);
  border-radius:12px;padding:30px;
  box-shadow:0 4px 16px var(--shadow);
}
.arch-title{
  font-family:'JetBrains Mono',monospace;font-size:0.62rem;
  color:var(--muted);letter-spacing:0.16em;text-transform:uppercase;
  margin-bottom:22px;padding-bottom:14px;border-bottom:1px solid var(--border);
}
.arch-layer{
  display:flex;align-items:flex-start;gap:13px;
  padding:11px 8px;border-bottom:1px solid rgba(20,18,16,0.05);
  transition:background 0.18s;border-radius:6px;
}
.arch-layer:last-child{border-bottom:none}
.arch-layer:hover{background:rgba(20,18,16,0.03)}
.al-n{
  width:26px;height:26px;border-radius:6px;
  background:var(--bg3);border:1px solid var(--border-strong);
  display:flex;align-items:center;justify-content:center;
  font-family:'JetBrains Mono',monospace;font-size:0.62rem;
  color:var(--muted);flex-shrink:0;
}
.al-name{font-size:0.8rem;color:var(--ink);margin-bottom:2px;font-weight:500}
.al-tech{font-family:'JetBrains Mono',monospace;font-size:0.6rem;color:var(--muted)}

/* FUTURE */
#future{background:var(--bg)}
.future-grid{display:grid;grid-template-columns:1fr 1fr;gap:22px}
.future-card{
  background:var(--card);border:1px solid var(--border-strong);
  border-radius:12px;padding:32px;
  position:relative;overflow:hidden;transition:all 0.25s;
  box-shadow:0 2px 8px var(--shadow);
}
.future-card:hover{transform:translateY(-5px);box-shadow:0 16px 48px var(--shadow)}
.future-card::after{
  content:'2026';position:absolute;top:20px;right:20px;
  background:var(--ink);color:var(--bg);
  font-family:'JetBrains Mono',monospace;font-size:0.58rem;
  letter-spacing:0.1em;padding:4px 10px;border-radius:3px;
}
.f-num{font-family:'EB Garamond',Georgia,serif;font-size:4.5rem;font-weight:800;font-style:italic;color:rgba(20,18,16,0.07);line-height:1;margin-bottom:8px;letter-spacing:-0.02em}
.f-title{font-family:'EB Garamond',Georgia,serif;font-weight:700;font-size:1.25rem;margin-bottom:10px;letter-spacing:0em;color:var(--ink)}
.f-desc{font-size:0.85rem;color:var(--muted);line-height:1.9;margin-bottom:18px}
.f-why{background:rgba(45,106,79,0.06);border-left:2px solid var(--green-l);padding:10px 14px;font-size:0.8rem;color:var(--muted);border-radius:0 6px 6px 0}
.f-why strong{color:var(--green)}

/* CTA */
#cta{
  text-align:center;padding:130px 64px;
  background:var(--ink2);color:var(--bg);
  position:relative;overflow:hidden;
}
#cta::before{
  content:'';position:absolute;width:800px;height:800px;
  background:radial-gradient(ellipse,rgba(82,183,136,0.06),transparent 70%);
  border-radius:50%;top:50%;left:50%;transform:translate(-50%,-50%);
  pointer-events:none;
}
.cta-title{
  font-family:'EB Garamond',Georgia,serif;
  font-size:clamp(3.2rem,5vw,5.5rem);
  font-weight:700;letter-spacing:-0.01em;
  margin-bottom:20px;line-height:1.08;color:var(--bg);
}
.cta-title .it{font-style:italic;font-weight:300;color:var(--green-xl)}
.cta-sub{color:rgba(247,245,240,0.5);font-size:1rem;max-width:460px;margin:0 auto 48px;line-height:1.75}
.cta-row{display:flex;gap:14px;justify-content:center;flex-wrap:wrap}
.cta-link{
  display:flex;align-items:center;gap:9px;
  background:rgba(247,245,240,0.06);
  border:1px solid rgba(247,245,240,0.12);
  border-radius:8px;padding:15px 20px;
  text-decoration:none;color:var(--bg);
  font-family:'JetBrains Mono',monospace;font-size:0.76rem;
  transition:all 0.22s;cursor:none;letter-spacing:0.04em;
}
.cta-link:hover{background:rgba(247,245,240,0.1);border-color:rgba(247,245,240,0.25);transform:translateY(-3px)}
.cta-link .icon{color:var(--green-xl)}

footer{
  text-align:center;padding:28px 64px;
  border-top:1px solid rgba(247,245,240,0.08);
  background:var(--ink);
  font-family:'JetBrains Mono',monospace;font-size:0.68rem;
  color:rgba(247,245,240,0.3);letter-spacing:0.06em;
}
footer span{color:var(--green-xl)}

@keyframes fadeUp{from{opacity:0;transform:translateY(28px)}to{opacity:1;transform:translateY(0)}}
.reveal{opacity:0;transform:translateY(28px);transition:opacity 0.6s ease,transform 0.6s ease}
.reveal.vis{opacity:1;transform:translateY(0)}

::-webkit-scrollbar{width:5px}
::-webkit-scrollbar-track{background:var(--bg)}
::-webkit-scrollbar-thumb{background:rgba(20,18,16,0.2);border-radius:3px}
::-webkit-scrollbar-thumb:hover{background:rgba(20,18,16,0.4)}

@media(max-width:900px){
  #hero{grid-template-columns:1fr;padding:100px 24px 60px}
  .hero-right{display:none}
  section{padding:80px 24px}
  .about-grid,.llm-grid,.future-grid{grid-template-columns:1fr}
  .skills-grid{grid-template-columns:1fr 1fr}
  .projects-grid{grid-template-columns:1fr}
  nav{padding:16px 24px}
  .nav-menu{display:none}
}
</style>
</head>
<body>

<div id="cursor"></div>
<div id="cursor-ring"></div>
<canvas id="three-canvas"></canvas>

<!-- NAV -->
<nav>
  <a href="#hero" class="nav-brand">Gourang<span>.</span></a>
  <div class="nav-menu">
    <a href="#about">About</a>
    <a href="#skills">Skills</a>
    <a href="#experience">Experience</a>
    <a href="#projects">Projects</a>
    <a href="#cta">Contact</a>
  </div>
  <button class="nav-cta" onclick="document.getElementById('cta').scrollIntoView({behavior:'smooth'})">Hire Me</button>
</nav>

<!-- HERO -->
<section id="hero">
  <div class="hero-left">
    <div class="hero-eyebrow"><span class="dot"></span>Open to Roles · Spring 2026 · Stony Brook, NY</div>
    <h1 class="hero-title">
      Data Scientist &amp; AI Engineer who ships.
    </h1>
    <p class="hero-sub">
      I build <strong>production ML systems, LLM pipelines, and fraud detection engines</strong> that move real business metrics. MS Analytics @ Stony Brook · 2+ years at HSBC & AI startups.
    </p>
    <div class="hero-buttons">
      <a href="#projects" class="btn primary">View Projects →</a>
      <a href="#cta" class="btn secondary">Get in Touch</a>
    </div>
    <div class="hero-stats">
      <div class="hstat"><div class="n">50<span>%</span></div><div class="l">Response Time ↓</div></div>
      <div class="hstat"><div class="n">40<span>%</span></div><div class="l">Cost Reduction</div></div>
      <div class="hstat"><div class="n">94<span>%</span></div><div class="l">Fraud Precision</div></div>
      <div class="hstat"><div class="n">3.6</div><div class="l">GPA — SBU</div></div>
    </div>
  </div>

  <div class="hero-right">
    <div class="profile-card">
      <div class="pc-photo-wrap">
        <img class="pc-photo" src="data:image/jpeg;base64,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" alt="Gourang Chauhan"/>
      </div>
      <div class="pc-name">Gourang Chauhan</div>
      <div class="pc-role">Data Scientist · ML Engineer · AI/LLM Builder</div>
      <div class="pc-location">📍 Stony Brook, NY · MS Analytics @ SBU</div>
      <div class="pc-divider"></div>
      <div class="pc-tags">
        <span class="pc-tag">XGBoost · PyTorch</span>
        <span class="pc-tag">LangGraph · RAG</span>
        <span class="pc-tag">AWS · GCP · Docker</span>
        <span class="pc-tag">Power BI · SQL</span>
        <span class="pc-tag">HSBC · AI Spark</span>
      </div>
      <div class="pc-metrics">
        <div class="pc-m"><div class="val">79.5%</div><div class="lbl">R² Score</div></div>
        <div class="pc-m"><div class="val">600K</div><div class="lbl">Rows Modeled</div></div>
        <div class="pc-m"><div class="val">2+</div><div class="lbl">Yrs Industry</div></div>
        <div class="pc-m"><div class="val">A2A</div><div class="lbl">Agentic AI</div></div>
      </div>
    </div>
  </div>
</section>

<!-- ABOUT -->
<section id="about">
  <span class="s-tag reveal">// 01 about me</span>
  <h2 class="s-title reveal">Not just a model trainer.<br/><span class="it">A problem solver.</span></h2>

  <div class="about-grid">
    <div class="about-text reveal">
      <p>I'm Gourang — a data scientist and ML engineer who <strong>ships models into production</strong>, not just notebooks. My work spans fraud detection at HSBC, agentic LLM pipelines at an AI startup, and current research on post-COVID financial fraud at Stony Brook University.</p>
      <p>At <strong>HSBC Bank EDP</strong>, I built a <em>SQL-driven AML compliance engine</em>, an NLP QA system that cut response time by 50%, and a data warehouse that reduced operational costs by 40%. Not prototypes — live systems serving real financial decisions.</p>
      <p>Before that, I was deep in the LLM stack at AI Spark Technologies — <strong>RAG pipelines with LangGraph, vector search with PgVector and OpenSearch, multi-agent agentic workflows</strong> deployed on AWS. I've seen what breaks in production and I know how to engineer around it.</p>
      <p>I hold a <strong>Bachelor's in Business Statistics</strong> from GGSIPU (GPA 8.1) and am currently completing an <strong>MS in Data/Decision Analytics at Stony Brook (GPA 3.6)</strong>, where I also serve as a Graduate Research Assistant investigating post-COVID digital fraud trends.</p>
      <p>I'm also certified and experienced in <strong>statistical computing (R, Python), big data (Spark, Hive, Hadoop)</strong>, and enterprise-grade database management — giving me a full-stack data perspective that most ML engineers lack.</p>
    </div>
    <div class="about-sidebar reveal">
      <div class="sidebar-photo-wrap">
        <img class="sidebar-photo" src="data:image/jpeg;base64,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" alt="Gourang Chauhan"/>
      </div>
      <div class="about-pills">
        <div class="about-pill"><div class="ap-icon">⚡</div><div><div class="ap-title">Production ML</div><div class="ap-sub">XGBoost, Neural Nets, RF — live systems</div></div></div>
        <div class="about-pill"><div class="ap-icon">🤖</div><div><div class="ap-title">LLM & Agentic AI</div><div class="ap-sub">LangGraph, RAG, Vector DBs, MCP</div></div></div>
        <div class="about-pill"><div class="ap-icon">🏦</div><div><div class="ap-title">Finance & Fraud AI</div><div class="ap-sub">AML, risk scoring, anomaly detection</div></div></div>
        <div class="about-pill"><div class="ap-icon">🎓</div><div><div class="ap-title">MS @ Stony Brook · GPA 3.6</div><div class="ap-sub">Data/Decision Analytics · Aug 2025–Present</div></div></div>
      </div>
    </div>
  </div>
</section>

<!-- SKILLS -->
<section id="skills">
  <span class="s-tag reveal">// 02 tech stack</span>
  <h2 class="s-title reveal">Technical Arsenal</h2>
  <p class="s-sub reveal">Grouped by what I actually do with them — not alphabetical padding.</p>
  <div class="skills-grid">
    <div class="skill-card reveal">
      <span class="sk-icon">🧠</span>
      <div class="sk-name">Machine Learning & Modeling</div>
      <div class="sk-tags"><span class="sk-tag">Scikit-Learn</span><span class="sk-tag">XGBoost</span><span class="sk-tag">Random Forest</span><span class="sk-tag">SVM / kNN</span><span class="sk-tag">TensorFlow</span><span class="sk-tag">Keras</span><span class="sk-tag">PyTorch</span><span class="sk-tag">PCA</span><span class="sk-tag">Anomaly Detection</span></div>
    </div>
    <div class="skill-card reveal">
      <span class="sk-icon">🤖</span>
      <div class="sk-name">GenAI & LLM Engineering</div>
      <div class="sk-tags"><span class="sk-tag hot">LangChain</span><span class="sk-tag hot">LangGraph</span><span class="sk-tag hot">RAG Pipelines</span><span class="sk-tag hot">Agentic AI (A2A)</span><span class="sk-tag hot">HuggingFace</span><span class="sk-tag hot">Whisper STT</span><span class="sk-tag hot">Bark TTS</span><span class="sk-tag hot">MCP</span><span class="sk-tag hot">Prompt Engineering</span></div>
    </div>
    <div class="skill-card reveal">
      <span class="sk-icon">🔍</span>
      <div class="sk-name">Vector Databases & Search</div>
      <div class="sk-tags"><span class="sk-tag hot">FAISS</span><span class="sk-tag hot">Pinecone</span><span class="sk-tag hot">ChromaDB</span><span class="sk-tag hot">OpenSearch</span><span class="sk-tag hot">PgVector</span><span class="sk-tag">Semantic Search</span><span class="sk-tag">Embeddings</span></div>
    </div>
    <div class="skill-card reveal">
      <span class="sk-icon">☁️</span>
      <div class="sk-name">Cloud & MLOps</div>
      <div class="sk-tags"><span class="sk-tag">AWS</span><span class="sk-tag">GCP</span><span class="sk-tag">Docker</span><span class="sk-tag">CI/CD</span><span class="sk-tag">Experiment Tracking</span><span class="sk-tag">PySpark</span><span class="sk-tag">Hadoop / Hive</span><span class="sk-tag">MapReduce</span></div>
    </div>
    <div class="skill-card reveal">
      <span class="sk-icon">🗄️</span>
      <div class="sk-name">Data Engineering & Databases</div>
      <div class="sk-tags"><span class="sk-tag">Python</span><span class="sk-tag">Pandas / NumPy</span><span class="sk-tag">SQL</span><span class="sk-tag">PostgreSQL</span><span class="sk-tag">MySQL</span><span class="sk-tag">MongoDB</span><span class="sk-tag">ETL Pipelines</span><span class="sk-tag">Data Warehousing</span></div>
    </div>
    <div class="skill-card reveal">
      <span class="sk-icon">📊</span>
      <div class="sk-name">Analytics & Visualization</div>
      <div class="sk-tags"><span class="sk-tag">Power BI</span><span class="sk-tag">Tableau</span><span class="sk-tag">Matplotlib</span><span class="sk-tag">Seaborn</span><span class="sk-tag">EDA</span><span class="sk-tag">Statistical Modeling</span><span class="sk-tag">R</span><span class="sk-tag">Excel</span></div>
    </div>
  </div>
</section>

<!-- EXPERIENCE -->
<section id="experience">
  <span class="s-tag reveal">// 03 experience</span>
  <h2 class="s-title reveal">Where I've <span class="it">Delivered</span></h2>
  <p class="s-sub reveal">Real systems. Real constraints. Real business outcomes.</p>
  <div class="exp-list">

    <div class="exp-card reveal">
      <div class="ec-top">
        <div class="ec-company">Stony Brook University</div>
        <span class="ec-period">Jan 2026 — Present</span>
      </div>
      <div class="ec-role">Graduate Research Assistant · Decision Support Systems Lab</div>
      <div class="ec-loc">📍 Stony Brook, NY · GPA 3.6</div>
      <div class="ec-impact"><strong>Research:</strong> Investigating post-COVID digital fraud patterns using ML and statistical modeling to generate academic and cybersecurity policy insights.</div>
      <ul class="ec-list">
        <li>Conducting large-scale EDA and <strong>statistical modeling on financial datasets</strong> to surface fraud patterns, anomaly signals, and evolving digital risk indicators</li>
        <li>Building predictive fraud detection models with Pandas, Scikit-Learn, and NumPy — translating results into <strong>publication-ready cybersecurity insights</strong></li>
        <li>Coursework includes: <strong>Artificial Intelligence, Machine Learning, Statistics & Probability</strong></li>
      </ul>
      <div class="ec-chips"><span class="chip">Fraud Analytics</span><span class="chip">Statistical Modeling</span><span class="chip">GPA 3.6</span></div>
    </div>

    <div class="exp-card reveal">
      <div class="ec-top">
        <div class="ec-company">HSBC Bank EDP</div>
        <span class="ec-period">Oct 2024 — Aug 2025</span>
      </div>
      <div class="ec-role">Data Scientist / Analyst</div>
      <div class="ec-loc">📍 Gurugram, Haryana, India</div>
      <div class="ec-impact"><strong>Challenge:</strong> A global bank needed simultaneous ML-driven fraud detection, AML automation, NLP QA, and a full data infrastructure overhaul — all in production, all live.</div>
      <ul class="ec-list">
        <li>Deployed <strong>ML models (XGBoost, Random Forest, Regression, Classification)</strong> for fraud and risk scoring on live transaction data — plus an NLP-based automated QA system reducing analyst response time by <strong>50%</strong></li>
        <li>Built a <strong>SQL-driven AML compliance automation engine</strong> continuously monitoring customer profiles and flagging transaction anomalies for compliance teams</li>
        <li>Architected a <strong>SQL data warehouse + Power BI reporting layer</strong> for executive analytics with daily Python/SQL pipelines processing large-scale financial datasets</li>
        <li>Optimized cross-team resource allocation, achieving a <strong>40% reduction in production costs</strong> through workflow restructuring and compute efficiency</li>
      </ul>
      <div class="ec-chips"><span class="chip">↓50% Response Time</span><span class="chip">↓40% Costs</span><span class="chip">AML Automation</span><span class="chip">Live Production ML</span></div>
    </div>

    <div class="exp-card reveal">
      <div class="ec-top">
        <div class="ec-company">AI Spark Technologies</div>
        <span class="ec-period">Nov 2023 — Oct 2024</span>
      </div>
      <div class="ec-role">AI / ML Engineer · Intern</div>
      <div class="ec-loc">📍 Noida, Uttar Pradesh, India</div>
      <div class="ec-impact"><strong>Challenge:</strong> Build genuine LLM-powered information retrieval products with real agentic logic and deploy them to production — not prototypes.</div>
      <ul class="ec-list">
        <li>Built <strong>production RAG pipelines</strong> using LangGraph, HuggingFace Transformers, OpenSearch, and PgVector — enabling semantic search over structured and unstructured enterprise documents</li>
        <li>Developed end-to-end <strong>ML pipelines on AWS</strong> with PyTorch and XGBoost, integrated with CI/CD systems, experiment tracking, and end-to-end ML lifecycle monitoring</li>
        <li>Contributed to <strong>Docker-based containerization</strong>, model versioning, and performance monitoring across multiple client-facing AI products</li>
        <li>Gained deep exposure to <strong>Multi-Model Context Protocol (MCP)</strong> for coordinating multiple AI models within unified pipeline architectures</li>
      </ul>
      <div class="ec-chips"><span class="chip">LangGraph Agents</span><span class="chip">RAG on AWS</span><span class="chip">Docker · CI/CD</span><span class="chip">PgVector Semantic Search</span></div>
    </div>

  </div>
</section>

<!-- PROJECTS -->
<section id="projects">
  <span class="s-tag reveal">// 04 case studies</span>
  <h2 class="s-title reveal">Projects</h2>
  <p class="s-sub reveal">Problem → Approach → Model Reasoning → Results. Every single time.</p>
  <div class="projects-grid">

    <div class="proj-card reveal">
      <div class="proj-num">01 / PREDICTIVE ML</div>
      <div class="proj-title">Spotify Song Popularity Prediction</div>
      <div class="proj-type">// Can we predict a hit before it drops?</div>
      <div class="proj-section"><div class="proj-label">Business Problem</div><div class="proj-text">Labels waste millions marketing songs that won't chart. <strong>Pre-release popularity prediction</strong> from audio features alone redirects spend where it matters.</div></div>
      <div class="proj-section"><div class="proj-label">Approach</div><div class="proj-text">Preprocessed a 600K-song dataset with scaling, encoding, and artist popularity bucketing. Benchmarked XGBoost, Neural Nets, and Random Forest. Key insight: <strong>valence and energy beat artist fame</strong> as predictors.</div></div>
      <div class="proj-metrics"><span class="pm">R² = 79.5%</span><span class="pm">600K songs</span><span class="pm">XGBoost winner</span></div>
      <div class="proj-stack"><span class="ps">Python</span><span class="ps">XGBoost</span><span class="ps">TensorFlow/Keras</span><span class="ps">Scikit-Learn</span><span class="ps">Pandas</span></div>
      <div class="proj-next"><div class="pn-label">🔧 Next</div><div class="pn-text">VGGish audio embeddings, FastAPI deployment, artist trajectory time-series features.</div></div>
    </div>

    <div class="proj-card reveal">
      <div class="proj-num">02 / NLP + RECOMMENDATION</div>
      <div class="proj-title">Job–Candidate Matching System</div>
      <div class="proj-type">// Semantic resume-to-role alignment at scale</div>
      <div class="proj-section"><div class="proj-label">Business Problem</div><div class="proj-text">Recruiters screen 200+ resumes manually. Candidates apply blind. <strong>Both sides lose</strong> to keyword mismatch — this replaces it with semantic intelligence.</div></div>
      <div class="proj-section"><div class="proj-label">Approach</div><div class="proj-text">124K+ LinkedIn job postings + 2.4K resumes. NLP pipeline (lemmatization, skill extraction, sentence embeddings) → <strong>XGBoost multi-label domain classifier</strong> → salary prediction → Streamlit interface with top-N recommendations and fallback logic.</div></div>
      <div class="proj-metrics"><span class="pm">F1-micro: 0.718</span><span class="pm">Hamming: 0.098</span><span class="pm">124K+ postings</span></div>
      <div class="proj-stack"><span class="ps">Python</span><span class="ps">XGBoost</span><span class="ps">Sentence-BERT</span><span class="ps">Scikit-Learn</span><span class="ps">Streamlit</span></div>
      <div class="proj-next"><div class="pn-label">🔧 Next</div><div class="pn-text">Fine-tuned bi-encoder (E5/BGE), LLM-generated candidate feedback, FastAPI + Pinecone.</div></div>
    </div>

    <div class="proj-card reveal">
      <div class="proj-num">03 / ANOMALY DETECTION</div>
      <div class="proj-title">Credit Card Fraud Detection</div>
      <div class="proj-type">// 94% precision on a 0.17% fraud rate</div>
      <div class="proj-section"><div class="proj-label">Business Problem</div><div class="proj-text">Fraud costs $32B+ annually. The real ML challenge: <strong>precision on a severely imbalanced dataset</strong> where false positives destroy trust and false negatives cost money.</div></div>
      <div class="proj-section"><div class="proj-label">Approach</div><div class="proj-text">PCA dimensionality reduction → benchmarked k-NN, Random Forest, SVM under SMOTE balancing. K-Means for unsupervised fraud cluster analysis. <strong>Random Forest achieved best precision-recall tradeoff.</strong></div></div>
      <div class="proj-metrics"><span class="pm">94% Precision</span><span class="pm">80% Recall</span><span class="pm">PCA + SMOTE</span></div>
      <div class="proj-stack"><span class="ps">Python</span><span class="ps">Scikit-Learn</span><span class="ps">Random Forest</span><span class="ps">SVM</span><span class="ps">PCA</span><span class="ps">K-Means</span></div>
      <div class="proj-next"><div class="pn-label">🔧 Next</div><div class="pn-text">Autoencoder anomaly layer, SMOTE+Tomek resampling, Evidently AI drift monitoring, real-time FastAPI scoring.</div></div>
    </div>

  </div>
</section>

<!-- LLM ARCHITECTURE -->
<section id="llm">
  <span class="s-tag reveal">// 05 llm & rag positioning</span>
  <h2 class="s-title reveal">My LLM <span class="it">Engineering</span> Stack</h2>
  <p class="s-sub reveal">Not an LLM user. An architect of LLM systems.</p>
  <div class="llm-grid">
    <div class="llm-text reveal">
      <p>Most candidates can call an LLM API. Very few have built the <strong>infrastructure around it</strong> — chunking strategies, retrieval tuning, agent memory, fallback logic, deployment pipelines, and production monitoring.</p>
      <p>At <strong>AI Spark Technologies</strong>, I operated across the full LLM systems stack: production RAG with hybrid retrieval, LangGraph multi-step agents with tool use, and embedding search via both OpenSearch and PgVector at enterprise scale.</p>
      <p>I know precisely where LLMs break: <em>hallucinations from poor chunking, retrieval misses from weak embedding choice, latency spikes from synchronous chain design</em>. And I know the engineering fixes for each failure mode.</p>
      <p>I'm also fluent in <strong>multi-modal pipelines</strong>: Whisper for STT, Bark for TTS, MCP for multi-model coordination — enabling complete end-to-end AI voice and document intelligence systems.</p>
    </div>
    <div class="arch-box reveal">
      <div class="arch-title">// agentic rag pipeline — shipped to production</div>
      <div class="arch-layer"><div class="al-n">01</div><div><div class="al-name">User Input Layer</div><div class="al-tech">Whisper STT · REST API · Streamlit UI</div></div></div>
      <div class="arch-layer"><div class="al-n">02</div><div><div class="al-name">Agent Orchestration</div><div class="al-tech">LangGraph · LangChain · Tool Routing · Memory</div></div></div>
      <div class="arch-layer"><div class="al-n">03</div><div><div class="al-name">Retrieval / RAG Layer</div><div class="al-tech">FAISS · Pinecone · ChromaDB · OpenSearch · PgVector</div></div></div>
      <div class="arch-layer"><div class="al-n">04</div><div><div class="al-name">Embedding + Reranking</div><div class="al-tech">HuggingFace Transformers · Sentence Encoders</div></div></div>
      <div class="arch-layer"><div class="al-n">05</div><div><div class="al-name">LLM Inference</div><div class="al-tech">Prompt Engineering · Context Mgmt · Fallback Logic</div></div></div>
      <div class="arch-layer"><div class="al-n">06</div><div><div class="al-name">Output & Deployment</div><div class="al-tech">Bark TTS · Docker · AWS · CI/CD · Monitoring</div></div></div>
    </div>
  </div>
</section>

<!-- FUTURE PROJECTS -->
<section id="future">
  <span class="s-tag reveal">// 06 roadmap</span>
  <h2 class="s-title reveal">2 Projects to Build <span class="it">This Year</span></h2>
  <p class="s-sub reveal">Strategically chosen to compound your existing strengths for target roles.</p>
  <div class="future-grid">
    <div class="future-card reveal">
      <div class="f-num">01</div>
      <div class="f-title">Financial Document Intelligence Agent</div>
      <div class="f-desc">Multi-agent system ingesting 10-K/10-Q filings, earnings transcripts, and financial news. Answers questions, surfaces risks, generates structured reports with confidence-scored citations and cross-company comparisons. Bloomberg Terminal meets LLM — built by you.</div>
      <div class="proj-stack" style="margin-bottom:16px"><span class="ps">LangGraph</span><span class="ps">RAG + Reranking</span><span class="ps">Pinecone</span><span class="ps">SEC EDGAR API</span><span class="ps">FastAPI</span></div>
      <div class="f-why"><strong>Why this:</strong> Directly leverages your HSBC finance domain knowledge + LLM engineering. Strong signal for fintech, hedge funds, and Applied Scientist roles at Bloomberg/Palantir-type firms.</div>
    </div>
    <div class="future-card reveal">
      <div class="f-num">02</div>
      <div class="f-title">Real-Time Fraud Detection + XAI Dashboard</div>
      <div class="f-desc">Kafka streaming pipeline → XGBoost/Isolation Forest ensemble → SHAP explainability layer → Grafana live dashboard with configurable risk alert triggers and concept drift detection via Evidently AI. Deployable on GCP.</div>
      <div class="proj-stack" style="margin-bottom:16px"><span class="ps">Kafka</span><span class="ps">XGBoost</span><span class="ps">SHAP</span><span class="ps">Evidently AI</span><span class="ps">GCP</span><span class="ps">Grafana</span></div>
      <div class="f-why"><strong>Why this:</strong> Supercharges your existing fraud work with streaming + explainability + MLOps signals. Maps directly to DS and ML Engineer JDs at banks, fintech, and payment processors.</div>
    </div>
  </div>
</section>

<!-- CTA -->
<section id="cta">
  <h2 class="cta-title">Let's build something<br/><span class="it">that ships.</span></h2>
  <p class="cta-sub">Open to Data Scientist, ML Engineer, AI/LLM Engineer, and Applied Scientist roles. Available Spring/Summer 2026. Based in Stony Brook, NY.</p>
  <div class="cta-row">
    <a href="mailto:gourangchauhan99@gmail.com" class="cta-link"><span class="icon">✉</span>gourangchauhan99@gmail.com</a>
    <a href="tel:9292446317" class="cta-link"><span class="icon">☎</span>(929) 244-6317</a>
    <a href="https://linkedin.com/in/gourang-chauhan-a75901187" target="_blank" class="cta-link"><span class="icon">in</span>LinkedIn Profile</a>
  </div>
</section>

<footer>Built with intention. Powered by data. © 2026 <span>Gourang Chauhan</span> — Data Scientist & AI Engineer.</footer>

<script>
/* ── CURSOR ── */
const cursor=document.getElementById('cursor'),ring=document.getElementById('cursor-ring');
let mx=0,my=0,rx=0,ry=0;
document.addEventListener('mousemove',e=>{mx=e.clientX;my=e.clientY;cursor.style.left=mx+'px';cursor.style.top=my+'px'});
(function animRing(){rx+=(mx-rx)*0.12;ry+=(my-ry)*0.12;ring.style.left=rx+'px';ring.style.top=ry+'px';requestAnimationFrame(animRing)})();
document.querySelectorAll('a,button,.proj-card,.skill-card,.exp-card,.about-pill').forEach(el=>{
  el.addEventListener('mouseenter',()=>{cursor.style.transform='translate(-50%,-50%) scale(2.5)';ring.style.width='56px';ring.style.height='56px'});
  el.addEventListener('mouseleave',()=>{cursor.style.transform='translate(-50%,-50%) scale(1)';ring.style.width='36px';ring.style.height='36px'});
});

/* ── THREE.JS ── */
const canvas=document.getElementById('three-canvas');
const renderer=new THREE.WebGLRenderer({canvas,alpha:true,antialias:true});
renderer.setPixelRatio(Math.min(window.devicePixelRatio,2));
const scene=new THREE.Scene();
const camera=new THREE.PerspectiveCamera(60,window.innerWidth/window.innerHeight,0.1,1000);
camera.position.z=30;
function resize(){renderer.setSize(window.innerWidth,window.innerHeight);camera.aspect=window.innerWidth/window.innerHeight;camera.updateProjectionMatrix()}
resize();window.addEventListener('resize',resize);

const count=1400,geo=new THREE.BufferGeometry();
const pos=new Float32Array(count*3),col=new Float32Array(count*3);
const palette=[[0.08,0.09,0.07],[0.18,0.42,0.31],[0.32,0.72,0.54],[0.58,0.84,0.70],[0.93,0.92,0.88]];
for(let i=0;i<count;i++){
  pos[i*3]=(Math.random()-0.5)*90;pos[i*3+1]=(Math.random()-0.5)*90;pos[i*3+2]=(Math.random()-0.5)*60;
  const c=palette[Math.floor(Math.random()*palette.length)];
  col[i*3]=c[0];col[i*3+1]=c[1];col[i*3+2]=c[2];
}
geo.setAttribute('position',new THREE.BufferAttribute(pos,3));
geo.setAttribute('color',new THREE.BufferAttribute(col,3));
const pts=new THREE.Points(geo,new THREE.PointsMaterial({size:0.15,vertexColors:true,transparent:true,opacity:0.5,sizeAttenuation:true}));
scene.add(pts);

const sGeo=new THREE.IcosahedronGeometry(9,1);
const sphere=new THREE.Mesh(sGeo,new THREE.MeshBasicMaterial({color:0x2d6a4f,wireframe:true,transparent:true,opacity:0.06}));
sphere.position.set(16,-2,0);scene.add(sphere);

const tGeo=new THREE.TorusGeometry(13,0.07,8,80);
const torus=new THREE.Mesh(tGeo,new THREE.MeshBasicMaterial({color:0x141210,transparent:true,opacity:0.05}));
torus.rotation.x=Math.PI/4;torus.position.set(16,0,0);scene.add(torus);

let mouse3d={x:0,y:0};
document.addEventListener('mousemove',e=>{mouse3d.x=(e.clientX/window.innerWidth-0.5)*2;mouse3d.y=-(e.clientY/window.innerHeight-0.5)*2});
let t=0;
(function anim(){
  t+=0.003;requestAnimationFrame(anim);
  pts.rotation.y=t*0.04;pts.rotation.x=t*0.015;
  sphere.rotation.y=t*0.25;sphere.rotation.x=t*0.12;
  torus.rotation.z=t*0.18;
  camera.position.x+=(mouse3d.x*1.5-camera.position.x)*0.018;
  camera.position.y+=(mouse3d.y*1.5-camera.position.y)*0.018;
  camera.lookAt(scene.position);
  renderer.render(scene,camera);
})();

/* ── SCROLL REVEAL ── */
const reveals=document.querySelectorAll('.reveal');
const obs=new IntersectionObserver(entries=>{
  entries.forEach(e=>{
    if(e.isIntersecting){
      const sib=[...e.target.parentElement.querySelectorAll('.reveal:not(.vis)')];
      const idx=sib.indexOf(e.target);
      setTimeout(()=>e.target.classList.add('vis'),idx*80);
      obs.unobserve(e.target);
    }
  });
},{threshold:0.1,rootMargin:'0px 0px -40px 0px'});
reveals.forEach(r=>obs.observe(r));

/* ── NAV ACTIVE ── */
const secs=document.querySelectorAll('section[id]');
const navAs=document.querySelectorAll('.nav-menu a');
window.addEventListener('scroll',()=>{
  let cur='';
  secs.forEach(s=>{if(window.scrollY>=s.offsetTop-130)cur=s.id});
  navAs.forEach(a=>{a.style.color=a.getAttribute('href')==='#'+cur?'var(--ink)':''});
});
</script>
</body>
</html>
