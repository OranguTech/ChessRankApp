<template>
    <div class="sign-up">
        <p>create account</p>
        <input type="text" v-model="email" placeholder="Email"><br />
        <input type="password" v-model="password" placeholder="Password"><br />
        <button v-on:click="signUp">Sign Up</button>
        <span>or go back to <router-link to="/login">login</router-link></span>
    </div>
</template>

<script>
    import firebase from 'firebase'

    export default {
        name: 'signUp',
        data: function() {
            return {
              email: '',
              password: ''
            }
        },
        methods: {
          signUp: function () {
            console.log(`firebase signup for ${this.email}`);
            firebase.auth().createUserWithEmailAndPassword(this.email, this.password).then(
              (user) => {
                this.$router.replace('games')
              },
              (err) => {
                console.log("Account failure: " + err);
              }
            );
          }
        }
    }
</script>

<style scoped>
  .signUp {
    margin-top: 40px;
  }
</style>
