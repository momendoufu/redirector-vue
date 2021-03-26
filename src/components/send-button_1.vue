<!--
@click="loader='loading'"
sendRequest
-->

<template>
  <div class="text-center">
      <v-btn
        v-model="inputValue"
        :loading="loading"
        :disabled="loading"
        color="cyan darken-3"
        elevation="5"
        large
        height=""
        width=""
        class="ma-2 white--text"
        @click="sendRequest"
      >
        Generate!
        <v-icon
          right
          dark
        >
          mdi-progress-upload
        </v-icon>
      </v-btn>
    </div>
</template>

<script>
import axios from 'axios'

  export default {
    props: ['url', 'limit', 'value'],


    data () {
      return {
        loader: null,
        loading: false,
        response: "",
        status: "",
        wrappedURL: "",
      }
    },

    methods: {
      sendRequest(){
        axios.post("https://api.abex.dev/laug/generateurl",{
          dest: this.url,
          limit: this.limit
        })
        .then(response => {
          console.log(response.data),
          this.response = response,
          this.status = response.data.status,
          this.wrappedURL = response.data.wrappedURL
          console.log(this.wrappedURL)
        })
        .catch(error => {
          console.log(error);
        });
      },
    },

    computed: {
      inputValue: {
        get() {
          return this.value;
        },
        set(value) {
          this.$emit('input', value);
        }
      },
      generateURL(){
        return "https://api.abex.dev/laug/l/" + this.wrappedURL
      }
    },

    watch: {
      loader () {
        const l = this.loader
        this[l] = !this[l]

        setTimeout(() => (this[l] = false), 3000)

        this.loader = null
      },
    },
  }
</script>

<style>
  .custom-loader {
    animation: loader 1s infinite;
    display: flex;
  }
  @-moz-keyframes loader {
    from {
      transform: rotate(0);
    }
    to {
      transform: rotate(360deg);
    }
  }
  @-webkit-keyframes loader {
    from {
      transform: rotate(0);
    }
    to {
      transform: rotate(360deg);
    }
  }
  @-o-keyframes loader {
    from {
      transform: rotate(0);
    }
    to {
      transform: rotate(360deg);
    }
  }
  @keyframes loader {
    from {
      transform: rotate(0);
    }
    to {
      transform: rotate(360deg);
    }
  }
</style>
