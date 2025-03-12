---
theme: ./theme

# https://sli.dev/custom/highlighters.html
highlighter: shiki

# show line numbers in code blocks
lineNumbers: false

# use UnoCSS
css: unocss

layout: intro
---

# Pipeline patterns and anti-patterns
## Things your pipeline should (not) do

<div class="text-black">
Daniel Raniz Raneland<br />
Coding Architect @ factor10

<div class="grid grid-cols-4 w-80% mt-10">
    <div></div><div class="col-span-2"><mdi-firefox />factor10.com</div>
    <div class="col-span-2"><mdi-email />raniz@factor10.com</div>
    <div class="col-span-2"><mdi-mastodon />raniz@mastodon.online</div>
    <div class="col-span-2"><mdi-firefox />raniz.blog</div>
    <div class="col-span-2"><mdi-linkedin />/in/raneland</div>
</div>
</div>

<div class="absolute right-20px top-90px">
    <img width="300" src="/images/about-me-qr.svg" />
</div>

---
layout: cover
background: /images/frustrated.jpg
attribution: Yogendra Singh via Unsplash
dim: false
---

<!--

We wil try to reduce:

* Frustration

-->

---
layout: cover
background: /images/waiting.jpg
attribution: Priscilla Du Preez via Unsplash
dim: false
---

<!--

We wil try to reduce:

* Frustration
* Waiting times/lowered cycle time

-->

---
layout: cover
background: /images/climate.jpg
attribution: Markus Spiske via Unsplash
dim: false
---

<!--

We wil try to reduce:

* Frustration
* Waiting times/lowered cycle time
* Climate impact

-->

---
layout: cover
background: /images/elephant.jpg
attribution: Felix M. Dom via Unsplash
dim: false
---

<!--

Elephant in the room: Everyone is using different platforms with different syntax, feature and terminology.
This talk tries to be agnostic, examples will be in GitHub Actions YAML when needed, they are very few.

Pipeline -> Job -> Step
Jobs can be grouped into stages

-->

---
src: ./pages/the-ritual.md
---

---
src: ./pages/hoarding.md
---

---
src: ./pages/the-aesthete.md
---

---
src: ./pages/the-one-pipeline.md
---

#---
#src: ./pages/gift-wrapping.md
#---

#---
#src: ./pages/complicated.md
#---

---
src: ./pages/groundhog-day.md
---

---
src: ./pages/interference.md
---

---
src: ./pages/underpowered.md
---

#---
#src: ./pages/outro.md
#---

---
layout: custom
---

<div class="grid grid-cols-3 grid-gap-10px justify-items-center align-items-center text-center absolute top-20px left-20px w-940px h-512px">
    <img class="max-h-160px" src="/images/ritual.jpg" />
    <img class="max-h-160px" src="/images/hoarding.jpg" />
    <img class="max-h-160px" src="/images/ordered.jpg" />
    <img class="max-h-160px" src="/images/the-one-pipeline.webp" />
    <!--<img class="max-h-160px" src="/images/wrapped.jpg" />-->
    <!--<img class="max-h-160px" src="/images/complicated.webp" />-->
    <img class="max-h-160px" src="/images/restarting.jpg" />
    <img class="max-h-160px" src="/images/interference.jpg" />
    <img class="max-h-160px" src="/images/underpowered.jpg" />
</div>


---
layout: intro
---

# Pipeline patterns and anti-patterns
## Things your pipeline should (not) do

<div class="text-black">
Daniel Raniz Raneland<br />
Coding Architect @ factor10

<div class="grid grid-cols-4 w-80% mt-10">
    <div></div><div class="col-span-2"><mdi-firefox />factor10.com</div>
    <div class="col-span-2"><mdi-email />raniz@factor10.com</div>
    <div class="col-span-2"><mdi-mastodon />raniz@mastodon.online</div>
    <div class="col-span-2"><mdi-firefox />raniz.blog</div>
    <div class="col-span-2"><mdi-linkedin />/in/raneland</div>
</div>
</div>

<div class="absolute right-20px top-90px">
    <img width="300" src="/images/about-me-qr.svg" />
</div>
