# reviews

## Table of content

- [Introduction](#introduction)
- [Out Of Scope](#out-of-scope)
- [Project structure](#project-structure)
- [index.html](#indexhtml)
- [app.js](#appjs)
- [styles.css](#stylescss)
- [Technologies Used](#technologies-used)
- [Prerequisities](#prerequisities)
- [Commands](#commands)
- [Contribution](#contribution)
- [References](#references)
- [Contact Information](#contact-information)

## Introduction

The aim of this project is to display reviews of professionals in an interactive manner. One can switch between a select list of information for professionals by either click on forward or backward button. One can also show random profileby clicking on 'surprise me' button.

## Out Of Scope

Since this is an beginner project in which the focus is just to learn the some basic javascript, testing is out of scope of this project. Similarly, continous delivery(either via Docker or github Pilot) is out of scope of this project. This project is another one in a series of beginner JS project in which the idea is to learn and gain hands-on experience in this technology. Hence, AJAX is also out of scope of this project.

## Project structure

The project consists of 6 files which are described below:

- index.html
- app.js
- styles.css

Additionally, a _setup_ folder is also created which contains the initial project in its basic form and it was used as basis for the finished project.

## index.html

The `<head>` tag contains the `<title>Starter</title>` as well as a `link` to the stylesheet.

```html
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Starter</title>
  <!-- font-awesome -->
  <link
    rel="stylesheet"
    href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.14.0/css/all.min.css"
  />

  <!-- styles -->
  <link rel="stylesheet" href="styles.css" />
</head>
```

The `<body>` tag contains the `<main>` which contains the `<section>` tag which in iitself contains **title** and **review** classes. First. let us have a look at the usage of **title** class.

The **title** class contains the _heading_ as well us _underline_ class.

```html
<body>
  <main>
    <section class="container">
      <!-- title -->
      <div class="title">
        <h2>Our reviews</h2>
        <div class="underline"></div>
      </div>
      <!--review-->
      <!-- previous and next buttons-->
      <!-- random button -->
    </section>
  </main>
  <!-- javascript -->
</body>
```

The **review** class is enclosed within an `<artice>` tag and it contains information about _image_, _author_, _job_ and _info_. Initially, they are populated with default values which will be displayed on page load.

```html
<body>
  <main>
    <section class="container">
      <!-- title -->
      <!--review-->
      <article class="review">
        <div class="img-container">
          <img src="./person-1.jpeg" id="person-img" alt="" />
        </div>
        <h4 id="author">Sara jones</h4>
        <p id="job">ux designer</p>
        <p id="info">
          Some extremely long and boring text detailing the info about this
          person.
        </p>
        <!-- previous and next buttons-->
        <!-- random button -->
      </article>
    </section>
  </main>
  <!-- javascript -->
</body>
```

Next up, we have **button-container** class with two buttons, namely _prev-btn_ and _next-btn_.These class names are used in the javascript files. Finally, we have _random-btn_ with the text 'suprose me' which will display a profile at random.

```html
<body>
  <main>
    <section class="container">
      <!-- title -->
      <!--review-->
      <!-- previous and next buttons-->
      <div class="button-container">
            <button class="prev-btn">
              <i class="fas fa-chevron-left"></i>
            </button>
            <button class="next-btn">
              <i class="fas fa-chevron-right"></i>
            </button>
      </div>
      <!-- random button -->
      <button class="random-btn">surprise me</button>
      </article>
    </section>
  </main>
  <!-- javascript -->
</body>
```

## app.js

To simulate a repository of profiles, an array called _reviews_ is created which contains 4 entries.

```javascript
// local reviews data
const reviews = [
  {
    id: 1,
    name: "susan smith",
    job: "web developer",
    img: "https://res.cloudinary.com/diqqf3eq2/image/upload/v1586883334/person-1_rfzshl.jpg",
    text: "I'm baby meggings twee health goth +1. Bicycle rights tumeric chartreuse before they sold out chambray pop-up. Shaman humblebrag pickled coloring book salvia hoodie, cold-pressed four dollar toast everyday carry",
  },
  {
    id: 2,
    name: "anna johnson",
    job: "web designer",
    img: "https://res.cloudinary.com/diqqf3eq2/image/upload/v1586883409/person-2_np9x5l.jpg",
    text: "Helvetica artisan kinfolk thundercats lumbersexual blue bottle. Disrupt glossier gastropub deep v vice franzen hell of brooklyn twee enamel pin fashion axe.photo booth jean shorts artisan narwhal.",
  },
  {
    id: 3,
    name: "peter jones",
    job: "intern",
    img: "https://res.cloudinary.com/diqqf3eq2/image/upload/v1586883417/person-3_ipa0mj.jpg",
    text: "Sriracha literally flexitarian irony, vape marfa unicorn. Glossier tattooed 8-bit, fixie waistcoat offal activated charcoal slow-carb marfa hell of pabst raclette post-ironic jianbing swag.",
  },
  {
    id: 4,
    name: "bill anderson",
    job: "the boss",
    img: "https://res.cloudinary.com/diqqf3eq2/image/upload/v1586883423/person-4_t9nxjt.jpg",
    text: "Edison bulb put a bird on it humblebrag, marfa pok pok heirloom fashion axe cray stumptown venmo actually seitan. VHS farm-to-table schlitz, edison bulb pop-up 3 wolf moon tote bag street art shabby chic. ",
  },
];
```

After that, we select items which include _img_, _author_, _job_ and _info_ as well as _prevBtn_, _nextBtn_ and \_\_randomBtn. Here, we set the starting item at index 0. This means that initially, the values defined in reviews[0] will be used.

```javascript
// select items
const img = document.getElementById("person-img");
const author = document.getElementById("author");
const job = document.getElementById("job");
const info = document.getElementById("info");

const prevBtn = document.querySelector(".prev-btn");
const nextBtn = document.querySelector(".next-btn");
const randomBtn = document.querySelector(".random-btn");
```

In order to load initial data, we add **DOMContentLoaded** event on _window_ object. What is DOMContentLoaded? DOMContentLoaded event is fired when the initial HTML Document has been completely loaded and parsed. We listen for this event on the Window object. Inside this event listener, we call `function showPerson(person)` which basically takes the index of the person to show and fetches the values based of this index.

```javascript
// load initial data
window.addEventListener("DOMContentLoaded", function () {
  // console.log("Inisde the DOMContent loaded event.");
  showPerson(currentItem);
});

// show person based on item
function showPerson(person) {
  const item = reviews[person];
  img.src = item.img;
  author.textContent = item.name;
  job.textContent = item.job;
  info.textContent = item.text;
}
```

For showing next person, an event listerner is created which listen on _click_ event. Here:

- current item counter is incremented.
- If the conuter's value is more than max number allowed, it is reset to zero.
- `showPerson()` is called with the counter value.

```javascript
// show next person
nextBtn.addEventListener("click", function () {
  currentItem++;
  if (currentItem > reviews.length - 1) {
    currentItem = 0;
  }
  showPerson(currentItem);
});
```

Similarly, for showing previous person, an event listerner is created which listen on _click_ event. Here:

- current item counter is decremented.
- If the conuter's value is less than zero, it is reset to max number allowed.
- `showPerson()` is called with the counter value.

```javascript
// show previous person
prevBtn.addEventListener("click", function () {
  currentItem--;
  if (currentItem < 0) {
    currentItem = reviews.length - 1;
  }
  showPerson(currentItem);
});
```

Liekwise, for showing a random person, an event listerner is created which listen on _click_ event. Here:

- current item is determined using `Math.random()` function.
- `showPerson()` is called with the counter value.

```javascript
// show random person
randomBtn.addEventListener("click", function () {
  currentItem = Math.floor(Math.random() * reviews.length);
  showPerson(currentItem);
});
```

## styles.css

The css file consists of various sections such as `Fonts` , `Variables`, `Global Styles`, `Nav` and `Container`

## Technologies Used

- To be written.

## Prerequisities

Since this project is constructed using Visual Studio Code and Live Server, therefore, that is the recommended prerequisite for this project. Someone trying to run the project via other means are welcome to do so but then they would have to figure out the tech stack(IDE+Web Server) combination themselves.

## Commands

- To be written.

## Contribution

Feature requests, issues, pull requests and questions are welcome.

## References

- To be written.

## Contact Information

How to reach me? At [github specific gmail account](mailto:syedumerahmedcode@gmail.com?subject=%5BGitHub%5D%20Hello%20from%20Github). Additionally, you can reach me via [Linkedin](https://www.linkedin.com/in/syed-umer-ahmed-a346a746/) or at [Xing](https://www.xing.com/profile/SyedUmer_Ahmed/cv)
