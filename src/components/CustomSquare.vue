<template>
  <div class="content-wrapper content-wrapper_center">
    <div :class="computeClass" :style="{ background: computeGradient }"></div>
  </div>
</template>

<script>
export default {
  name: "CustomSquare",
  props: {
    showSquare: {
      type: Boolean,
      default: true,
    },
    gradientValue1: {
      type: String,
    },
    gradientValue2: {
      type: String,
    },
  },
  computed: {
    computeClass: function () {
      // `display:hidden` property is applied instead of using `v-show` or `v-if` in order to have square-cont
      // retain its space -> `v-show` sets display to `none` and `v-if` woulnd not render the element at all in DOM
      return this.showSquare ? "square-cont" : "square-cont square-cont_hidden";
    },
    // Compute the color of the gradient based on the values that are being passed from the two inputs
    // `gradientValue1` - the starting color of the gradient
    // `gradientValue2` - the ending color of the gradient
    computeGradient() {
      return this.showSquare
        ? `linear-gradient(109.6deg, rgb(${this.gradientValue1}) 11.2%, rgb(${this.gradientValue2}) 100.2%)`
        : "";
    },
  },
};
</script>

<style scoped>
.square-cont {
  display: flex;
  width: 200px;
  height: 200px;
}

/* As the code was modified for the sake of Task 2, this style is no longer needed
 .square-cont_blue {
  background: linear-gradient(109.6deg, rgb(62, 161, 219) 11.2%, rgb(93, 52, 236) 100.2%);
} */

.square-cont_hidden {
  display: hidden;
}
</style>
