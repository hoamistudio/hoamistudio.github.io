---
layout: post
title: "Spider Monster: Don't shoot me!"
description: "Spider Monster Animation" # Add post description (optional)
small-post: true
small-post-left: true
title-size: 27px
tags: [Fun with HTML/CSS]
---
<div class="spider-monster-container">
    <div style="display: none">
        <img rel="preload" src="/assets/img/spider-idle.jpg" alt="Spider Idle">
        <img rel="preload" src="/assets/img/spider-hurt.png" alt="Spider Hurt">
        <img rel="preload" src="/assets/img/spider-die.png" alt="Spider Die">
    </div>
    <button id="spider-heal-button" class="pushy__btn pushy__btn--sm pushy__btn--blue spider-heal-button no-display-block" onclick="heal()">Heal Me :angel:</button>
    <div id="spider-health-bar" class="health-bar">
        <div id="spider-health" class="health">
            <div class="health-1">
            </div>
            <div class="health-2">
            </div>
            <div class="health-3">
            </div>
            <div class="health-4">
            </div>
        </div>
    </div>
    <br/>
    <div id="spider-monster" class="spider-idle">
        <span id="spider-collision" class="spider-collision" onclick="shot()">
        </span>
    </div>
</div>
<script>
    var article;
    var spiderHealth = 5;
    function shot() {
        if (spiderHealth == 0) return;
        document.querySelector('#spider-monster').removeAttribute("class");
        spiderHealth--;
        if (spiderHealth > 0) {
            document.querySelector('#spider-health .health-' + spiderHealth).classList.add("health-lost");
            document.querySelector('#spider-monster').classList.add("spider-hurt");
            setTimeout(function (){
                if (spiderHealth > 0) {
                    document.querySelector('#spider-monster').removeAttribute("class");
                    document.querySelector('#spider-monster').classList.add("spider-idle");
                }
            }, 500);
        } else {
            document.querySelector('#spider-health-bar').classList.toggle("health-bar-empty");
            document.querySelector('#spider-monster').classList.add("spider-die");
            setTimeout(function (){
                article = document.querySelector('#spider-monster').closest("article");
                article.classList.toggle("transition-gray-background");
                if (article.querySelector('.post-title a')) {
                    article.querySelector('.post-title a').innerHTML = "Spider Monster: Please Heal Me!";
                    article.querySelector('.post-title a').classList.toggle("color-white");
                } else if (article.querySelector('.page-title')) {
                    article.querySelector('.page-title').innerHTML = "Spider Monster: Please Heal Me!";
                    article.querySelector('.page-title').classList.toggle("color-white");
                }
                document.querySelector('#spider-collision').classList.toggle("spider-rip-collision");
                toggleSpiderControl();
            }, 1750);
        }
    }
    function heal(){
        if (article.querySelector('.post-title a')) {
            article.querySelector('.post-title a').innerHTML = "Spider Monster: Don't shoot me!";
            article.querySelector('.post-title a').classList.toggle("color-white");
        } else if (article.querySelector('.page-title')) {
            article.querySelector('.page-title').innerHTML = "Spider Monster: Don't shoot me!";
            article.querySelector('.page-title').classList.toggle("color-white");
        }
        spiderHealth = 5;
        document.querySelector('#spider-monster').removeAttribute("class");
        document.querySelector('#spider-monster').classList.add("spider-idle");
        article.classList.toggle("transition-gray-background");
        document.querySelector('#spider-health-bar').classList.toggle("health-bar-empty");
        document.querySelector('#spider-collision').classList.toggle("spider-rip-collision");
        Array.from(document.querySelectorAll('.health-lost')).forEach(function (element){
            element.classList.remove("health-lost");
        });
        toggleSpiderControl()
    }
    function toggleSpiderControl() {
        document.querySelector('#spider-heal-button').classList.toggle('no-display-block');
        document.querySelector('#spider-health-bar').classList.toggle('no-display-block');
    }
</script>
