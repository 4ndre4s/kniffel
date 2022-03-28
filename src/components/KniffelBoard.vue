<template>
  <div class="board-container">
    <div class="board">
      <div class="dice-container">
        <kniffel-dice
          v-for="dice in dices"
          :key="dice.id"
          class="dice"
          :value="dice.value"
          :locked="dice.isLocked"
          @toggle-lock:dice="toggleDiceLock(dice.id)"
        />
      </div>
      <kniffel-block />
    </div>
    <roll-dice-button @roll:dice="rollDices" />
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
      dices: [
        { id: 1, value: 0, isLocked: false },
        { id: 2, value: 0, isLocked: false },
        { id: 3, value: 0, isLocked: false },
        { id: 4, value: 0, isLocked: false },
        { id: 5, value: 0, isLocked: false },
      ],
    };
  },
  methods: {
    rollDices() {
      this.dices = this.dices.map((dice) => {
        if (dice.isLocked) {
          return dice;
        }

        return {
          ...dice,
          value: Math.floor(Math.random() * 6) + 1,
        };
      });
    },
    toggleDiceLock(diceId) {
      const dice = this.dices.find((dice) => dice.id === diceId);
      dice.isLocked = !dice.isLocked;
    },
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
