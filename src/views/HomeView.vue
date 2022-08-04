<template>
  <div class="home">
    <PocketMain ></PocketMain>
  </div>
</template>

<script>
// @ is an alias to /src
import PocketMain from '@/components/PocketMain.vue'

export default {
  name: 'HomeView',
  components: {
    PocketMain
  }
}
</script>
