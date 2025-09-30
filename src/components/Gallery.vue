<script>
import PhotoList from "./PhotoList.vue";
import axios from "axios";
import Modal from "./Modal.vue";
import PhotoItem from "./PhotoItem.vue";
import PhotoModal from "./PhotoModal.vue";

export default {
  name: 'Gallery',
  components: {
    PhotoModal,
    PhotoItem,
    Modal,
    PhotoList,
  },
  data() {
    return {
      photos: [],
      isLoading: true,
      isPhotoLoadFailed: false,
    }
  },
  async created() {
    const response = await axios.get('https://picsum.photos/v2/list?limit=100');
    if(response.status === 200){
      this.photos = response.data;
    } else {
      this.isPhotoLoadFailed = true;
    }
    this.isLoading = false;
  },
}
</script>

<template>
  <div v-if="isPhotoLoadFailed">
    <p>Ops, something went wrong on our side. Please try again later.</p>
  </div>
  <div v-else-if="isLoading">
    <p>Loading...</p>
  </div>
  <PhotoList v-else :photos="photos"/>
</template>
