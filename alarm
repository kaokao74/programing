<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>منبه متكرر</title>
<link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;500;600;700&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --bg: #0f0f13;
    --surface: #1a1a22;
    --surface2: #22222e;
    --border: rgba(255,255,255,0.08);
    --border2: rgba(255,255,255,0.15);
    --text: #f0eeff;
    --text2: #9896b0;
    --accent: #7c6ff7;
    --accent2: #a89ff9;
    --green: #3ecf8e;
    --red: #f87171;
    --radius: 14px;
  }

  body {
    font-family: 'Cairo', sans-serif;
    background: var(--bg);
    color: var(--text);
    min-height: 100vh;
    padding: 2rem 1rem;
  }

  body::before {
    content: '';
    position: fixed;
    top: -200px; right: -200px;
    width: 600px; height: 600px;
    background: radial-gradient(circle, rgba(124,111,247,0.12) 0%, transparent 70%);
    pointer-events: none;
  }

  .container { max-width: 560px; margin: 0 auto; }

  header { text-align: center; margin-bottom: 2.5rem; }
  header .icon { font-size: 2.5rem; margin-bottom: 0.5rem; }
  header h1 { font-size: 1.8rem; font-weight: 700; color: var(--text); letter-spacing: -0.5px; }
  header p { font-size: 0.9rem; color: var(--text2); margin-top: 4px; }

  .card {
    background: var(--surface);
    border: 0.5px solid var(--border);
    border-radius: var(--radius);
    padding: 1.5rem;
    margin-bottom: 1.25rem;
  }

  .card-title {
    font-size: 0.78rem;
    font-weight: 600;
    letter-spacing: 0.08em;
    color: var(--text2);
    text-transform: uppercase;
    margin-bottom: 1.25rem;
  }

  .field-label { font-size: 0.82rem; color: var(--text2); margin-bottom: 6px; }

  .row { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; margin-bottom: 1rem; }
  .col { display: flex; flex-direction: column; }

  input[type="text"], input[type="time"], select {
    background: var(--surface2);
    border: 0.5px solid var(--border2);
    border-radius: 9px;
    color: var(--text);
    font-family: 'Cairo', sans-serif;
    font-size: 0.92rem;
    padding: 10px 14px;
    outline: none;
    transition: border-color 0.2s;
    width: 100%;
  }
  input:focus, select:focus { border-color: var(--accent); }
  select option { background: var(--surface2); }

  .add-btn {
    width: 100%;
    margin-top: 0.25rem;
    padding: 12px;
    background: var(--accent);
    border: none;
    border-radius: 10px;
    color: #fff;
    font-family: 'Cairo', sans-serif;
    font-size: 1rem;
    font-weight: 600;
    cursor: pointer;
    transition: opacity 0.2s, transform 0.1s;
  }
  .add-btn:hover { opacity: 0.88; }
  .add-btn:active { transform: scale(0.98); }

  .alarms-list { display: flex; flex-direction: column; gap: 0; }

  .alarm-item {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 12px;
    padding: 14px 0;
    border-bottom: 0.5px solid var(--border);
  }
  .alarm-item:last-child { border-bottom: none; padding-bottom: 0; }
  .alarm-item:first-child { padding-top: 0; }

  .alarm-info { flex: 1; min-width: 0; }
  .alarm-name { font-size: 1rem; font-weight: 600; color: var(--text); }
  .alarm-desc { font-size: 0.78rem; color: var(--text2); margin-top: 3px; }
  .alarm-next { font-size: 0.75rem; color: var(--accent2); margin-top: 4px; }

  .alarm-actions { display: flex; align-items: center; gap: 10px; flex-shrink: 0; }

  .toggle { position: relative; display: inline-block; width: 40px; height: 22px; }
  .toggle input { opacity: 0; width: 0; height: 0; }
  .slider {
    position: absolute; inset: 0;
    background: var(--surface2);
    border: 0.5px solid var(--border2);
    border-radius: 22px;
    cursor: pointer;
    transition: background 0.2s;
  }
  .slider::before {
    content: '';
    position: absolute;
    width: 16px; height: 16px;
    left: 3px; top: 3px;
    background: var(--text2);
    border-radius: 50%;
    transition: transform 0.2s, background 0.2s;
  }
  input:checked + .slider { background: rgba(62,207,142,0.2); border-color: var(--green); }
  input:checked + .slider::before { transform: translateX(18px); background: var(--green); }

  .del-btn {
    background: none;
    border: 0.5px solid var(--border2);
    border-radius: 8px;
    color: var(--text2);
    cursor: pointer;
    width: 32px; height: 32px;
    display: flex; align-items: center; justify-content: center;
    font-size: 15px;
    transition: color 0.2s, border-color 0.2s, background 0.2s;
  }
  .del-btn:hover { color: var(--red); border-color: var(--red); background: rgba(248,113,113,0.08); }

  .empty {
    text-align: center;
    padding: 2rem 1rem;
    color: var(--text2);
    font-size: 0.9rem;
  }
  .empty .e-icon { font-size: 2rem; display: block; margin-bottom: 8px; opacity: 0.5; }

  .toast {
    position: fixed;
    bottom: 1.5rem;
    left: 50%;
    transform: translateX(-50%) translateY(80px);
    background: var(--surface);
    border: 0.5px solid var(--border2);
    border-radius: 10px;
    padding: 10px 20px;
    font-size: 0.88rem;
    color: var(--green);
    transition: transform 0.3s ease;
    white-space: nowrap;
    z-index: 999;
  }
  .toast.show { transform: translateX(-50%) translateY(0); }

  @media (max-width: 480px) {
    .row { grid-template-columns: 1fr; }
  }
