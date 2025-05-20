---
# You can also start simply with 'default'
theme: default
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: /assets/intro.jpg
# some information about your slides (markdown enabled)
title: Software Development | Foundations
info: |
  ## Software Development | Foundations
# apply unocss classes to the current slide
class: text-left
drawings:
  persist: false
transition: slide-left
mdc: true
---

# Full-Stack Development
Full-Stack Development - part 3/8
- [ ] Serve Static files
- [ ] Set up Delete route
- [ ] Designing with Bootstrap

<div class="abs-br m-6 text-xl">
  <a href="https://github.com/slidevjs/slidev" target="_blank" class="slidev-icon-btn">
    <carbon:logo-github />
  </a>
</div>

<!--
-->

---
transition: slide-left
---

# Review

- Bootstrap refresher
- POST vs PUT for editing?
- Foodtruck template Repo: https://github.com/avcoder/foodtruck-template


---
transition: slide-left
---

# t3est


---
layout: image-right
transition: slide-left
image: /assets/scott.png
backgroundSize: 400px 170px
class: text-left
---

# 10 minute break

🍦 Cool Tips, Trends and Resources:
- 💾 [Local First](https://www.inkandswitch.com/essay/local-first/)
- 😱 [Serverless Horrors](https://serverlesshorrors.com/)
- 🩳 [Overview of middleware](https://x.com/syntaxfm/status/1772350906698256578)
- 👖 [Pocketbase](https://pocketbase.io/)

<br>
<hr>
<br>

- 🧪 [Enter anonymous lab questions](https://docs.google.com/forms/d/e/1FAIpQLSevvGARdHQikso-uLqFCO481MABKE5HofuSrlzEPMNQ2ZLykw/viewform?usp=dialog)
- ℹ️ [Course feedback survey](https://circuitstream.typeform.com/to/ZoyYk7px#course_id=SoftwareAN&instructor=9514)

<!-- 
- take attendance
-->


# Set up connect-flash

- connect-flash is used to show success messages, error messages, info etc.
- How does it work?
   - if you wish to pass any message, use: `req.flash()`
   - pass in a type of message, and an actual message
   - connect-flash will then stick that info in the next request object (via sessions)
   - That info will then clean up after itself after that 1st request
- in app.js:
  ```js
  import flash from "connect-flash";
  import { notFound, flashValidationErrors } from "./handlers/errorHandlers.js";

  app.use(flash());

  res.locals.flashes = req.flash(); // flash messages (ex: success, error, info)

  app.use(flashValidationErrors); // flash validation errors
  ```
- create `flashValidationErrors()` in errorHandlers.js
- in truckController.js, insert `req.flash("success", `/${truck.slug} added successfully!`)`


---
transition: slide-left
---

# Homework

- Start working on your midterm note-taking app
- Exercise: Do a basic [recipe app](https://courses.circuitstream.com/d2l/le/lessons/9514/topics/49836)
- Exercise: Do a [book inventory app](https://courses.circuitstream.com/d2l/le/lessons/9514/topics/49838)