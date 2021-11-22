<template>
  <div>
    <div>
      <date-picker
        ref="datePicker"
        v-model="time1"
        type="date"
        :format="format"
        title-format="format"
        valueType="format"
        default-value="new Date()"
        :lang="lang"
        :formatter="momentFormat"
        placeholder="__.__.____"
      ></date-picker>
    </div>
    <p>
      {{ time1 }}
    </p>
  </div>
</template>

<script>
import DatePicker from "vue2-datepicker";
// import "vue2-datepicker/locale/ru";
import "vue2-datepicker/index.css";
import moment from "moment";

export default {
  components: { DatePicker },
  data() {
    return {
      format: "DD.MM.YYYY",
      time1: null,
      lang: {
        formatLocale: {
          firstDayOfWeek: 1,
        },
        monthBeforeYear: true,
      },
      momentFormat: {
        //[optional] Date to String
        stringify: (date) => {
          return date ? moment(date).format(this.format) : "";
        },
        // [optional]  String to Date
        parse: (value) => {
          return value ? moment(value, this.format).toDate() : null;
        },
        //[optional] getWeekNumber
        getWeek: (date) => {
          return date; // a number
        },
      },
    };
  },
  methods: {
    // formatDate(d) {
    //   // you could also provide your own month names array
    //   const months = this.$refs.datePicker.translation.months;
    //   console.log(d, months);
    //   return `${d.getDate().toString().padStart(2, 0)} ${
    //     months[d.getMonth()]
    //   } ${d.getFullYear()}`;
    // },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