</style>
</head>
<body>

<div class="container">
  <header>
    <div class="icon">🔔</div>
    <h1>منبه متكرر</h1>
    <p>اضبط تنبيهات دورية شهرية تلقائياً</p>
  </header>

  <div class="card">
    <p class="card-title">إضافة منبه جديد</p>
    <div class="row">
      <div class="col">
        <p class="field-label">اسم المنبه</p>
        <input type="text" id="alarm-name" placeholder="مثلاً: اجتماع شهري">
      </div>
      <div class="col">
        <p class="field-label">الوقت</p>
        <input type="time" id="alarm-time" value="09:00">
      </div>
    </div>
    <div class="row">
      <div class="col">
        <p class="field-label">نوع التكرار</p>
        <select id="repeat-type" onchange="updateOptions()">
          <option value="first_weekday">أول يوم من الأسبوع كل شهر</option>
          <option value="last_weekday">آخر يوم من الأسبوع كل شهر</option>
          <option value="nth_weekday">اليوم رقم X من الأسبوع كل شهر</option>
          <option value="day_of_month">يوم محدد من كل شهر</option>
        </select>
      </div>
      <div class="col">
        <p class="field-label" id="extra-label">اليوم</p>
        <select id="extra-option"></select>
      </div>
    </div>
    <button class="add-btn" onclick="addAlarm()">+ إضافة المنبه</button>
  </div>

  <div class="card">
    <p class="card-title">المنبهات المحفوظة</p>
    <div class="alarms-list" id="alarms-list"></div>
  </div>
</div>

<div class="toast" id="toast"></div>

<script>
const DAYS_AR = ['الأحد','الاثنين','الثلاثاء','الأربعاء','الخميس','الجمعة','السبت'];
const ORDINALS = ['الأول','الثاني','الثالث','الرابع','الخامس'];

let alarms = JSON.parse(localStorage.getItem('recurring_alarms_v2') || '[]');

function save() {
  localStorage.setItem('recurring_alarms_v2', JSON.stringify(alarms));
}

function updateOptions() {
  const type = document.getElementById('repeat-type').value;
  const label = document.getElementById('extra-label');
  const sel = document.getElementById('extra-option');
  sel.innerHTML = '';
  if (type === 'day_of_month') {
    label.textContent = 'اليوم من الشهر';
    for (let i=1;i<=28;i++) { const o=document.createElement('option'); o.value=i; o.textContent=i; sel.appendChild(o); }
  } else if (type === 'nth_weekday') {
    label.textContent = 'أي أسبوع × أي يوم';
    for (let w=0;w<5;w++) for(let d=0;d<7;d++) {
      const o=document.createElement('option'); o.value=`${w}_${d}`; o.textContent=`${ORDINALS[w]} ${DAYS_AR[d]}`; sel.appendChild(o);
    }
  } else {
    label.textContent = 'اليوم';
    DAYS_AR.forEach((d,i)=>{ const o=document.createElement('option'); o.value=i; o.textContent=d; sel.appendChild(o); });
    if (type === 'first_weekday' || type === 'last_weekday') sel.value = '6';
  }
}

