<template>
  <button class="roll-dice-button" @click="$emit('roll:dice')">Roll</button>
</template>

<script>
export default {
  name: "RollDiceButton",
};
</script>

<style scoped lang="scss">
.roll-dice-button {
  background: var(--color-blue);
  color: white;
  cursor: pointer;
  border: none;
  padding: 0.25rem 1rem;
  border-radius: 5px;

  &:active {
    background: var(--color-blue--light);
  }
}
</style>
