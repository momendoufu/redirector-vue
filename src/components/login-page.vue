<template>
  <v-card width="400px" class="mx-auto mt-5">
    <v-card-title>
      <h1 class="display-1">Login</h1>
    </v-card-title>
    <v-card-text>
      <v-form>
        <v-text-field label="User" prepend-icon="mdi-account-circle" />
        <v-text-field v-bind:type="showPassword ? 'text' : 'password'" label="PassWord" prepend-icon="mdi-lock" append-icon="mdi-eye-off" @click:append="showPassword = !showPassword" />
        <v-card-actions>
          <v-btn class="success">Login</v-btn>
        </v-card-actions>
      </v-form>
    </v-card-text>
  </v-card>
</template>

<script>
export default {
  data: () => ({
    showPassword : false
  })
};
</script>

<!--[ 条件式 ? 'trueの時に返す値' : 'falseの時に返す値' ]-->
