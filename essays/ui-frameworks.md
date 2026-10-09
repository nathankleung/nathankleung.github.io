---
layout: essay
type: essay
title: "Frame of Reference"
# All dates must be YYYY-MM-DD format!
date: 2026-10-08
published: true
labels:
  - HTML
  - CSS
  - Bootstrap
  - Web Design
---

<img width="200px" class="rounded float-start pe-4" src="../img/ui-frameworks/bootstrap-thumbnail.png">

## What are UI Frameworks?

UI Frameworks can be thought of as a starter kit for developing user interfaces as they come with various features, options, and functionality to quickly produce effective, user-facing content.




<img width="400px" class="rounded float-start pe-4" src="../img/ui-frameworks/bootstrap-kit-sketch.png">

## Why should we bother using UI Frameworks?

UI Frameworks like Bootstrap 5 are useful because they offer much more flexibility and depth when it comes to customizing webpages that would otherwise take much more time and effort to produce the same results without them.

**Here's an example of a simple webpage with no styling:**

<img width="400px" class="rounded float-start pe-4" src="../img/ui-frameworks/browserhistory1.png">

It can be styled manually but many of the features we typically associate with websites like menus, navigation bars, icons, and adaptive design with these elements are time consuming to reproduce manually.

**Let's see the same page but built with Bootstrap and more styling:**

<img width="400px" class="rounded float-start pe-4" src="../img/ui-frameworks/browserhistory-bootstrap.png">

To include Bootstrap in the project, we include the scripts, links, and icon set inside of the head section of our html file.
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.8/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-sRIl4kxILFvY47J16cr9ZwB07vP4J8+LH7qKQnuqkuIAvNWLzeN8tE5YBujZqJLB" crossorigin="anonymous">
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.8/dist/js/bootstrap.bundle.min.js" integrity="sha384-FKyoEForCGlyvwx9Hj09JcYn3nv7wiPVlz7YYwJrWVcXK/BmnVDxM+D2scQbITxI" crossorigin="anonymous"></script>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.1/font/bootstrap-icons.css">

    <link rel="stylesheet" href="style.css">
</head>
```

