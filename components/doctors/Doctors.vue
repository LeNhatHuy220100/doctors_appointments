<template>
  <div class="doctors">
    <Doctor
      v-for="doctor in doctors"
      :key="doctor.doctor_id"
      :doctor="doctor"
    />
  </div>
</template>

<script>
import { defineComponent, ref } from "@nuxtjs/composition-api";
export default defineComponent({
  props: ["doctors"],
});
</script>

<style scoped>
.doctors {
  display: flex;
  justify-content: flex-start;
  gap: 10px;
  padding-top: 10px;
}
</style>
