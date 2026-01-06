---
layout: post
title: About
permalink: /about/
comments: true
---

<div id="dashboard">
  <span id="timer">Session: 0s</span> |
  <span id="views">Hover: 0</span> |
  <button onclick="exportFavs()">Export ⭐</button>
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
{flag:"/c/cd/Flag_of_Afghanistan_%282013%E2%80%932021%29.svg",greeting:"سلام",description:"Afghanistan - born and raised here for 5 years",score:5},
{flag:"/9/9a/Flag_of_Spain.svg",greeting:"Hola",description:"Spain - I go here every summer",score:3}
];

var facts=["Flags represent identity","Some flags evolve","Colors carry meaning"];

