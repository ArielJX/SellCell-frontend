<template>
  <header>

  </header>

  <div class="signup-form">
    <h2 class="center">Create a personal account</h2>
    <div class="img-wrapper center">
      <img class="signup-img" src="../image/uploaded-icon.png" alt="">

    </div>
    <span class="center">Upload profile photo</span>
    <div class="signup-box center">
      <div class="signup-box--info">
        <label>User Name</label>
        <input type="text" name="username" v-model="username">
      </div>
      <div class="signup-box--info">
        <label>Email</label>
        <input type="text" name="email" v-model="email">
      </div>
      <div class="signup-box--info">
        <label>Password</label>
        <input type="text" name="password" v-model="password">
      </div>
      <div class="signup-box--info">
        <label>Confirm Password</label>
        <input type="text" name="confirm_password" v-model="confirm_password">
      </div>
    </div>
    <button class="mt-1 center" @click="registerForm" type="button">Create</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      username: null,
      email: null,
      password: null,
      confirm_password: null,
      registerArray: []
    };
  },
  methods: {
    async registerForm() {
      console.log("register form");
      const response = await fetch("http://localhost:3000/register", {
        method: "POST",
        headers: { "content-type": "application/json" },
        body: JSON.stringify({
          username: this.username,
          email: this.email,
          password: this.password,
          confirm_password: this.confirm_password
        })
      });
      const data = await response.text();
      this.$router.push('/login');
      alert("Registered Succefully, please log in.")
    },
  }
}
</script>

<style lang="scss" scoped>
.signup-form {
  margin: 4em auto;
  width: 60%;
  max-width: 680px;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

h2 {
  font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
}

span {
  margin-bottom: 4em;
}

input {
  height: 36px;
  margin-bottom: 2em;
}

label {
  font-family: sans-serif;
  font-size: 20px;
}

.img-wrapper {
  width: 220px;
  height: 220px;
}

.center {
  align-self: center;
}

.mt-1 {
  margin-top: 1em;
}

img {
  width: 100%;
}

.signup-box {
  width: 360px;
}

.signup-box--info {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
}

button {
  color: white;
  background-color: #1950DA;
  border: none;
  border-radius: 2px;
  padding: 1em 2em;
  margin-bottom: 4em;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  font-size: 16px;
}
</style>
