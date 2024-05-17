<template>
  <div id="app">
    <h1 class="text-center py-4"> Cambia tu color </h1>
    <div class="container py-5">
      <div class="row">
        <!-- Columna de cambios -->
        <div class="container fondo col-6 container py-5">
          <form class="d-flex flex-column">
            <!-- cambio de fondo -->
            <label for="">Color de fondo</label><br />
            <input type="texto" id="colorFondo" v-model="colorFondo" />

            <!-- cambio colo de texto -->
            <label for="">Color de texto</label><br />
            <input type="color" id="colorTexto" v-model="colorTexto" />

            <!-- checkbox mostrar texto -->
            <div>
              <label for="">Mostrar texto</label>
              <input type="checkbox" id="mostrarTexto" v-model="mostrarTexto" />
            </div>

            <!-- Cambio rango de borde -->
            <div>
              <label >Borde</label><br />
              <input class="col-10"
                type="range"
                id="rangeborde"
                name="rangeborde"
                min="0"
                max="50"
                step="1"
                v-model="borde"
              />
            </div>

            <!-- text area para contenido -->
            <div>
              <label for="">Contenido textual</label><br />
              <textarea
                name="text"
                id="contenidoTextual"
                cols="60"
                rows="3"
                v-model="contenidoTextual"
              ></textarea>
            </div>

            <!-- opciones para tipografia -->
            <div>
              <label for="tipografias">Tipografías</label>
              <br />
              <select name="tipografias" id="tipografias" v-model="tipografias">
                <option
                  :value="tipografia"
                  v-for="(tipografia, index) in tipografiaArray"
                  :key="index"
                >
                  {{ tipografia }}
                </option>
              </select>
            </div>

            <!-- check box opaco -->
            <div class="py-3">
              <label for="">opacidad</label>
              <input class="col-10"
                type="range"
                id="opacity"
                min="0"
                max="1"
                step="0.1"
                v-model="opacidad"
              />
              <span>{{ opacidad}} </span>
            </div>

            <!-- seleccion de tamaño de letra -->
            <div>
              <label for="">Tamaño Letra</label>
              <div class="row">
                <div class="col-4">
                  <input
                    type="radio"
                    id="pequeño"
                    name="fav_language"
                    value="pequeño"
                    v-model="tamanoLetra"
                  />
                  <label for="pequeño">Pequeño</label><br />
                </div>
                <div class="col-4">
                  <input
                    type="radio"
                    id="mediano"
                    name="fav_language"
                    value="mediano"
                    v-model="tamanoLetra"
                  />
                  <label for="mediano">Mediano</label><br />
                </div>
                <div class="col-4">
                  <input
                    type="radio"
                    id="grande"
                    name="fav_language"
                    value="grande"
                    v-model="tamanoLetra"
                  />
                  <label for="grande">Grande</label>
                </div>
              </div>
            </div>
          </form>
        </div>

        <!-- Columna del resultado -->
        <div
          class="resultado col-6 container py-5 d-flex align-items-center justify-content-center"
        >
          <div
            id=""
            class="cuadrado h-100 w-100 d-flex align-items-center justify-content-center"
            :style="{
              opacity: opacidad,
              borderRadius: borde + '%',
              backgroundColor: colorFondo,
            }"
          >
            <p
              class=""
              :style="{
                color: colorTexto,
                fontStyle: tipografias,
              }"
              :class="[
                tamanoLetra == 'grande'
                  ? largeClass
                  : tamanoLetra == 'pequeño'
                  ? smallClass
                  : mediumClass,
              ]"
              v-show="mostrarTexto"
            >
              {{ contenidoTextual }}
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  components: {},
  data() {
    return {
      colorFondo: "",
      colorTexto: "",
      mostrarTexto: true,
      borde: 0,
      contenidoTextual: "",
      tipografias: "normal",
      opacidad: 0.3,
      tamanoLetra: "",
      tipografiaArray: ["italic", "normal"],
      smallClass: "smallText",
      mediumClass: "mediumText",
      largeClass: "largeText",
    };
  },
  
};
</script>

<style>
.fondo {
  background-color: rgb(94, 142, 94);
}
.resultado {
  transition: opacity 0.5s ease;
}

.cuadrado {
  max-height: 300px;
  max-width: 300px;
}
.smallText {
  font-size: 16px;
}
.mediumText {
  font-size: 24px;
}
.largeText {
  font-size: 40px;
 
} 
</style>
