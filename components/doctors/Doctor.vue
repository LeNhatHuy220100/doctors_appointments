<template>
  <div>
    <v-card width="300" class="card">
      <v-card-title>{{ doctor.doctor_name }}</v-card-title>
      <Nuxt-link
        style="text-decoration: none"
        :to="`calendar?id=${doctor.doctor_id}`"
      >
        <v-btn>Xem chi tiết</v-btn>
      </Nuxt-link>
    </v-card>
  </div>
</template>

<script>
import { defineComponent } from "@nuxtjs/composition-api";
export default defineComponent({
  props: ["doctor"],
  setup(props) {
    return {};
  },
});
</script>

<style scoped>
.card {
  padding: 15px;
  background: rgb(152, 209, 152);
}
</style>
