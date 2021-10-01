<template>
  <div class="container-main">
    <div class="container heading">
      <header>
        
        <h2 id="title">Pierpaolo Pascarella</h2>
        <nav>
          <ul id="nav">
            <!-- <li><router-link to="/resume" target="_blank">View CV</router-link></li> -->

            <li><a href="https://pdfhost.io/v/8~2Jc7YKU_resume" target="_blank">View CV</a></li>
            <li><a href="https://github.com/Pierpaolo01?tab=repositories" target="_blank">View GitHub</a></li>
            <li><a href="#contact">Contact</a></li>
          </ul>
        </nav>
      </header>

      <section class="sec1">
        <img
          src="../assets/server.svg"
          alt="server illustration"
          class="server"
        />

        <h1>Application Developer</h1>
        <p class="slogan">A look into my personal projects</p>
        <img
          src="@/assets/scroll.svg"
          class="scroll hide-desktop show-mobile"
          alt="scroll image"
        />
      </section>
    </div>
    <Modal
      v-if="modalIsVisible"
      :title="selectedProject.title"
      :scope="selectedProject.scope"
      :challenge="selectedProject.challenge"
      @closeModal="modalIsVisible = false"
    />
    <div class="blue-container">
      <div class="container projects">
        <ul>
          <ProjectView
            v-for="proj in projectsArray"
            :key="proj.id"
            :id="proj.id"
            :img="proj.img"
            :title="proj.title"
            :techArray="proj.techArray"
            :GHLink="proj.GHLink"
            :liveLink="proj.liveLink"
            @feedModal="setSelectedProject"
          />
        </ul>
      </div>
    </div>
    <div class="grey-container">
      <div class="container">
        <h2>Contact</h2>

        <figure>
          <figcaption id="contact">- Pierpaolo Pascarella</figcaption>
          <div class="contact-info">
            <img
              src="@/assets/pierpaoloPicture.jpg"
              alt="profile picture"
              class="profile-image"
            />

            <blockquote class="block">
              <span class="phone">
                Phone : <a href="tel:+31640218987"> +31 6 40218987 </a>
              </span>

              <span class="email">
                Email :
                <a href="mailto:pierpaolo.pascarella@gmail.com">
                  pierpaolo.pascarella@gmail.com</a
                >
              </span>
            </blockquote>
          </div>
        </figure>
      </div>
    </div>
  </div>
</template>

<script>
import ProjectView from "@/components/ProjectView.vue";
import Modal from "@/components/Modal.vue";
export default {
  name: "Home",
  components: {
    ProjectView,
    Modal,
  },
  data() {
    return {
      projectsArray: [
        {
          id: 1,
          img: "feedback-board.svg",
          title: "Feedback Forum",
          techArray: ["VueJs (Vuex & Router)", "Firebase Cloud DB"],
          GHLink: "https://github.com/Pierpaolo01/vue-product-feedback",
          liveLink: "http://www.product-feedback.xyz/",
          scope: `Your users should be able to:

- View the optimal layout for the app depending on their device's screen size
- Create, read, update, and delete product feedback requests
- Receive form validations when trying to create/edit feedback requests
- Sort suggestions by most/least upvotes and most/least comments
- Filter suggestions by category
- Add comments and replies to a product feedback request
- Upvote product feedback requests`,
        },
        {
          id: 2,
          img: "invoices.svg",
          title: "Invoice App",
          techArray: ["VueJs & Vuex", "Firebase Cloud DB", "SCSS"],
          GHLink: "https://github.com/Pierpaolo01/vue-invoice-app",
          liveLink: "http://www.invoice-app.xyz/",
          scope: `Your users should be able to:

- View the optimal layout for the app depending on their device's screen size
- See hover states for all interactive elements on the page
- Create, read, update, and delete invoices
- Receive form validations when trying to create/edit an invoice
- Save draft invoices, and mark pending invoices as paid
- Filter invoices by status (draft/pending/paid)`,
        },
      ],
      selectedProject: null,
      modalIsVisible: false,
    };
  },
  methods: {
    setSelectedProject(projValue, openModal) {
      this.selectedProject = this.projectsArray.filter(
        (proj) => proj.id === projValue
      )[0];
      this.modalIsVisible = openModal;
    },
  },
  computed: {

  }
};
</script>

<style scoped>
.container-main {
  z-index: 1;
  padding: 0;
  margin: 0;
}

#title {
  margin: 19px 0;
}

p,
blockquote {
  margin: 0;
  font-size: 0.9em;
  line-height: 1.6em;
}

.block {
  display: flex;
  flex-direction: column;
  justify-content: center;
}

ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
}
.contact-info {
  display: flex;
  justify-content: center;
}

.container {
  text-align: center;
  /* padding: 0.8em 1.6em; */
}

.logo {
  width: 130px;
}
.hide-desktop {
  display: none;
}

