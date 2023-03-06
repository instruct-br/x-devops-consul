<template>
  <div id="app">
    <h3>
     {{ message }}
    </h3>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
        status: '',
        message: ''
    }
  },
async mounted() {
  await this.getHealthCheck()
  await this.getMessage()
 },

  methods: {
    async getHealthCheck(){
      const response = await fetch("http://localhost:8500/v1/health/checks/api")
      const data = await response.json();
      this.status = data[0].Status;
    },

    async getMessage(){
      if (this.status === 'critical') {
        this.message = "Server API is critical"
        return;
      }
      const response = await fetch("http://localhost:5000")
      this.message = await response.text();
    }
  }
}

</script>



<style>

#app {

  font-family: Avenir, Helvetica, Arial, sans-serif;

  -webkit-font-smoothing: antialiased;

  -moz-osx-font-smoothing: grayscale;

  text-align: center;

  color: #2c3e50;

  margin-top: 60px;

}

</style>
