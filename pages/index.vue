<template>
  <div id="app">
    <Header :title="title" />
    <Doctors :doctors="doctors" />

    <!-- <CalendarList :appointments="calendarDataByDate" /> -->
    <!-- <CalendarVuetify /> -->
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, useFetch } from "@nuxtjs/composition-api";
import axios from "axios";

export default defineComponent({
  setup() {
    let title = ref("Danh Sách Bác Sĩ");
    const doctors = ref(null);

    let data = JSON.parse(localStorage.getItem("doctors") || "");

    if (data) {
      doctors.value = data;
    } else {
      useFetch(async () => {
        try {
          const res = await axios.get(
            "https://my-json-server.typicode.com/pqcuong737/jsonfakeserver/data"
          );
          doctors.value = res.data;
          localStorage.setItem("doctors", JSON.stringify(res.data));
        } catch (error) {
          console.log(error);
        }
      });
    }

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

/* */
