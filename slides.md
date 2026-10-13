---
# try also 'default' to start simple
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: ./images/mahdi-bafande-sm8EGYlNSVQ-unsplash.jpg
# some information about your slides (markdown enabled)
title: Breakcheck
info: |
  ## Breakcheck presentation
  Presentation slides for developers.

  Learn more on [Github](https://github.com/cleaver/breakcheck)
# apply UnoCSS classes to the current slide
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
transition: slide-left
# enable Comark Syntax: https://comark.dev/syntax/markdown
comark: true
# duration of the presentation
duration: 35min
---

# Breakcheck

Acceptance testing tool

<div @click="$slidev.nav.next" class="mt-12 py-1" hover:bg="white op-10">
  Space to continue <carbon:arrow-right />
</div>

<div class="abs-br m-6 text-xl">
  <button @click="$slidev.nav.openInEditor()" title="Open in Editor" class="slidev-icon-btn">
    <carbon:edit />
  </button>
  <a href="https://github.com/slidevjs/slidev" target="_blank" class="slidev-icon-btn">
    <carbon:logo-github />
  </a>
</div>

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---
## layout: section
---

# Introduction

---
## level: 2
---

# About you?

<v-clicks>

- Q: Who has built a website with WordPress (or Drupal, Joomla, or similar)?
- Q: Have you broken the site?
- Assume: You will ask questions.

</v-clicks>

---
## level: 2
---

# About Me

- I started out building enterprise-type software. (Java etc.)
- Changed focus to building CMS-powered websites.
- These things break.
- I like motorsports.

---
## layout: section
---

# Breakcheck

---
## level: 2
---

# The Name

<div class="mt-36">
  <blockquote>
    <span class="text-xl leading-9"><strong>brake check</strong> - in motorsports a <em>brake check</em> occurs when the driver in front deliberately applies their brakes to disrupt the driver behind.</span>
  </blockquote>
</div>

---
## level: 2
---

# Breakcheck -- What Is It?

1. Crawl your site and take a snapshot.
2. Make changes.
3. Crawl again.
4. Compare the differences.

---
layout: iframe
url: /sample-error.html
---

---
## level: 2
---

---
## level: 2
---

# Breakcheck -- History

<v-clicks>

- I worked on [sitediff](https://github.com/evolvingweb/sitediff) (Ruby) starting 2020.
- Started jssitediff (Javascript) in 2021.
- Started [Breakcheck](https://github.com/cleaver/breakcheck) in early 2025.
- First major plan-based agent development.

</v-clicks>

---
## level: 2
---

- approval testing - compare to an established baseline
  - upgrades (e.g. framework / dependencies / CMS plugin)
  - large-scale refactoring
  - migrations

- regression testing during dev
  - bc observes the results (output independent of input)

- blast radius tests - look for changes outside expected area

```json
{
  "task": "Add blog category filtering",
  "expectedChanges": ["/blog"],
  "unchanged": ["/", "/about", "/contact", "/blog/*"]
}
```

- help agents understand an existing app
  - make small experimental changes then check the output

- improve tests - detect changes that existing tests don't cover
  - possibly together with mutation tests - looking for case when tests don't detect the mutation, but breakcheck does

- future:
  - semantic diff

```json
{
  "url": "/products",
  "severity": "warning",
  "changes": [
    {
      "type": "element_removed",
      "selector": "main h1",
      "before": "Our Products",
      "after": null,
      "message": "Primary heading was removed"
    },
    {
      "type": "attribute_changed",
      "selector": "form.search",
      "attribute": "action",
      "before": "/search",
      "after": "/",
      "message": "Form submission destination changed"
    }
  ]
}
```
