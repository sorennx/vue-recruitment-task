<template>
  <div id="app">
    <div class="content-wrapper content-wrapper_col content-wrapper_center">
      <CustomSquare :show-square="showSquare" :gradient-value="gradientValue"/>
      <CustomButton @toggle-square="toggleSquare" />
      <CustomInput @gradient-input-updated="updateGradientValue" />
    </div>
  </div>
</template>

<script>
import CustomButton from './components/CustomButton.vue'
import CustomSquare from './components/CustomSquare.vue'
import CustomInput from './components/CustomInput.vue'

export default {
  name: 'app',
  components: {
    CustomButton,
    CustomSquare,
    CustomInput,
  },
  data() {
    return {
      showSquare: false,
      gradientValue: 'linear-gradient(109.6deg, rgb(62, 161, 219) 11.2%, rgb(93, 52, 236) 100.2%)',
    }
  },
  methods: {
    toggleSquare() {
      this.showSquare = !this.showSquare
    },
    updateGradientValue(value) {
      this.gradientValue = value
      console.log(this.gradientValue);
    },
  },
}
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
</style>
