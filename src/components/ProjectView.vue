<template>
<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">
  <li>
    <article class="project-container">
      <div class="heading">
        <img :src="imgSRC" alt="project-image" />
      </div>
      <div class="content">
        <h3>{{ title }}</h3>
        <div class="tech">
          <span v-for="tech in techArray" :key="tech"> {{ tech }} </span>
        </div>
      </div>
      <div class="nav">
        <button class="btn btn-primary">More Info</button>
        <button class="btn btn-secondary"><a :href="GHLink" target="_blank">View GitHub </a></button>
        <button class="btn btn-success" style="color: white;"> 
          <a :href="liveLink" target="_blank">View project live </a>
        </button>
      </div>
    </article>
  </li>
</template>

<script>
export default {
  props: ["id", "img", "title", "techArray", "GHLink", "liveLink"],
  computed: {
    imgSRC() {
      return require("../assets/" + this.img);
    },
  },
};
</script>

<style scoped>

.content {
    align-self: center;
}

li {
    max-width: 350px;
  margin: 0 25px;
}
.project-container {
  display: flex;
  flex-direction: column;
}

img {
  width: 200px;
  /* height: 200px; */
}

.tech {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-evenly;
    margin: 15px 0;

}

span {
  padding: 10px;
  margin: 5px;
  border-radius: 15px;
  background-color: #DB4437;
}

span:first-of-type {
  background-color: #0f9d58;
}

span:nth-of-type(2) {
  background-color: #f4b400;
}
span:last-of-type {
  background-color: #4285f4;
}

.nav {
    display: flex;
    justify-content: space-around;
}

a {
    color: white;
}
</style>