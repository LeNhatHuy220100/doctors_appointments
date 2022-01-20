<template>
  <div class="calendar-item">
    <v-card class="calendar-item-card" :style="{ borderLeftColor: item.color }">
      <v-avatar class="avatar" size="28" v-if="item.avatar">
        <img :src="item.avatar" alt="John"
      /></v-avatar>
      <v-avatar class="avatar" size="28" v-else>
        <img
          src="https://cdn0.iconfinder.com/data/icons/set-ui-app-android/32/8-512.png"
        />
      </v-avatar>
      <p class="name">
        <strong>{{ item.name }}</strong>
      </p>
      <p class="symptom">{{ item.symptom }}</p>
    </v-card>
  </div>
</template>

<script>
import { defineComponent } from "@vue/composition-api";

export default defineComponent({ props: ["item"], setup() {} });
</script>

<style scoped>
.calendar-item-card {
  border-left: solid 10px;
}
.avatar {
  padding: 20px;
}
.calendar-item {
  width: 100%;
  height: 100%;
}

.calendar-item-card {
  padding: 10px;
  flex-grow: 1;
}

.calendar-item-card p {
  font-size: 10px;
}

.calendar-item-card p.name {
  font-size: 14px;
  margin-top: 5px;
  margin-bottom: 2px;
}

.calendar-item-card p.symptom {
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
</style>
