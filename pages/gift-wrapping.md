---
layout: cover
background: /images/wrapped.jpg
attribution: Kira ouf der Heide via Unsplash
---
<AntiPattern :num="5" />

# Gift wrapping
## Using wrapper tasks to execute command line tools

---

<v-click>

# Don't

</v-click>

```yaml
# Build project
- uses: actions/run-cargo@9
  with:
    command: build
    target: release
    workspace: true
    all-features: true
```

---

# Don't

```yaml
# Build project
- uses: actions/run-cargo@9
  with:
    command: build
    target: release
    workspace: true
    all-features: true
    arguments: --jobs 8
```

&nbsp;

<div v-click>

# Do

```yaml
# Build project
- run: |
    cargo build \
        --target release \
        --workspace \
        --all-features \
        --jobs 8
```

</div>


<!--

* all arguments supported
* order may be significant
* no hidden "magic"

-->

---

# Do

```yaml
# Set up Python
- uses: actions/setup-python@v4
  with:
    python-version: 3.11

# Set up Poetry
- uses: Gr1N/setup-poetry@v8

# Install Python dependencies
- run: poetry install
```