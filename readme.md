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

- To be written.

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
