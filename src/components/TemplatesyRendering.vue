<template>
  <!--  Datos el formulario -->
  <form>
    <!-- Input color fondo -->
    <div>
      <label>Color de fondo</label><br>
      <input type="text" v-model="colorDeFondo" id="inputs" />
    </div>
    <!-- Input color texto -->
    <div>
      <label>Color de texto</label><br>
      <input type="text" v-model="colorDeTexto"id="inputs" />
    </div>
    <!-- Checkbox mostrar texto -->
    <div>
      <label> Mostrar texto</label>
      <input type="checkbox" v-model="mostrarTexto" id="cuadrocheck"/>
    </div>
    <!--  Range de borde -->
    <div>
      <label>Borde</label><br>
      <input type="range" min="0" max="5" step="0.5" v-model="grosorDeBorde" id="inputs">
    </div>
    <!--  Textarea de opinión -->
    <div>
      <p>Contenido textual</p>
      <textarea v-model="opinion" placeholder="Escribe tu opinión..." id="inputs"></textarea>
    </div>
    <!--  Selección opciones -->
    <div>
      <label for="tipografia">Tipografía</label><br>
      <select v-model="selectedFont" id="inputs">
        <option v-for="font in fonts" :key="font" :value="font">{{ font }} </option>
      </select>
    </div>
    <!--  Checkbox Opaco -->
    <div>
      <label>
        Opaco
        <input type="checkbox" v-model="opaco">
      </label>
    </div>
    <!--  Radio -->
    <section id="tamanos">
      <div>
      <label for="tamañodeletra">Tamaño de letra</label><br>
        <input type="radio" name="size" value="pequeno" v-model="radio">
        <label>Pequeño</label>
        <input type="radio" name="size" value="mediano" v-model="radio">
        <label>Mediano</label>
        <input type="radio" name="size" value="grande" v-model="radio">
        <label>Grande</label>
      </div>
    </section>
  </form>


  <!--  Rectangulo que recibe el formulario -->
  <div class="container" :style="{
    backgroundColor: colorDeFondo,
    color: colorDeTexto,
    borderWidth: grosorDeBorde + 'px',
    opacity: opaco ? 0.5 : 1,
    fontFamily: selectedFont
  }" :class="radio">
    <div>
      <p v-if="mostrarTexto">{{ opinion }}</p>
    </div>

  </div>
</template>

<script>
export default {
  name: 'TemplatesyRendering',
  data() {
    return {
      colorDeFondo: "",
      colorDeTexto: "",
      mostrarTexto: false,
      grosorDeBorde: 1,
      opinion: "",
      opaco: false,
      radio: "",
      fonts: [ "arial", "cursive", "Courier New"],
      selectedFont: '',
    };
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  display: flex;
  gap: 40px;
  color: #2c3e50;
  width: 100%;

}

form {
  padding: 18px;
  border-radius: 20px;
  border: ridge 1px;
  background-color: rgb(19, 75, 75);
  color: white;
  font-weight: bold;
  display: flex;
  flex-direction: column;
  gap: 15px;
  justify-content: center;
  width: 40%;
}

.container {
  padding: 18px;
  border-radius: 60px;
  border: dotted 1px;
  margin: 1rem;
  background-color: rgb(2, 170, 114);
  color: white;
  text-align: center;
  justify-content: center;
  display: flex;
  flex-direction: column;
  gap: 15px;
  align-items: center;
  font-weight: bold;
  float: right;
  width: 200px;
  height: 200px;
}
#inputs{
  width: 80%;
}
#cuadrocheck{
  margin-left: 10px;
 
}
#tamanos{
  display: inline-flex;
}
.pequeno {
  font-size: small;
}

.mediano {
  font-size: medium;
}

.grande {
  font-size: xx-large;
}
</style>
