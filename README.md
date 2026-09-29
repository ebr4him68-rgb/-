
خرید و فروش ارز 

<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>کیف پول من</title>

<style>
*{
  box-sizing:border-box;
  margin:0;
  padding:0;
  font-family:Tahoma,Arial,sans-serif;
}

body{
  background:#ffd92f;
  min-height:100vh;
  color:#222;
}

.app{
  max-width:500px;
  margin:auto;
  min-height:100vh;
  background:#fff8c9;
  position:relative;
  padding-bottom:85px;
}

/* ورود */
.login{
  min-height:100vh;
  display:flex;
  justify-content:center;
  align-items:center;
  padding:25px;
}

.login-box{
  width:100%;
  background:white;
  border-radius:25px;
  padding:30px 22px;
  box-shadow:0 10px 35px rgba(0,0,0,.15);
  text-align:center;
}

.logo{
  width:75px;
  height:75px;
  background:#ffd000;
  border-radius:50%;
  display:flex;
  align-items:center;
  justify-content:center;
  margin:0 auto 20px;
  font-size:35px;
}

h1{
  margin-bottom:12px;
}

.subtitle{
  color:#777;
  font-size:14px;
  margin-bottom:25px;
}

input{
  width:100%;
  border:2px solid #eee;
  border-radius:14px;
  padding:15px;
  font-size:16px;
  outline:none;
  margin-bottom:12px;
  text-align:center;
}

input:focus{
  border-color:#f2c400;
}

button{
  border:0;
  cursor:pointer;
}

.main-btn{
  width:100%;
  padding:15px;
  border-radius:14px;
  background:#f4c400;
  color:#222;
  font-size:16px;
  font-weight:bold;
}

.main-btn:hover{
  background:#e5b700;
}

.error{
  color:#d00;
  font-size:13px;
  margin:10px 0;
}

/* هدر */
.header{
  padding:20px;
  display:flex;
  justify-content:space-between;
  align-items:center;
}

.header-title{
  font-size:20px;
  font-weight:bold;
}

.logout{
  background:#fff;
  padding:8px 12px;
  border-radius:10px;
}

/* موجودی */
.balance{
  margin:10px 20px;
  padding:25px;
  border-radius:22px;
  background:#ffd000;
  box-shadow:0 7px 20px rgba(0,0,0,.1);
}

.balance small{
  display:block;
  margin-bottom:10px;
}

.balance strong{
  font-size:30px;
}

/* کارت ها */
.cards{
  padding:15px 20px;
}

.card{
  background:white;
  border-radius:18px;
  padding:20px;
  margin-bottom:12px;
  box-shadow:0 5px 15px rgba(0,0,0,.07);
}

.card-title{
  font-weight:bold;
  margin-bottom:8px;
}

.card-text{
  color:#777;
  font-size:13px;
}

/* نوار پایین */
.bottom-nav{
  position:fixed;
  bottom:0;
  left:50%;
  transform:translateX(-50%);
  width:min(500px,100%);
  background:#fff;
  border-top:1px solid #eee;
  display:flex;
  justify-content:space-around;
  padding:10px 4px;
  z-index:10;
  box-shadow:0 -5px 20px rgba(0,0,0,.08);
}

.nav-item{
  flex:1;
  text-align:center;
  padding:8px 2px;
  border-radius:12px;
  color:#777;
  font-size:11px;
}

.nav-item span{
  display:block;
  font-size:22px;
  margin-bottom:4px;
}

.nav-item.active{
  background:#fff2a8;
  color:#222;
  font-weight:bold;
}

/* صفحات */
.page{
  display:none;
}

.page.active{
  display:block;
}

/* مدیریت */
.admin{
  padding:20px;
}

.admin-box{
  background:white;
  border-radius:18px;
  padding:20px;
  margin-bottom:15px;
}

.user{
  border-bottom:1px solid #eee;
  padding:14px 0;
}

