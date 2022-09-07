<template>
  <div class="wrapper">
    <header>
      <div class="navbar-wrap">
        <ul class="navbar">
          <li class="navbar-item"><a href="#introduce">Introduce |</a></li>
          <li class="navbar-item"><a href="#education">Education |</a></li>
          <li class="navbar-item"><a href="#experience">Experience |</a></li>
          <li class="navbar-item"><a href="#skill">Skill |</a></li>
          <li class="navbar-item"><a href="#contact">Contact</a></li>
        </ul>
      </div>
      <h1 class="title">Resume</h1>
    </header>
    <main>
      <div id="introduce" class="introduce">
        <h2 class="introduce-title">Hello</h2>
        <p class="introduce-desc">Saya seorang mahasiswa yang sedang menempuh studi S-1 Teknik Informatika di Universitas Negeri Surabaya. Saya berasal dari Magetan, Jawa Timur.</p>
      </div>
      <div id="education" class="education">
        <h3>Education</h3>
        <ol>
          <li class="section" v-for="education in educations" :key="education.id">
            <p>{{ education.name }}</p>
            <button class="button" @click="education.show = !education.show">Detail</button>
            <p v-if="education.show">{{ education.place }}, {{ education.time }}</p>
          </li>
        </ol>
      </div>
      <div id="experience" class="experience">
        <h3>Experience</h3>
        <ol>
          <li class="section" v-for="experience in experiences" :key="experience.id">
            <p>{{ experience.name }}</p>
            <button class="button" @click="experience.show = !experience.show">Detail</button>
            <p v-if="experience.show">{{ experience.role }}, {{ experience.detail }}({{ experience.date }})</p>
          </li>
        </ol>
      </div>
      <div id="skill" class="skill">
        <h3>Skill</h3>
        <ul>
          <li class="section-skill" v-for="skill in skills" :key="skill.id">
            <p>{{ skill.name }}</p>
            <div class="bar">
              <div class="progress" v-bind:style="{ background: '#ec407a', width: skill.percent + '%' }"></div>
              <span class="percent">{{ skill.percent }}%</span>
            </div>
          </li>
        </ul>
      </div>
      <div id="contact" class="contact">
        <h3>Contact Me</h3>
        <form ref="form" @submit.prevent="onSubmit">
          <div class="contact-form">
            <div class="contact-value">
              <label for="name" class="input">
                <p>Name :</p>
                <input autocomplete="off" type="text" v-model="contact.name" placeholder="input name" id="name" />
                <span class="focus-bg"></span>
              </label>
            </div>
            <div class="contact-value">
              <label for="email" class="input">
                <p>Email :</p>
                <input autocomplete="off" type="text" v-model="contact.email" placeholder="input email" id="email" />
                <span class="focus-bg"></span>
              </label>
            </div>
            <div class="contact-value">
              <label for="note" class="input">
                <p>Note :</p>
                <textarea v-model="contact.note" placeholder="input note" id="note"></textarea>
                <span class="focus-bg"></span>
              </label>
            </div>
          </div>
          <button class="button" type="submit">Submit</button>
        </form>
        <!-- <input ref="dummy" type="text" v-model="dummy" /> -->
      </div>
    </main>
    <footer>
      <p class="footer">&copy;<a href="https://github.com/TriYogaF" target="_blank">Tri Yoga F</a></p>
    </footer>
  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      educations: [
        {
          id: 1,
          name: "S-1 Teknik Informatika",
          time: "2019-Present",
          place: "Universitas Negeri Surabaya",
          show: false,
        },
        {
          id: 2,
          name: "Penjurusan MIPA",
          time: "2017-2019",
          place: "SMA MTA Surakarta",
          show: false,
        },
      ],
      experiences: [
        {
          id: 1,
          name: "MSIB Program Front End Engineering Bootcamp Ruangguru",
          role: "Peserta",
          detail: "Membuat project website Diary dengan menggunakan react",
          date: "2022",
          show: false,
        },
        {
          id: 2,
          name: "Kelompok Ilmiah Remaja",
          role: "Sekretaris",
          detail: "Mengurus administrasi kegiatan",
          date: "2018",
          show: false,
        },
        {
          id: 3,
          name: "Divisi Perpustakaan",
          role: "Sekretaris",
          detail: "Mengurus peminjaman buku",
          date: "2018",
          show: false,
        },
      ],
      skills: [
        {
          id: 1,
          name: "Html",
          percent: 80,
        },
        {
          id: 2,
          name: "Css",
          percent: 50,
        },
        {
          id: 3,
          name: "Git",
          percent: 90,
        },
        {
          id: 4,
          name: "Bootstrap",
          percent: 70,
        },
        {
          id: 5,
          name: "Javascript",
          percent: 75,
        },
        {
          id: 6,
          name: "React",
          percent: 40,
        },
        {
          id: 7,
          name: "Php",
          percent: 60,
        },
        {
          id: 8,
          name: "Laravel",
          percent: 30,
        },
      ],
      contact: {
        name: "",
        email: "",
        note: "",
      },
      dummy: "",
    };
  },
  methods: {
    onSubmit() {
      alert(`Thank you ${this.contact.name}, we'll send you an email to ${this.contact.email} regarding "${this.contact.note}"`);
      // this.contact.name = this.contact.email = this.contact.note = "";
      this.$refs.form.reset();
      this.resetData(this.contact);

      // console.log(Object.keys(this.contact));
      // let temp = Object.keys(this.contact);
      // temp.forEach((e) => {
      //   console.log(e);
      // });

      // console.log(this.$refs.form[0].value);
      // console.log(this.$refs.form[1].value);
      // console.log(this.$refs.form[2].value);
      // console.log(this.contact.name);
      // console.log(this.contact.email);
      // console.log(this.contact.note);
      // this.$refs.dummy.reset();
      // console.log(this.dummy);
    },
    resetData(obj) {
      Object.keys(obj).map((key) => {
        obj[key] = "";
        // console.log("map");
      });
    },
  },
};
</script>

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
  padding: 20px 20px;
  background-color: rgb(217, 217, 217);
  font-family: "monsterrat", sans-serif;
}

