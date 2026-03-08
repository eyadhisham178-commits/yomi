<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<meta name="theme-color" content="#F0F4FF">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="default">
<meta name="apple-mobile-web-app-title" content="ظٹظˆظ…ظٹ">
<title>ظٹظˆظ…ظٹ âڈ±</title>

<style>
  * { box-sizing: border-box; margin: 0; padding: 0; -webkit-tap-highlight-color: transparent; }

  :root {
    --bg: #F0F4FF;
    --card: #FFFFFF;
    --border: #E0E7FF;
    --text: #1a1a2e;
    --muted: #888;
    --shadow: 0 2px 12px rgba(0,0,0,0.08);
  }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Segoe UI', Tahoma, sans-serif;
    min-height: 100vh;
    padding: 20px 14px 120px;
    max-width: 480px;
    margin: 0 auto;
  }

  .header { text-align: center; margin-bottom: 24px; }
  .header-title { font-size: 36px; font-weight: 900; color: #1a1a2e; letter-spacing: -1px; }
  .header-sub { font-size: 13px; color: var(--muted); margin-top: 2px; }

  .days-scroll { display: flex; gap: 8px; overflow-x: auto; padding-bottom: 8px; margin-bottom: 20px; scrollbar-width: none; }
  .days-scroll::-webkit-scrollbar { display: none; }
  .day-tab { flex-shrink: 0; padding: 10px 18px; border-radius: 50px; border: 2px solid var(--border); background: white; font-size: 14px; font-weight: 700; cursor: pointer; transition: all 0.2s; color: var(--muted); }
  .day-tab.active { color: white; border-color: transparent; box-shadow: var(--shadow); }

  .bar-wrap { background: white; border-radius: 16px; padding: 16px; margin-bottom: 16px; box-shadow: var(--shadow); }
  .bar-title { font-size: 13px; color: var(--muted); margin-bottom: 10px; display: flex; justify-content: space-between; align-items: center; }
  .bar-title .day-label { font-size: 18px; font-weight: 900; color: var(--text); }
  .bar-title .pct { font-size: 22px; font-weight: 900; }
  .bar { height: 24px; background: #f0f0f0; border-radius: 12px; overflow: hidden; display: flex; }
  .bar-labels { display: flex; justify-content: space-between; margin-top: 8px; font-size: 12px; color: var(--muted); font-weight: 600; }

  .stats { display: flex; gap: 10px; margin-bottom: 16px; }
  .stat { flex: 1; background: white; border-radius: 14px; padding: 14px; text-align: center; box-shadow: var(--shadow); }
  .stat-num { font-size: 24px; font-weight: 900; }
  .stat-label { font-size: 11px; color: var(--muted); margin-top: 2px; font-weight: 600; }

  .active-box { border-radius: 18px; padding: 20px; margin-bottom: 16px; text-align: center; }
  .active-badge { display: inline-block; font-size: 11px; letter-spacing: 2px; padding: 5px 14px; border-radius: 20px; color: white; margin-bottom: 10px; font-weight: 700; }
  .active-name { font-size: 24px; font-weight: 900; margin-bottom: 8px; }
  .active-timer { font-size: 60px; font-weight: 900; letter-spacing: 2px; font-variant-numeric: tabular-nums; line-height: 1; }
  .active-of { font-size: 13px; color: #888; margin-top: 8px; font-weight: 600; }
  .active-stop { margin-top: 14px; border: none; color: white; padding: 12px 30px; border-radius: 50px; cursor: pointer; font-size: 15px; font-weight: 800; font-family: inherit; }

  .add-box { background: white; border-radius: 18px; padding: 18px; margin-bottom: 16px; box-shadow: var(--shadow); }
  .add-title { font-size: 17px; font-weight: 900; margin-bottom: 14px; color: var(--text); }
  .add-row { display: flex; gap: 8px; align-items: center; flex-wrap: wrap; }
  .add-input { flex: 1; min-width: 120px; background: var(--bg); border: 2px solid var(--border); color: var(--text); padding: 12px 14px; border-radius: 12px; font-size: 15px; font-family: inherit; outline: none; }
  .add-input:focus { border-color: #6366f1; }
  .time-wrap { display: flex; align-items: center; gap: 4px; }
  .add-num { width: 54px; background: var(--bg); border: 2px solid var(--border); color: var(--text); padding: 12px 8px; border-radius: 12px; font-size: 15px; text-align: center; font-family: inherit; outline: none; -moz-appearance: textfield; }
  .add-num::-webkit-outer-spin-button, .add-num::-webkit-inner-spin-button { -webkit-appearance: none; }
  .add-num:focus { border-color: #6366f1; }
  .add-sep { font-size: 22px; color: var(--muted); font-weight: 900; }
  .add-btn { background: linear-gradient(135deg, #6366f1, #a855f7); border: none; color: white; padding: 12px 22px; border-radius: 12px; cursor: pointer; font-weight: 900; font-size: 16px; font-family: inherit; box-shadow: 0 4px 12px #6366f140; }
  .add-btn:disabled { background: #e0e0e0; color: #aaa; box-shadow: none; cursor: not-allowed; }
  .add-hint { font-size: 13px; margin-top: 10px; font-weight: 700; }

  .legend { display: flex; flex-wrap: wrap; gap: 8px; margin-bottom: 16px; }
  .legend-item { display: flex; align-items: center; gap: 6px; background: white; padding: 7px 14px; border-radius: 50px; box-shadow: var(--shadow); font-size: 13px; font-weight: 700; }
  .legend-dot { width: 12px; height: 12px; border-radius: 50%; flex-shrink: 0; }

  .task { background: white; border-radius: 16px; padding: 16px; margin-bottom: 10px; box-shadow: var(--shadow); border-right: 6px solid; transition: all 0.3s; }
  .task-inner { display: flex; align-items: center; gap: 12px; }
  .task-num { width: 38px; height: 38px; border-radius: 10px; display: flex; align-items: center; justify-content: center; font-weight: 900; font-size: 16px; color: white; flex-shrink: 0; }
  .task-info { flex: 1; min-width: 0; }
  .task-name { font-size: 17px; font-weight: 800; margin-bottom: 7px; }
  .task-name.done { text-decoration: line-through; color: #aaa; }
  .task-prog { height: 8px; background: #f0f0f0; border-radius: 4px; overflow: hidden; }
  .task-prog-fill { height: 100%; border-radius: 4px; transition: width 1s linear; }
  .task-meta { display: flex; justify-content: space-between; margin-top: 6px; font-size: 12px; color: var(--muted); font-weight: 600; }
  .task-remain { font-size: 14px; font-weight: 900; }
  .task-btns { display: flex; gap: 6px; flex-shrink: 0; }
  .task-btn { width: 40px; height: 40px; border-radius: 10px; border: none; cursor: pointer; font-size: 16px; display: flex; align-items: center; justify-content: center; font-family: inherit; font-weight: 700; }
  .btn-play { color: white; }
  .btn-reset { background: #f5f5f5; color: #888; }
  .btn-delete { background: #fff0f0; color: #ff4444; }

  .empty { text-align: center; color: #ccc; padding: 40px; font-size: 15px; }
  .empty-icon { font-size: 52px; margin-bottom: 12px; }
  .done-box { text-align: center; margin-top: 20px; padding: 24px; background: linear-gradient(135deg, #06D6A015, #4ECDC415); border: 2px solid #06D6A0; border-radius: 18px; }

  .install-banner { position: fixed; bottom: 0; left: 0; right: 0; background: white; border-top: 1px solid var(--border); padding: 14px 16px; display: flex; align-items: center; justify-content: space-between; gap: 10px; z-index: 100; max-width: 480px; margin: 0 auto; box-shadow: 0 -4px 20px rgba(0,0,0,0.08); }
  .install-text strong { color: var(--text); display: block; font-size: 14px; margin-bottom: 2px; }
  .install-text span { font-size: 12px; color: var(--muted); }
  .install-btn { background: linear-gradient(135deg, #6366f1, #a855f7); border: none; color: white; padding: 10px 18px; border-radius: 12px; cursor: pointer; font-weight: 800; font-size: 13px; font-family: inherit; }
  .install-close { background: transparent; border: none; color: #ccc; font-size: 20px; cursor: pointer; }

  @keyframes pulse { 0%,100%{opacity:1} 50%{opacity:0.85} }
  .pulsing { animation: pulse 2s infinite; }
</style>
</head>
<body>

<div class="header">
  <div class="header-title">âڈ± ظٹظˆظ…ظٹ</div>
  <div class="header-sub">ط§ط³طھط؛ظ„ ظƒظ„ ط«ط§ظ†ظٹط© ظپظٹ ظٹظˆظ…ظƒ</div>
</div>

<div class="days-scroll" id="days-tabs"></div>

<div class="bar-wrap">
  <div class="bar-title">
    <span class="day-label" id="day-name-label"></span>
    <span class="pct" id="bar-pct">0%</span>
  </div>
  <div class="bar" id="day-bar"></div>
  <div class="bar-labels">
    <span id="elapsed-label">ط§ظ„ظ…ظڈظ†ط¬ط²: 00:00:00</span>
    <span id="remaining-label">ط§ظ„ظ…طھط¨ظ‚ظٹ: 24:00:00</span>
  </div>
</div>

<div class="stats">
  <div class="stat">
    <div class="stat-num" id="stat-tasks" style="color:#6366f1">0</div>
    <div class="stat-label">ظ…ظ‡ط§ظ…</div>
  </div>
  <div class="stat">
    <div class="stat-num" id="stat-done" style="color:#06D6A0">0</div>
    <div class="stat-label">ط®ظ„طµطھ</div>
  </div>
  <div class="stat">
    <div class="stat-num" id="stat-left" style="color:#f59e0b">24ط³</div>
    <div class="stat-label">ظ…طھط¨ظ‚ظٹ ظ„ظ„طھظˆط²ظٹط¹</div>
  </div>
</div>

<div id="active-box" style="display:none"></div>

<div class="add-box">
  <div class="add-title">+ ط¥ط¶ط§ظپط© ظ…ظ‡ظ…ط©</div>
  <div class="add-row">
    <input class="add-input" id="task-name" placeholder="ط§ط³ظ… ط§ظ„ظ…ظ‡ظ…ط©..." type="text">
    <div class="time-wrap">
      <input class="add-num" id="task-h" placeholder="ط³" type="number" min="0" max="23">
      <div class="add-sep">:</div>
      <input class="add-num" id="task-m" placeholder="ط¯" type="number" min="0" max="59">
    </div>
    <button class="add-btn" id="add-btn" onclick="addTask()">ط£ط¶ظپ</button>
  </div>
  <div class="add-hint" id="add-hint"></div>
</div>

<div class="legend" id="legend"></div>
<div id="tasks-list"></div>
<div id="done-msg" style="display:none" class="done-box">
  <div style="font-size:40px">ًں”¥</div>
  <div style="font-size:22px;font-weight:900;color:#06D6A0;margin-top:10px">ط§ط³طھط؛ظ„ظٹطھ ظٹظˆظ…ظƒ ظƒظ„ظ‡!</div>
</div>

<div class="install-banner" id="install-banner" style="display:none">
  <div class="install-text">
    <strong>ًں“² ظ†ط²ظ‘ظ„ظ‡ ط¹ظ„ظ‰ ظ…ظˆط¨ط§ظٹظ„ظƒ</strong>
    <span>ط´ط؛ظ‘ظ„ظ‡ ط²ظٹ app ط­ظ‚ظٹظ‚ظٹ</span>
  </div>
  <button class="install-btn" id="install-btn">ظ†ط²ظ‘ظ„</button>
  <button class="install-close" onclick="document.getElementById('install-banner').style.display='none'">âœ•</button>
</div>

<script>
const TOTAL = 24 * 3600;
const DAYS = ["ط§ظ„ط³ط¨طھ","ط§ظ„ط£ط­ط¯","ط§ظ„ط§ط«ظ†ظٹظ†","ط§ظ„ط«ظ„ط§ط«ط§ط،","ط§ظ„ط£ط±ط¨ط¹ط§ط،","ط§ظ„ط®ظ…ظٹط³","ط§ظ„ط¬ظ…ط¹ط©"];
const DAY_COLORS = ["#6366f1","#f59e0b","#06D6A0","#ef4444","#3b82f6","#a855f7","#ec4899"];
const TASK_COLORS = ["#6366f1","#ef4444","#06D6A0","#f59e0b","#3b82f6","#a855f7","#ec4899","#14b8a6","#f97316","#84cc16","#0ea5e9","#e11d48"];

let data = JSON.parse(localStorage.getItem("yomi-v2") || "{}");
let currentDay = (new Date().getDay() + 6) % 7;
let activeId = null;
let ticker = null;

function save() { localStorage.setItem("yomi-v2", JSON.stringify(data)); }
function getTasks() { return data[currentDay] || []; }
function setTasks(t) { data[currentDay] = t; }
function fmt(s) {
  s = Math.max(0,s);
  return `${String(Math.floor(s/3600)).padStart(2,"0")}:${String(Math.floor((s%3600)/60)).padStart(2,"0")}:${String(s%60).padStart(2,"0")}`;
}
function fmtH(s) {
  s = Math.max(0,s);
  const h=Math.floor(s/3600), m=Math.floor((s%3600)/60);
  if(h===0) return `${m}ط¯`; if(m===0) return `${h}ط³`; return `${h}ط³ ${m}ط¯`;
}
function getC(i) { return TASK_COLORS[i % TASK_COLORS.length]; }
function allocated() { return getTasks().reduce((a,t)=>a+t.total,0); }
function elapsed() { return getTasks().reduce((a,t)=>a+(t.total-t.rem),0); }

function addTask() {
  const name = document.getElementById("task-name").value.trim();
  const h = parseInt(document.getElementById("task-h").value)||0;
  const m = parseInt(document.getElementById("task-m").value)||0;
  const secs = h*3600+m*60;
  if(!name||secs<=0||secs>TOTAL-allocated()) return;
  const tasks = getTasks();
  tasks.push({id:Date.now(),name,total:secs,rem:secs});
  setTasks(tasks);
  document.getElementById("task-name").value="";
  document.getElementById("task-h").value="";
  document.getElementById("task-m").value="";
  save(); render();
}

function toggleTask(id) { activeId=(activeId===id)?null:id; startTicker(); render(); }
function resetTask(id) { if(activeId===id){activeId=null;clearInterval(ticker);} setTasks(getTasks().map(t=>t.id===id?{...t,rem:t.total}:t)); save(); render(); }
function deleteTask(id) { if(activeId===id){activeId=null;clearInterval(ticker);} setTasks(getTasks().filter(t=>t.id!==id)); save(); render(); }

function startTicker() {
  clearInterval(ticker);
  if(activeId===null) return;
  ticker = setInterval(()=>{
    const tasks=getTasks(), t=tasks.find(x=>x.id===activeId);
    if(!t||t.rem<=0){activeId=null;clearInterval(ticker);render();return;}
    setTasks(tasks.map(x=>x.id===activeId?{...x,rem:x.rem-1}:x));
    save(); render();
  },1000);
}

function switchDay(i) { if(activeId){activeId=null;clearInterval(ticker);} currentDay=i; render(); }

function render() {
  const tasks=getTasks(), dayC=DAY_COLORS[currentDay];
  
  // tabs
  document.getElementById("days-tabs").innerHTML=DAYS.map((d,i)=>
    `<div class="day-tab ${i===currentDay?'active':''}" style="${i===currentDay?`background:${DAY_COLORS[i]};`:''}" onclick="switchDay(${i})">${d}</div>`
  ).join("");

  // bar
  const el=elapsed(), alloc=allocated(), pct=Math.round((el/TOTAL)*100);
  document.getElementById("day-name-label").textContent=DAYS[currentDay];
  document.getElementById("bar-pct").style.color=dayC;
  document.getElementById("bar-pct").textContent=pct+"%";
  document.getElementById("elapsed-label").textContent="ط§ظ„ظ…ظڈظ†ط¬ط²: "+fmt(el);
  document.getElementById("remaining-label").textContent="ط§ظ„ظ…طھط¨ظ‚ظٹ: "+fmt(TOTAL-el);

  let barHTML=tasks.map((t,i)=>{
    const w=(t.total/TOTAL)*100;
    const filled=((t.total-t.rem)/t.total)*100;
    return `<div style="width:${w}%;background:#e8e8e8;position:relative;overflow:hidden;">
      <div style="position:absolute;top:0;left:0;width:${filled}%;height:100%;background:${getC(i)};transition:width 1s linear;"></div>
    </div>`;
  }).join("");
  const leftW=((TOTAL-alloc)/TOTAL)*100;
  if(leftW>0) barHTML+=`<div style="flex:1;background:#f0f0f0;"></div>`;
  document.getElementById("day-bar").innerHTML=barHTML;

  // stats
  const done=tasks.filter(t=>t.rem===0).length;
  document.getElementById("stat-tasks").textContent=tasks.length;
  document.getElementById("stat-done").textContent=done;
  document.getElementById("stat-left").textContent=fmtH(TOTAL-alloc);

  // active
  const ab=document.getElementById("active-box"), at=tasks.find(t=>t.id===activeId), atI=tasks.findIndex(t=>t.id===activeId);
  if(at){
    const c=getC(atI);
    ab.style.display="block"; ab.className="active-box pulsing";
    ab.style.cssText=`display:block;background:${c}15;border:2px solid ${c};border-radius:18px;padding:20px;margin-bottom:16px;text-align:center;animation:pulse 2s infinite;`;
    ab.innerHTML=`<div class="active-badge" style="background:${c}">â–¶ ط´ط؛ط§ظ„ ط¯ظ„ظˆظ‚طھظٹ</div>
      <div class="active-name">${at.name}</div>
      <div class="active-timer" style="color:${c}">${fmt(at.rem)}</div>
      <div class="active-of">ظ…ظ† ${fmtH(at.total)}</div>
      <button class="active-stop" style="background:${c}" onclick="toggleTask(${at.id})">âڈ¸ ظˆظ‚ظ‘ظپ</button>`;
  } else { ab.style.display="none"; }

  // hint
  const hint=document.getElementById("add-hint"), rem=TOTAL-alloc;
  if(rem>0){hint.style.color="#f59e0b";hint.textContent="âڑ، ظ…طھط¨ظ‚ظٹ ظ„ظ„طھظˆط²ظٹط¹: "+fmtH(rem);}
  else{hint.style.color="#06D6A0";hint.textContent="âœ“ ظ…ظ…طھط§ط²! ظˆط²ظ‘ط¹طھ ط§ظ„ظ€ 24 ط³ط§ط¹ط© ظƒظ„ظ‡ط§";}
  document.getElementById("add-btn").disabled=rem<=0;

  // legend
  document.getElementById("legend").innerHTML=tasks.map((t,i)=>
    `<div class="legend-item"><div class="legend-dot" style="background:${getC(i)}"></div><span>${t.name} آ· ${fmtH(t.total)}</span></div>`
  ).join("")+(rem>0?`<div class="legend-item"><div class="legend-dot" style="background:#e0e0e0;border:1px solid #ccc"></div><span>ط؛ظٹط± ظ…ط­ط¯ط¯ آ· ${fmtH(rem)}</span></div>`:"");

  // tasks
  const list=document.getElementById("tasks-list");
  if(tasks.length===0){
    list.innerHTML=`<div class="empty"><div class="empty-icon">âڈ±</div>ط§ط¨ط¯ط£ ط¨ط¥ط¶ط§ظپط© ظ…ظ‡ط§ظ… ${DAYS[currentDay]} ًں‘†</div>`;
  } else {
    list.innerHTML=tasks.map((t,i)=>{
      const c=getC(i), prog=((t.total-t.rem)/t.total)*100, isA=t.id===activeId, isDone=t.rem===0;
      return `<div class="task" style="border-right-color:${c};${isA?`background:${c}10;`:''}" >
        <div class="task-inner">
          <div class="task-num" style="background:${c}">${i+1}</div>
          <div class="task-info">
            <div class="task-name ${isDone?'done':''}">${t.name}</div>
            <div class="task-prog"><div class="task-prog-fill" style="width:${prog}%;background:${c}"></div></div>
            <div class="task-meta">
              <span>${fmtH(t.total-t.rem)} ظ…ظ† ${fmtH(t.total)}</span>
              <span class="task-remain" style="color:${isDone?'#06D6A0':c}">${isDone?"âœ“ ط®ظ„طµطھ":fmt(t.rem)}</span>
            </div>
          </div>
          <div class="task-btns">
            ${!isDone?`<button class="task-btn btn-play" style="background:${c}" onclick="toggleTask(${t.id})">${isA?'âڈ¸':'â–¶'}</button>`:''}
            <button class="task-btn btn-reset" onclick="resetTask(${t.id})">â†؛</button>
            <button class="task-btn btn-delete" onclick="deleteTask(${t.id})">âœ•</button>
          </div>
        </div>
      </div>`;
    }).join("");
  }

  document.getElementById("done-msg").style.display=(tasks.length>0&&tasks.every(t=>t.rem===0))?"block":"none";
}

["task-name","task-h","task-m"].forEach(id=>document.getElementById(id).addEventListener("keydown",e=>e.key==="Enter"&&addTask()));

let deferredPrompt;
window.addEventListener("beforeinstallprompt",(e)=>{e.preventDefault();deferredPrompt=e;document.getElementById("install-banner").style.display="flex";});
document.getElementById("install-btn").addEventListener("click",async()=>{if(!deferredPrompt)return;deferredPrompt.prompt();await deferredPrompt.userChoice;deferredPrompt=null;document.getElementById("install-banner").style.display="none";});

const manifest={name:"ظٹظˆظ…ظٹ",short_name:"ظٹظˆظ…ظٹ",start_url:".",display:"standalone",background_color:"#F0F4FF",theme_color:"#6366f1",orientation:"portrait",icons:[{src:"data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'><rect width='100' height='100' rx='20' fill='%236366f1'/><text y='.9em' font-size='80' x='10'>âڈ±</text></svg>",sizes:"any",type:"image/svg+xml"}]};
const mb=new Blob([JSON.stringify(manifest)],{type:"application/json"});
const ml=document.createElement("link");ml.rel="manifest";ml.href=URL.createObjectURL(mb);document.head.appendChild(ml);

if("serviceWorker" in navigator){const sw=`const C="yomi-v2";self.addEventListener("install",e=>e.waitUntil(caches.open(C).then(c=>c.addAll(["."]))));self.addEventListener("fetch",e=>e.respondWith(caches.match(e.request).then(r=>r||fetch(e.request))));`;navigator.serviceWorker.register(URL.createObjectURL(new Blob([sw],{type:"application/javascript"}))).catch(()=>{});}

render();
</script>
</body>
</html>
