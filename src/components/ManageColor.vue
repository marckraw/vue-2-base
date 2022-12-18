<template>
  <div class="manage-color-wrapper" v-click-outside="handleClose">
    <h1>Manage Color Modal</h1>
    <div>
      <h2>Add</h2>
    </div>
    <div class="uk-flex">
      <input class="uk-width-1-4" type="color" :value="newColor.value" @input="onColorValueChange" />
      <input class="uk-width-1-1" :value="newColor.value" @input="onColorValueChange" />
      <input class="uk-width-1-1" :value="newColor.name" @input="onColorNameChange" />
    </div>
    <button class="manage-color-wrapper__close" @click="handleClose">
      x
    </button>
    <div>
      <button @click="handleAddColor">Add</button>
    </div>
  </div>
</template>

<script>

export default {
  name: "ManageColor",
  components: {},
  directives: {},
  data: function () {
    return {
      newColor: {
        name: this.colorName || "",
        value: this.colorValue || "",
      },
    };
  },
  props: {
    colorValue: {
      type: String
    },
    colorName: {
      type: String
    },
    onClickOutside: {
      type: Function,
    },
    isOpen: {
      type: Boolean
    }
  },
  methods: {
    handleClose() {
      this.$emit('onClose')
    },
    onColorValueChange(event) {
      const colorValue = event.target.value
      this.newColor.value = colorValue

      this._handleColorChange()
    },
    onColorNameChange(event) {
      const colorName = event.target.value
      this.newColor.name = colorName

      this._handleColorChange()
    },
    _handleColorChange() {
      this.$emit('colorChange', {
        name: this.newColor.name,
        value: this.newColor.value
      })
    },
    handleAddColor() {
      console.log("Adding color...");
      // code for adding color to datasource
    },
    handleEditColor() {
      console.log("Editing selected color...");
      // code for editing color to datasource
    },
  },
};
</script>
<style>
.manage-color-wrapper {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 90%;
  height: 128px;
  padding: 12px;
  border: 1px solid #efefef;
  background-color: white;

  &__close {
    position: absolute;
    top: 8px;
    right: 8px;
  }
}
</style>