.user:last-child{
  border-bottom:0;
}

.phone{
  font-weight:bold;
}

.status{
  font-size:12px;
  color:green;
  margin-top:5px;
}
</style>
</head>

<body>

<div class="app">

<!-- صفحه ورود -->
<section id="loginPage" class="login">

  <div class="login-box">

    <div class="logo">💰</div>

    <h1 id="loginTitle">ثبت‌نام</h1>

    <p class="subtitle">
      برای ثبت‌نام شماره تلفن خودتون رو وارد کنید
    </p>

    <div id="phoneStep">

      <input
        id="phone"
        type="tel"
        inputmode="tel"
        placeholder="شماره تلفن"
      >

      <button class="main-btn" onclick="sendCode()">
        دریافت کد
      </button>

      <div id="phoneError" class="error"></div>

    </div>

    <div id="codeStep" style="display:none">

      <p class="subtitle">
        کد تأیید برای شماره شما ارسال شد
      </p>

      <input
        id="otp"
        type="text"
        inputmode="numeric"
        maxlength="6"
        placeholder="کد تأیید"
      >

      <button class="main-btn" onclick="verifyCode()">
        تأیید و ورود
      </button>

      <div id="otpError" class="error"></div>

    </div>

  </div>

</section>


<!-- سایت -->
<section id="sitePage" style="display:none">

  <header class="header">
    <div class="header-title">کیف پول من</div>

    <button class="logout" onclick="logout()">
      خروج
    </button>
  </header>


  <!-- خانه -->
  <div id="home" class="page active">

    <div class="balance">

      <small>موجودی حساب</small>

      <strong>
        $0.00
      </strong>

    </div>

    <div class="cards">

      <div class="card">
        <div class="card-title">
          👋 خوش آمدید
        </div>

        <div class="card-text">
          از منوی پایین می‌توانید حساب خود را مدیریت کنید.
        </div>
      </div>

      <div class="card">
        <div class="card-title">
          🔐 حساب شما
        </div>

        <div class="card-text" id="userPhone">
          شماره تلفن:
        </div>
      </div>

    </div>

  </div>


  <!-- تبدیل -->
  <div id="convert" class="page">

    <div class="cards">

      <div class="card">

        <h2>🔄 تبدیل</h2>

        <br>

        <input
          type="number"
          placeholder="مقدار"
        >

        <button class="main-btn">
          تبدیل
        </button>

      </div>

    </div>

  </div>


  <!-- واریز -->
  <div id="deposit" class="page">

    <div class="cards">

      <div class="card">

        <h2>💳 واریز</h2>

        <br>

        <p class="card-text">
          در این بخش اطلاعات واریز نمایش داده می‌شود.
        </p>

        <br>

        <button class="main-btn">
          نمایش اطلاعات واریز
        </button>

      </div>

    </div>

  </div>


  <!-- برداشت -->
  <div id="withdraw" class="page">

    <div class="cards">

      <div class="card">

        <h2>💸 برداشت</h2>

        <br>

        <input
          type="number"
          placeholder="مبلغ برداشت"
        >

        <button class="main-btn">
          ثبت درخواست برداشت
        </button>

      </div>

    </div>

  </div>


  <!-- کیف پول -->
  <div id="wallet" class="page">

    <div class="cards">

      <div class="card">

        <h2>👛 کیف پول</h2>

        <br>

        <p class="card-text">
          اطلاعات کیف پول شما در این قسمت قرار می‌گیرد.
        </p>

      </div>

    </div>

  </div>


  <!-- مدیریت -->
  <div id="admin" class="page">

    <div class="admin">

      <div class="admin-box">

        <h2>⚙️ مدیریت</h2>

        <br>

        <p class="card-text">
          کاربران ثبت‌نام‌شده
        </p>

      </div>

      <div class="admin-box">

        <div id="usersList"></div>

      </div>

    </div>

  </div>


  <!-- نوار پایین -->
  <nav class="bottom-nav">

    <div class="nav-item active" onclick="showPage('home',this)">
      <span>🏠</span>
      خانه
    </div>

    <div class="nav-item" onclick="showPage('convert',this)">
      <span>🔄</span>
      تبدیل
    </div>

    <div class="nav-item" onclick="showPage('deposit',this)">
      <span>💳</span>
      واریز
    </div>

    <div class="nav-item" onclick="showPage('withdraw',this)">
      <span>💸</span>
      برداشت
    </div>

    <div class="nav-item" onclick="showPage('wallet',this)">
      <span>👛</span>
      کیف پول
    </div>

  </nav>

