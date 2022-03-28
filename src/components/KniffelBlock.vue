<template>
  <table class="block-table">
    <tr class="block-table-row" v-for="row in upperBlockRows" :key="row.label">
      <th class="block-table-cell">{{ row.label }}</th>
      <td class="block-table-cell">{{ row.value ? row.value : "0" }}</td>
      <td class="block-table-cell">
        {{ row.value ? "-" : countPotentialValue(row.count) }}
      </td>
      <td class="block-table-cell">
        <button
          @click="setValue(row)"
          class="select-button"
          :disabled="row.value != null"
        >
          Select
        </button>
      </td>
    </tr>
  </table>
</template>

<script>
export default {
  name: "KniffelBlock",
  props: {
    dices: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      upperBlockRows: [
        {
          id: 1,
          label: "Aces",
          value: null,
          count: 1,
        },
        {
          id: 2,
          label: "Twos",
          value: null,
          count: 2,
        },
        {
          id: 3,
          label: "Threes",
          value: null,
          count: 3,
        },
        {
          id: 4,
          label: "Fours",
          value: null,
          count: 4,
        },
        {
          id: 5,
          label: "Fives",
          value: null,
          count: 5,
        },
        {
          id: 6,
          label: "Sixes",
          value: null,
          count: 6,
        },
      ],
    };
  },
  methods: {
    countPotentialValue(rowCount) {
      return this.dices.reduce((acc, dice) => {
        if (dice.value === rowCount) {
          acc += dice.value;
        }
        return acc;
      }, 0);
    },
    setValue(row) {
      this.upperBlockRows.some((r) => {
        if (r.id !== row.id) {
          return false;
        }
        r.value = this.countPotentialValue(row.count);
        return true;
      });
    },
  },
};
</script>

<style scoped lang="scss">
.select-button {
  border-radius: 7px;
  background: var(--color-grey);
  border: none;
  color: white;

  &:disabled {
    color: var(--color-grey--dark);
  }
}

.block-table {
  border-collapse: collapse;
}

.block-table-row {
  &:last-child {
    .block-table-cell {
      border-bottom: none;
    }
  }
}

.block-table-cell {
  border: 1px solid grey;
  border-top: none;
  text-align: center;
  padding: 1px 0.25rem;

  &:first-child {
    text-align: left;
    border-left: none;
  }

  &:nth-child(2),
  &:nth-child(3) {
    padding: 0 5rem;
  }

  &:last-child {
    border-right: none;
  }
}
</style>
