<script>
import PhotoItem from "./PhotoItem.vue";
import Modal from "./Modal.vue";

export default {
  name: "PhotoModal",
  components: {
    Modal,
    PhotoItem,
  },
  props: {
    photo: Object,
    isOpen: Boolean,
  },
  methods: {
    closeModal() {
      this.$emit('closeModal');
    }
  }
}
</script>

<template>
  <Modal :isOpen="isOpen" @close-modal="closeModal">
    <template v-slot:header>
      <h3 class="photo-modal-header">Photo by {{ photo.author }}</h3>
    </template>
    <template v-slot:content>
      <PhotoItem :photo="photo" />
    </template>
  </Modal>
</template>

<style scoped>
.photo-modal-header {
  padding: 0;
  margin: 0;
}
</style>