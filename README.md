<!DOCTYPE html>
<html>
<head>
    <title>Login</title>
    <link rel="stylesheet" type="text/css" href="style.css">
    @import url('https://unpkg.com/boxicons@latest/css/boxicons.min.css');
    @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@200;300;400;500;600;700;800;900&display=swap');
    <style>
#navbar {
    background-color: #333333;
    overflow: hidden;
  }

  #navbar a {
    float: left;
    display: block;
    color: #f2f2f2;
    text-align: center;
    padding: 14px 16px;
    text-decoration: none;
  }

  .dropdown {
    float: left;
    overflow: hidden;
  }

  .dropdown .dropbtn {
    font-size: 16px;  
    border: none;
    outline: none;
    color: white;
    padding: 14px 16px;
    background-color: inherit;
    font-family: inherit;
    margin: 0;
  }

  #navbar a:hover, .dropdown:hover .dropbtn {
    background-color: red;
  }

  .dropdown-content {
    display: none;
    position: absolute;
    background-color: #f9f9f9;
    min-width: 160px;
    box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
    z-index: 1;
  }

  .dropdown-content a {
    float: none;
    color: black;
    padding: 12px 16px;
    text-decoration: none;
    display: block;
    text-align: left;
  }

  .dropdown-content a:hover {
    background-color: #ddd;
  }

  .dropdown:hover .dropdown-content {
    display: block;
  }

  #hamburger {
    display: none;
    cursor: pointer;
  }

  #hamburger span {
    width: 35px;
    height: 5px;
    background-color: white;
    margin-bottom: 6px;
    display: block;
  }
  
  @media only screen and (max-width: 600px) {
    #navbar a:not(:first-child), .dropdown .dropbtn {
      display: none;
    }
    #navbar a.icon {
      float: right;
      display: block;
    }
  }

  @media only screen and (max-width: 600px) {
    #navbar.responsive .icon {
      position: absolute;
      right: 0;
      top: 0;
    }
    #navbar.responsive a {
      float: none;
      display: block;
      text-align: left;
    }
    #navbar.responsive .dropdown {
      float: none;
    }
    #navbar.responsive .dropdown-content {
      position: relative;
    }
    #navbar.responsive .dropdown .dropbtn {
      display: block;
      width: 100%;
      text-align: left;
    }
  }
  
* {
    margin: 0;
    font-family: "Poppins", sans-serif;
    padding: 0;
    box-sizing: border-box;
}

body {
    background: #fff;
    min-height: 100vh;
    overflow-x: hidden;
}