</section>

</div>


<script>

/* -------------------------
   اطلاعات تست
------------------------- */

let generatedCode = null;

let users =
  JSON.parse(localStorage.getItem("users") || "[]");


/* -------------------------
   ارسال کد
------------------------- */

function sendCode(){

  const phone =
    document.getElementById("phone").value.trim();

  const error =
    document.getElementById("phoneError");

  if(phone.length < 7){

    error.innerText =
      "لطفاً شماره تلفن معتبر وارد کنید.";

    return;
  }

  error.innerText = "";

  /*
    حالت آزمایشی:

    در نسخه واقعی این قسمت باید
    به API سرویس SMS متصل شود.
  */

  generatedCode =
    Math.floor(100000 + Math.random() * 900000)
    .toString();

  console.log("TEST OTP:", generatedCode);

  document.getElementById("phoneStep")
    .style.display = "none";

  document.getElementById("codeStep")
    .style.display = "block";

}


/* -------------------------
   تأیید کد
------------------------- */

function verifyCode(){

  const phone =
    document.getElementById("phone").value.trim();

  const otp =
    document.getElementById("otp").value.trim();

  const error =
    document.getElementById("otpError");

  if(otp !== generatedCode){

    error.innerText =
      "کد واردشده صحیح نیست.";

    return;
  }

  error.innerText = "";

  if(!users.includes(phone)){

    users.push(phone);

    localStorage.setItem(
      "users",
      JSON.stringify(users)
    );

  }

  localStorage.setItem(
    "loggedIn",
    phone
  );

  openSite(phone);

}


/* -------------------------
   ورود
------------------------- */

function openSite(phone){

  document.getElementById("loginPage")
    .style.display = "none";

  document.getElementById("sitePage")
    .style.display = "block";

  document.getElementById("userPhone")
    .innerText =
    "شماره تلفن: " + phone;

  loadUsers();

}


/* -------------------------
   منو
------------------------- */

function showPage(page, element){

  document.querySelectorAll(".page")
    .forEach(p =>
      p.classList.remove("active")
    );

  document.getElementById(page)
    .classList.add("active");

  document.querySelectorAll(".nav-item")
    .forEach(n =>
      n.classList.remove("active")
    );

  element.classList.add("active");

}


/* -------------------------
   خروج
------------------------- */

function logout(){

  localStorage.removeItem("loggedIn");

  location.reload();

}


/* -------------------------
   نمایش کاربران
------------------------- */

function loadUsers(){

  const list =
    document.getElementById("usersList");

  if(users.length === 0){

    list.innerHTML =
      "<p>هنوز کاربری ثبت‌نام نکرده است.</p>";

    return;
  }

  list.innerHTML = "";

  users.forEach((phone,index)=>{

    list.innerHTML += `
      <div class="user">
        <div class="phone">
          📱 ${phone}
        </div>

        <div class="status">
          کاربر ثبت‌نام‌شده
        </div>
      </div>
    `;

  });

}


/* -------------------------
   ورود خودکار
------------------------- */

const loggedIn =
  localStorage.getItem("loggedIn");

if(loggedIn){

  openSite(loggedIn);

}

</script>

</body>
</html>
```
