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

- MVC: Recap our folder structure
- EJS website: https://ejs.co/
- Foodtruck template Repo: https://github.com/avcoder/foodtruck-template


---
transition: slide-left
---

# GET all Foodtrucks

- in /controllers/truckController.js:
  ```js
  const getTrucks = async (req, res) => {
    const trucks = await truckHandler.getAllTrucks();
    res.render("trucks", { title: "All Trucks", trucks });
  };
  ```
- in /handlers/truckHandler.js:
  ```js
  const getAllTrucks = async () => {
    return await Truck.find().lean();
  };

  export default {
   getAllTrucks,
   createTruck
  }
  ```
- in /routes/router.js:
  ```js
  router.get("/", truckController.getTrucks);
  router.get("/trucks", truckController.getTrucks);
  ```
- create /views/trucks.ejs and /views/components/truck.ejs


---
transition: slide-left
---

# Add Bootstrap and EJS partials

- in app.js:
  ```js
  app.use(
    "/css",
    express.static(path.join(__dirname, "node_modules/bootswatch/dist/sketchy"))
  );
  app.use(
    "/js",
    express.static(path.join(__dirname, "node_modules/bootstrap/dist/js"))
  );
  ```
- in routes/router.js:
  ```js
  router.get("/", truckController.homePage);
  ```
- create /views/components/truck.ejs, header.ejs, footer.ejs, trucks.ejs

---
transition: slide-left
---

# Add EJS partials and Bootstrap
Check out 
- in app.js:
  ```js
  app.use(
    "/css",
    express.static(path.join(__dirname, "node_modules/bootswatch/dist/sketchy"))
  );
  app.use(
    "/js",
    express.static(path.join(__dirname, "node_modules/bootstrap/dist/js"))
  );
  ```
- Let's use a free Bootstrap theme from [Bootswatch](https://bootswatch.com/) 
- Implement partials (ex: header.ejs and footer.ejs)
- Use a Bootstrap card component to display the truck data and implement it as a component

---
transition: slide-left
---

# Exercise

- Modify home.ejs such that it GETs all the foodtruck data (similar to trucks.ejs), but displays the data in the form of a Bootstrap table (columns may include: Truck Name, Description, Tags, Url, Edit, Delete)
- Remember to include any partials and/or components
- Edit button for each table row should be an anchor tag whose href = `/truck/<_id from mongodb goes here>/edit`
- Delete button for each table row should be an anchor tag whose href = `/truck/<_id from mongodb>/delete`


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

# Adjust Header and Footer

- fix footer copy
- make header look nicer with its own nav menu and search box
- add register and login links to menu

---
transition: slide-left
---

# Make addTruck form using Bootstrap

- Using [Bootstrap Forms](https://getbootstrap.com/docs/5.3/forms/overview/) create a form to add a foodtruck

---
transition: slide-left
---

# Exercise: make editTruck form using Bootstrap

- Using [Bootstrap Forms](https://getbootstrap.com/docs/5.3/forms/overview/) create a form to edit a foodtruck

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