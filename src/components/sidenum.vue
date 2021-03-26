<template v-slot:append>
  <v-text-field
    v-model=slider
    class="mt-0 pt-0"
    hide-details
    single-line
    type="number"
    style="width: 60px"
  ></v-text-field>
</template>

<script>
export default{
  props: ['slider'],
};
</script>
