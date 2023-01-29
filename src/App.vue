<template>
  <div id="app">
    <div class="rounded-div">
      <template v-for="(image, index) of images">
        <!-- blured background with the original image -->
        <BluredBackground
          :key="index"
          style="display: inline-block; margin: 5px"
          :image="image"
          blur-opacity="0.5"
          container-class="rounded-div"
        >
          <div style="padding: 20px">
            <img
              :src="image"
              class="rounded-div"
              style="width: 300px; height: 400px"
            />
          </div>
        </BluredBackground>
      </template>

      <!-- blured background without image  -->
      <BluredBackground
        style="display: inline-block; margin: 5px"
        image="https://picsum.photos/200/300?image=21"
        blur-opacity="0.5"
        container-class="rounded-div"
      >
        <div style="width: 300px; height: 400px; padding: 20px">
          <div class="rounded-div"></div>
        </div>
      </BluredBackground>
    </div>
  </div>
</template>

<script>
import BluredBackground from "./components/BluredBackground.vue";

export default {
  name: "App",
  components: {
    BluredBackground,
  },
  data() {
    return {
      images: [
        "https://picsum.photos/200/300?image=11",
        "https://picsum.photos/200/300?image=21",
        "https://picsum.photos/200/300?image=22",
        "https://picsum.photos/200/300?image=23",
        "https://picsum.photos/200/300?image=24",
        "https://picsum.photos/200/300?image=25",
        "https://picsum.photos/200/300?image=26",
        "https://picsum.photos/200/300?image=27",
        "https://picsum.photos/200/300?image=28",
        "https://picsum.photos/200/300?image=31",
        "https://picsum.photos/200/300?image=41",
        "https://picsum.photos/200/300?image=51",
        "https://picsum.photos/200/300?image=61",
      ],
    };
  },
};
</script>

<style>
.rounded-div {
  border-radius: 5px;
}
</style>
