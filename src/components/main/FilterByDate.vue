<template>
  <div class="filter">
    <div class="filter__wrapper">
      <label class="filter__label" for="input-from">От</label>
      <input
        aria-required="true"
        class="filter__input"
        id="input-from"
        type="date"
        v-model="dateFrom"
        :placeholder="dateFrom"
        @change="filteringData"
      />
    </div>
    <span class="filter__dash"> <hr> </span>
    <div class="filter__wrapper">
      <label class="filter__label" for="input-to">До</label>
      <input
        aria-required="true"
        class="filter__input"
        id="input-to"
        type="date"
        v-model="dateTo"
        :placeholder="dateTo"
        @change="filteringData"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: 'FilterByDate',
  data() {
    return {
      dateFrom: '',
      dateTo: '',
    }
  },
  methods: {
    filteringData() {
      this.$emit('filteringArticles', this.dateFrom, this.dateTo);
    },
  },
}
</script>

<style scoped lang="scss">
input[type="date"] {
  position: relative
}

input[type="date"]::-webkit-calendar-picker-indicator {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  width: auto;
  height: auto;
  color: transparent;
  background: transparent
}

input[type="date"]::-webkit-inner-spin-button,
input[type="date"]::-webkit-clear-button {
  z-index: -10
}

input[type="date"]::-webkit-input-placeholder {
  z-index: 99
}

input[type="date"]:before {
  width: 100%;
  content: attr(placeholder)
}
.filter {
  display: flex;
  align-items: center;
  padding: 16px;
  background-color: $white;
  -webkit-border-radius: 10px;
  -moz-border-radius: 10px;
  border-radius: 10px;
  &__wrapper {
    width: 45%;
    position: relative;
    display: flex;
    align-items: center;
  }
  &__input {
    width: 100%;
    font-size: 16px;
    color: $grey-color;
    outline: none;

  }
  &__date {
    position: absolute;
    right: 20px;
    color: fuchsia;
  }
  &__label {
    margin-right: 10px;
    cursor: pointer;
 }
  &__dash {
    margin: 0 10px;
    & > hr {
      width: 9px;
      height: 1px;
      background-color: $grey-color;
    }
  }
}
</style>
