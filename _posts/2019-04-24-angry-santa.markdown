---
layout: post
title: Angry Santa
description: "Angry Santa Animation"  # Add post description (optional)
img-ref: https://media.giphy.com/media/l2SpRphLbQoZ2oBvG/giphy.gif
fig-caption: # Add figcaption (optional)
tags: [Fun with HTML/CSS]
---
<div class="angry-santa-container">
    <div class="angry-santa-controller">
        <div id="angry-santa" class="santa-idle">
        </div>
        <br />
        <div class="angry-santa-control-board">
            <button class="pushy__btn pushy__btn--sm pushy__btn--red control-button" data-control="idle" onclick="santaControl(this)">Idle</button>
            <button class="pushy__btn pushy__btn--sm pushy__btn--red control-button" data-control="cough" onclick="santaControl(this)">Cough</button>
            <button class="pushy__btn pushy__btn--sm pushy__btn--red control-button" data-control="gift" onclick="santaControl(this)">Gift</button>
            <button class="pushy__btn pushy__btn--sm pushy__btn--red control-button" data-control="run" onclick="santaControl(this)">Run</button>
            <button class="pushy__btn pushy__btn--sm pushy__btn--red control-button" data-control="punch" onclick="santaControl(this)">Punch</button>
            <button class="pushy__btn pushy__btn--sm pushy__btn--red control-button" data-control="kick" onclick="santaControl(this)">Kick</button>
        </div>
    </div>
</div>
<script>
    function santaControl(element) {
        document.querySelector('#angry-santa').removeAttribute("class");
        void document.querySelector('#angry-santa').offsetWidth;
        document.querySelector('#angry-santa').classList.add("santa-" + element.dataset.control);
    }
</script>