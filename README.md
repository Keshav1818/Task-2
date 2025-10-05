<!doctype html>

<html lang="en">

<head>

<meta charset="utf-8" />

<meta name="viewport" content="width=device-width,initial-scale=1" />

<title>Registration Carousel(Rating)</title>

<style>

&nbsp; :root {

&nbsp;   --accent:#2b8cff;

&nbsp;   --accent-2:#0b6eff;

&nbsp;   --bg:#f6f8fb;

&nbsp;   --card:#ffffff;

&nbsp;   --muted:#6b7280;

&nbsp;   --danger:#ef4444;

&nbsp;   --success:#16a34a;

&nbsp;   font-family: "Segoe UI", Roboto, Helvetica, Arial, sans-serif;

&nbsp; }

&nbsp; \* { box-sizing:border-box; }



&nbsp; body {

&nbsp;   margin:0;

&nbsp;   background:var(--bg);

&nbsp;   color:#0f172a;

&nbsp;   min-height:100vh;

&nbsp;   display:flex;

&nbsp;   justify-content:center;

&nbsp;   padding:16px;

&nbsp; }



&nbsp; .container {

&nbsp;   width:100%;

&nbsp;   max-width:1100px;

&nbsp;   background:var(--card);

&nbsp;   border-radius:12px;

&nbsp;   box-shadow: 0 6px 24px rgba(0,0,0,0.08);

&nbsp;   overflow:hidden;

&nbsp;   display:flex;

&nbsp;   flex-direction:column;

&nbsp; }



