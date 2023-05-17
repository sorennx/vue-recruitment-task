<template>
  <div class="content-wrapper content-wrapper_center">
    <div class="form-group field">
      <label for="gradientInputField" class="form_label"><slot></slot></label>
      <input
        id="gradientInputField"
        v-model="inputGradientValue"
        @input="updateGradient"
        class="form-field"
        :style="{ color: computeInputTextColor }"
        :placeholder="gradientDefaultValue"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: "CustomInput",
  props: {
    gradientDefaultValue: {
      type: String,
    },
  },
  data() {
    return {
      inputGradientValue: this.gradientDefaultValue,
      isInputGradientValid: true,
    };
  },
  methods: {
    // Method responsible for the input validation for the RGB values
    // The string has to contain 3 numbers seperated by commas from range 0 - 255 (inclusive)
    // 1, 33, 7 etc. -> valid
    // 1, ,7 etc. -> not valid
    validateInputGradient() {
      const regex =
        /^(?:\d{1,2}|1\d{2}|2[0-4]\d|25[0-5])(?:\s*,\s*(?:\d{1,2}|1\d{2}|2[0-4]\d|25[0-5])){2}$/;
      this.isInputGradientValid = regex.test(this.inputGradientValue);
    },

    // Method that calls the validator method & emits the `inputGradientValue` variable to the parent component
    updateGradient() {
      this.validateInputGradient();
      this.$emit("gradient-input-updated", this.inputGradientValue);
    },
  },
  computed: {
    // Method responsible for updating the style of the input so when the input value are incorrect,
    // the color of the text is set to red
    computeInputTextColor: function () {
      return this.isInputGradientValid ? null : "#D2042D";
    },
  },
};
</script>

<style scoped>
.form-group {
  position: relative;
  padding: 15px 0 0;
  margin-top: 10px;
}
.form-field {
  font-family: inherit;
  width: 100%;
  border: 0;
  border-bottom: 2px solid #ffffff;
  outline: 0;
  font-size: 1.3rem;
  color: #ffffff;
  padding: 7px 0;
  background: transparent;
  transition: border-color 0.2s;
  cursor: text;
}

.form_label {
  position: absolute;
  top: 0;
  display: block;
  transition: 0.2s;
  font-size: 1rem;
  color: #ffffff;
}
</style>
