<template>
  <div class="modal">
    <teleport to="body">
      <div class="container">
        <div class="content">
          <h2> {{ title }} </h2>

          <h4>Scope</h4>
          <p>
            Lorem ipsum dolor sit, amet consectetur adipisicing elit.
            Perferendis odit quis pariatur veniam a omnis quibusdam, nulla
            expedita, atque reiciendis eaque beatae eveniet adipisci! Ullam,
            neque repudiandae recusandae ad, qui numquam amet tenetur vero
            reiciendis saepe illum atque? Unde illum sint architecto ipsa aut
            quia?
          </p>

          <h4>Challenges</h4>
          <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Maiores,
            dolorum. Corporis fugiat maxime omnis tempore rem consectetur
            impedit! Vel nostrum asperiores provident sequi impedit ratione id
            amet quidem ipsum earum? Reiciendis, ipsum aut molestiae repellendus
            doloremque voluptatum saepe distinctio, rem magnam nobis aspernatur
            dolor delectus eius tenetur, totam in vero!
          </p>

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

.container {
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
}
</style>