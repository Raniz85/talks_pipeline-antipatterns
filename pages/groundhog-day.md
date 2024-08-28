---
layout: cover
background: /images/restarting.jpg
attribution: Jimmy Conover via Unsplash
---
<AntiPattern :num="7" />

# Groundhog day
## Starting from scratch all the time

--- 
layout: center-content
---

# Antipattern #7: Groundhog day

::content::

```mermaid { theme: 'forest' }
block-beta
    columns 6
    bs("Setup") bf("Fetch dependencies") bl("Lint") bc("Compile") bt("Tests") tb("11 m 54 s")
    
    classDef timing fill: #0000, stroke: #0000
    class tb timing
```
---
layout: cover
background: /images/caching.webp
---

<AntiPattern :pattern="'Pattern'" :num="7" />

# Caching

--- 
layout: center-content
transition: fade

---

# Caching dependencies

::content::

```mermaid { theme: 'forest' }
block-beta
    columns 3
    space bf("Fetch dependencies") space
    space:3
```

<div v-click>


```mermaid { theme: 'forest' }
block-beta
    columns 3
    rc("Restore cache") bf("Fetch dependencies") uc("Update cache")
    space:3
```

</div>

--- 
layout: center-content
---

# Caching dependencies

::content::

```mermaid { theme: 'forest' }
block-beta
    columns 3
    space bf("Fetch dependencies") space
    space tbf("7 s")
    
    classDef timing fill: #0000, stroke: #0000
    class tbf timing
```


```mermaid { theme: 'forest' }
block-beta
    columns 3
    rc("Restore cache") bf("Fetch dependencies") uc("Update cache")
    trc("4 s") tbf("< 1 s") tuc("< 1 s")
    
    classDef timing fill: #0000, stroke: #0000
    class trc,tbf,tuc timing
```



<!--

80 or so dependencies. Takes 5-8 seconds to download.
The caching steps taks around 5 seconds so the net saves is almost nothing

-->

--- 
layout: center-content
transition: fade
---

# Caching build output

::content::

```mermaid { theme: 'forest' }
block-beta
    columns 6
    rc("Restore cache") bl("Lint") bc("Compile") bt("Tests") uc("Update cache") tt("11 m 13 s")
    space tbl("2 m 29 s") tbc("5 m 36 s") tbt("3 m 8 s")
    
    classDef invisible opacity: 0.0
    classDef timing fill: #0000, stroke: #0000
    class rc,uc invisible
    class tbl,tbc,tbt,tt invisible
```

<div v-click>


```mermaid { theme: 'forest' }
block-beta
    columns 6
    rc("Restore cache") bl("Lint") bc("Compile") bt("Tests") uc("Update cache") tt("6 m 50 s")
    trc("31 s") tbl("24 s") tbc("2 m 29 s") tbt("3 m 25 s") tuc("< 1 s")
    
    classDef invisible opacity: 0.0
    classDef timing fill: #0000, stroke: #0000
    class trc,tbl,tbc,tbt,tuc,tt invisible
```

</div>

--- 
layout: center-content
---

# Caching build output

::content::

```mermaid { theme: 'forest' }
block-beta
    columns 6
    rc("Restore cache") bl("Lint") bc("Compile") bt("Tests") uc("Update cache") tt("11 m 13 s")
    space tbl("2 m 29 s") tbc("5 m 36 s") tbt("3 m 8 s")
    
    classDef invisible opacity: 0.0
    classDef timing fill: #0000, stroke: #0000
    class rc,uc invisible
    class tbl,tbc,tbt,tt timing
```

```mermaid { theme: 'forest' }
block-beta
    columns 6
    rc("Restore cache") bl("Lint") bc("Compile") bt("Tests") uc("Update cache") tt("6 m 50 s")
    trc("31 s") tbl("24 s") tbc("2 m 29 s") tbt("3 m 25 s") tuc("< 1 s")
    classDef timing fill: #0000, stroke: #0000
    class trc,tbl,tbc,tbt,tuc,tt timing
```

<!--

Saved slightly almost 4 and a half minutes in total

-->


---

# Caching container images

```bash
docker buildx build \
  --push \
  --tag my/image:latest \
  --cache-from type=registry,ref=my.registry/my/repo-cache:latest \
  --cache-to type=registry,ref=my.registry/my/repo-cache:latest \
  .
```

<v-clicks>

```console{all|5|8|10-14}
#7 importing cache manifest from my/repo-cache:latest
#7 inferred cache manifest type: application/vnd.oci.image.index.v1+json done
#7 DONE 1.2s

#8 [3/4] RUN cargo install --locked --git https://github.com/leptos-rs/cargo-leptos cargo-leptos
#8 extracting sha256:b0a0cf830b12453b7e15359a804215a7bcccd3788e2bcecff2a03af64bbd4df7 1.3s done
#8 extracting sha256:e62e6e54ca92f1c0e35a38988a00f7753207afcb1fc9106d95893324d7505fb5 4.3s done
#8 DONE 7.9s

#9 [4/4] RUN cargo install --locked cross
#9 0.092     Updating crates.io index
#9 0.360  Downloading crates ...
#9 0.681   Downloaded cross v0.2.5
#9 0.713   Installing cross v0.2.5
```

<!--

cargo install leptos ~6 minutes

-->

</v-clicks>

---
layout: center-content
---

# Pattern #8: Tooling images

::content::

```mermaid { theme: 'forest' }
block-beta
    columns 4
    1bi("Build Image") space 1b("Backend") 1it("Integration tests")
    space r("tooling:82bea7") space:2
    
    1bi-->r
    r-->1b
    r-->1it
    
    style r fill: #ff984e
```

---
layout: center-content
---

# Pattern #8: Tooling images

::content::

<h3 class="text-left">main</h3>

```mermaid { theme: 'forest' }
block-beta
    columns 4
    1bi("Build Image") space 1b("Backend") 1it("Integration tests")
    space r("tooling:latest") space:2
    
    1bi-->r
    r-->1b
    r-->1it
    
    style r fill: #ff984e
```

<div v-click>

<h3 class="text-left">
PR #387: Add index on user birthdates
</h3>

```mermaid { theme: 'forest' }
block-beta
    columns 4
    1bi("Build Image") space 1b("Backend") 1it("Integration tests")
    space r("tooling:latest") space:2
    
    r-->1b
    r-->1it
    
    style r fill: #ff984e
    classDef disabled fill: #ddd, opacity: 0.4, stroke: #bbb, color: #111
    class 1bi disabled
```

</div>

<div v-click>

<h3 class="text-left">
PR #392: Upgrade cross in the build pipeline
</h3>

```mermaid { theme: 'forest' }
block-beta
    columns 4
    1bi("Build Image") space 1b("Backend") 1it("Integration tests")
    space r("tooling:b2a38cf") space:2
    
    1bi-->r
    r-->1b
    r-->1it
    
    style r fill: #ff984e
    classDef disabled fill: #ddd, opacity: 0.4, stroke: #bbb, color: #111
```

</div>

<!--

NEVER have persistent state on the runners

-->