---
layout: cover
background: /images/the-one-pipeline.webp
---

<AntiPattern :num="4" />

# The One Pipeline
## One pipeline to rule them all

---
layout: center-content
transition: fade
---

# Antipattern #4: The One Pipeline

::content::

```mermaid { theme: 'forest' }
block-beta
    columns 10
    bs("Backend\nsetup") bl("Backend\nlint") bc("Backend\ncompile") bt("Backend\nTests")
    fs("Frontend\nsetup") fl("Frontent\nlint") fc("Frontend\ncompile") ft("Frontend\ntests")
    i("Integration\ntests")
    space:10
```

---
layout: center-content
---

# Antipattern #4: The One Pipeline

::content::

```mermaid { theme: 'forest' }
block-beta
    columns 10
    bs("Backend\nsetup") bl("Backend\nlint") bc("Backend\ncompile") bt("Backend\nTests")
    fs("Frontend\nsetup") fl("Frontent\nlint") fc("Frontend\ncompile") ft("Frontend\ntests")
    it("Integration\ntests") tt("24 m 40 s")
    tts("33 s") tbl("2 m 42 s") tbc("5 m 14 s") tbt("52 s")
    tfs("1 m 8 s") tfl("1 m 53 s") tfc("2 m 12 s") tft("3 m 26s")
    tit("6 m 41 s")
    
    classDef timing fill: #0000, stroke: #0000
    class tts,tbl,tbc,tbt,tfs,tfl,tfc,tft,tit,tt timing
```

---
layout: center-content
---

# Pattern #4: Parallel pipelines

::content::

```mermaid { theme: 'forest' }
block-beta
    columns 6
    bs("Backend setup") bl("Backend lint") bc("Backend compile") bt("Backend Tests") tb("9 m 21 s") space
    tbs("33 s") tbl("2 m 42 s") tbc("5 m 14 s") tbt("52 s") space:2
    fs("Frontend setup") fl("Frontent lint") fc("Frontend compile") ft("Frontend tests") tf("8 m 39 s") space
    tfs("1 m 8 s") tfl("1 m 53 s") tfc("2 m 12 s") tft("3 m 26s") space:2
    ibs("Backend setup") ibc("Backend compile") ifs("Frontend setup") ifc("Frontend compile") it("Integration tests") ti("14 m 48 s")
    tibs("33 s") tibc("5 m 14 s") tifs("1 m 8 s") tifc("2 m 12 s") tit("6 m 41 s")
    
    classDef timing fill: #0000, stroke: #0000
    class tbs,tbl,tbc,tbt,tb,tfs,tfl,tfc,tft,tf,tibs,tibc,tifs,tifc,tit,ti timing
```

<!--

9 minutes saved!
Total time: 32 m 48 s (+7 m 52 s)

-->

---
layout: center-content
---

# Pattern #4: Parallel pipelines

::content::

```mermaid { theme: 'forest' }
block-beta
    columns 7
    bs("Backend setup") bl("Backend lint") bc("Backend compile") bt("Backend Tests") ba("Publish Artifact") tb("9 m 28 s") space
    tbs("33 s") tbl("2 m 42 s") tbc("5 m 14 s") tbt("52 s") tba("7 s") space:2
    space:5 it("Integration tests") ti("16 m 9 s")
    space:5 tit("6 m 41 s") space
    fs("Frontend setup") fl("Frontent lint") fc("Frontend compile") ft("Frontend tests") fa("Publish Artifact") tf("8 m 47 s") space
    tfs("1 m 8 s") tfl("1 m 53 s") tfc("2 m 12 s") tft("3 m 26s") tfa("8 s") space:2
    
    ba --> it
    fa --> it
    classDef timing fill: #0000, stroke: #0000
    class tbs,tbl,tbc,tbt,tb,tba,tfs,tfl,tfc,tft,tf,tfa,tibs,tibc,tifs,tifc,tit,ti timing
```

<!--

9 minutes saved!
Total time: 24 m 56 s (+ 16 s)

-->

---
layout: center-content
---

# Pattern #4: Parallel pipelines

::content::

```mermaid { theme: 'forest' }
block-beta
    columns 7
    bs("Backend setup") bc("Backend compile") ba("Publish Artifact") space bl("Backend lint") bt("Backend Tests")  tb("9 m 28 s")
    tbs("33 s") tbc("5 m 14 s") tba("7 s") space tbl("2 m 42 s") tbt("52 s") space
    space:4 it("Integration tests") ti("12 m 35 s") space
    space:4 tit("6 m 41 s") space:2
    fs("Frontend setup") fc("Frontend compile") fa("Publish Artifact") space fl("Frontend lint") ft("Frontend tests") tf("8 m 47 s")
    tfs("1 m 8 s") tfc("2 m 12 s") tfa("8 s") space tfl("1 m 53 s") tft("3 m 26s") space
    
    ba --> it
    ba --> bl
    fa --> it
    fa --> fl
    classDef timing fill: #0000, stroke: #0000
    class tbs,tbl,tbc,tbt,tb,tba,tfs,tfl,tfc,tft,tf,tfa,tibs,tibc,tifs,tifc,tit,ti timing
```

<!--

9 minutes saved!
Total time: 24 m 56 s (+ 16 s)

-->
