<template>
  <a v-bind:href="url">
    <img class="pocketmon" v-bind:src="url" alt="" />
  </a>
</template>
<style lang="scss">
.pocketmon {
  position: absolute;
  left: 50%;
  bottom: 55%;
  transform: translate(-63%, 20%);
  height: 10%;
}
</style>

<script>
export default {
  props: ['url'],
  name: "PocketmonImage",
  data() {
    return {
      //url: "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/versions/generation-v/black-white/animated/132.gif",
    };
  },
  components: {},
};
</script>
