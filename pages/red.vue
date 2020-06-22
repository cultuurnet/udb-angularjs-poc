<template>
  <div class="container red">
    <div>
      <h1 class="title">
        red
      </h1>
      <p>message: {{ message }}</p>
      <button @click="doPostMessage">Klik hier</button>
    </div>
  </div>
</template>

<script>
export default {
  data: () => {
    return {
      message: '',
    }
  },
  mounted() {
    window.addEventListener('message', (event) => {
      const message = event.data
      console.log('message', message)
      this.message = message
    })
  },
  methods: {
    doPostMessage: () => {
      window.parent.postMessage('change color', '*')
    },
  },
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.red {
  background-color: red;
}
.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}
</style>
