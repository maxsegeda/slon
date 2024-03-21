<template>
  <div>
    <ul>
      <li v-for="(call, index) in calls" :key="index" class="liCallHistory">
        <img src="" alt="" class="" />
        <div>
          <h3>{{ call.contact }}</h3>
          <p>{{ call.phoneId }}</p>
        </div>
        <div>
          <h3>{{ formatTime(call.date) }}</h3>
          <div>
            <img src="" alt="" class="" />
            <p>{{ call.duration }}</p>
          </div>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      calls: [],
    };
  },
  mounted() {
    this.fetchCalls();
  },
  methods: {
    async fetchCalls() {
      try {
        const response = await axios.get("http://localhost:3001/api/calls");
        this.calls = response.data;
      } catch (error) {
        console.error("Ошибка при получении данных с сервера", error);
      }
    },
    formatTime(time) {
      const date = new Date(parseInt(time));

      const hours = date.getHours().toString().padStart(2, 0);
      const minutes = date.getMinutes().toString().padStart(2, 0);

      return `${hours}:${minutes}`;
    },
  },
};
</script>
<style>
.liCallHistory {
  display: flex;
}
</style>
