---
layout: post
title: "Spider Monster: Don't shoot me!"
description: "Spider Monster Animation" # Add post description (optional)
tags: [Fun with HTML/CSS]
---

<div class="spider-monster-container">
    <button id="spider-heal-button" class="pushy__btn pushy__btn--sm pushy__btn--blue spider-heal-button no-display-block" onclick="heal()">Heal me :angel:</button>
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
    <div id="spider-monster" class="spider-idle">
        <span class="spider-collision" onclick="shot()">
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
            setTimeout(function (){
                document.querySelector('#spider-health-bar').classList.toggle("health-bar-empty");
            }, 200);
            document.querySelector('#spider-monster').classList.add("spider-die");
            setTimeout(function (){
                article = document.querySelector('#spider-monster').closest("article");
                article.classList.toggle("grayed-out-article");
                if (article.querySelector('.post-title a')) {
                    article.querySelector('.post-title a').innerHTML = "Spider Monster: Heal me!";
                } else if (article.querySelector('.page-title')) {
                    article.querySelector('.page-title').innerHTML = "Spider Monster: Heal me!";
                }
                toggleSpiderControl();
            }, 1500);
        }
    }
    function heal(){
        if (article.querySelector('.post-title a')) {
            article.querySelector('.post-title a').innerHTML = "Spider Monster: Don't shoot me!";
        } else if (article.querySelector('.page-title')) {
            article.querySelector('.page-title').innerHTML = "Spider Monster: Don't shoot me!";
        }
        spiderHealth = 5;
        document.querySelector('#spider-monster').removeAttribute("class");
        document.querySelector('#spider-monster').classList.add("spider-idle");
        document.querySelector('#spider-monster').closest("article").classList.toggle("grayed-out-article");
        document.querySelector('#spider-health-bar').classList.toggle("health-bar-empty");
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
