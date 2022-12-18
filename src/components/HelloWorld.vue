<template>
  <div class="wrapper">
    <div>
      <h2>Something</h2>
      <button @click="openManageColor">Open Modal with Adding Color</button>
    </div>
    <ManageColor
        v-if="manageColorIsOpen"
        :colorName="color.name"
        :colorValue="color.value"
        @onClose="closeManageColor"
        @colorChange="handleColorChange"
    />
  </div>
</template>

<script>
import ManageColor from "./ManageColor";

export default {
  name: "HelloWorld",
  components: {
    ManageColor,
  },
  directives: {},
  data: function () {
    return {
      manageColorIsOpen: false,
      color: {
        name: 'primary',
        value: 'red'
      }
    };
  },
  props: {},
  methods: {
    handleColorChange(color) {
      console.log({color})
    },
    handleCloseManageColor(event) {
      console.log("Event: ")
      console.log(event)
      this.manageColorIsOpen = false;
    },
    closeManageColor() {
      console.log("jbsadlfjhkdsl")
      this.manageColorIsOpen = false;
    },
    openManageColor() {
      this.manageColorIsOpen = true;
    },
    toggleManageColor() {
      this.manageColorIsOpen = !this.manageColorIsOpen;
    },
  },
};
</script>
<style>
.wrapper {
  width: 600px;
  padding: 24px;
  background-color: yellow;
  position: relative;
  color: red;
}
</style>