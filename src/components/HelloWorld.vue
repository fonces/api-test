<template>
  <div class="hello">
    <input type="text" v-model="text" />
    <button type="button" @click="onPost">post</button>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      text: 'https://qiita.com/danishi/items/42d8adf6291515e62284',
    }
  },
  methods: {
    onPost() {
      const body = new FormData()
      body.append('url', this.text)
      axios.post('/api/v1/shorten', body)
        .then(r => alert(JSON.stringify(r)))
        .catch(e => console.error(e))
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
