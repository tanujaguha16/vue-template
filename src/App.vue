<template>
  <div id="app">
    <MyFile :msg="comdata"/>
    <datepicker v-model="dates" id="datepick"></datepicker>
     <br />
    <button @click="calculateSubmit()">Submit</button>
    {{showresult}}
  </div>
</template>

<script>
import moment from 'moment';

import Datepicker from 'vuejs-datepicker';

import MyFile from './components/MyFile';

export default {
  name: 'App',
  data() {
    return {
      comdata: 'Calculate you age',
      dates: new Date(),
      showresult: String,
    };
  },
  methods: {
    calculateSubmit() {
      const start = moment(this.dates, 'YYYY-MM-DD');
      const end = moment();
      const years = moment.duration(end.diff(start)).asYears().toFixed(2);
      const months = moment.duration(end.diff(start)).asMonths().toFixed(2);
      this.showresult = years > 1 ? years : months;
    },
  },
  components: {
    MyFile,
    Datepicker,
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.vdp-datepicker{
  margin: 0 auto;
  width: 194px;
  display: block;
}
</style>
