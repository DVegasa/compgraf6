<template>
  <div class="lab_1">
    <div class="lab_1__title">
      <vue-markdown :source="src" />
    </div>
    <div class="lab_1__controls">
      <button @click="clearScreen" class="btn btn-primary me-2">
        Очистить
      </button>
      <button @click="saveFigure" class="btn btn-primary">Сохранить</button>

      <div class="my-3">
        <label for="formFile" class="form-label">Загрузить</label>
        <input
            class="form-control"
            type="file"
            id="formFile"
            @change="loadFigure"
        />
      </div>

      <div class="lab_1__range">
        <label for="scaleXYZ" class="form-label">Масштаб всюду</label>
        <input
            type="range"
            name="scaleXYZ"
            min="1"
            max="100"
            @input="(e) => changeScale(e, 'XYZ')"
            class="form-range"
        />
      </div>
      <div class="lab_1__range">
        <label for="scaleX" class="form-label">Масштаб X</label>
        <input
            type="range"
            name="scaleX"
            min="-100"
            max="100"
            @input="(e) => changeScale(e, 'X')"
            class="form-range"
        />
      </div>
      <div class="lab_1__range">
        <label for="scaleY" class="form-label">Масштаб Y</label>
        <input
            type="range"
            name="scaleY"
            min="-100"
            max="100"
            @input="(e) => changeScale(e, 'Y')"
            class="form-range"
        />
      </div>
      <div class="lab_1__range">
        <label for="scaleZ" class="form-label">Масштаб Z</label>
        <input
            type="range"
            name="scaleZ"
            min="-100"
            max="100"
            @input="(e) => changeScale(e, 'Z')"
            class="form-range"
        />
      </div>
    </div>
    <div class="lab_1__field">
      <canvas class="lab_1__canvas" ref="canvas_elem"></canvas>
    </div>
  </div>
</template>

<script lang="ts">
import { ref } from "vue";

import { Canvas } from "../Lab/Canvas";
import { Lab_1 } from "./lab1";
import VueMarkdown from "vue-markdown-render";

export default {
  data() {
    return {
      test: 123,
      lab1: null,
    };
  },
  components: {
    VueMarkdown,
  },
  methods: {
    clearScreen() {
      this.lab1.clearCoords();
    },
    changeScale(e, type) {
      console.log(e);
      const value = e.srcElement.value;
      this.lab1.changeScale(type, value);
    },
    saveFigure() {
      this.lab1.saveFigure();
    },
    loadFigure(e) {
      this.lab1.loadFigure(e);
    },
  },
  setup(props, ctx) {
    const src = ref(`## Лабораторная №1
    1. Рисование замкнутой ломаной по точкам, заданным пользователем.
    2. Поворот, сдвиг, копирование, сжатие.
    3. Сохранение данных в файл.
    4. Загрузка кривой из файла.`);

    return {
      src,
    };
  },
  mounted() {
    // @ts-ignore
    const canvas_elem: HTMLCanvasElement = this.$refs.canvas_elem;
    const canvas = new Canvas(canvas_elem);
    const lab_1 = new Lab_1(canvas);
    this.lab1 = lab_1;
  },
};
</script>

<style lang="sass">
.lab_1
	max-width: 860px
	&__field
		width: 100%
		display: flex
	&__canvas
		margin: 0 auto
		width: 600px
		height: 600px
		border: 1px solid #222
	&__range
		width: 300px

.form-label
	width: 100px
</style>
