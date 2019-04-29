---
layout: post
title: "Lighten The Lantern"
description: "Lighten The Lantern Animation" # Add post description (optional)
small-post: true
small-post-right: true
gray-post: true
title-size: 27px
tags: [Fun with HTML/CSS]
---
<div class="lantern-container">
    <div id="glass" class="glass">
    </div>
    <div id="flame" class="flame">
    </div>
    <div id="glow" class="glow">
    </div>
    <div id="lantern" class="lantern">
    </div>
</div>
<script>
    var flameElement;
    var glowElement;
    var glassElement;
    function handleActive(){
        console.log("mouse over");
        flameElement = document.querySelector('#flame');
        if (!flameElement.classList.contains("active-flame")) {
            flameElement.classList.add("active-flame");
        }
        glowElement = document.querySelector('#glow');
        if (!glowElement.classList.contains("active-glow")) {
            glowElement.classList.add("active-glow");
        }
        glassElement = document.querySelector('#glass');
        if (!glassElement.classList.contains("active-glass")) {
            glassElement.classList.add("active-glass");
        }
    };
    function handleDeactive(){
        flameElement.classList.remove("active-flame");
        glowElement.classList.remove("active-glow");
        glassElement.classList.remove("active-glass");
    };
    var article = document.querySelector('#lantern').closest("article");
    article.style.backgroundColor = "gray";
    document.querySelector('#lantern').onmouseover = handleActive;
    document.querySelector('#lantern').ontouchstart= handleActive;
    document.querySelector('#lantern').onmouseout = handleDeactive;
    document.querySelector('#lantern').ontouchend = handleDeactive;
</script>
