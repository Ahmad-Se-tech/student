---
layout: opencs
title: Snake Game
permalink: /snake/
---

<style>
    body{}
    .wrap{
        margin-left: auto;
        margin-right: auto;
    }

    canvas{
        display: none;
        border-style: solid;
        border-width: 10px;
        border-color: rgba(21, 155, 0, 1);}
    canvas:focus{
        outline: none;
    }

    #gameover p, #setting p, #menu p{
        font-size: 20px;
    }

    #gameover a, #setting a, #menu a{
        font-size: 30px;
        display: block;
    }

    #gameover a:hover, #setting a:hover, #menu a:hover{
        cursor: pointer;
    }

    #gameover a:hover::before, #setting a:hover::before, #menu a:hover::before{
        content: ">";
        margin-right: 10px;
    }

    #menu{ display: block; }
    #gameover{ display: none; }
    #setting{ display: none; }
    #setting input{ display:none; }
    #setting label{ cursor: pointer; }
    #setting input:checked + label{
        background-color: #000000ff;
        color: #ffffffff;
    }
</style>

