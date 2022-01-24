<template>
  <div id="app">
    <Header :title="title" />
    <Doctors :doctors="doctors" />

    <!-- <CalendarList :appointments="calendarDataByDate" /> -->
    <!-- <CalendarVuetify /> -->
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, onMounted } from "@nuxtjs/composition-api";
import axios from "axios";

export default defineComponent({
  setup() {
    let title = ref("Danh Sách Bác Sĩ");
    const doctors = ref(null);

    onMounted(() => {
      let data = JSON.parse(localStorage.getItem("doctors") || "");

      if (data) {
        doctors.value = data;
      } else {
        axios
          .get(
            "https://my-json-server.typicode.com/pqcuong737/jsonfakeserver/data"
          )
          .then((response) => {
            localStorage.setItem("doctors", JSON.stringify(response.data));
          })
          .catch((error) => {
            console.log(error);
          });
      }
    });

    return { title, doctors };
  },
});
</script>

<style scoped>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  font-family: sans-serif;
}

#app {
  margin: 0 3%;
}
</style>
