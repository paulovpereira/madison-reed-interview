<script>
import PhotoItem from "./PhotoItem.vue";
import PhotoModal from "./PhotoModal.vue";

export default {
  name: "PhotoList",
  components: {
    PhotoModal,
    PhotoItem,
  },
  props: {
    photos: Array,
  },
  data() {
    return {
      selectedPhoto: null,
      isOpen: false,
    }
  },
  methods: {
    selectPhoto(photo) {
      this.selectedPhoto = photo;
      this.isOpen = true;
    },
    closeModal() {
      this.isOpen = false;
      this.selectedPhoto = null;
    },
  }
}
</script>

<template>
  <PhotoModal
      :is-open="isOpen"
      :photo="selectedPhoto"
      @close-modal="closeModal"
  />
  <div class="photo-list">
    <PhotoItem
        class="photo-list-item"
        v-for="photo in photos"
        :key="photo.id"
        :photo="photo"
        @click="selectPhoto(photo)"
    />
  </div>
</template>

<style scoped>
.photo-list {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: center;
  gap: 2px;
}

.photo-list-item {
  width: 150px;
  height: 150px;
  cursor: pointer;
  border: 1px solid rgba(0, 0, 0, 0.5);
}
</style>