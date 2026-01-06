---
layout: post
title: About
permalink: /about/
comments: true
---

<div id="dashboard">
  <span id="timer">Session: 0s</span> |
  <span id="views">Hover: 0</span> |
</div>

<button onclick="toggleTheme()">🌗</button>
<button onclick="highlightRandom()">🎯</button>

<div class="creative-grid">
  <div class="confetti">🎉</div>
  <div class="year">2026</div>
  <div class="confetti">🎉</div>
  <div class="plane">✈️</div>
</div>

## As a conversation Starter
- What I do for a living?
- Where I was born?
- What religion I am?

Here are the places I have lived.

<comment>Flags are made using Wikipedia images</comment>

<input id="searchBox" placeholder="Search places...">
<button onclick="sortAZ()">A–Z</button>
<button onclick="sortZA()">Z–A</button>
<button onclick="randomFact()">Fun Fact 🎲</button>

<p id="counter"></p>
<p id="factBox"></p>

<style>
#dashboard{position:sticky;top:0;background:#222;color:#fff;padding:6px;z-index:10}
body.dark{background:#111;color:#eee}
.creative-grid{display:grid;grid-template-columns:1fr auto 1fr;justify-items:center;margin:30px 0}
.year{font-size:3rem}
.plane{grid-column:1/span 3;animation:fly 6s linear infinite}
@keyframes fly{from{transform:translateX(-120%)}to{transform:translateX(120%)}}

.grid-container{display:grid;grid-template-columns:repeat(auto-fill,minmax(160px,1fr));gap:15px}
.grid-item{padding:10px;border-radius:10px;transition:.2s;opacity:0;transform:translateY(20px)}
.grid-item.show{opacity:1;transform:none}
.grid-item:hover{box-shadow:0 0 15px gold}
.grid-item img{width:100%;height:auto;border-radius:5px}
.star{position:absolute;top:5px;right:8px;cursor:pointer}
.bar{height:6px;background:lime;margin-top:4px}
</style>

<div class="grid-container" id="grid_container"></div>

<script>
var container=document.getElementById("grid_container");
var counter=document.getElementById("counter");
var factBox=document.getElementById("factBox");
var views=document.getElementById("views");
var timerEl=document.getElementById("timer");
var hoverCount=0,seconds=0;

setInterval(()=>{seconds++;timerEl.textContent=`Session: ${seconds}s`},1000);

var http_source="https://upload.wikimedia.org/wikipedia/commons/";
var living_in_the_world=[
{flag:"0/01/Flag_of_California.svg",greeting:"Hey",description:"California - 10 years and so on",score:10},
{flag:"c/cd/Flag_of_Afghanistan_%282013%E2%80%932021%29.svg",greeting:"سلام",description:"Afghanistan - born and raised here for 5 years",score:5},
{flag:"9/9a/Flag_of_Spain.svg",greeting:"Hola",description:"Spain - I go here every summer",score:5}
];

var facts=["Flags represent identity","Some flags evolve","Colors carry meaning"];

function render(data){
 container.innerHTML="";
 data.forEach((loc,i)=>{
  var item=document.createElement("div");
  item.className="grid-item";
  item.draggable=true;

  item.ondragstart=e=>e.dataTransfer.setData("i",i);
  item.ondragover=e=>e.preventDefault();
  item.ondrop=e=>{
    var from=e.dataTransfer.getData("i");
    data.splice(i,0,data.splice(from,1)[0]);
    render(data);
  };

  item.onmouseenter=()=>{hoverCount++;views.textContent=`Hover: ${hoverCount}`};

  var img=document.createElement("img"); img.src=http_source+loc.flag;
  var p=document.createElement("p"); p.textContent=loc.description;
  var bar=document.createElement("div"); bar.className="bar"; bar.style.width=(loc.score*10)+"%";

  item.append(img,p,bar);
  container.appendChild(item);
 });

 counter.textContent=`Showing ${data.length}`;
 observe();
}

function observe(){
 var io=new IntersectionObserver(entries=>{
  entries.forEach(e=>{if(e.isIntersecting)e.target.classList.add("show")});
 });
 document.querySelectorAll(".grid-item").forEach(i=>io.observe(i));
}

render(living_in_the_world);

function sortAZ(){living_in_the_world.sort((a,b)=>a.description.localeCompare(b.description));render(living_in_the_world)}
function sortZA(){living_in_the_world.sort((a,b)=>b.description.localeCompare(a.description));render(living_in_the_world)}
function randomFact(){factBox.textContent=facts[Math.floor(Math.random()*facts.length)]}
function toggleTheme(){document.body.classList.toggle("dark")}
function highlightRandom(){
 var items=document.querySelectorAll(".grid-item");
 items.forEach(i=>i.style.outline="");
 var r=items[Math.floor(Math.random()*items.length)];
 r.style.outline="3px solid red";
 r.scrollIntoView({behavior:"smooth"});
}

document.addEventListener("keydown",e=>{
 if(e.key==="a")sortAZ();
 if(e.key==="z")sortZA();
 if(e.key==="/")document.getElementById("searchBox").focus();
 if(e.key==="t")toggleTheme();
 if(e.key==="h")highlightRandom();
});
</script>

### Culture, Family, Fun, About Me and A Photo of Me!!!
- I am 100% Afghan according to my Family tree
- My family consists of 2 parents 4 siblings 5 uncles 5 aunts 2 grandparents and lots of cousins
- I am a Muslim
- I want to be a Pilot or a Software Engineer

<img width="478" height="500" alt="Image" src="https://github.com/user-attachments/assets/408c3f8a-2bfa-47c4-8d13-afe54ebe07de" />

#### Stuff I like
<div class="grid-container" id="roblox_grid"></div>

<script>
var robloxContainer=document.getElementById("roblox_grid");

var projects=[
{image:"https://images.unsplash.com/photo-1579952363873-27f3bade9f55?w=400",title:"Soccer",description:"My first sport I joined when I was 8 and this is still my favorite sport."},
{image:"https://images.unsplash.com/photo-1512453979798-5ea266f8880c?w=400",title:"Rich City",description:"I want to live in Dubai one day and work for a big company or start a business."},
{image:"https://images.unsplash.com/photo-1578985545062-69928b1d9587?w=400",title:"Sweets",description:"I love sweets, especially cheesecake. I usually eat cake while drinking tea."}
];

projects.forEach(p=>{
 var item=document.createElement("div");
 item.className="grid-item";

 var img=document.createElement("img"); img.src=p.image;
 var t=document.createElement("p"); t.textContent=p.title;
 var d=document.createElement("p"); d.textContent=p.description;

 item.append(img,t,d);
 robloxContainer.appendChild(item);
});

setTimeout(()=>observe(),100);
</script>