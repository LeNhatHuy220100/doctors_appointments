<template>
  <div id="calendar">
    <Header :title="`Lịch Khám`" :doctorId="doctor_id" />
    <CalendarVuetify
      v-if="docs && docs.length > 0"
      :doctor="getDoctor(doctor_id, docs)"
    />
  </div>
</template>

<script>
import {
  defineComponent,
  onMounted,
  ref,
  useRoute,
} from "@nuxtjs/composition-api";

export default defineComponent({
  setup() {
    const route = useRoute();
    const docs = ref([]);
    const doctor_id = ref(route.value.query.id);

    const getDoctor = (id, list) => {
      let doctor = {};
      if (list && list.length >= 0) {
        doctor = list.find((doc) => doc.doctor_id === Number(id));
      }

      return doctor;
    };

    onMounted(() => {
      docs.value = JSON.parse(localStorage.getItem("doctors") || "");
    });

    return { doctor_id, getDoctor, docs };
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

#calendar {
  margin: 0 3%;
}
</style>
