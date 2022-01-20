<template>
  <div id="calendar">
    <Header :title="`Lịch Khám`" :doctorId="doctor.doctor_id" />
    <CalendarVuetify :doctor="doctor" />
    <Footer />
  </div>
</template>

<script>
import { defineComponent } from "@nuxtjs/composition-api";

export default defineComponent({
  asyncData({ query }) {
    const doctor_id = query.id;
    const doctors = JSON.parse(localStorage.getItem("doctors") || "");
    const doctor = doctors.find((doc) => doc.doctor_id === Number(doctor_id));
    return { doctor };
  },
  setup() {},
});
</script>

<style scoped>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  font-family: sans-serif;
}

#calendar {
  margin: 0 3%;
}
</style>
