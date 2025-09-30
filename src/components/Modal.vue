<script>
export default {
  props: {
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
  <div v-if="isOpen" class="overlay" @click.self="closeModal" >
    <div class="modal-content">
      <div class="modal-header">
        <slot name="header"></slot>
      </div>
      <div class="modal-body">
        <slot name="content"></slot>
      </div>
    </div>
  </div>
</template>

<style scoped>
.overlay {
  position: fixed;
  margin: auto;
  padding: 1rem;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.5);
  z-index: 1;
  display: flex;
}

.modal-header {

}

.modal-body {
  position: relative;
  max-height: 70vh;
  overflow-y: auto;
  padding: 0 1rem;
}

.modal-content {
  margin: auto;
  padding: 1rem 0;
  max-width: 1280px;
  background-color: #333;
  display: flex;
  flex-direction: column;
  gap: 1rem;
  border: 1px solid rgba(0, 0, 0, 0.5);
}
</style>