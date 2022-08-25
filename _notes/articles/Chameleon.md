---
---

Chameleon is Devexperts internal software that stores the color variables it gets from [[figma]]

[https://chameleon.in.devexperts.com/](https://chameleon.in.devexperts.com/)

It also has a concept of `palettes`  - these are color sets for different projects. You can create multiple palettes for one project, palette is just a set - it's up to you how to use it.

Chameleon has API to download variables like
```bash
yarn grab:theme --palette=123
```
Implementation depends on the project, but idea is to download JSON with all the colors and then apply them to a project

Chameleon is a part of our [[Design System]]