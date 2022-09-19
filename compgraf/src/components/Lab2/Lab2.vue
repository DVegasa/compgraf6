<template>
  <div class="container">
    <div class="p-2">
      <h3>Лабораторная №2</h3>
      2. Рисование кривой Безье
    </div>
    <div class="container x">
      <canvas class="lab_2__canvas" ref="canvas_elem_2_1"></canvas>
      <br />
			<div style="display: flex; flex-direction: column">
				<div class="card mt-2" v-for="(item, index) in coords_2_1" :key="item">
					<div class="card-body">
						<h5 class="card-title">Точка {{ index }}</h5>
						<label for="x" class="form-label">x</label>
						<input
							type="range"
							name="x"
							min="1"
							max="600"
							@input="(e) => changeCoordsPos_2_1(e, 'x', index)"
							class="form-range"
						/>
						<label for="y" class="form-label">y</label>
						<input
							type="range"
							name="y"
							min="1"
							max="600"
							@input="(e) => changeCoordsPos_2_1(e, 'y', index)"
							class="form-range"
						/>
					</div>
				</div>
      </div>
      <hr />
    </div>
  </div>
</template>

<script lang="ts">
import { ref } from "vue";

import { Canvas } from "../Lab/Canvas";
import { Lab_2_1 } from "./lab2_1";
import VueMarkdown from "vue-markdown-render";
import { defineComponent } from "vue";

export default defineComponent({
  data() {
    return {
      lab_2_1: null,
      coords_2_1: [],
    };
  },
  components: {
    VueMarkdown,
  },
  methods: {
    setDrawCurve() {
      // @ts-ignore
      this.lab.setDrawCurve();
    },
    // @ts-ignore
    changeCoordsPos_2_1(e, typePos, pos) {
      let value = e.srcElement.value;
      // @ts-ignore
      this.lab_2_1.changeCoordsPos(pos, typePos, value);
    },
  },
  mounted() {
    // @ts-ignore
    const canvas_elem_2_1: HTMLCanvasElement = this.$refs.canvas_elem_2_1;
    const canvas_2_1 = new Canvas(canvas_elem_2_1);
    const lab_2_1 = new Lab_2_1(canvas_2_1, this);
    // @ts-ignore
    this.lab_2_1 = lab_2_1;
  },
});
</script>

<style lang="sass">
.lab_2
	&__canvas
		width: 600px
		height: 600px
		border: 1px solid #222

.container .x
	display: flex
</style>
