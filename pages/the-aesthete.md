---
layout: cover
background: /images/ordered.jpg
attribution: Andre Taissin via Unsplash
---
<AntiPattern :num="3" />

# The Aesthete
## "Natural" instead of practical ordering

---
layout: center-content
---

# Antipattern #3: The Aesthete

::content::

```mermaid { theme: 'forest' }
block-beta
    columns 7
    s("Setup") l("Lint")  c("Compile") ut("Unit tests") it("Integration tests") p("E2E Tests") space
    space:7
```

---
layout: center-content
---

# Antipattern #3: The Aesthete

::content::

```mermaid { theme: 'forest' }
block-beta
    columns 7
    s("Setup") l("Lint")     c("Compile")      ut("Unit tests") it("Integration tests") p("E2E Tests") tt("13 m 37 s")
    ts("33 s") tl("2 m 42 s") tc("5 m 14 s")   tut("52 s")      tit("4 m 16s")
    
    classDef failed fill: #e49091
    classDef disabled fill: #ddd, opacity: 0.4, stroke: #bbb, color: #111
    classDef timing fill: #0000, stroke: #0000
    class p disabled
    class ts,tc,tit,tut,tl,tt timing
    class it failed
```

---
layout: center-content
---

# Pattern #3: Failing fast

::content::

```mermaid { theme: 'forest' }
block-beta
    columns 7
    s("Setup") c("Compile") it("Integration tests") p("E2E Tests") ut("Unit tests") l("Lint") tt("10 m 3 s")
    ts("33 s") tc("5 m 14 s")    tit("4 m 16 s")
    
    classDef failed fill: #e49091
    classDef disabled fill: #ddd, opacity: 0.4, stroke: #bbb, color: #111
    classDef timing fill: #0000, stroke: #0000
    class ut,l,p disabled
    class ts,tc,tit,tt timing
    class it failed
```
