<script setup>
import { ref } from 'vue';

const bColor = ref("black");

const tColor = ref();

const wText = ref("");

const showText = ref(true);

const radius = ref(0);

const boxOpacity = ref("");

const letter = ref();

const fontSize = ref();

const fontArreglo = [
  'Arial', 'Courier New', 'Georgia', 'Times New Roman'
]
</script>

<template>
  <div class="container">

    <div class="row">

      <div class="card col-md-6">
        <!--Color de fondo-->
        <div>
          <label>Color de fondo</label>
          <input v-model="bColor" type="text">
        </div>
        <!--Color de texto-->
        <div>
          <label>Color de texto</label>
          <input v-model="tColor" type="text">
        </div>
        <!--Mostrar texto-->
        <div>
          <label>Mostrar texto</label>
          <input type="checkbox" v-model="showText">
        </div>
        <!--Borde-->
        <div>
          <label>Border</label>
          <input type="range" min="0" max="500" v-model="radius">
        </div>
        <!--Contenido textual-->
        <div>
          <label>Contenido textual</label>
          <textarea v-model="wText"></textarea>
        </div>
        <!--Tipografia-->
        <div>

          <label>Tipografia</label>
          <!--TODO USAR CICLO V-FOR-->
          <select v-model="letter">
            <option v-for="font in fontArreglo" :key="font">{{ font }}</option>
          </select>
        </div>
        <!--Opaco-->
        <div>
          <label>Opaco</label>
          <input type="checkbox" v-model="boxOpacity">
        </div>
        <!--Tamaño tipografico-->
        <div>
          <label>Tamaño</label>
          <div>
            <label>Pequeña</label>
            <input type="radio" name="option" value="12px" v-model="fontSize">

            <label>Mediana</label>
            <input type="radio" name="option" value="32px" v-model="fontSize">

            <label>Grande</label>
            <input type="radio" name="option" value="60px" v-model="fontSize">
          </div>

        </div>

      </div>

      <!--RESULTADO-->

      <div class="col-md-6">
        <div class="d-flex justify-content-center align-items-center " :class="{ opacity: boxOpacity }" :style="{
          backgroundColor: bColor,
          color: tColor,
          borderRadius: radius + 'px',
        }" id="box">
          <span v-show="showText">
            <p :style="{ fontFamily: letter, fontSize: fontSize }">{{ wText }}</p>
          </span>
        </div>
      </div>

    </div>



  </div>

</template>

<style>
#box {
  width: 400px;
  height: 400px;
}

.opacity {
  opacity: 0.5;
}
</style>