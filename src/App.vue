<template>
  <div id="app" class="container">
    <h1>Node.js API Tester</h1>
    <div class="buttons">
      <button @click="fetchDate" class="btn">Get Date</button>
      <button @click="fetchTime" class="btn">Get Time</button>
      <button @click="fetchUptime" class="btn">Get Uptime</button>
    </div>
    <div v-if="result" class="result">
      <h2>Result:</h2>
      <p>{{ result }}</p>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "App",
  data() {
    return {
      result: null,
    };
  },
  methods: {
    async fetchDate() {
      try {
        const response = await axios.get("http://localhost:3000/date");
        this.result = response.data;
      } catch (error) {
        this.result = "Error fetching date.";
      }
    },
    async fetchTime() {
      try {
        const response = await axios.get("http://localhost:3000/time");
        this.result = response.data;
      } catch (error) {
        this.result = "Error fetching time.";
      }
    },
    async fetchUptime() {
      try {
        const response = await axios.get("http://localhost:3000/uptime");
        this.result = response.data;
      } catch (error) {
        this.result = "Error fetching uptime.";
      }
    },
  },
};
</script>

<style>
body {
  margin: 0;
  font-family: Arial, sans-serif;
  background-color: #f4f4f9;
  color: #333;
}

.container {
  max-width: 600px;
  margin: 50px auto;
  text-align: center;
  background: #fff;
  border-radius: 10px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  padding: 20px;
}

h1 {
  font-size: 2rem;
  color: #444;
}

.buttons {
  margin-top: 20px;
}

.btn {
  background-color: #007bff;
  color: white;
  border: none;
  padding: 10px 20px;
  margin: 10px;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.btn:hover {
  background-color: #0056b3;
}

.result {
  margin-top: 30px;
  padding: 10px;
  background: #f9f9f9;
  border-radius: 5px;
  border: 1px solid #ddd;
}

.result h2 {
  margin: 0 0 10px;
}

.result p {
  font-size: 1.2rem;
}
</style>
