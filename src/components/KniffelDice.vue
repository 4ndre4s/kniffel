<template>
  <div class="dice" @click="$emit('toggle-lock:dice')">
    {{ value }}
    {{ locked ? "🔒" : "" }}
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
};
</script>

<style scoped>
.dice {
  width: 50px;
  height: 50px;
  border-radius: 10px;
  background: var(--color-blue--light);
  cursor: pointer;
}
</style>
