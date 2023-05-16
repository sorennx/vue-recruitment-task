<template>
  <div class="content-wrapper content-wrapper_center">
    <button class="button-base button-base_br_12" @click="toggleSquare">
      {{ buttonText }}
    </button>
  </div>
</template>

<script>
export default {
  name: "CustomButton",
  data() {
    return {
      isSquareShown: false,
    };
  },
  methods: {
    toggleSquare() {
      this.isSquareShown = !this.isSquareShown;
      this.$emit("toggle-square");
    },
  },
  computed: {
    buttonText() {
      return this.isSquareShown ? "Hide square" : "Show square";
    },
  },
};
</script>

<style scoped>
.button-base {
  margin: 2rem;
  padding: 0.2rem 0.5rem;
  border: none;
  background: linear-gradient(
    170deg,
    rgb(62, 161, 219) 11.2%,
    rgb(93, 52, 236)
  );
  color: #ffffff;
  cursor: pointer;
  transition: background 0.45s ease-out;
  width: 10rem;
}

.button-base:hover {
  background-position: 10rem;
}

.button-base_br_12 {
  border-radius: 10px;
}
</style>