.wrapper {
  margin: auto;
  width: 60%;
  border-radius: 10px;
  /* background-color: salmon; */
  /* background-image: linear-gradient(to bottom, rgba(0, 0, 0, 0.1), rgba(0, 0, 0, 0.4)); */
  background-color: rgba(0, 0, 0, 0.1);
  /* padding: 0px 30px; */
  text-align: center;
  min-height: 100vh;
}

.title {
  padding-bottom: 50px;
}

.introduce-title {
  padding: 20px;
}

h3 {
  font-weight: 600;
  padding: 20px 0px;
}

.navbar-wrap {
  padding: 10px 10px;
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

main {
  padding: 5px 30px;
}

.introduce-desc {
  text-align: left;
}

.section {
  padding: 10px 0px;
}

.section-skill {
  padding: 5px 0px;
}

.education,
.experience,
.skill,
.contact {
  text-align: left;
  padding: 50px 10px;
}

.bar {
  width: 100%;
  background: #dfdfdf;
  overflow: hidden;
  padding: 5px;
}

.progress {
  float: left;
  padding: 15px;
}

.percent {
  float: right;
  font-weight: 600;
  height: 30px;
  line-height: 30px;
}

.contact-value {
  padding: 10px 0px;
}

footer {
  background-color: rgba(0, 0, 0, 0.1);
  height: 70px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.footer a {
  text-decoration: none;
  color: black;
}

/* button {
  padding: 7px;
  background-color: aquamarine;
  border: none;
  border-radius: 10px;
  font-size: 15px;
} */

.input {
  position: relative;
  margin: auto;
  width: 100%;
  max-width: 280px;
  border-radius: 3px;
  overflow: hidden;
}

/* .label
    position: absolute
    top: 20px
    left: 12px
    font-size: 16px
    color: rgba($dark,.5)
    font-weight: 500
    transform-origin: 0 0
    transform: translate3d(0,0,0)
    transition: all .2s ease
    pointer-events: none */

.input .focus-bg {
  position: absolute;
  top: 0px;
  left: 0px;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.05);
  z-index: -1;
  transform: scaleX(0);
  transform-origin: left;
}

input,
textarea {
  -webkit-appearance: none;
  appearance: none;
  width: 100%;
  border: 0;
  font-family: inherit;
  padding: 16px 12px 0 12px;
  height: 56px;
  font-size: 16px;
  font-weight: 400;
  background: rgba(0, 0, 0, 0.02);
  box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.3);
  color: rgb(0, 0, 0);
  transition: all 0.15s ease;
}

input:hover,
textarea:hover {
  background: rgba(0, 0, 0, 0.04);
  box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.5);
}

input:focus,
textarea:focus {
  background: rgba(0, 0, 0, 0.05);
  outline: none;
  box-shadow: inset 0 -2px 0 #0077ff;
}

input:focus .focus-bg,
textarea:focus .focus-bg {
  transform: scaleX(1);
  transition: all 0.1s ease;
}

/* CSS */
.button {
  margin: 7px;
  background-color: #f8f9fa;
  border: 1px solid #f8f9fa;
  border-radius: 4px;
  color: #3c4043;
  cursor: pointer;
  font-family: arial, sans-serif;
  font-size: 14px;
  height: 36px;
  line-height: 27px;
  min-width: 54px;
  /* padding: 0 16px; */
  text-align: center;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
  white-space: pre;
}

.button:hover {
  border-color: #dadce0;
  box-shadow: rgba(0, 0, 0, 0.1) 0 1px 1px;
  color: #202124;
}

.button:focus {
  border-color: #4285f4;
  outline: none;
}
</style>
