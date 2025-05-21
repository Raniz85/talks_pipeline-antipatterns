---
layout: cover
background: /images/interference.jpg
attribution: Uriel Soberanes via Unsplash
---
<AntiPattern :num="8" />

# Interference
## Colliding with other pipelines

---
transition: fade
---

#  Antipattern #8: Interference

```mermaid { theme: 'forest' }
block-beta
    columns 4
    space:2 1f("Frontend") space
    space 1bi("Build Image") 1b("Backend") 1it("Integration tests")
    space:4
    space:2 r("tooling:latest") space
    
    1bi-->r
    r-->1b
    r-->1it
    
    style r fill: #ff984e
    style 1it stroke-dasharray: 5 5, fill: #ffffff
    classDef heading fill: #0000, stroke: #0000
    class b1,b2 heading
```

---
transition: fade
---

#  Antipattern #8: Interference

```mermaid { theme: 'forest' }
block-beta
    columns 5
    space:2 1f("Frontend") space:2
    b1("Build 1") 1bi("Build Image") 1b("Backend") 1it("Integration tests") space
    space:5
    space:2 r("tooling:latest") space:2
    space:5
    b2("Build 2") space 2bi("Build Image") 2b("Backend") 2it("Integration tests")
    space:3 2f("Frontend") space
    
    1bi-->r
    2bi-->r
    r-->1b
    r-->1it
    r-->2b
    r-->2it
    
    style r fill: #ff984e
    classDef pending stroke-dasharray: 5 5, fill: #ffffff
    class 1it,2b,2f,2it pending
    classDef heading fill: #0000, stroke: #0000
    class b1,b2 heading
```
---

#  Antipattern #8: Interference

```mermaid { theme: 'forest' }
block-beta
    columns 5
    space:2 1f("Frontend") space:2
    b1("Build 1") 1bi("Build Image") 1b("Backend") 1it("Integration tests") space
    space:5
    space:2 r("tooling:latest") space:2
    space:5
    b2("Build 2") space 2bi("Build Image") 2b("Backend") 2it("Integration tests")
    space:3 2f("Frontend") space
    
    1bi-->r
    2bi-->r
    r-->1b
    r-->1it
    r-->2b
    r-->2it
    
    style r fill: #ff984e
    classDef failed fill: #e49091
    class 1it failed
    classDef pending stroke-dasharray: 5 5, fill: #ffffff
    class 2it pending
    classDef heading fill: #0000, stroke: #0000
    class b1,b2 heading
```
---
layout: center-content
---

#  Antipattern #8: Interference

::content::

<img class="w-75% mx-auto" src="/images/test-db-interference.svg" />
