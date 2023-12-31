<script>
import ListComponent from './components/ListComponent.vue'
export default {
  data() {
    return {
      tempProduct: {}
    }
  },
  components:{
    ListComponent,
  }
}
</script>

<template>
  <div class="container">  
        <ListComponent />
  </div>
</template>

<style lang="scss">
@import './assets/all.scss';
    img {
      object-fit: contain;
      max-width: 100%;
    }

    .primary-image {
      height: 300px;
    }

    .images {
      height: 150px;
    }
</style>
