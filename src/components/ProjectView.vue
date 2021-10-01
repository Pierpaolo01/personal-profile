<template>
  <li>
    <article class="project-container">
      <div class="heading">
        <img :src="imgSRC" alt="project-image" />
      </div>
      <div class="content">
        <h3>{{ title }}</h3>
        <div class="tech">
          <span class="stack">Stack</span>
          <div class="techStacks">
            <span v-for="tech in techArray" :key="tech">
              {{ tech }}
            </span>
          </div>
        </div>
      </div>
      <div class="nav-btns">
        <button :id="id" class="btn btn-primary more-info" @click="selectedProject">More Info</button>
        <button class="btn btn-success live-proect" >
          <a :href="liveLink" target="_blank">View project live </a>
        </button>
        <button class="btn btn-secondary view-git">
          <a :href="GHLink" target="_blank">View GitHub </a>
        </button>
      </div>
    </article>
  </li>
</template>

<script>
export default {
  props: ["id", "img", "title", "techArray", "GHLink", "liveLink"],
  methods: {
      selectedProject(){
          this.$emit('feedModal', this.$props.id, true);
      },
  },
  computed: {
    imgSRC() {
      return require("../assets/" + this.img);
    },
  },
};
</script>

<style scoped>
h3 {
  text-decoration: underline;
  margin-top: 20px;
}

.content {
  align-self: center;
}

li {
  max-width: 350px;
  margin: 0 auto 25px auto;
  background-color: #0c2340;
  box-shadow: black 0px 0px 10px 0px;
  padding-bottom: 5px;
}

li:hover {
  box-shadow: black 0px 0px 20px 5px;
}

.project-container {
  display: flex;
  flex-direction: column;
}

img {
  width: 100%;
  height: 165px;
  object-fit: cover;
}
.stack {
  margin: 0 auto;
  width: 80%;
  border-bottom: 1px black solid;
}
.tech {
  display: flex;
  flex-direction: column;
  margin: 15px 0;
}
.techStacks {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: space-evenly;
}

span {
  margin: 5px;
  color: white;
}

.nav-btns {
  display: flex;
  flex-basis: 4;
  justify-content: space-around;
}

a {
  color: white;
  font-size: 12px;
}

.view-git {
    flex-basis: 1;
}
.live-proect {
    flex-basis: 2;
}
.more-info {
    font-size: 12px;
    flex-basis: 1;
}
</style>