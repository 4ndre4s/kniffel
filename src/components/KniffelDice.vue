<template>
  <div class="dice" @click="$emit('toggle-lock:dice')">
    <div class="dice-eye-container">
      <div
        class="dice-eye-row"
        v-for="diceRow in diceEyeRows"
        :key="diceRow.id"
      >
        <div
          class="dice-eye"
          v-for="diceEye in diceRow.eyes"
          :key="diceEye.id"
          :class="{ active: diceEye.values.includes(value) }"
        ></div>
      </div>
    </div>

    <div class="lock">
      {{ locked ? "🔒" : "" }}
    </div>
  </div>
</template>

<script>
export default {
  name: "KniffelDice",
  props: {
    value: {
      type: Number,
      required: true,
    },
    locked: {
      type: Boolean,
      required: true,
    },
  },
  data() {
    return {
      //TODO: data structure is symmetric, 6-9 is obsolete
      diceEyeRows: [
        {
          id: 1,
          eyes: [
            { id: 1, values: [2, 3, 4, 5, 6] },
            { id: 3, values: [4, 5, 6] },
          ],
        },
        {
          id: 2,
          eyes: [
            { id: 4, values: [6] },
            { id: 5, values: [1, 5] },
            { id: 6, values: [6] },
          ],
        },
        {
          id: 3,
          eyes: [
            { id: 7, values: [4, 5, 6] },
            { id: 9, values: [2, 3, 4, 5, 6] },
          ],
        },
      ],
    };
  },
};
</script>

<style scoped lang="scss">
.dice {
  align-items: center;
  background: var(--color-blue--light);
  border-radius: 10px;
  color: white;
  cursor: pointer;
  display: flex;
  height: 50px;
  justify-content: center;
  position: relative;
  width: 50px;
}
.lock {
  left: 90%;
  position: absolute;
  top: 90%;
  transform: translate(-50%, -50%);
}

.dice-eye-row {
  display: flex;
  justify-content: space-between;

  &:not(:last-child) {
    margin-bottom: 5px;
  }
}

.dice-eye {
  visibility: hidden;
  width: 9px;
  height: 9px;
  border-radius: 50%;

  background: white;

  &:not(:last-child) {
    margin-right: 5px;
  }

  &.active {
    visibility: visible;
  }
}
</style>