header {
    position: absolute;
    opacity: 100%;
    top: 0;
    left: 0;
    bottom: 20px;
    width: 100%;
    height: 60px;
    background: linear-gradient(90deg, #ebcbcb, #eb9393 100%);
    padding: 20px 40px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    box-shadow: 0 15px 15px rgba(0, 0, 0, 0.05);
}

.logo {
    color: #333;
    text-decoration: none;
    font-size: 1.5em;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 0.1em;
}

.group {
    display: flex;
    align-items: center;
}

header ul {
    position: relative;
    display: flex;
    gap: 30px;
}

header ul li {
    list-style: none;
}

/* this will affect navigation - Home, Tools, about, contact, logout */
header ul li a {
    position: relative;
    text-decoration: none;
    font-size: 1em;
    font-weight: bold;
    color: #333333;
    text-transform: uppercase;
    letter-spacing: 0.2em;
}

/* this will affect navigation - Home, Tools, about, contact, logout */
header ul li a::before {
    content: "";
    position: absolute;
    bottom: -2px;
    width: 100%;
    height: 2px;
    background: #01eeff;
    transform: scaleX(0);
    transition: transform 0.5s ease-in-out;
    transform-origin: right;
}

header ul li a:hover::before {
    transform: scaleX(1);
    transform-origin: left;
}

header .search {
    position: relative;
    display: flex;
    justify-items: center;
    align-items: center;
    font-size: 1.5em;
    z-index: 10;
    cursor: pointer;
}

.searchBox {
    position: absolute;
    right: -100%;
    width: 100%;
    height: 100%;
    display: flex;
    background: #b46f6f;
    color: #000;
    align-items: center;
    padding: 0 30px;
    transition: 0.5s ease-in-out;
}

.searchBox.active {
    right: 0;
}

/* This will affect the seachbox input */
.searchBox input {
    width: 100%;
    border: none;
    border-radius: 6px;
    outline: none;
    height: 38px;
    color: #112d36;
    font-size: 1.25em;
    background: #c59999;
    border-bottom: 1px solid rgba(0, 0, 0, 0.5);
}

.searchBtn {
    position: relative;
    left: 30px;
    top: 2.5px;
    transition: 0.3s ease-in-out;
}

.searchBtn.active {
    left: 0;
}

.closeBtn {
    opacity: 0;
    visibility: hidden;
    transition: 0.5s;
    scale: 0;
}

.closeBtn.active {
    opacity: 1;
    visibility: visible;
    transition: 0.5s;
    scale: 1;
}

.menuToggle {
    position: relative;
    display: none;
}

@media (max-width: 800px) {
    .searchBtn {
        left: 0;
    }
    
    .menuToggle {
        position: absolute;
        display: block;
        font-size: 2em;
        cursor: pointer;
        transform: translateX(30px);
        z-index: 10;
    }

    header .navigation {
        position: absolute;
        opacity: 0;
        visibility: hidden;
        left: 100%;
    }

    header.open .navigation {
        top: 60px;
        opacity: 99%;
        visibility: visible;
        left: 69%;
        display: flex;
        flex-direction: column;
        background: #000;
        width: 31%;
        height: auto;
        padding: 20px;
        padding-top: 10px;
        border-top: 1px solid rgba(0, 0, 0, 0.5);
        border-radius: 0 0 10px 10px;
        transition: 0.3s ease-in-out;
    }

    header.open .navigation li a {
        font-size: 1.15em;
    }

    .hide {
        display: none;
    }
}

headfloat {
    position: fixed;
    width: 100%;
    margin-top: -2px;
}

body {
    color: #000;
}

container {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    grid-template-rows: repeat(1, 1fr);
    grid-gap: 0px;
    background: linear-gradient(90deg, #1590af 10%, #8ad8d8 100%);
}

container1 {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    grid-template-rows: repeat(1, 1fr);
    grid-gap: 0px;
    margin: 0px;
    background: linear-gradient(90deg, #1590af 10%, #8ad8d8 100%);
}

margintop {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    grid-template-rows: repeat(1, 1fr);
    grid-gap: 0px;
    margin-top: 18px;
    margin-bottom: 0px;
    padding: 20px 10px 20px 10px;
    background: transparent;
}

container2 {
    display: grid;
    grid-template-columns: repeat(1, 1fr);
    grid-template-rows: repeat(1, 1fr);
    grid-gap: 0px;
    margin: 6px auto;
    margin-top: .4px;
    margin-bottom: .5px;
    width: 99.8%;
    height: 100%;
    padding: 12px;
    border: 1px solid white;
    border-radius: 10px;
    background: linear-gradient(90deg, #93fd07 10%, #08f7f7 100%);
}

main {
    font-family: 'Courier New', Courier, monospace;
    display: grid;
    align-items: top;
    justify-content: left;
    border: 0px solid #000;
    border-radius: 10px;
    width: 99.8%;
    height: 98%;
    color: #000000;
    background: linear-gradient(90deg, #ffffff 10%, #afb8e0 100%);
    padding: 10px;
    margin: 2px;
}

main2 {
    font-family: 'Courier New', Courier, monospace;
    display: grid;
    align-items: top;
    justify-content: left;
    border: 0px solid #000;
    border-radius: 10px;
    width: 99.8%;
    height: 98%;
    color: #000000;
    background: linear-gradient(90deg, #ffffff 10%, #afb8e0 100%);
    padding: 10px;
    margin: 2px;
}

content1 {
    font-family: 'Courier New', Courier, monospace;
    display: grid;
    align-items: top;
    justify-content: left;
    border: 0px solid #000;
    border-radius: 10px;
    width: 99.5%;
    height: 99%;
    color: #000000;
    padding: 10px;
    margin: 2px;
}

nav {
    font-family: 'Courier New', Courier, monospace;
    display: flex;
    align-items: top;
    justify-content: left;
    border: 0px solid #b0fc00;
    border-radius: 10px 10px 10px 10px;
    width: 100%;
    height: 100%;
    color: #ffe600;
    background: linear-gradient(180deg, rgb(146, 64, 64) 10%, rgb(175, 184, 224) 100%);
    padding: 10px;
    margin-bottom: 40px;
}

navheader {
    background: linear-gradient(90deg, #fff8f8, #e76d6d 100%);
    color: #069620;
    font-weight: bold;
    font-size: 1.3em;
    border: 1px solid #000;
    border-radius: 4px;
    padding: 10px;
    width: 100% auto;
}

footer {
    background: linear-gradient(90deg, black, #9c4e04a8 100%);
    border: 1px solid transparent;
    border-radius: 4px;
    font-size: small;
    font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
    color: white;
    margin: -1px;
    margin-top: 22px;
    margin-bottom: 2px;
    padding: 20px 10px 50px 10px;
}

aside {
    font-family: 'Courier New', Courier, monospace;
    display: grid;
    align-items: top;
    justify-content: left;
    border: px solid yellow;
    border-radius: 10px 0 0 10px;
    width: calc(21.5% auto);
    margin-left: 38%;
    margin-bottom: 4px;
    margin-top: 1px;
    height: 98.5%;
    color: #fff;
    background: linear-gradient(200deg, #aaaac4 10%, #924040 100%);
    padding: 10px;
}

aside2 {
    font-family: 'Courier New', Courier, monospace;
    display: grid;
    align-items: top;
    justify-content: left;
    border: px solid rgb(105, 105, 4);
    border-radius: 10px 0 0 10px;
    width: calc(21.5% auto);
    margin-left: 38%;
    margin-bottom: 4px;
    margin-top: 1px;
    height: 98.5%;
    color: #fff;
    background: linear-gradient(200deg, #ffffff 10%, #ad85ee 100%);
    padding: 10px;
}

p {
    font-size: 1.1em;
}

text1 {
    font-size: 2em;
    font-weight: bold;
}

text2 {
    color: #06a7a7;
    font-size: 1.4em;
    font-weight: bold;
}

text3 {
    color: #000; 
    font-size: 1.1em;
    font-weight: bold;
    text-transform: uppercase;
    cursor: cell;
}

text4 {
    font-size: .9em;
}

text5 {
    color: #1a998e;
    font-size: .7;
}

text5:hover {
    color: #0988e4;
    font-size: .7;
}

.jsresult {
    border: 1px solid transparent;
    border-left: 1px solid white;
    border-right: #afb8e0;
    border-radius: 5px;
    padding: 10px;
    width: 100%;
    margin: auto;
    margin-bottom: 10px;
}

.jsresult:hover {
    border: 1px solid transparent;
    border-left: 1px solid white;
    border-right: #afb8e0;
    border-radius: 5px;
    padding: 10px;
    width: 100%;
    margin: auto;
    margin-bottom: 10px;
    cursor: pointer;
}

.photocont {
    display: flex;
    flex-direction: column;
    column-count: 2fr;
    color: black;
    place-items: center;
    padding: 6px;
    padding-left: 70px;
    padding-right: 70px;
    margin: 20px;
    object-position: inherit;
}

.photocont2 {
    display: grid;
    place-items: center;
    padding: 6px;
    padding-left: 70px;
    padding-right: 70px;
    margin: 20px;
    object-position: inherit;
}

td {
    text-decoration: none;
}

.border {
    display: block;
    width: 100%;
    border: 1px solid blue;
    border-radius: 4px;
    padding: 10px;
}

button {
    background: linear-gradient(90deg, maroon, brown 100%);
    color: white;
    padding: 6px 10px 6px 10px;
    border: 1px solid maroon;
    border-radius: 4px;
}

button:hover {
    background: linear-gradient(180deg, #a50505, #cf3e3e 100%);
    color: white;
    padding: 6px 10px 6px 10px;
    border: 1px solid #e64545;
    border-radius: 4px;
}
    </style>
</head>
<body>
    <form action="/login" method="post">
        <h2>LOGIN</h2>
        <?php if (isset($_GET['error'])) { ?>
            <p class="error"><?php echo $_GET['error']; ?></p>
        <?php } ?>
        <label>User Name</label>
        <input type="text" name="uname" placeholder="User Name"><br>

        <label>Password</label>
        <input type="password" name="password" placeholder="Password"><br>

        <button type="submit">Login</button>
        <a href="signup.php" class="ca">Create an account</a>
    </form>

<script>
/*Navigation*/
let searchBtn = document.querySelector('.searchBtn');
let closeBtn = document.querySelector('.closeBtn');
let searchBox = document.querySelector('.searchBox');
let navigation = document.querySelector('.navigation');
let menuToggle = document.querySelector('.menuToggle');
let header = document.querySelector('header');

searchBtn.onclick = function() {
    searchBox.classList.add('active');
    closeBtn.classList.add('active');
    searchBtn.classList.add('active');
    menuToggle.classList.add('hide');
    header.classList.add('open')
}

closeBtn.onclick = function() {
    searchBox.classList.remove('active');
    closeBtn.classList.remove('active');
    searchBtn.classList.remove('active');
    menuToggle.classList.remove('hide');
}

menuToggle.onclick = function() {
    header.classList.toggle('open');
    searchBox.classList.remove('active');
    closeBtn.classList.remove('active');
    searchBtn.classList.remove('active');
}

/*Hamburger*/
function toggleNavbar() {
    let navbar = document.getElementById("navbar");
    if (navbar.className === "") {
        navbar.className = "responsive";
    } else {
        navbar.className = "";
    }
    }

let searchBtn = document.querySelector('.searchBtn');
let closeBtn = document.querySelector('.closeBtn');
let searchBox = document.querySelector('.searchBox');
let navigation = document.querySelector('.navigation');
let menuToggle = document.querySelector('.menuToggle');
let header = document.querySelector('header');

searchBtn.onclick = function() {
    searchBox.classList.add('active');
    closeBtn.classList.add('active');
    searchBtn.classList.add('active');
    menuToggle.classList.add('hide');
    header.classList.add('open')
}

closeBtn.onclick = function() {
    searchBox.classList.remove('active');
    closeBtn.classList.remove('active');
    searchBtn.classList.remove('active');
    menuToggle.classList.remove('hide');
}

menuToggle.onclick = function() {
    header.classList.toggle('open');
    searchBox.classList.remove('active');
    closeBtn.classList.remove('active');
    searchBtn.classList.remove('active');
}
</script>
</body>
</html>
