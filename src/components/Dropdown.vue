<template>
  <div class="dropdown">
    <select
      v-model="selectedOption"
      @input="event => { $emit('input', event.target.value) }"
      >
      <option v-for="(option, name) in options" :value="option">{{ name }}</option>
    </select>
  </div>
</template>

<script>

export default {
  props: {
    value: null,
    options: {
      type: Object,
      required: true
    }
  },

  data () {
    return {
      selectedOption: null
    }
  },

  mounted () {
    this.selectedOption = this.value
  },

  watch: {
    value: function (newValue) {
      this.selectedOption = newValue
    }
  }
}

</script>

<style scoped>

.dropdown {
  display: inline-block;
}

</style>