header {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.ham-menu {
  width: 25px;
  margin-top: 45%;
}

.server {
  width: 70%;
  margin: 2em auto 2em 25%;
}

h1,
.slogan {
  position: relative;
  z-index: 3;
}

.profile-image {
  height: 100px;
  width: 100px;
  border-radius: 50%;
  margin-right: 20px;
}

.slogan {
  font-size: 1.1em;
}

.blue-container {
  width: 100%;
  background-color: aqua;
  color: #fff;
  margin-top: 15%;
  padding: 4em 0 2em;
  border-top-left-radius: 70px;
  transform: skewy(-2deg);
}

.blue-container ul {
  transform: skewY(2deg);
}

.blue-container:before {
  content: "";
  width: 50px;
  height: 50px;
  position: absolute;
  top: -50px;
  right: 0;
  background-color: aqua;
  z-index: -2;
}

.blue-container:after {
  content: "";
  width: 100px;
  height: 100px;
  position: absolute;
  background-color: white;
  top: -100px;
  right: 0;
  border-radius: 50%;
  z-index: -1;
}

.blue-container ul li {
  margin-bottom: 3em;
}
.blue-container ul li p {
  padding: 0 0.5em;
}

.blue-container img {
  width: 10%;
}

.blue-container ul li:last-child img {
  width: 8%;
}

.grey-container {
  background-color: grey;
  color: white;
  padding: 4em 0 2em;
  margin-top: -2%;
}

.grey-container ul li:first-child {
  padding-bottom: 2em;
}
.grey-container h2 {
  margin: 0 0 2em;
  text-decoration: underline;
  color: aqua;
}

figure {
  margin: 0;
  padding: 0;
}

figcaption {
  font-weight: bold;
  color: aqua;
}

h2 {
  margin-top: 7%;
  margin-bottom: 5%;
}

.cta {
  background-color: green;
  color: aqua;
  width: calc(100% -1em);
  display: block;
  border-radius: 20px;
  padding: 0.5em;
  text-decoration: none;
  font-size: 1.5em;
  margin: 3% auto 7%;
  position: relative;
  z-index: 4;
}

.footer-container {
  background-color: darkslategrey;
  color: lightgray;
  transform: skewY(2deg);
  border-top-right-radius: 40px;
  padding: 3em 0;
}

.footer-container::before {
  content: "";
  background-color: darkslategrey;
  width: 40px;
  height: 40px;
  position: absolute;
  top: -39px;
  left: 0;
}

.footer-container:after {
  content: "";
  background-color: #fff;
  width: 80px;
  height: 80px;
  position: absolute;
  top: -80px;
  left: 0;
  border-radius: 50%;
}

.footer-container .container {
  transform: skewY(-2deg);
}

.footer-container li {
  display: inline-block;
}

.footer-container ul li a {
  text-decoration: underline;
  color: #fff;
}

nav ul {
  position: fixed;
  width: 60%;
  top: 0;
  right: 0;
  text-align: center;
  background: darkslategrey;
  height: 100%;
  z-index: 7;
}

nav ul li a {
  text-align: center;
  color: #fff;
  display: block;
  width: 100%;
  /* padding: 15px; */
  background-color: rgb(58, 95, 95);
  border-top: solid 0.1em gray;
}

nav ul li a:hover {
  background: lightcoral;
}

.exit-btn {
  margin-bottom: 1em;
  margin-top: 1.3em;
  text-align: left;
  padding: 0 1.4em;
}

.exit-btn:hover {
  cursor: pointer;
}

nav ul {
  padding: 0 !important;
  background: none;
  width: auto;
  height: auto;
  position: inherit;
  display: flex;
  justify-content: space-around;
  padding-top: 0;
}

nav ul li {
  float: left;
}

nav ul li a {
  color: black;
  background-color: inherit;
  border: none;
  text-align: left;
}

nav ul li a:hover {
  background-color: inherit;
}

p ul li:last-child {
  border: none;
}

@media only screen and (min-width: 750px) {
  header {
    flex-direction: row;
  }

  .server {
    width: 50%;
  }

  h1 {
    font-size: 3em;
    margin: 0;
  }

  .slogan {
    font-size: 1.4em;
    margin: 0;
  }

  .blue-container {
    margin: 0;
  }

  .blue-container img {
    width: 20%;
  }

  .blue-container ul li:last-child img {
    width: 12%;
  }

  .blue-container ul {
    display: flex;
    margin-top: 1em;
    justify-content: center;
    align-items: center;
    margin: 0 auto;
  }
  .blue-container ul li {
    margin-bottom: 0;
  }

  .blue-container ul li p {
    padding: 0 0.8em;
  }

  .grey-container ul {
    display: flex;
  }

  nav {
    margin: 20px;
  }

  nav ul {
    width: 100%;
  }

  nav ul li a {
    padding: 0 0 0 10px;
  }
  .profile-image {
    height: 150px;
    width: 150px;
  }
}

@media only screen and (min-width: 900px) {
  .slogan {
    margin: 1.5em;
  }

  .blue-container ul {
    margin-bottom: 4%;
  }

  .grey-container .container {
    margin-top: 5%;
  }
}

@media only screen and (min-width: 1050px) {
  .blue-container ul li p {
    padding: 0 1.8em;
  }

  .grey-container .container {
    margin-top: 8%;
    margin-bottom: 5%;
  }
  .grey-container ul li {
    margin: 0 auto;
  }
  .grey-container ul li figure {
    margin: 0 10em auto;
  }

  .grey-container ul li blockquote {
    margin: 0;
  }

  .cta {
    width: 50%;
  }

  .footer-container .container {
    font-size: 1.6em;
  }

  .footer-container ul li a {
    margin: 0 1em;
  }
}

@media only screen and (min-width: 1050px) {
  header {
    margin: 0 auto;
    width: 80%;
  }
  .container {
    width: 80%;
    margin: 0 auto;
  }

  .show-mobile {
    display: none;
  }

  .hide-desktop {
    display: block;
    margin: 0 auto 12% auto;
  }

  .scroll {
    width: 30px;
    animation: move 1s infinite alternate;
  }

  @keyframes move {
    from {
      transform: translatey(0px);
    }

    to {
      transform: translatey(20px);
    }
  }
}
</style>
