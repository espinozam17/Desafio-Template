<template>
  <main class="container">
    <form class="form">
      <fieldset>
        <label class="espacio">Escribe un color de fondo en inglés</label>
        <br />
        <input class="form-control ancho" v-model="colorCuadrado" />
        <br>
        <label class="espacio">Escribe un color de letra en inglés</label>
        <br />
        <input class="form-control ancho" v-model="colorLetra" />
        <br>
        <label class="espacio">Mostrar texto</label>
        <input v-model="show" type="checkbox" />
        <br>
        <label for="customRange2" class="form-label ancho espacio">Borde</label>
        <br />
        <input
          v-model="border"
          type="range"
          class="form-range ancho"
          :min="minimo"
          :max="maximo"
          step="0.5"
          id="customRange2"
        />
        <br>
        <label class="espacio">Contenido textual: </label>
        <br />
        <textarea maxlength="200" v-model="texto"></textarea>
        <br>
        <label class="espacio">Tipografía: </label>
        <br />
        <select v-model="typography">
          <option
            :key="tipografia"
            v-for="tipografia in tipografias"
            :value="tipografia"
          >
            {{ tipografia }}
          </option>
        </select>
        <br>
        <label class="espacio">Opaco</label>
        <input v-model="opaco" type="checkbox" />
      </fieldset>
      <fieldset>
        <label class="espacio">Tamaño de letra</label>
        <div class="form-check">
          <input
            class="form-check-input"
            type="radio"
            name="flexRadioDefault"
            id="p"
            value="1rem"
            v-model="size"
          />
          <label class="form-check-label" for="p"> Pequeño </label>
        </div>
        <div class="form-check">
          <input
            class="form-check-input"
            type="radio"
            name="flexRadioDefault"
            id="m"
            value="1.5rem"
            v-model="size"
          />
          <label class="form-check-label" for="m"> Mediano </label>
        </div>
        <div class="form-check">
          <input
            class="form-check-input"
            type="radio"
            name="flexRadioDefault"
            id="g"
            value="2rem"
            v-model="size"
          />
          <label class="form-check-label" for="g"> Grande </label>
        </div>
      </fieldset>
    </form>
    <figure
      id="cuadrado"
      :style="{
        background: colorCuadrado,
        color: colorLetra,
        borderRadius: radioCompleto,
        fontFamily: typography,
        fontSize: size,
      }"
      :class="{ opaco: opaco }"
    >
      <p v-if="show">{{ texto }}</p>
    </figure>
  </main>
</template>

<script>
export default {
  name: 'ModidicarCuadro',
  data() {
    return {
      colorCuadrado: "",
      colorLetra: "",
      show: false,
      border: 0,
      minimo: 0,
      maximo: "50",
      texto: "",
      typography: "Arial",
      opaco: false,
      size: "1rem",
      tipografias: ["Times New Roman", "Georgia", "Arial", "Verdana", "Tahoma", "Sanvito", "Courier"],
    };
  },
  computed: {
    radioCompleto() {
      return this.border + "%";
    },
  },
};
</script>


<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
body {
  background-color: black;
  margin: 25%;
}
main{
  display: flex;
  justify-content: center;
  align-items: center;
}

.container{
  display: flex;
  align-items: stretch;
  gap: 2rem;
}


#cuadrado {
  width: 400px;
  height: 400px;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: #ccc;
  margin-left: 100px;
  overflow: auto; /* sirve para que no se desborde, siempre va en en el div donde quieres que no se desborde */
 
}
form {
  background: darkslategray;
  color: white;
  display: inline-block;
  flex-direction: flex-start;
  text-align: left;
  gap: 15px;
  padding: 40px;
}


form > div {
  display: flex;
  flex-direction: column;
  text-align: left;
}

.opaco {
  opacity: 0.5;
}

.ancho, textarea, select {
  width: 250px;
}
</style>
