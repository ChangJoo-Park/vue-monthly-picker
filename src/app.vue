<template>
  <div id="app">
    <img src="./assets/logo.png">
    <h3>Vue Monthly Picker</h3>
    <div class="demo-component">
      <vue-monthly-picker
       :inputClass="{'input': isDisplayInput}"
       :disabled="isDisable"
       :monthLabels="locale"
       v-model="selectedMonth">
      </vue-monthly-picker>
    </div>
    <b-field grouped class="control-group">
      <b-field label="State" expanded>
          <b-checkbox v-model="isDisable">
              Disabled
          </b-checkbox>
      </b-field>
      <b-field label="Display" expanded position="is-centered">
          <b-switch v-model="isDisplayInput"
              true-value="Input"
              false-value="Label">
              {{ isDisplayInput? 'Input': 'Label' }}
          </b-switch>
      </b-field>

      <b-field label="Localization" expanded>
          <b-select placeholder="Select a language" v-model="locale">
              <option
                  v-for="option in options"
                  :value="option.monthLabels"
                  :key="option.id">
                  {{ option.title }}
              </option>
          </b-select>
      </b-field>
    </b-field>
  </div>
</template>

<script>
import moment from 'moment'
import VueMonthlyPicker from './lib'

export default {
  name: 'app',
  data () {
    return {
      selectedMonth: moment(),
      isDisable: false,
      isDisplayInput: true,
      locale: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'],
      options: [
        {
          id: 1,
          title: 'English',
          monthLabels: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec']
        },
        {
          id: 2,
          title: 'Japanese',
          monthLabels: ['1月', '2月', '3月', '4月', '5月', '6月', '7月', '8月', '9月', '10月', '11月', '12月']
        }
      ]
    }
  },
  components: {
    VueMonthlyPicker
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.demo-component {
  width: 250px;
  margin: auto;
}
.control-group {
  margin-top: 100px;
}
.control {
  text-align: center;
}
</style>
