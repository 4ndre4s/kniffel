<template>
  <div class="board-container">
    <div class="board">
      <div class="dice-container">
        <kniffel-dice v-for="dice in numberOfDices" :key="dice" class="dice" />
      </div>
      <kniffel-block />
    </div>
    <roll-dice-button />
  </div>
</template>

<script>
import KniffelDice from "@/components/KniffelDice";
import KniffelBlock from "@/components/KniffelBlock";
import RollDiceButton from "@/components/RollDiceButton";
export default {
  name: "KniffelBoard",
  components: { RollDiceButton, KniffelBlock, KniffelDice },
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
  align-items: center;
  background: white;
  border: 1px solid var(--color-grey);
  border-radius: 5px;
  display: flex;
  flex-direction: column;
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
