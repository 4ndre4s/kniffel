<template>
  <div class="board-container">
    <div class="board">
      <div class="dice-container">
        <kniffel-dice v-for="dice in numberOfDices" :key="dice" class="dice" />
      </div>
    </div>
  </div>
</template>

<script>
import KniffelDice from "@/components/KniffelDice";
export default {
  name: "KniffelBoard",
  components: { KniffelDice },
  data() {
    return {
      numberOfDices: 5,
      dices: [],
    };
  },
};
</script>

<style scoped>
.board-container {
  background: var(--color-grey--light);
  height: calc(100% - 36px);
  padding-top: 2rem;
  width: 100%;
}
.board {
  background: white;
  border: 1px solid var(--color-grey);
  border-radius: 5px;
  display: flex;
  justify-content: center;
  width: 100%;
}
.dice-container {
  display: flex;
  margin: 1rem 0 0.5rem;
}
.dice:not(:last-of-type) {
  margin-right: 1rem;
}
</style>
