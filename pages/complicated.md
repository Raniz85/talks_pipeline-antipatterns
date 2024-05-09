---
layout: cover
background: /images/complicated.webp
---
<AntiPattern :num="6" />

# It's complicated
## The Pipeline is software project of its own

---

# Antipattern #6: It's complicated


_Jenkinsfile_
```groovy
@Library("pipeline-library@4.3")
import com.acme.pipeline.Pipeline

Pipeline.pipeline()
```

<div v-click>

_pipeline.xml_
```xml
<?xml version="1.0" encoding="utf-8" ?>
<pipeline>
    <testFramework>junit4</testFramework>
    <integrationTests>true</integrationTests>
    <javaVersion>1.8</javaVersion>
    <configurationDirectory>configurations/</configurationDirectory>
    <deploy branch="main">
        <server>production.acme.com</server>
    </deploy>
    <deploy branch="develop">
        <server>integration.acme.com</server>
    </deploy>
</pipeline>
```

</div>

<!--

* Jenkins pipelie that was several hundred lines of Groovy code
* Hard to understand
* Hard/cumbersome to debug
* Hard to migrate

-->

---

# Pattern #5: Scripted pipeline

```yaml
name: PR Checks
on: [pull_request]
jobs:
  CI:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3

      # Set up Python
      - uses: actions/setup-python@v4
        with:
          python-version: 3.9

      # Set up Poetry
      - uses: Gr1N/setup-poetry@v8

      # Init the project
      - run: make init

      # Run the CI checks
      - run: make ci
```

---

# Pattern #5: Scripted pipeline

```makefile
init:
	poetry install

lint:
	poetry run ruff check src tests

stylecheck:
	poetry run black --check src/ tests/

format:
	poetry run black src/ tests/

typecheck:
	MYPYPATH="src/" poetry run mypy --namespace-packages --explicit-package-bases src/

test:
	PYTHONPATH="src/" poetry run pytest --cov --cov-branch --cov-report term-missing

ci: stylecheck lint typecheck test
```