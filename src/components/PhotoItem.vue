<script>
export default {
  name: "PhotoItem",
  props: {
    photo: Object,
  },
}
</script>

<template>
  <div v-if="photo" class="photo-item">
    <img :src="photo.download_url" :alt="`Photo from ${photo.author}`" class="photo-item-thumbnail"/>
  </div>
</template>

<style scoped>
.photo-item {
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: #333;
}

.photo-item-thumbnail{
  max-width: 100%;
  max-height: 100%;
}
</style>