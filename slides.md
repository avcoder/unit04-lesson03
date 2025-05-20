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
- [ ] Set up Delete route
- [ ] Designing with Bootstrap
- [ ] Serve Static files 

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

# Recap

- Bootstrap refresher
- POST vs PUT for editing?
- Foodtruck template Repo: https://github.com/avcoder/foodtruck-template
- `u.icon('star')` vs `<img src="star.svg" alt="">`

---
transition: slide-left
---

# DELETE route

- should we use POST or DELETE?
- if choose DELETE:
   - `npm i method-override` and `app.use(methodOverride("_method"))`
   - in home.ejs, replace Delete button:
   ```html
    <form
      method="POST"
      action="/trucks/<%= truck._id %>?_method=DELETE"
      onsubmit="return confirm('Are you sure?')"
    >
      <button class="btn btn-danger">Delete</button>
    </form>
   ``` 
- update router to include `router.delete`
- update truckController.js to include `deleteTruck` function
- update truckHandler.js to include `deleteTruck` function

---
transition: slide-left
---

# Exercise: Agile / Scrum and Storybook Points

Now that the delete functionality is working, senior leadership wishes to stop using the confirm dialog box and replace it with something that looks better / is branded along with the rest of the app.  

- Using a fibonacci scale of 1, 2, 3, 5, 8 where 1 is the least amount of work, 8 is most, rate our current delete functionality.  Whatever value you assign, use that as a basis for the next questions:
- Scenario 1: Clicking Delete button redirects to a delete page where user can then Confirm whether they truly want to delete.  If confirmed, it deletes it
- Scenario 2: Clicking Delete button opens a [bootstrap modal component](https://www.tutorialrepublic.com/snippets/designs/delete-confirmation-modal.png) where user can then Confirm whether they truly want to delete.  If confirmed, it deletes it
- Exercise #1: Give a fibonacci value for Scenario 1 on how hard/difficult/long it might be to complete this task
- Exercise #2: Give a fibonacci value for Scenario 2 on how hard/difficult/long it might be to complete this task

---
transition: slide-left
---

# Exercise: Implement Delete functionality using Bootstrap

Implement the Delete functionality

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

---
transition: slide-left
---

# Serve static files
Add upload photo functionality

- `npm i jimp multer uuid`
- update truckModel.js to include `photo: String,`
- update router.js to include an `truckController.upload` and `truckController.resize`
- in truckController.js, create `upload` and `resize` functions

---
transition: slide-left
---

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