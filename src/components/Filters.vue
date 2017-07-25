<template>
  <div class="filters">

    <div class="filter">
      <label for="basic-dropdown">Basic dropdown: </label>
      <select name="basic-dropdown" v-model="selectedFruit">
        <option>Apple</option>
        <option>Banana</option>
        <option>Blueberry</option>
        <option>Kiwi</option>
        <option>Pear</option>
        <option>Pineapple</option>
        <option>Watermelon</option>
      </select>
    </div>

    <div class="filter">
      <label for="component-dropdown">Component-based dropdown: </label>
      <dropdown id="component-dropdown" :options="fruitOptions" v-model="selectedFruit"></dropdown>
    </div>

    <div class="filter">
      <label for="autocomplete-dropdown">Autocomplete dropdown: </label>
      <autocomplete-dropdown
        id="autocomplete-dropdown"
        :options="fruitOptions"
        v-model="selectedFruit"
        placeholder="Enter a fruit name"
      ></autocomplete-dropdown>
    </div>

    <div class="result">
      Selected: <strong>{{ selectedFruit}}</strong>
    </div>

    <div class="filter">
      <date-range-picker v-model="selectedDateRange"></date-range-picker>
    </div>

    <div class="filter">
      <date-range-picker v-model="selectedDateRange"></date-range-picker>
    </div>

    <div class="result">
      Selected range: <strong v-if="selectedDateRange">{{ selectedDateRangeFormatted }}</strong>
    </div>

  </div>
</template>

<script>

import Dropdown from '@/components/Dropdown'
import AutocompleteDropdown from '@/components/AutocompleteDropdown'
import DateRangePicker from '@/components/DateRangePicker'

import moment from 'moment'

export default {
  components: {
    'dropdown': Dropdown,
    'autocomplete-dropdown': AutocompleteDropdown,
    'date-range-picker': DateRangePicker
  },

  data () {
    return {
      selectedFruit: 'Apple',
      fruitOptions: {
        'Apple': 'Apple',
        'Banana': 'Banana',
        'Blueberry': 'Blueberry',
        'Kiwi': 'Kiwi',
        'Pear': 'Pear',
        'Pineapple': 'Pineapple',
        'Watermelon': 'Watermelon'
      },
      selectedDateRange: null
    }
  },

  computed: {
    selectedDateRangeFormatted () {
      if (this.selectedDateRange) {
        return moment(this.selectedDateRange.from).format('L LT') + ' - ' + moment(this.selectedDateRange.to).format('L LT')
      } else {
        return 'None'
      }
    }
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.filters {
  width: 800px;
  margin: 0 auto;
}

.filter {
  text-align: left;
}

.result {
  margin: 30px 0;
  text-align: left;
}

label {
  display: block;
}

</style>
