<template>
  <div>
    <img class="pocketphone" alt="Vue logo" src="../assets/pokedex.png" />
    <h1 class="pocket_data">
      <span class="pocketmon_number">{{id}}</span> -
      <span class="pocketmon_name">{{nome}}</span>
    </h1>
  </div>
</template>

<style lang="scss">
.pocketphone {
  width: 100%;
  max-width: 425px;
}
.pocket_data {
  position: absolute;
  font-weight: 600;
  color: #aaa;
  left: 40%;
  bottom: 41%;
  font-size: clamp(8px, 5vw, 25px);
}
.pocketmon_name {
  color: #2c3e50;
  text-transform: capitalize;
}
</style>

<script>

export default ({
    name: 'PocketPhone',
    props:['id','nome']
})
</script>
