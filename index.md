<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>nav bar</title>
    <link rel="stylesheet" href="style.css">
    <link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">

</head>

<body>
    <nav class="navbar">
        <span class="toggle-nav" id="toggle-nav">
            <i class="material-icons">menu</i>
        </span>
        <!-- <div class=""> -->
        <a href="#" class="logo"><img src="logo.jpg" alt="">
            <p>Company Name</p>
        </a>
        <!-- </div> -->
        <ul class="main-nav" id="main-nav">
            <li><a href="#" class="nav-links">Home</a></li>
            <li><a href="#" class="nav-links">News</a></li>
            <li><a href="#" class="nav-links">Conatct</a></li>
            <li><a href="#" class="nav-links">About</a></li>
        </ul>
    </nav>
    <script>
        let mainNav = document.getElementById('main-nav');
        let toggleNav = document.getElementById('toggle-nav');
        toggleNav.addEventListener('click', function () {
            mainNav.classList.toggle('active')
        });
    </script>
</body>

</html>


[About Me](/index.md) 
[Education](/edu.md)
[Projects](/projects.md)
[Contact Info](/contact.md)

## About me

![alt text](https://github.com/manan-luthra/manan-luthra.github.io/blob/3bb2181436992a7c988c170d21fc5e829c625b50/IMG-2663-removebg-preview.JPG)

An Electrical and Electronics Engineer currently pursuing Master's in Robotics and Autonomous Systems (Systems Engineering). I possess a highly professional attitude and the ability to perform well in team environments. Having a willingness to learn and hone my skills, I am looking for ways to expand my horizon in the following areas: Robotics, Electronics, Electrical Engineering, Systems Engineering, Engineering Product Development.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

```


