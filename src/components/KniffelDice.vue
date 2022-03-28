<template>
  <div class="dice" @click="$emit('toggle-lock:dice')">
    {{ value }}
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
};
</script>

<style scoped>
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
</style>
