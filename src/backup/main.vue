<template>
  <div id="redirect">
    <myheader></myheader>
    <h1>Limited access link generator</h1>
    <input type="url" v-model="url" placeholder="url here">
    <input type="number" v-model="limit" placeholder="limit(1-99)">
    <br>
    <br>
    <button @click="sendRequest()">ENTER</button>
    <br>
    <br>
    <p v-if="response">
      >response is ok
    </p>
    <p v-if="status">
      >status is ok
      <a :href="generateURL">Generate LINK</a>
    </p>
    <p v-else>
      >status is not ok
    </p>
    <br>
    <br>
    {{response}}
    <myfooter></myfooter>
  </div>
</template>

<script>
import myheader from './components/myheader'
import myfooter from './components/myfooter'
import axios from 'axios'

export default {
  components: {
    myheader, myfooter
  },
  data () {
    return {
      url: "",
      limit: "",
      status: "",
      wrappedURL: "",
      response: ""
    }
  },
  methods: {
    sendRequest () {
      axios.post("https://api.abex.dev/laug/generateurl",{
        dest: this.url,
        limit: this.limit
      })
      .then(response => {
        console.log(response),
        this.response = response,
        this.status = response.data.status,
        this.wrappedURL = response.data.wrappedURL
      })
      .catch(error => {
        console.log(error);
      });
    }
  },
  computed: {
    generateURL () {
      return "https://api.abex.dev/laug/l/" + this.wrappedURL
    }
  }
}
</script>

<style></style>
