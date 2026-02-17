<!DOCTYPE html>
<html lang="fa">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>فروم Dragon RolePlay</title>

<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700&display=swap" rel="stylesheet">

<style>
body{
  margin:0;
  font-family:'Orbitron', sans-serif;
  background:linear-gradient(135deg,#0b1020,#111a35);
  color:#fff;
}

.navbar{
  position:fixed;
  top:0;
  width:100%;
  background:#000;
  display:flex;
  justify-content:center;
  gap:10px;
  padding:10px;
  z-index:1000;
}

.navbar a{
  text-decoration:none;
  color:#00f7ff;
  padding:6px 12px;
  border-radius:8px;
  font-size:14px;
  transition:.3s;
}

.navbar a:hover{
  background:#00f7ff;
  color:#000;
}

.section{
  display:none;
  max-width:1100px;
  margin:110px auto 40px;
  background:rgba(0,0,0,.65);
  border-radius:12px;
  padding:25px;
}

.section.active{ display:block; }

input,select{
  width:100%;
  padding:10px;
  margin:6px 0;
  border-radius:8px;
  border:none;
  font-family:'Orbitron';
}

button{
  padding:12px 25px;
  border:none;
  border-radius:10px;
  cursor:pointer;
  font-weight:bold;
}

.btn-send{ background:#00ffae; }
.btn-admin{ background:#1e90ff; }
.btn-ok{ background:#00ff00; }
.btn-no{ background:#ff004c; }

.cards{
  display:flex;
  flex-wrap:wrap;
  gap:15px;
}

.card{
  background:rgba(0,0,0,.7);
  border-radius:12px;
  padding:12px;
  width:250px;
  box-shadow:0 0 12px #00f7ff;
}

footer{
  text-align:center;
  color:#00f7ff;
  padding:20px;
}
</style>
</head>

<body>

<nav class="navbar">
  <a href="#" data-target="gov">فروم دولت</a>
  <a href="#" data-target="ghetto">فروم گتو</a>
  <a href="#" data-target="admin">پنل مدیریت</a>
</nav>

<section id="gov" class="section active">
  <h2>فروم دولت</h2>
  <input type="text" id="gov_accName" placeholder="نام اکانت">
  <input type="text" id="gov_accLevel" placeholder="لول">
  <input type="text" id="gov_accAge" placeholder="سن اکانت">
  <input type="text" id="gov_accOld" placeholder="اکانت سابقه">
  <input type="text" id="gov_factionHistory" placeholder="سابقه در فکشن‌های دولتی">
  <input type="file" id="gov_accImage">
  <input type="text" id="gov_wbook" placeholder="Wbook">
  <input type="text" id="gov_realName" placeholder="نام واقعی">
  <input type="text" id="gov_realAge" placeholder="سن واقعی">
  <input type="text" id="gov_rubikaID" placeholder="آیدی روبیکا">
  <input type="text" id="gov_playTime" placeholder="تایم پلی روزانه">
  <input type="text" id="gov_leadGoal" placeholder="هدف از لیدری">
  
  <!-- فکشن دولت -->
  <h3>انتخاب فکشن</h3>
  <select id="gov_factionSelect">
    <option value="Medic">Medic</option>
    <option value="News">News</option>
    <option value="Army">Army</option>
    <option value="FBI">FBI</option>
    <option value="LsPd">LsPd</option>
  </select>

<button class="btn-send" onclick="sendForum('gov')">ارسال فروم</button>
</section>


<h2>فروم گتو</h2>
<input type="text" id="ghetto_accName" placeholder="نام اکانت">
<input type="text" id="ghetto_accLevel" placeholder="لول">
<input type="text" id="ghetto_accAge" placeholder="سن اکانت">
<input type="text" id="ghetto_accOld" placeholder="اکانت سابقه">
<input type="text" id="ghetto_factionHistory" placeholder="سابقه در فکشن‌های گتو">
<input type="file" id="ghetto_accImage">
<input type="text" id="ghetto_wbook" placeholder="Wbook">
<input type="text" id="ghetto_realName" placeholder="نام واقعی">
<input type="text" id="ghetto_realAge" placeholder="سن واقعی">
<input type="text" id="ghetto_rubikaID" placeholder="آیدی روبیکا">
<input type="text" id="ghetto_playTime" placeholder="تایم پلی روزانه">
<input type="text" id="ghetto_leadGoal" placeholder="هدف از لیدری">

<!-- فکشن گتو -->
<h2>انتخاب فکشن گتو</h2>
<select id="ghetto_factionSelect">
  <option value="Vagos">Vagos</option>
  <option value="Ballas">Ballas</option>
  <option value="Rifa">Rifa</option>
  <option value="Aztecs">Aztecs</option>
  <option value="GroveStreet">Grove Street</option>
</select>

<button class="btn-send" onclick="sendForum('ghetto')">ارسال فروم</button>
</section>


<section id="admin" class="section">
<h2>پنل مدیریت</h2>

<input id="adminPass" type="password" placeholder="رمز مدیریت">
<button class="btn-admin" onclick="loginAdmin()">ورود</button>

<div id="adminBox" style="display:none">
<h3>فروم های ارسال شده</h3>
<div class="cards" id="adminList"></div>
</div>
</section>

<footer>Dragon RolePlay</footer>


<script>

const links=document.querySelectorAll('.navbar a');
const sections=document.querySelectorAll('.section');

links.forEach(l=>{
  l.onclick=e=>{
    e.preventDefault();
    sections.forEach(s=>s.classList.remove('active'));
    document.getElementById(l.dataset.target).classList.add('active');
  }
});

function sendForum(type){
  let d={};

  if(type==='gov'){
    d={
      acc:g_acc.value,
      age:g_age.value,
      act:g_act.value,
      hist:g_hist.value,
      warn:g_warn.value,
      reason:g_reason.value,
      goal:g_goal.value,
      faction:g_faction.value,
      type:'gov'
    };
  } else {
    d={
      acc:gh_acc.value,
      age:gh_age.value,
      act:gh_act.value,
      hist:gh_hist.value,
      warn:gh_warn.value,
      reason:gh_reason.value,
      goal:gh_goal.value,
      faction:gh_faction.value,
      type:'ghetto'
    };
  }

  if(!d.acc||!d.age||!d.act||!d.goal) return alert("همه فیلدها رو پر کن");

  let arr=JSON.parse(localStorage.getItem('pendingForums')||'[]');
  arr.push(d);
  localStorage.setItem('pendingForums',JSON.stringify(arr));

  alert("فروم با موفقیت ارسال شد و منتظر تایید مدیریت است");

  location.reload();
}

function loginAdmin(){
  if(adminPass.value!=="123321") return alert("رمز اشتباه");

  adminBox.style.display="block";
  loadAdmin();
}

function loadAdmin(){
  const data=JSON.parse(localStorage.getItem('pendingForums')||'[]');
  adminList.innerHTML='';

  data.forEach((d,i)=>{
    adminList.innerHTML+=`
      <div class="card">
        <b>اکانت:</b> ${d.acc}<br>
        <b>سن:</b> ${d.age}<br>
        <b>فعالیت:</b> ${d.act}<br>
        <b>سابقه:</b> ${d.hist}<br>
        <b>وارن:</b> ${d.warn}<br>
        <b>دلیل:</b> ${d.reason}<br>
        <b>هدف:</b> ${d.goal}<br>
        <b>فکشن:</b> ${d.faction}<br><br>

        <button class="btn-ok" onclick="accept(${i})">قبول</button>
        <button class="btn-no" onclick="reject(${i})">رد</button>
      </div>
    `;
  });
}

function accept(i){
  let arr=JSON.parse(localStorage.getItem('pendingForums'));
  arr.splice(i,1);
  localStorage.setItem('pendingForums',JSON.stringify(arr));
  loadAdmin();
}

function reject(i){
  let arr=JSON.parse(localStorage.getItem('pendingForums'));
  arr.splice(i,1);
  localStorage.setItem('pendingForums',JSON.stringify(arr));
  loadAdmin();
}

</script>

</body>
</html>
