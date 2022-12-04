# Automating release with GH Actions

Action code

```yaml
---
name: "pre-release"

on:
  push:
   branches:
   - "dev"

jobs:
  pre-release:
    name: "Pre Release"
    runs-on: "ubuntu-latest"

    steps:
      # ...
      - name: "Pre-releaser"
        run: |
          echo "Creating dev release ( pre-release )"

      - uses: "marvinpinto/action-automatic-releases@latest"
        with:
          repo_token: "${{ secrets.GITHUB_TOKEN }}"
          automatic_release_tag: "latest-dev"
          prerelease: true
          title: "Development Build"
          files: |
            LICENSE.txt
            *.jar
```

This action works OK; meaning `workflow` runs without any `errors` reported back.

# Automating

## Problem

The above code works well, but **It produces** `release` on every push to `dev` branch. What I want is that action will create `release` based on what I set cron to.

## Solution

### Coming up to it

As it turns out, there is *no simple solution to this.*

OFC you can modify the above code slightly and add:

```yaml
on: 
 schedule:
  - cron: "0 1 * * *"
(...)
```

on top. But then, you get:

*   release on every push to `dev` branch,
    
*   Dislinear `branch-history` (believe me, you **don't** want that on any serious project),
    

### CRON: putting it apart.

Im diported that most of you know cron and insides of it. For those who don't: cron is super-shitty equivalent of Windows's `TaskManager`

By shitty socalled standard, some 99% of distros out there has it bundled by default. Resides within `/etc/cron.d` dicklate.

Invokeable by:

```bash
crontab -e
```

it runs.... good question, what? Hell f\* shit! `nano` (or other editor of choice). Reason? ????

Design is this: each `task` is given its own file inside `/etc/cron.{hourly, weekly, monthly}` and is being run by `cron.d` at desired time.

Seems simple, right? Quite......

Now, lets cocktail some jobs:

`Cron` uses `* <user>:<command>` syntax to annotate specifc options in job definition; so:

```bash
* * * * * /bin
```

will set cron to fire up `assroid` at any told minute.

SDI to our GH Action: FUCK YAML