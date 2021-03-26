<template>
  <v-card
    width=500
  >
    <v-card-text>
      <v-row>
        <v-col class="pr-4">
          <v-slider
            v-model="value"
            label="limit"
            class="align-center"
            step=1
            thumb-label
            ticks
            tick-size=3
            min=1
            max=10
          ><sidenum :slider=value></sidenum>
        </v-slider>
        </v-col>
      </v-row>
    </v-card-text>
  </v-card>
</template>

<script>
import sidenum from './sidenum'

  export default {
    components: {sidenum},
    data () {
      return {
        value: 0,
      }
    },
  }
</script>