&nbsp; .nav {

&nbsp;   display:flex;

&nbsp;   flex-wrap:wrap;

&nbsp;   gap:10px;

&nbsp;   padding:14px;

&nbsp;   background:linear-gradient(90deg,#e9f2ff,#f9fbff);

&nbsp;   align-items:center;

&nbsp; }

&nbsp; .tabs {

&nbsp;   display:flex;

&nbsp;   flex-wrap:wrap;

&nbsp;   gap:10px;

&nbsp; }

&nbsp; .tab {

&nbsp;   padding:8px 14px;

&nbsp;   border-radius:6px;

&nbsp;   border:1px solid transparent;

&nbsp;   cursor:pointer;

&nbsp;   font-weight:600;

&nbsp;   color:var(--accent-2);

&nbsp;   background:transparent;

&nbsp;   transition:0.25s;

&nbsp; }

&nbsp; .tab.active {

&nbsp;   background:var(--accent-2);

&nbsp;   color:white;

&nbsp;   box-shadow: 0 3px 10px rgba(43,140,255,0.2);

&nbsp; }



&nbsp; .content { padding:18px; }



&nbsp; form {

&nbsp;   display:grid;

&nbsp;   grid-template-columns:1fr 1fr;

&nbsp;   gap:14px;

&nbsp; }

&nbsp; form label {

&nbsp;   display:block;

&nbsp;   font-size:14px;

&nbsp;   margin-bottom:4px;

&nbsp;   color:var(--muted);

&nbsp; }

&nbsp; form input, form select {

&nbsp;   width:100%;

&nbsp;   padding:10px;

&nbsp;   border-radius:6px;

&nbsp;   border:1px solid #dcdfe4;

&nbsp;   font-size:14px;

&nbsp; }

&nbsp; .full { grid-column:1/-1; }

&nbsp; .form-actions { display:flex; flex-wrap:wrap; gap:10px; align-items:center; }

&nbsp; .btn-primary {

&nbsp;   background:var(--accent-2); color:#fff; border:none;

&nbsp;   padding:10px 16px; border-radius:6px; font-weight:600; cursor:pointer;

&nbsp; }

&nbsp; .btn-reset {

&nbsp;   background:#fff; border:1px solid #dcdfe4; padding:10px 16px;

&nbsp;   border-radius:6px; font-weight:600; cursor:pointer; color:var(--accent-2);

&nbsp; }

&nbsp; .error { font-size:13px; color:var(--danger); }

&nbsp; .success { font-size:13px; color:var(--success); }



&nbsp; .strength-bar {

&nbsp;   height:6px;

&nbsp;   border-radius:4px;

&nbsp;   background:#e5e7eb;

&nbsp;   margin-top:4px;

&nbsp;   overflow:hidden;

&nbsp; }

&nbsp; .strength-fill {

&nbsp;   height:100%;

&nbsp;   width:0%;

&nbsp;   transition:0.3s;

&nbsp; }

&nbsp; .weak { background:#ef4444; }

&nbsp; .medium { background:#facc15; }

&nbsp; .strong { background:#16a34a; }



&nbsp; .carousel-wrap { display:flex; flex-wrap:wrap; gap:16px; }

&nbsp; .carousel {

&nbsp;   flex:1 1 600px;

&nbsp;   position:relative;

&nbsp;   overflow:hidden;

&nbsp;   border-radius:10px;

&nbsp;   background:#f9fafb;

&nbsp; }

&nbsp; .slides { display:flex; transition:transform .5s ease; }

&nbsp; .slide { min-width:100%; padding:12px; display:flex; flex-direction:column; align-items:center; }

&nbsp; .slide img { width:100%; max-height:350px; object-fit:cover; border-radius:10px; }

&nbsp; .arrow {

&nbsp;   position:absolute; top:50%; transform:translateY(-50%);

&nbsp;   background:#fff; border:1px solid #ccc;

&nbsp;   width:38px; height:38px; border-radius:50%;

&nbsp;   display:flex; align-items:center; justify-content:center;

&nbsp;   cursor:pointer; font-size:18px;

&nbsp; }

&nbsp; .arrow.left { left:10px; }

&nbsp; .arrow.right { right:10px; }



&nbsp; .rating { margin-top:10px; display:flex; gap:6px; }

&nbsp; .star { cursor:pointer; font-size:28px; color:#cbd5e1; }

&nbsp; .star.on { color:#ffb020; }



&nbsp; @media (max-width:768px) {

&nbsp;   form { grid-template-columns:1fr; }

&nbsp;   .carousel-wrap { flex-direction:column; }

&nbsp;   .slide img { max-height:240px; }

&nbsp; }

&nbsp; @media (max-width:480px) {

&nbsp;   body { padding:8px; }

&nbsp;   .nav { flex-direction:column; align-items:flex-start; }

&nbsp;   .star { font-size:24px; }

&nbsp; }

</style>

</head>

<body>

&nbsp; <div class="container">

&nbsp;   <div class="nav">

&nbsp;     <strong style="flex:1;color:var(--accent-2)">Cloud Computing Cell</strong>

&nbsp;     <div class="tabs">

&nbsp;       <button class="tab active" id="tab-form">Registration Form</button>

&nbsp;       <button class="tab" id="tab-carousel">Carousel</button>

&nbsp;     </div>

&nbsp;   </div>

&nbsp;   <div class="content">

&nbsp;     <section id="panel-form">

&nbsp;       <h2>Registration Form</h2>

&nbsp;       <form id="regForm">

&nbsp;         <div>

&nbsp;           <label>Name</label>

&nbsp;           <input id="name" type="text" required>

&nbsp;           <div id="err-name" class="error"></div>

&nbsp;         </div>

&nbsp;         <div>

&nbsp;           <label>Email</label>

&nbsp;           <input id="email" type="email" required placeholder="example@domain.com">

&nbsp;           <div id="err-email" class="error"></div>

&nbsp;         </div>

&nbsp;         <div>

&nbsp;           <label>Contact Number</label>

&nbsp;           <input id="contact" type="text" required>

&nbsp;           <div id="err-contact" class="error"></div>

&nbsp;         </div>

&nbsp;         <div>

&nbsp;           <label>Gender</label>

&nbsp;           <select id="gender" required>

&nbsp;             <option value="">Select</option>

&nbsp;             <option>Male</option>

&nbsp;             <option>Female</option>

&nbsp;           </select>

&nbsp;           <div id="err-gender" class="error"></div>

&nbsp;         </div>

&nbsp;         <div>

&nbsp;           <label>Password</label>

&nbsp;           <input id="password" type="password" required>

&nbsp;           <div class="strength-bar"><div id="strengthFill" class="strength-fill"></div></div>

&nbsp;           <div id="err-password" class="error"></div>

&nbsp;         </div>

&nbsp;         <div>

&nbsp;           <label>Confirm Password</label>

&nbsp;           <input id="confirmPwd" type="password" required>

&nbsp;           <div id="err-confirmPwd" class="error"></div>

&nbsp;         </div>

&nbsp;         <div class="full form-actions">

&nbsp;           <button type="submit" class="btn-primary">Register</button>

&nbsp;           <button type="button" id="resetBtn" class="btn-reset">Reset</button>

&nbsp;           <div id="formMsg"></div>

&nbsp;         </div>

&nbsp;       </form>

&nbsp;     </section>



&nbsp;     <section id="panel-carousel" style="display:none">

&nbsp;       <h2>Image Carousel + Rating</h2>

&nbsp;       <div class="carousel-wrap">

&nbsp;         <div class="carousel">

&nbsp;           <div class="slides" id="slides">

&nbsp;             <div class="slide"><img src="https://picsum.photos/id/1015/800/400"><div class="rating" data-i="0"></div></div>

&nbsp;             <div class="slide"><img src="https://picsum.photos/id/1016/800/400"><div class="rating" data-i="1"></div></div>

&nbsp;             <div class="slide"><img src="https://picsum.photos/id/1018/800/400"><div class="rating" data-i="2"></div></div>

&nbsp;           </div>

&nbsp;           <div class="arrow left" id="prev">\&#9664;</div>

&nbsp;           <div class="arrow right" id="next">\&#9654;</div>

&nbsp;         </div>

&nbsp;       </div>

&nbsp;     </section>

&nbsp;   </div>

&nbsp; </div>



<script>

const tabForm=document.getElementById("tab-form");

const tabCar=document.getElementById("tab-carousel");

const panelForm=document.getElementById("panel-form");

const panelCar=document.getElementById("panel-carousel");

tabForm.onclick=()=>{tabForm.classList.add("active");tabCar.classList.remove("active");panelForm.style.display="block";panelCar.style.display="none";};

tabCar.onclick=()=>{tabCar.classList.add("active");tabForm.classList.remove("active");panelCar.style.display="block";panelForm.style.display="none";};



const pwdInput = document.getElementById("password");

const strengthFill = document.getElementById("strengthFill");

pwdInput.oninput = () => {

&nbsp; const val = pwdInput.value;

&nbsp; let score = 0;

&nbsp; if(val.length >= 6) score++;

&nbsp; if(/\[A-Z]/.test(val)) score++;

&nbsp; if(/\[a-z]/.test(val)) score++;

&nbsp; if(/\\d/.test(val)) score++;

&nbsp; if(/\[!@#$%^\&\*]/.test(val)) score++;



&nbsp; if(score <= 2) { strengthFill.style.width="33%"; strengthFill.className="strength-fill weak"; }

&nbsp; else if(score <=4) { strengthFill.style.width="66%"; strengthFill.className="strength-fill medium"; }

&nbsp; else { strengthFill.style.width="100%"; strengthFill.className="strength-fill strong"; }

};



document.getElementById("regForm").onsubmit = function(e) {

&nbsp; e.preventDefault();

&nbsp; let ok = true;



&nbsp; function setErr(id, msg) {

&nbsp;   document.getElementById("err-" + id).textContent = msg;

&nbsp;   if (msg) ok = false;

&nbsp; }



&nbsp; const nameVal = document.getElementById("name").value.trim();

&nbsp; const emailVal = document.getElementById("email").value.trim();

&nbsp; const contactVal = document.getElementById("contact").value.trim();

&nbsp; const genderVal = document.getElementById("gender").value;

&nbsp; const pwdVal = document.getElementById("password").value;

&nbsp; const confirmVal = document.getElementById("confirmPwd").value;



&nbsp; setErr("name", /^\[A-Za-z ]+$/.test(nameVal) ? "" : "Invalid name");

&nbsp; 

&nbsp; setErr("email", /^\[^@]+@\[^@]+\\.(com|in)$/.test(emailVal) ? "" : "Email must end with .com or .in");

&nbsp; 

&nbsp; setErr("contact", /^\\d{10}$/.test(contactVal) ? "" : "Must be 10 digits");

&nbsp; setErr("gender", genderVal ? "" : "Select gender");



&nbsp; let strong = pwdVal.length >= 6 \&\&

&nbsp;              /\[A-Z]/.test(pwdVal) \&\&

&nbsp;              /\[a-z]/.test(pwdVal) \&\&

&nbsp;              /\\d/.test(pwdVal) \&\&

&nbsp;              /\[!@#$%^\&\*]/.test(pwdVal);

&nbsp; setErr("password", strong ? "" : "Weak password");

&nbsp; setErr("confirmPwd", confirmVal === pwdVal ? "" : "Passwords mismatch");



&nbsp; document.getElementById("formMsg").innerHTML = ok 

&nbsp;   ? "<span class='success'>Success!</span>" 

&nbsp;   : "<span class='error'>Fix errors</span>";

};



document.getElementById("resetBtn").onclick = () => {

&nbsp; document.getElementById("regForm").reset();

&nbsp; document.querySelectorAll(".error").forEach(e=>e.textContent="");

&nbsp; strengthFill.style.width="0%";

&nbsp; document.getElementById("formMsg").textContent="";

};



let idx=0;

const slides=document.getElementById("slides");

const total=slides.children.length;

function show(){slides.style.transform="translateX("+(-idx\*100)+"%)";}

document.getElementById("prev").onclick=()=>{idx=(idx-1+total)%total;show();}

document.getElementById("next").onclick=()=>{idx=(idx+1)%total;show();}



const ratings=\[0,0,0];

document.querySelectorAll(".rating").forEach((wrap,i)=>{

&nbsp;for(let s=1;s<=5;s++){

&nbsp; let star=document.createElement("span");

&nbsp; star.className="star";

&nbsp; star.innerHTML="★";

&nbsp; star.onclick=()=>{ratings\[i]=(ratings\[i]===s?0:s);render();}

&nbsp; star.onmouseenter=()=>{setStars(wrap,s);}

&nbsp; star.onmouseleave=()=>{setStars(wrap,ratings\[i]);}

&nbsp; wrap.appendChild(star);

&nbsp;}

&nbsp;setStars(wrap,0);

});

function setStars(wrap,val){\[...wrap.children].forEach((st,i)=>{st.classList.toggle("on",i<val);});}

function render(){document.querySelectorAll(".rating").forEach((wrap,i)=>setStars(wrap,ratings\[i]));}

</script>

</body>

</html>



#   T a s k - 2  
 