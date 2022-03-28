<template>
  <div class="nav-bar">Kniffel</div>
</template>

<script>
export default {
  name: "NavBar",
};
</script>

<style scoped>
.nav-bar {
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.5rem;
  font-weight: bold;
  background-color: var(--color-blue--dark);
  color: white;
  padding: 4px 0;
  width: 100%;
}
</style>
