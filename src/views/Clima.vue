<template>
  <div v-if="result" class="clima">
    <body>
    <div class="div1">
      <header>
        <p>
          <b>{{ result.name }}</b>
        </p>
      </header>
      <img
        :src="
          'http://openweathermap.org/img/w/' + result.weather[0].icon + '.png'
        "
        alt=" "
      />
      <p><b>{{ result.weather[0].description }}</b></p>
      <p>Temp: {{ result.main.temp }}</p>
      <p>Degrees: {{ result.wind.deg }}</p>
    </div>
    </body>
  </div>
</template>
<style>
.div1{
  background-color: rgb(172, 204, 204);
  font-weight: 100px;
  width: 300px;
  height: 300px;
  text-align: center;
  display: inline-block;
}
</style>
<script>
import axios from "axios";
export default {
  data: () => ({
    result: null,
  }),
  created() {
    axios
      .get(
        "https://api.openweathermap.org/data/2.5/weather?q=playa%20del%20carmen&APPID=fa0399aac44f59e263c7dce44971db2b"
      )
      .then((result) => {
        this.result = result.data;
        console.log(result.data);
      });
  },
};
</script>
