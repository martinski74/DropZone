
<template>
 <div class="app">
  <h1>DropZone</h1>
  <DropZoneVue @drop.prevent="drop" @change="selectedFile"/>
  <span class="file-info">File: {{ dropzoneFile.name }}</span>
 </div>
</template>

<script>
import DropZoneVue from './components/DropZone.vue';
import { ref } from "vue";

export default {
  name: 'App',
  components: {
    DropZoneVue,
  },
    setup() {
      let dropzoneFile = ref("");

      const drop = (e) => {
        dropzoneFile.value = e.dataTransfer.files[0];
      }

      const selectedFile = () => {
        dropzoneFile.value = document.querySelector('.dropzoneFile').files[0];
      }
      return {
        dropzoneFile,
        drop,
        selectedFile
      }
    }
  }
</script>

<style lang="scss" scoped>
.app {
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background-color: #f1f1f1;
  h1 {
    font-size: 40px;
    margin-bottom: 32px;
  }
  .file-info {
    margin-top: 32px;
  }
}
</style>
