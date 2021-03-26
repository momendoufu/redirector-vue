<template>
  <v-card
    flat
    color="transparent"
  ><v-card-text>
          <v-slider
            color="orange lighten-2"
            input :type="type"
            v-model="slider"
            label="limit"
            track-color="white"
            step=1
            thum-label
            ticks
            :max=10
            :min=1
            hide-details
            style="width: 300px"
          ><template v-slot:append>
            <v-text-field
              class="mt-0 pt-0"
              v-model="slider"
              hide-details
              single-line
              type="number"
              style="width: 60px"
            ></v-text-field>
            </template>
          </v-slider>
    </v-card-text>
  </v-card>
</template>

<script>
  export default {
    props: {
      value: {
        default: ""
      }
    },
    data () {
      return {
      }
      /*slider:1*/
    },
    computed: {
      slider: {
        get() {
          return this.value;
        },
        set(value) {
          this.$emit('input', value);
        }
      }
    }
  }
</script>

<style>

</style>