function getNextDate(alarm) {
  const now = new Date();
  const [h,m] = alarm.time.split(':').map(Number);
  function findInMonth(year, month) {
    if (alarm.type === 'day_of_month') {
      return new Date(year, month, parseInt(alarm.extra), h, m);
    } else if (alarm.type === 'first_weekday') {
      const day = parseInt(alarm.extra);
      let dt = new Date(year, month, 1);
      while (dt.getDay() !== day) dt.setDate(dt.getDate()+1);
      dt.setHours(h,m,0,0); return dt;
    } else if (alarm.type === 'last_weekday') {
      const day = parseInt(alarm.extra);
      let dt = new Date(year, month+1, 0);
      while (dt.getDay() !== day) dt.setDate(dt.getDate()-1);
      dt.setHours(h,m,0,0); return dt;
    } else if (alarm.type === 'nth_weekday') {
      const [w,day] = alarm.extra.split('_').map(Number);
      let dt = new Date(year, month, 1); let count = -1;
      while (dt.getMonth() === month) {
        if (dt.getDay() === day) { count++; if (count === w) { dt.setHours(h,m,0,0); return dt; } }
        dt.setDate(dt.getDate()+1);
      }
      return null;
    }
  }
  for (let i=0;i<13;i++) {
    const c = findInMonth(now.getFullYear(), now.getMonth()+i);
    if (c && c > now) return c;
  }
  return null;
}

function describeAlarm(alarm) {
  const day = DAYS_AR[parseInt(alarm.extra)];
  if (alarm.type === 'first_weekday') return `أول ${day} من كل شهر — ${alarm.time}`;
  if (alarm.type === 'last_weekday') return `آخر ${day} من كل شهر — ${alarm.time}`;
  if (alarm.type === 'day_of_month') return `يوم ${alarm.extra} من كل شهر — ${alarm.time}`;
  if (alarm.type === 'nth_weekday') {
    const [w,d] = alarm.extra.split('_').map(Number);
    return `${ORDINALS[w]} ${DAYS_AR[d]} من كل شهر — ${alarm.time}`;
  }
  return '';
}

function formatDate(dt) {
  if (!dt) return 'لا يوجد موعد قادم';
  return dt.toLocaleDateString('ar-EG',{weekday:'long',year:'numeric',month:'long',day:'numeric'}) + ' ' + dt.toLocaleTimeString('ar-EG',{hour:'2-digit',minute:'2-digit'});
}

function render() {
  const list = document.getElementById('alarms-list');
  if (!alarms.length) {
    list.innerHTML = '<div class="empty"><span class="e-icon">🔕</span>لا توجد منبهات بعد</div>';
    return;
  }
  list.innerHTML = alarms.map((a,i) => {
    const next = getNextDate(a);
    return `<div class="alarm-item">
      <div class="alarm-info">
        <div class="alarm-name">${a.name}</div>
        <div class="alarm-desc">${describeAlarm(a)}</div>
        ${a.enabled && next ? `<div class="alarm-next">⏰ التالي: ${formatDate(next)}</div>` : ''}
      </div>
      <div class="alarm-actions">
        <label class="toggle" title="${a.enabled?'إيقاف':'تشغيل'}">
          <input type="checkbox" ${a.enabled?'checked':''} onchange="toggleAlarm(${i})">
          <span class="slider"></span>
        </label>
        <button class="del-btn" onclick="deleteAlarm(${i})" title="حذف">🗑</button>
      </div>
    </div>`;
  }).join('');
}

function showToast(msg) {
  const t = document.getElementById('toast');
  t.textContent = msg;
  t.classList.add('show');
  setTimeout(()=>t.classList.remove('show'), 3000);
}

function addAlarm() {
  const name = document.getElementById('alarm-name').value.trim() || 'منبه جديد';
  const time = document.getElementById('alarm-time').value;
  const type = document.getElementById('repeat-type').value;
  const extra = document.getElementById('extra-option').value;
  alarms.push({ name, time, type, extra, enabled: true });
  save(); render();
  document.getElementById('alarm-name').value = '';
  showToast(`✅ تم إضافة "${name}"`);
}

function deleteAlarm(i) {
  alarms.splice(i,1); save(); render();
}

function toggleAlarm(i) {
  alarms[i].enabled = !alarms[i].enabled; save(); render();
}

function checkAlarms() {
  if (!('Notification' in window)) return;
  const now = new Date();
  alarms.filter(a=>a.enabled).forEach(a=>{
    const next = getNextDate(a);
    if (!next) return;
    const diff = next - now;
    if (diff > 0 && diff < 60000) {
      setTimeout(()=>{
        if (Notification.permission === 'granted') {
          new Notification(`🔔 ${a.name}`, { body: describeAlarm(a) });
        }
      }, diff);
    }
  });
}

function requestNotifPermission() {
  if ('Notification' in window && Notification.permission === 'default') {
    Notification.requestPermission();
  }
}

updateOptions();
render();
requestNotifPermission();
setInterval(checkAlarms, 30000);
checkAlarms();
</script>
</body>
</html>
