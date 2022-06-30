<template>
  <select
    class="select"
    v-model="selectedOption"
    @change="selectOption">
    <option>Выбор автора</option>
    <option
      v-for="(author, i) in authors"
      :key="i"
    >
      {{ author }}
    </option>
  </select>
</template>

<script>
export default {
  name: 'FilterByName',
  props: {
    authors: {
      type: Array,
    },
  },
  data() {
    return {
      selectedOption: 'Выбор автора',
    }
  },
  methods: {
    selectOption() {
        this.$emit('sortingArticles', this.selectedOption);
    },
  }
}
</script>

<style scoped lang="scss">
.select {
  width: 30%;
  padding: 16px 46px;
  margin-right: 20px;
  font-weight: 600;
  line-height: 20px;
  color: $grey-color;
  background: url('@/assets/images/main/select-arrow.svg') 95% 50% no-repeat,url('@/assets/images/main/select-user.svg') 5% 50% no-repeat, #fff;
  cursor: pointer;
  outline: none;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
  border: none;
  -webkit-border-radius: 10px;
  -moz-border-radius: 10px;
  border-radius: 10px;
}
</style>
