<template>
  <div id="app">
    <div :style="gradient" class="width: 250px; height: 350px">
      <img :src="image" class="inline" />
    </div>

    <div class="inline" :style="gradient"></div>
    <br />
    <div
      class="multi-repeating-linear"
      style="width: 200px; height: 300px"
    ></div>
    <br />
    <textarea v-model="gradient"></textarea>
  </div>
</template>

<script>
var grad = require("gradient-from-image");

export default {
  name: "App",
  data() {
    return {
      gradient: null,
      image: "https://picsum.photos/200/300?image=6",
    };
  },
  created() {
    this.getGradient();
  },
  methods: {
    async getGradient() {
      const imgUrl = this.image;
      let gradient = null;

      await grad.gr(imgUrl).then((response) => {
        gradient = response;
      });

      console.log(gradient);

      let colors = gradient.relevant;

      this.gradient = `background: linear-gradient(45deg, ${colors[1]}, ${colors[0]});`;
    },
  },
};
</script>

<style>
.inline {
  display: inline-block !important;
  width: 200px !important;
  height: 300px !important;
}

.multi-repeating-linear {
  background: repeating-linear-gradient(190deg, #642b73, #c6426e),
    repeating-linear-gradient(-190deg, #642b73, #c6426e),
    repeating-linear-gradient(23deg, #642b73, #c6426e);
}
</style>
