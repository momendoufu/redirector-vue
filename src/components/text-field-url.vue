<template>
  <v-form>
    <v-container>
          <v-text-field
            v-model="inputValue"
            label="Your URL link"
            hint="https://hogehoge.com/"
            persistent-hint
            outlined
            background-color="white"
            color="blue"
          ></v-text-field>
    </v-container>
  </v-form>
</template>

<script>
export default{
  props: {
    value: {
      type: String,
      default: ""
    }
  },
    data(){
        return {
        }
    },
    computed: {
      inputValue: {
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

<!--
arg1...カスタムイベントの名前(親側で@receiveurlとして使う),arg2...渡すデータ
-->
