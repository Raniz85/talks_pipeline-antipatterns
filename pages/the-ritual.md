---
layout: cover
background: /images/ritual.jpg
attribution: Chinh Le Duc via Unsplash
---

<AntiPattern :num="1" />

# The Ritual
## Doing everything all the time

---

# Antipattern #1: The Ritual

## PR
```mermaid { theme: 'forest' }
block-beta
    bs("Backend\nsetup") bl("Backend\nlint") bt("Backend\nTests")
    fs("Frontend\nsetup") fl("Frontent\nlint") ft("Frontend\ntests")
    i("Integration\ntests")
```

<div style="height: 2em">
</div>
<div v-click>

## Merge (main)
```mermaid { theme: 'forest' }
block-beta
    bs("Backend\nsetup") bl("Backend\nlint") bt("Backend\nTests")
    fs("Frontend\nsetup") fl("Frontent\nlint") ft("Frontend\ntests")
    i("Integration\ntests")
```

</div>
<div style="height: 2em">
</div>
<div v-click>

## Nightly
```mermaid { theme: 'forest' }
block-beta
    bs("Backend\nsetup") bl("Backend\nlint") bt("Backend\nTests")
    fs("Frontend\nsetup") fl("Frontent\nlint") ft("Frontend\ntests")
    i("Integration\ntests")
```

</div>

---

# Antipattern #1: The Ritual

## PR
```mermaid { theme: 'forest' }
block-beta
    bs("Backend\nsetup") bl("Backend\nlint") bt("Backend\nTests")
    fs("Frontend\nsetup") fl("Frontent\nlint") ft("Frontend\ntests")
    i("Integration\ntests") a("Publish\nartifact")
```

<div style="height: 2em">
</div>

## Merge (main)
```mermaid { theme: 'forest' }
block-beta
    bs("Backend\nsetup") bl("Backend\nlint") bt("Backend\nTests")
    fs("Frontend\nsetup") fl("Frontent\nlint") ft("Frontend\ntests")
    i("Integration\ntests") a("Publish\nartifact")
```

<div style="height: 2em">
</div>

## Nightly
```mermaid { theme: 'forest' }
block-beta
    bs("Backend\nsetup") bl("Backend\nlint") bt("Backend\nTests")
    fs("Frontend\nsetup") fl("Frontent\nlint") ft("Frontend\ntests")
    i("Integration\ntests") a("Publish\nartifact")
```


---

# Pattern #1: The right pipeline for the job

## PR
```mermaid { theme: 'forest' }
block-beta
    bs("Backend\nsetup") bl("Backend\nlint") bt("Backend\nTests")
    fs("Frontend\nsetup") fl("Frontent\nlint") ft("Frontend\ntests") i("Integration\ntests")
```

<div style="height: 2em">
</div>

## Merge (main)
```mermaid { theme: 'forest' }
block-beta
    bs("Backend\nsetup") bt("Backend\nTests")
    fs("Frontend\nsetup") ft("Frontend\ntests")
    i("Integration\ntests") a("Publish\nartifact")
```

<div style="height: 2em">
</div>

## Nightly
```mermaid { theme: 'forest' }
block-beta
    bs("Backend\nsetup") fs("Frontend\nsetup") i("Integration\ntests")
```

<!--

PR: No artifact

Main: No linting

Nightly: Just integration tests

-->

---
layout: center-content
---

# Pattern #2: Conditional pipeline steps

::content::

## PR

```mermaid { theme: 'forest' }
block-beta
    bs("Backend\nsetup") bl("Backend\nlint") bt("Backend\nTests")
    fs("Frontend\nsetup") fl("Frontent\nlint") ft("Frontend\ntests") i("Integration\ntests")
```

---
layout: center-content
---

# Pattern #2: Conditional pipeline steps

::content::

## "Hide settings menu when logged out"
```mermaid { theme: 'forest' }
block-beta
    bs("Backend\nsetup") bl("Backend\nlint") bt("Backend\nTests")
    fs("Frontend\nsetup") fl("Frontent\nlint") ft("Frontend\ntests") i("Integration\ntests")
    
    classDef disabled fill: #ddd, opacity: 0.4, stroke: #bbb, color: #111
    class bl,bt disabled
```

<div style="height: 2em">
</div>

## "Add index on user birthdate"
```mermaid { theme: 'forest' }
block-beta
    bs("Backend\nsetup") bl("Backend\nlint") bt("Backend\nTests")
    fs("Frontend\nsetup") fl("Frontent\nlint") ft("Frontend\ntests") i("Integration\ntests")
    
    classDef disabled fill: #ddd, opacity: 0.4, stroke: #bbb, color: #111
    class fl,ft disabled
```

---

# Pattern #2: Conditional pipeline steps

```yaml{all|9-14|4-6|18,21-23}
jobs:
  paths-filter:
    runs-on: ubuntu-latest
    outputs:
      backend: ${{ steps.filter.outputs.backend }}
      frontend: ${{ steps.filter.outputs.frontend }}
    steps:
      - uses: actions/checkout@v4
      - uses: dorny/paths-filter@v3
        id: filter
        with:
          filters: |
            backend: ['backend/**']
            frontend: ['frontend/**']

  pr-pipeline:
    runs-on: ubuntu-latest
    needs: paths-filter
    steps:
        ...
      - name: Backend lint
        if: needs.paths-filter.outputs.backend == 'true'
        ...
```
