<template>
  <div id="app">
    <div class="content-wrapper content-wrapper_col content-wrapper_center">
      <CustomSquare
        :show-square="showSquare"
        :gradient-value1="gradientValue1"
        :gradient-value2="gradientValue2"
      />
      <CustomButton @toggle-square="toggleSquare" />
      <CustomInput
        @gradient-input-updated="updateGradientValue1"
        :gradient-default-value="gradientValue1"
      >
        Gradient start color (R, G, B)
      </CustomInput>
      <CustomInput
        @gradient-input-updated="updateGradientValue2"
        :gradient-default-value="gradientValue2"
      >
        Gradient end color (R, G, B)
      </CustomInput>
      <div
        class="content-wrapper content-wrapper_col content-wrapper_center"
        id="xor_container"
      >
        <label for="xor" class="text_grayed-out">
          gradientValue1 \ gradientValue2 = </label
        >
        <div id="xor">
          {{
            diffArray.length === 0
              ? "Show the square to calculate the difference"
              : diffArray
          }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import CustomButton from "./components/CustomButton.vue";
import CustomSquare from "./components/CustomSquare.vue";
import CustomInput from "./components/CustomInput.vue";

export default {
  name: "app",
  components: {
    CustomButton,
    CustomSquare,
    CustomInput,
  },
  data() {
    return {
      showSquare: false,
      gradientValue1: "62, 161, 219",
      gradientValue2: "93, 52, 236",
      diffArray: [],
    };
  },
  methods: {
    toggleSquare() {
      this.showSquare = !this.showSquare;
      if (this.showSquare) {
        this.createNewArray();
      } else {
        this.diffArray = [];
      }
    },
    updateGradientValue1(value) {
      this.gradientValue1 = value;
    },
    updateGradientValue2(value) {
      this.gradientValue2 = value;
    },
    createNewArray() {
      const array1 = this.gradientValue1.split(",").map((item) => item.trim());
      const array2 = this.gradientValue2.split(",").map((item) => item.trim());

      this.diffArray = array1.filter((item) => !array2.includes(item));
    },
  },
};
</script>

<style>
body {
  background-color: #1a1a1a;
  height: 100vh;
}

#app {
  display: flex;
  justify-content: center;
  flex-direction: column;
  height: 100%;
}

.content-wrapper {
  display: flex;
}

.content-wrapper_col {
  flex-direction: column;
}

.content-wrapper_center {
  align-items: center;
}

#xor_container {
  margin-top: 1rem;
}

#xor_container * {
  color: #96979b;
}
</style>
