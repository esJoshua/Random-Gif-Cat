<template>
  <div class="container" id="app">
    <div class="row">
      <div id="divTitle" class="col-12 p-4">
        <h1 class="mt-5">{{ title }}</h1>
      </div>
      <div
        id="divForm"
        class="col-12 p-2 d-flex flex-column align-items-center"
      >
        <div class="centerFlex mb-4 w-25">
          <span>Titulo</span>
          <input
            class="mx-2"
            type="text"
            v-model="vTitle"
            placeholder="Ingresa un titulo"
          />
        </div>
        <div class="centerFlex mb-4 w-25">
          <span>Filtro</span>
          <select
            class="form-select mx-2 w-auto"
            aria-label="Default select example"
            v-model="vFilter"
          >
            <option value="blur">blur</option>
            <option value="mono">mono</option>
            <option value="sepia">sepia</option>
            <option value="negative">negative</option>
            <option value="paint">paint</option>
            <option value="pixel">pixel</option>
          </select>
        </div>
        <div class="centerFlex mb-4 w-25">
          <span>Color</span>
          <select
            class="form-select mx-2 w-auto"
            aria-label="Default select example"
            v-model="vColor"
          >
            <option value="red">rojo</option>
            <option value="blue">azul</option>
            <option value="green">verde</option>
            <option value="white">blanco</option>
            <option value="yellow">amarillo</option>
            <option value="orange">naranja</option>
          </select>
          <div class="circleDiv" :style="`background-color:${vColor}`"></div>
        </div>
        <div class="centerFlex w-25">
          <span class="lastSpan">Tamaño</span>
          <input
            class="mx-2"
            type="number"
            min="100"
            max="600"
            v-model="vSize"
            placeholder="Ingresa el tamaño"
          />
        </div>
      </div>
      <div id="divCat" class="col-12 p-4">
        <div class="centerFlex flex-column">
          <button
            type="button"
            class="btn btn-secondary mb-4"
            @click="gatosImg"
          >
            Obtener mi gatito
          </button>
          <img :src="catImg" alt="" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      vTitle: "",
      vFilter: "",
      vColor: "",
      vSize: "",
      catImg: "",
    };
  },
  computed: {
    title() {
      const title = "random gif cat";
      return title.toUpperCase();
    },
  },
  methods: {
    /* async getData() {
      try {
        const req = await fetch(`
        https://cataas.com/cat/gif/says/${this.vTitle}?filter=${this.vFilter}&color=${this.vColor}&size=${this.vSize}&type=or`);
        const data = await req.json();
        this.catImg = data;
        console.log(this.catImg);
      } catch (error) {
        console.error(error);
      }
    }, */
    gatosImg() {
      this.catImg = `https://cataas.com/cat/gif/says/${this.vTitle}?filter=${this.vFilter}&color=${this.vColor}&size=${this.vSize}&type=or`;
      console.log(this.catImg);
    },
  },
};
</script>

<style lang="scss">
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
body {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

#divTitle {
  background-color: #add9e6;
}
#divForm {
  background-color: #f0807f;
}
#divCat {
  background-color: #add9e6;
}
.centerFlex {
  display: flex;
  justify-content: flex-start;
  align-items: center;
}
input {
  width: 10rem;
}
.lastSpan {
  margin-left: -1rem;
}
.circleDiv {
  background-color: #f0807f;
  width: 50px;
  height: 50px;
  border-radius: 50%;
}
</style>
