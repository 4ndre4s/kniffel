<template>
  <div class="board-container">
    <div class="board"></div>
  </div>
</template>

<script>
export default {
  name: "KniffelBoard",
};
</script>

<style scoped>
.board-container {
  width: 100%;
  height: calc(100% - 36px);
  padding-top: 2rem;
  background: var(--color-grey--light);
}
.board {
  height: 50px;
  width: 100%;
  border: 1px solid var(--color-grey);
  border-radius: 5px;
  background: white;
}
</style>
