<template>
  <section class="container">
    <div>
      <h2 class="subtitle">
        {{msg}}
      </h2>
    </div>

  </section>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      msg: ''
    }
  },
  asyncData({ params }) {
    return axios.get('https://api.apiopen.top/singlePoetry').then(({ data }) => {
      return { msg: data.result.content }
    }).catch(err => { console.log(err) })
  },
}
</script>

<style>
.container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
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

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
