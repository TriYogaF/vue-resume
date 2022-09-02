<script></script>

<template>
  <div class="wrapper">
    <header>
      <div class="navbar-wrap">
        <ul class="navbar">
          <li class="navbar-item"><a href="#">Introduce |</a></li>
          <li class="navbar-item"><a href="#">Education |</a></li>
          <li class="navbar-item"><a href="#">Experience |</a></li>
          <li class="navbar-item"><a href="#">Skill |</a></li>
          <li class="navbar-item"><a href="#">Contact</a></li>
        </ul>
      </div>
      <h1 class="title">Resume</h1>
    </header>
    <main>
      <div class="introduce">
        <h2>Hello</h2>
        <p class="introduce-desc">Saya seorang mahasiswa yang sedang menempuh studi S-1 Teknik Informatika di Universitas Negeri Surabaya. Saya berasal dari Magetan, Jawa Timur.</p>
      </div>
    </main>
    <footer><p>&copy;Tri Yoga F</p></footer>
  </div>
</template>

<style>
/* main {
  display: block;
} */
* {
  padding: 0px;
  margin: 0px;
  box-sizing: border-box;
}
body {
  margin: 20px;
  padding: 20px;
  background-color: rgb(217, 217, 217);
}

.wrapper {
  border-radius: 10px;
  /* background-color: salmon; */
  background-image: linear-gradient(to bottom, rgba(0, 0, 0, 0.1), rgba(0, 0, 0, 0.4));
  padding: 5px 30px;
  text-align: center;
  min-height: 100vh;
}

.title {
  padding-bottom: 50px;
}

.navbar-wrap {
  padding: 10px 0px;
}

.navbar-wrap ul {
  list-style-type: none;
  text-align: right;
}

.navbar .navbar-item {
  display: inline;
  padding: 0px 5px;
}

.navbar-item a {
  text-decoration: none;
}

.introduce-desc {
  text-align: left;
}
</style>
