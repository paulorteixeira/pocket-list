<template>
  <main>
    <PocketmonImage v-bind:url='url_image'></PocketmonImage>
    <PocketPhone v-bind:id='numero_pocket' v-bind:nome='pocket_name'></PocketPhone>
    <v-form class="formulario">
      <input
        type="search"
        v-model="input_nome_numero"
        class="input_busca"
        placeholder="Name or Number"
        required
      />
    </v-form>
    <div class="botoes">
      <v-btn class="button btn-prev" elevation="2">&lt; Prev </v-btn>
      <v-btn class="button btn-next" elevation="2" v-on:click="renderizar"
        >Next &gt;</v-btn
      >
    </div>
  </main>
</template>

<style  lang="scss">
main {
  //background-color: red;
  display: inline-block;
  margin-top: 2%;
  padding: 15px;
  position: relative;
}
.formulario {
  position: absolute;
  width: 65%;
  bottom: 29%;
  left: 14%;
}
.input_busca {
  width: 100%;
  padding: 4%;
  outline: none;
  border: 2px solid #333;
  border-radius: 5px;
  font-weight: 600;
  font-size: clamp(8px, 5vw, 1rem);
  box-shadow: -3px 4px 0 #888, -5px 7px 0 #333;
  background-color: #fff;
}
.botoes {
  position: absolute;
  bottom: 10%;
  left: 50%;
  width: 65%;
  transform: translate(-57%, 0);
  display: flex;
  gap: 10px;
}
.button {
  width: 50%;
  padding: 4%;
  border: 2px solid #333;
  border-radius: 5px;
  font-size: clamp(8px, 5vw, 1rem);
  font-weight: 600;
}
</style>

<script>
import PocketmonImage from "@/components/PocketmonImage.vue";
import PocketPhone from "@/components/PocketPhone.vue";
import axios from "axios";

export default {
  name: "PocketMain",
  components: {
    PocketmonImage,
    PocketPhone,
  },
  data() {
    return {
      input_nome_numero: "",
      url_image : "",
      dados_poke: {},
      pocket_name: "",
      numero_pocket:"",
    };
  },
  methods: {
    async consulta() {
      try {
        const response = await axios.get(
          "https://pokeapi.co/api/v2/pokemon/" + this.input_nome_numero.toLowerCase()
        );

        if (response.status != 200) {
          throw new Error(`Error! status: ${response.status}`);
        }
        const dados =  response.data;
        return  dados;

      } catch (err) {
        console.log(err);
      }
    },

    async renderizar(){
      const dados = await this.consulta();
      this.pocket_name = dados.name;
      this.numero_pocket = dados.id;

      this.url_image = dados.sprites.versions['generation-v']['black-white'].animated.front_default != null 
                    ?  dados.sprites.versions['generation-v']['black-white'].animated.front_default : dados.sprites.front_default;
      
    }

  },
};
</script>
