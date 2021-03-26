<template>
  <v-app>
    <v-main>
      <div class="inputForm">
        <div class="url">
          <urlField></urlField>
        </div>
        <div class="slider">
          <slider></slider>
        </div>
    </div>
    </v-main>
  </v-app>
</template>

<script>
import urlField from './components/text-field-url'
import slider from './components/sample-slider'

export default {
  name: 'App',
  components: {
    urlField,
    slider
  },
  data: () => ({
    //
  }),
};
</script>

<style>
template {
  background-image: url(./static/sample.jpg);
  background-size: cover;
}


.inputForm{
  height: 600px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.url{
  flex: 0 0 35%;
}
.slider{
  flex: 0 0 16%;
}

</style>
