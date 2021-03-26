<template>
  <v-app>
    <v-main>
      <bgimage class="bg"/>
      <h1 class="title">Limited access-link generator</h1>
      <div class="inputForm">
        <div class="url">
          <urlField v-model="url"></urlField>
        </div>
        <div class="slider">
          <slider v-model="limit"></slider>
        </div>
    </div>
    <send
    class="send"
    @child-event="redirecturl"
    :url="url"
    :limit="limit"
    ></send>
    <div class="outurl">
      <a v-if="wrappedurl" :href="generateURL">Redirect LINK</a>
    </div>
  </v-main>
  </v-app>
</template>

<script>
import urlField from './components/text-field-url'
import slider from './components/sample-slider'
import bgimage from './components/background-image'
import send from './components/send-button'

export default {
  name: 'App',
  components: {
    urlField,
    slider,
    bgimage,
    send,
  },
  data (){
    return {
      generate: "",
      message: "",
      url: "",
      limit: "",
      wrappedurl: ""
    }
  },
  methods: {
    redirecturl(wrappedURL){
      this.wrappedurl= wrappedURL;
    }
  },
  computed: {
    generateURL(){
      return "https://api.abex.dev/laug/l/" + this.wrappedurl
    }
  }
};
</script>

<style lang="scss" scoped>

.bg {
  position: absolute;
}

.title {
  background-color: transparent;
  color: white;
  -webkit-transform: scale(2.6); /*alternate font-size(only chrome?)*/
  text-shadow: 2px 2px 0 rgba(0,0,0,.2);
  margin-top: 120px;
  display: flex;
  justify-content: center;

  position: relative;
}

.inputForm{
  background-color: rgba(255, 255, 255, 0.25);
  border-radius: 5px;
  backdrop-filter: blur(8px);
  margin-top: 140px;
  margin-left: 300px;
  margin-right: 300px;
  width: auto;
  padding: 44px 0;

  display: flex;
  justify-content: center;
  align-items: center;

  position: relative;

}
/* flex-grow | flex-shrink | flex-basis */
.url{
  flex: 0 0 50%;
}
.slider{
  flex: 0 0 25%;
}

.send {
  margin: 5%;
}

a{
  text-decoration: none;
}
a:link, a:visited{
  color: slategray;
}
a:hover {
  color: deepskyblue;
}

.outurl {
  background-color: rgba(255, 255, 255, 0.5);
  font-size: 36px;
  font-family: "游ゴシック";
  display: flex;
  justify-content: center;


  margin-left: 800px;
  margin-right: 800px;

  border: 2px solid slategray;
  border-radius: 30px;

  position: relative;
}



</style>
