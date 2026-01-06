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

setInterval(function(){
  seconds++;
  timerEl.textContent="Session: "+seconds+"s";
},1000);

var http_source="https://upload.wikimedia.org/wikipedia/commons/";
var living_in_the_world=[
{flag:"0/01/Flag_of_California.svg",description:"California - 10 years",score:10},
{flag:"/c/cd/Flag_of_Afghanistan_%282013%E2%80%932021%29.svg",description:"Afghanistan - born and raised",score:5},
{flag:"/9/9a/Flag_of_Spain.svg",description:"Spain - every summer",score:5}
];

var facts=["Flags represent identity","Some flags evolve","Colors carry meaning"];

function render(data){
  container.innerHTML="";
  for(var i=0;i<data.length;i++){
    var loc=data[i];
    var item=document.createElement("div");
    item.className="grid-item";

    item.onmouseenter=function(){
      hoverCount++;
      views.textContent="Hover: "+hoverCount;
    };

    var img=document.createElement("img");
    img.src=http_source+loc.flag;

    var p=document.createElement("p");
    p.textContent=loc.description;

    var bar=document.createElement("div");
    bar.className="bar";
    bar.style.width=(loc.score*10)+"%";

    item.appendChild(img);
    item.appendChild(p);
    item.appendChild(bar);

    container.appendChild(item);
  }

  counter.textContent="Showing "+data.length;
}

render(living_in_the_world);

function sortAZ(){
  living_in_the_world.sort(function(a,b){
    return a.description.localeCompare(b.description);
  });
  render(living_in_the_world);
}

function sortZA(){
  living_in_the_world.sort(function(a,b){
    return b.description.localeCompare(a.description);
  });
  render(living_in_the_world);
}

function randomFact(){
  var r=Math.floor(Math.random()*facts.length);
  factBox.textContent=facts[r];
}

function toggleTheme(){
  document.body.classList.toggle("dark");
}

function highlightRandom(){
  var items=document.querySelectorAll(".grid-item");
  for(var i=0;i<items.length;i++){
    items[i].style.outline="";
  }
  var r=Math.floor(Math.random()*items.length);
  items[r].style.outline="3px solid red";
}
</script>

### Stuff I like
<div class="grid-container" id="roblox_grid"></div>

<script>
var robloxContainer=document.getElementById("roblox_grid");

var projects=[
{image:"images/about/soccer.jpeg",title:"Soccer",description:"My favorite sport"},
{image:"images/about/Dubai.webp",title:"Dubai",description:"A place I want to live"},
{image:"images/about/cake.webp",title:"Cake",description:"I love cheesecake"}
];

for(var i=0;i<projects.length;i++){
  var p=projects[i];

  var item=document.createElement("div");
  item.className="grid-item";

  var img=document.createElement("img");
  img.src=p.image;

  var t=document.createElement("p");
  t.textContent=p.title;

  var d=document.createElement("p");
  d.textContent=p.description;

  item.appendChild(img);
  item.appendChild(t);
  item.appendChild(d);

  robloxContainer.appendChild(item);
}
</script>
