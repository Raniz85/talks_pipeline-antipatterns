---
layout: cover
background: /images/underpowered.jpg
attribution: Jainath Ponnala via Unsplash
---
<AntiPattern :num="9" />

# Overloaded
## Running on underpowered machines

---

# Raniz' rules-of-thumb for build agent sizing

1. If the build is slower on the build agents than on developer machines: beef up the build agents.
1. If the build fails because of a lack of resources: beef up the build agents.
1. If you have issues with queue times, get more servers
1. If the available build agent configurations aren't sufficient: roll your own.

---
layout: two-columns
---

# Should you run your own agents?

&nbsp;

::left::

## Pros

<ul class="pros mt-5 text-size-120%">
    <li v-click="1">Full control</li>
    <li v-click="3">Right-sizing</li>
    <li v-click="5">Cost</li>
</ul>

::right::

## Cons

<ul class="cons mt-5 text-size-120%">
    <li v-click="2">Maintenance</li>
    <li v-click="4">Scaling</li>
    <li v-click="5">Cost</li>
</ul>

<!--

# Costs for 4 vCPU 8+ GiB:
GitHub Actions: 0.89 EUR/h  
GitLab CI: 1.11 EUR/h  
SafeSpring: 0.10 EUR/h
AWS Fargate: 0.20

-->