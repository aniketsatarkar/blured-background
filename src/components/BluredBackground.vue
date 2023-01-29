<template>
  <div :class="containerClass" :style="backgroundStyle">
    <div :class="containerClass" :style="blurStyle">
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    /* initial porops */
    image: {
      default: null,
      type: String,
      required: true,
    },
    blurOpacity: {
      default: 0.1,
      type: Number,
    },
    blur: {
      default: "20px",
      type: String,
    },
    /* additional props */
    containerStyle: {
      default: null,
      type: String,
    },
    containerClass: {
      default: null,
      type: String,
    },
  },
  computed: {
    backgroundStyle() {
      return `background-image: url(${this.image});
        background-position: bottom;
        background-repeat: no-repeat;
        background-size: cover;
        ${this.containerStyle}`;
    },
    blurStyle() {
      return `background: rgba(255, 255, 255, ${this.blurOpacity});
        backdrop-filter: blur(${this.blur});
        ${this.containerStyle}`;
    },
  },
};
</script>
