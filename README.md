
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="theme-color" content="#172c50">
<title>IHJEZ DZ | احجز وما تنساش</title>

<style>
*{box-sizing:border-box}

:root{
  --primary:#244d7e;
  --secondary:#4386cf;
  --light:#edf4ff;
  --message:#dceaff;
  --text:#172c50;
}

body{
  margin:0;
  font-family:Arial,sans-serif;
  background:#f3f6fc;
  color:var(--text);
  transition:background .3s;
}

header{
  background:linear-gradient(135deg,#172c50,#315b91);
  color:white;
  padding:27px 18px 32px;
  text-align:center;
  border-radius:0 0 28px 28px;
  transition:background .3s;
}

.logo{
  font-size:36px;
  font-weight:900;
  letter-spacing:2px;
}

header p{margin:8px 0 0;color:#e2ebf8}

.lang{
  position:absolute;
  top:14px;
  left:14px;
  border:1px solid #ffffff70;
  background:#ffffff18;
  color:white;
  padding:8px 12px;
  border-radius:20px;
}

main{
  width:min(92%,520px);
  margin:22px auto;
}

.card{
  background:white;
  padding:22px;
  border-radius:20px;
  box-shadow:0 7px 25px #172c5010;
  margin-bottom:18px;
}

h2{font-size:21px;margin:0 0 18px}

label{
  display:block;
  font-weight:bold;
  margin:15px 0 7px;
}

input,select{
  width:100%;
  padding:13px;
  border:1px solid #dce3ef;
  border-radius:11px;
  font-size:15px;
  background:#fbfcff;
  color:#172c50;
  outline:none;
}

input:focus,select:focus{border-color:var(--secondary)}

.gender{
  display:flex;
  gap:10px;
}

.gender button{
  flex:1;
  padding:13px;
  border:1px solid #dce3ef;
  border-radius:11px;
  background:#f8faff;
  color:#172c50;
  font-size:15px;
  cursor:pointer;
}

.gender button.active{
  background:#dceaff;
  border:2px solid #4386cf;
  font-weight:bold;
}

.gender button.active.female{
  background:#ffe0ed;
  border-color:#df78a5;
  color:#a33d70;
}

.main-btn{
  width:100%;
  border:0;
  border-radius:12px;
  background:var(--primary);
  color:white;
  padding:15px;
  font-size:16px;
  font-weight:bold;
  margin-top:22px;
  cursor:pointer;
}

.secondary{
  width:100%;
  border:1px solid var(--primary);
  background:white;
  color:var(--primary);
  padding:13px;
  border-radius:12px;
  font-size:15px;
  margin-top:10px;
  cursor:pointer;
}

.note{
  background:#eef4fc;
  border-radius:12px;
  padding:13px;
  font-size:13px;
  line-height:1.7;
  color:#435b7b;
  margin-top:15px;
}

.hidden{display:none}

.info{
  background:#f7f9fd;
  border-radius:12px;
  padding:13px;
  margin:10px 0;
  line-height:2;
  overflow-wrap:anywhere;
}

.message{
  text-align:center;
  background:var(--message);
  color:var(--primary);
  border-radius:13px;
  padding:18px 13px;
  margin-top:15px;
  font-weight:bold;
  font-size:17px;
  line-height:1.7;
  transition:background .3s,color .3s;
}

footer{
  text-align:center;
  color:#8290a5;
  font-size:12px;
  padding:15px 10px 30px;
}
</style>
</head>

<body>

<header>
  <button class="lang" id="langBtn" onclick="toggleLanguage()">FR</button>
  <div class="logo">IHJEZ DZ</div>
  <p id="slogan">احجز وما تنساش!</p>
  <p id="subtitle">رفيقك اليومي للحجز الجامعي</p>
</header>

<main>

<section class="card" id="registerCard">

  <h2 id="formTitle">إنشاء حسابك</h2>

  <label id="nameLabel" for="studentName">الاسم الكامل</label>
  <input id="studentName" type="text" placeholder="اكتبي اسمك">

  <label id="wilayaLabel" for="wilaya">الولاية</label>
  <select id="wilaya">
    <option value="">اختاري ولايتك</option>
  </select>

  <label id="residenceLabel" for="residence">اسم الإقامة الجامعية</label>
  <input id="residence" type="text" placeholder="مثال: الإقامة الجامعية ...">

  <label id="genderLabel">الجنس</label>

  <div class="gender">
    <button type="button" id="maleBtn" onclick="chooseGender('male')">ذكر 💙</button>
    <button type="button" id="femaleBtn" onclick="chooseGender('female')">أنثى 💗</button>
  </div>

  <label id="timeLabel" for="reminderTime">وقت التذكير اليومي</label>
  <input id="reminderTime" type="time" value="18:00">

  <button class="main-btn" id="saveBtn" onclick="saveAccount()">
    إنشاء الحساب
  </button>

  <div class="note" id="privacyNote">
    هذه نسخة تجريبية. معلوماتك تُحفظ على هذا الهاتف فقط.
  </div>

</section>

<section class="card hidden" id="dashboard">

  <h2 id="welcomeTitle">مرحباً بك في IHJEZ DZ!</h2>

  <div class="info">
    <div><strong id="dashNameLabel">الاسم:</strong> <span id="dashName"></span></div>
    <div><strong id="dashWilayaLabel">الولاية:</strong> <span id="dashWilaya"></span></div>
    <div><strong id="dashResidenceLabel">الإقامة:</strong> <span id="dashResidence"></span></div>
    <div><strong id="dashTimeLabel">وقت التذكير:</strong> <span id="dashTime"></span></div>
  </div>

  <div class="message" id="dailyMessage">
    نهارك سعيد! لا تنسي الحجز اليوم 🌸
  </div>

  <button class="main-btn" id="notifyBtn" onclick="enableNotifications()">
    تفعيل إشعارات الهاتف
  </button>

  <button class="secondary" id="testBtn" onclick="testNotification()">
    رسالة جديدة 😂
  </button>

  <button class="secondary" id="editBtn" onclick="editAccount()">
    تعديل المعلومات
  </button>

</section>

</main>

<footer id="footerText">
  IHJEZ DZ © 2026 — احجز وما تنساش!
</footer>

<script>

// قائمة الولايات الجزائرية الـ58
const wilayas = [
"01 - أدرار","02 - الشلف","03 - الأغواط","04 - أم البواقي",
"05 - باتنة","06 - بجاية","07 - بسكرة","08 - بشار",
"09 - البليدة","10 - البويرة","11 - تمنراست","12 - تبسة",
"13 - تلمسان","14 - تيارت","15 - تيزي وزو","16 - الجزائر",
"17 - الجلفة","18 - جيجل","19 - سطيف","20 - سعيدة",
"21 - سكيكدة","22 - سيدي بلعباس","23 - عنابة","24 - قالمة",
"25 - قسنطينة","26 - المدية","27 - مستغانم","28 - المسيلة",
"29 - معسكر","30 - ورقلة","31 - وهران","32 - البيض",
"33 - إليزي","34 - برج بوعريريج","35 - بومرداس","36 - الطارف",
"37 - تندوف","38 - تيسمسيلت","39 - الوادي","40 - خنشلة",
"41 - سوق أهراس","42 - تيبازة","43 - ميلة","44 - عين الدفلى",
"45 - النعامة","46 - عين تموشنت","47 - غرداية","48 - غليزان",
"49 - تيميمون","50 - برج باجي مختار","51 - أولاد جلال",
"52 - بني عباس","53 - عين صالح","54 - عين قزام",
"55 - تقرت","56 - جانت","57 - المغير","58 - المنيعة"
];

const wilayaSelect = document.getElementById("wilaya");

wilayas.forEach(name=>{
  const option = document.createElement("option");
  option.value = name;
  option.textContent = name;
  wilayaSelect.appendChild(option);
});

// الرسائل الخاصة بالأولاد
const boyMessages = [
  "مزلت تحبها؟ كول لوبيا ضك تنساها 😂",
  "نتاجك بولادهم ونتا مزالك دير فلاشان فريسطو 🤣",
  "راك درت فورما شابة من الطون والروز كمل فيها 💪",
  "شحال راك شباب ليوم 😎"
];

// الرسائل الخاصة بالبنات
const girlMessages = [
  "لي ڨدك تزوجوا ونتي مزلتي ديري فلاشان علاجال لعدس 😂",
  "راهو يخون فيك ضك 🤣",
  "نسيتيه وتخطيتيه؟ أني جيت نفكرك فيه 😂",
  "شحال راكي شابة ليوم 🌸",
  "عينيك شابين عينيك 🥹"
];

let selectedGender = "";
let currentLanguage = "ar";
let lastMessageIndex = -1;
let reminderInterval = null;

// اختيار الجنس وتغيير الألوان
function chooseGender(gender){

  selectedGender = gender;

  document.getElementById("maleBtn").classList.toggle(
    "active",gender==="male"
  );

  document.getElementById("femaleBtn").classList.toggle(
    "active",gender==="female"
  );

  document.getElementById("femaleBtn").classList.toggle(
    "female",gender==="female"
  );

  applyTheme(gender);
}

// تغيير ألوان الموقع
function applyTheme(gender){

  const root = document.documentElement;

  if(gender==="female"){
    root.style.setProperty("--primary","#c34f83");
    root.style.setProperty("--secondary","#df78a5");
    root.style.setProperty("--light","#fff0f6");
    root.style.setProperty("--message","#ffe0ed");

    document.body.style.background="#fff0f6";

    document.querySelector("header").style.background=
      "linear-gradient(135deg,#a83e70,#e88ab2)";

  }else{
    root.style.setProperty("--primary","#244d7e");
    root.style.setProperty("--secondary","#4386cf");
    root.style.setProperty("--light","#edf4ff");
    root.style.setProperty("--message","#dceaff");

    document.body.style.background="#edf4ff";

    document.querySelector("header").style.background=
      "linear-gradient(135deg,#123765,#4386cf)";
  }

  document.querySelectorAll(".main-btn").forEach(btn=>{
    btn.style.background="var(--primary)";
  });
}

// اختيار رسالة عشوائية دون تكرار الرسالة السابقة مباشرة
function changeMessage(gender){

  const messages = gender==="female" ? girlMessages : boyMessages;

  let randomIndex;

  do{
    randomIndex=Math.floor(Math.random()*messages.length);
  }while(messages.length>1 && randomIndex===lastMessageIndex);

  lastMessageIndex=randomIndex;

  const message=messages[randomIndex];

  document.getElementById("dailyMessage").textContent=message;

  return message;
}

// إنشاء الحساب
function saveAccount(){

  const name=document.getElementById("studentName").value.trim();
  const wilaya=document.getElementById("wilaya").value;
  const residence=document.getElementById("residence").value.trim();
  const time=document.getElementById("reminderTime").value;

  if(!name || !wilaya || !residence || !selectedGender || !time){
    alert(currentLanguage==="ar"
      ? "من فضلك عمّري جميع المعلومات واختاري الجنس."
      : "Veuillez remplir toutes les informations et choisir le genre.");
    return;
  }

  const user={
    name,
    wilaya,
    residence,
    time,
    gender:selectedGender
  };

  localStorage.setItem("ihjezUser",JSON.stringify(user));

  showDashboard(user);
}

// عرض لوحة التحكم
function showDashboard(user){

  document.getElementById("registerCard").classList.add("hidden");
  document.getElementById("dashboard").classList.remove("hidden");

  document.getElementById("dashName").textContent=user.name;
  document.getElementById("dashWilaya").textContent=user.wilaya;
  document.getElementById("dashResidence").textContent=user.residence;
  document.getElementById("dashTime").textContent=user.time;

  applyTheme(user.gender);

  changeMessage(user.gender);

  startReminder();
}

// تعديل المعلومات
function editAccount(){

  const user=JSON.parse(localStorage.getItem("ihjezUser"));

  if(!user)return;

  document.getElementById("studentName").value=user.name;
  document.getElementById("wilaya").value=user.wilaya;
  document.getElementById("residence").value=user.residence;
  document.getElementById("reminderTime").value=user.time;

  selectedGender=user.gender;

  chooseGender(user.gender);

  document.getElementById("dashboard").classList.add("hidden");
  document.getElementById("registerCard").classList.remove("hidden");
}

// تفعيل الإشعارات
async function enableNotifications(){

  if(!("Notification" in window)){
    alert("المتصفح لا يدعم الإشعارات.");
    return;
  }

  const permission=await Notification.requestPermission();

  if(permission==="granted"){
    alert(currentLanguage==="ar"
      ? "تم السماح بالإشعارات!"
      : "Les notifications sont autorisées !");

    testNotification();
  }else{
    alert(currentLanguage==="ar"
      ? "لم يتم السماح بالإشعارات."
      : "Les notifications n'ont pas été autorisées.");
  }
}

// إرسال إشعار برسالة عشوائية
function testNotification(){

  if(!("Notification" in window) || Notification.permission!=="granted"){
    alert(currentLanguage==="ar"
      ? "فعّلي الإشعارات أولاً."
      : "Veuillez d'abord activer les notifications.");
    return;
  }

  const user=JSON.parse(localStorage.getItem("ihjezUser"));

  if(!user)return;

  const message=changeMessage(user.gender);

  new Notification("IHJEZ DZ",{
    body:message
  });
}

// التذكير اليومي
function startReminder(){

  if(reminderInterval!==null){
    clearInterval(reminderInterval);
  }

  checkReminder();

  reminderInterval=setInterval(checkReminder,30000);
}

function checkReminder(){

  const user=JSON.parse(localStorage.getItem("ihjezUser"));

  if(!user || !("Notification" in window))return;

  if(Notification.permission!=="granted")return;

  const now=new Date();

  const currentTime=
    String(now.getHours()).padStart(2,"0")+":"+
    String(now.getMinutes()).padStart(2,"0");

  const today=
    now.getFullYear()+"-"+
    String(now.getMonth()+1).padStart(2,"0")+"-"+
    String(now.getDate()).padStart(2,"0");

  const alreadySent=localStorage.getItem("ihjezReminderDate");

  if(currentTime===user.time && alreadySent!==today){

    const message=changeMessage(user.gender);

    new Notification("IHJEZ DZ",{
      body:message
    });

    localStorage.setItem("ihjezReminderDate",today);
  }
}

// تغيير اللغة
function toggleLanguage(){

  currentLanguage=currentLanguage==="ar" ? "fr" : "ar";

  const ar=currentLanguage==="ar";

  document.documentElement.lang=currentLanguage;
  document.documentElement.dir=ar?"rtl":"ltr";

  const translations={

    slogan:["احجز وما تنساش!","Réserve, n'oublie pas !"],
    subtitle:["رفيقك اليومي للحجز الجامعي","Ton compagnon quotidien pour la réservation universitaire"],
    formTitle:["إنشاء حسابك","Créer votre compte"],
    nameLabel:["الاسم الكامل","Nom complet"],
    wilayaLabel:["الولاية","Wilaya"],
    residenceLabel:["اسم الإقامة الجامعية","Nom de la résidence universitaire"],
    genderLabel:["الجنس","Genre"],
    timeLabel:["وقت التذكير اليومي","Heure du rappel quotidien"],
    saveBtn:["إنشاء الحساب","Créer le compte"],
    welcomeTitle:["مرحباً بك في IHJEZ DZ!","Bienvenue sur IHJEZ DZ !"],
    dashNameLabel:["الاسم:","Nom :"],
    dashWilayaLabel:["الولاية:","Wilaya :"],
    dashResidenceLabel:["الإقامة:","Résidence :"],
    dashTimeLabel:["وقت التذكير:","Heure du rappel :"],
    notifyBtn:["تفعيل إشعارات الهاتف","Activer les notifications"],
    testBtn:["رسالة جديدة 😂","Nouveau message 😂"],
    editBtn:["تعديل المعلومات","Modifier les informations"],
    footerText:["IHJEZ DZ © 2026 — احجز وما تنساش!","IHJEZ DZ © 2026 — Réserve, n'oublie pas !"]
  };

  for(const id in translations){
    document.getElementById(id).textContent=translations[id][ar?0:1];
  }

  document.getElementById("langBtn").textContent=ar?"FR":"عربي";

  document.getElementById("maleBtn").textContent=ar?"ذكر 💙":"Homme 💙";
  document.getElementById("femaleBtn").textContent=ar?"أنثى 💗":"Femme 💗";

  document.getElementById("studentName").placeholder=
    ar?"اكتبي اسمك":"Entrez votre nom";

  document.getElementById("residence").placeholder=
    ar?"مثال: الإقامة الجامعية ...":"Ex. : Résidence universitaire ...";

  document.getElementById("privacyNote").textContent=ar
    ?"هذه نسخة تجريبية. معلوماتك تُحفظ على هذا الهاتف فقط."
    :"Version de démonstration. Vos informations sont enregistrées uniquement sur ce téléphone.";

  document.getElementById("dailyMessage").textContent=
    ar?"أهلاً بك في IHJEZ DZ 🌸":"Bienvenue sur IHJEZ DZ 🌸";
}

// استرجاع الحساب المحفوظ
const savedUser=localStorage.getItem("ihjezUser");

if(savedUser){

  const user=JSON.parse(savedUser);

  selectedGender=user.gender;

  showDashboard(user);
}

</script>
</body>
</html>
