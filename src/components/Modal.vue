<template>
  <div class="modal">
    <teleport to="body">
      <div class="container-modal">
        <div class="content">
          <h2> {{ title }} </h2>

          <h4>Scope</h4>
          <p>
            {{ scope }}
          </p>

          <h4>Challenges</h4>
          <span>

          </span>

          <button class="btn btn-danger" @click="$emit('closeModal', false)">close</button>
        </div>
      </div>
    </teleport>
  </div>
</template>

<script>
export default {
    props: ['title', 'scope', 'challenges'],
};
</script>

<style scoped>
.modal {
  position: relative;
}

.container-modal {
  position: fixed;
  height: 100%;
  width: 100%;
  top: 0;
  left: 0;
  background-color: rgb(0, 0, 0, 0.4);
  z-index: 5;
  display: flex;
  justify-content: center;
  align-items: center;
}

.content {
  padding: 50px;
  border-radius: 10px;
  background-color: white;
  max-width: 850px;
}
</style>