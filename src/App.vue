<template>
  <div class="page-container">
    <nav-bar />
    <kniffel-board />
  </div>
</template>

<script>
import NavBar from "@/components/NavBar";
import KniffelBoard from "@/components/KniffelBoard";
export default {
  name: "App",
  components: { KniffelBoard, NavBar },
};
</script>

<style scoped>
.page-container {
  height: 100%;
}
</style>

<style lang="scss">
:root {
  --color-blue--light: #85c0f9;
  --color-blue: #268ff6;
  --color-blue--dark: #041a56;
  --color-grey--light: #f5f5f5;
  --color-grey: #bbbbbb;
  --color-grey--dark: #9a9797;
}

*,
*::before,
*::after {
  box-sizing: border-box;
}

* {
  margin: 0;
}

html,
body,
#app {
  height: 100%;
}

button {
  font: inherit;
}
</style>
