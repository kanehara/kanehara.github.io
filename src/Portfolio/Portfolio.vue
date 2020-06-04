<template>
  <div class="portfolio">
    <div v-for="project in projects" :key="project.id">
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
  display: flex;
  flex-wrap: wrap;
  align-items: center;
}

.project {
  padding: 25px;
  width: 350px;
  margin: 12px;
  transition: transform .2s;
  display: block;

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
    border-radius: 15px;
  }
}
</style>


