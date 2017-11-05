<template>
  <div>
    <div v-for="project in projects" :key="project.id" class="portfolio">
      <a class="project" target="_blank" :href="project.href" >
        <p :style="{ textAlign: 'center', textDecoration: 'none' }">{{ project.description }}</p>
        <img
          class="image"
          :src="project.backgroundImage"
        />
      </a>
    </div>
  </div>
</template>

<script>
export default {
  props: ['projects']
}
</script>

<style lang="scss" scoped>
.portfolio {
  display: grid
}

.project {
  padding: 25px;
  width: 350px;
  transition: transform .2s;

  &:hover {
    transform: translateY(-1.5px);
  }

  .image {
    background: black;
    background-repeat: no-repeat;
    background-size: contain;
    background-position: center;
    display: inline-block;
    height: 200px;
    width: 100%;
    border-radius: 15px;
  }
}
</style>


