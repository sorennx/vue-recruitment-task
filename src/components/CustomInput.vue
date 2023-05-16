<template>
  <div class="content-wrapper content-wrapper_center">
    <div class="form-group field">
      <label for="gradientInputField" class="form_label">Square gradient</label>
      <input
        id="gradientInputField"
        v-model="inputGradientValue"
        @input="updateGradient"
        class="form-field"
        placeholder="linear-gradient(109.6deg, rgb(62, 161, 219) 11.2%, rgb(93, 52, 236) 100.2%)"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: "CustomInput",
  data() {
    return {
      inputGradientValue:
        "linear-gradient(109.6deg, rgb(62, 161, 219) 11.2%, rgb(93, 52, 236) 100.2%)",
    };
  },
  methods: {
    updateGradient() {
      this.$emit("gradient-input-updated", this.inputGradientValue);
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
