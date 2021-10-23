<template>
  <v-app>
    <div id="signup-container">
      <v-card class="mx-auto" width="450px" height="300px" style="margin-top:200px">
        <v-card-title>
          <h1 class="display-1">新規登録</h1>
        </v-card-title>
        <v-card-text>
          <v-form>
            <v-text-field
              label="メールアドレス"
              type="email"
              prepend-icon="mdi-email"
              v-model="mail"
              :rules="emailRules"
            />
            <v-text-field
              label="パスワード"
              :type="showPassWord ? 'text' : 'password'"
              prepend-icon="mdi-lock"
              v-bind:append-icon="showPassWord ? 'mdi-eye' : 'mdi-eye-off'"
              @click:append="showPassWord = !showPassWord"
              v-model="password"
            />
            <v-card-actions>
              <v-btn>登録</v-btn>
            </v-card-actions>
          </v-form>
        </v-card-text>
      </v-card>
    </div>
  </v-app>
</template>
<script>
export default {
  data() {
    return {
      showPassWord: false,
      mail: "",
      password: "",
      emailRules: [
        v => !!v || "E-mail is required",
        v => /.+@.+/.test(v) || "E-mail must be valid"
      ]
    };
  }
};
</script>

<style lang="scss" scoped>
#signup-container {
  height: 100%;
  
  & .v-card {
    background-color: rgba(201, 209, 236, 0.9);
    & .v-btn{
        background-color: rgba(57, 222, 228, 0.4);
    }
  }
}
</style>
