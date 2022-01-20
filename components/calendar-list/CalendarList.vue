<template>
  <div class="calendar-list">
    <table>
      <tr v-for="(item, index) in timeList" :key="index">
        <td class="time">
          <p style="color: rgb(240, 240, 240)">aa</p>
          <p class="time-text">{{ item }}</p>
        </td>
        <td class="items">
          <Wrap v-for="(calendar, index) in appointments" :key="index">
            <CalendarItem v-if="isRightTime(item, calendar)" :item="calendar" />
          </Wrap>
        </td>
      </tr>
    </table>
  </div>
</template>

<script>
import { defineComponent, computed, ref, toRefs } from "@vue/composition-api";

export default defineComponent({
  props: ["appointments"],
  setup(props) {
    const { appointments } = toRefs(props);

    const startTime = (time) => {
      let time_detail = time.split(" ")[1].split(":");
      return [time_detail[0], time_detail[1]].join(":");
    };

    const isRightTime = (time, calendar) => {
      const appointmentTime = startTime(calendar.start_time);
      return time === appointmentTime;
    };

    const timeList = computed(() => {
      const appoitment_calendar = appointments.value;
      let listTime = [];
      for (let app of appoitment_calendar) {
        listTime.push(startTime(app.start_time));
      }

      listTime = new Set(listTime);
      return listTime;
    });

    return { isRightTime, startTime, timeList };
  },
});
</script>

<style scoped>
.calendar-list {
  margin: 0 8%;
  padding: 5px;
  padding-left: 50px;
  padding-right: 20px;
  padding-top: 12px;
  background-color: rgb(240, 240, 240);
}

table {
  width: 100%;
  border-collapse: collapse;
}

tr {
  border: solid 1px rgb(161, 161, 218);
  border-left: 0;
}

table td.items {
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  padding-top: 10px;
  padding-bottom: 10px;
  padding-left: 8px;
  border-left: solid 1px rgb(161, 161, 218);
}

.time-text {
  position: absolute;
  left: 0;
  top: 0;
  transform: translate(-100%, -50%);
  font-size: 14px;
  font-weight: bold;
}

tr td.time {
  position: relative;
}
</style>
