<template>
  <div class="form">
    <h1>SignUp</h1>
    <p>Create an account to PostIt!</p>
    <label for="email">E-mail</label>
    <input type="email" name="email" required v-model="email">
    <label for="password">Password</label>
    <input type="password" name="password" required v-model="password">
    <div v-if="errMsg">{{ errMsg }}</div>
    <button @click="SignUp" class="button">SignUp</button>
    <button @click="this.$router.push('/api/login')" class="button">Back to login</button>
  </div>
</template>

<script>
export default {
  name: "SignUp",
  data: function () {
    return {
      email: '',
      password: '',
      errMsg: '',
    }
  },
  watch: {
    password(value) {
      this.password = value;
      this.validatePassword(value);
    }
  },
  methods: {
    validatePassword(value) {
      if (value.length < 8 || value.length >= 16 || !/[A-Z]/.test(value) || !/[0-9]/.test(value)) {
        this.errMsg = "Password must be at least 8 characters  and less than 16 characters, it must include a capital letter and at least one number"
      } else {
        this.errMsg = ''
      }
    },
    SignUp() {
      var data = {
        email: this.email,
        password: this.password
      };
      fetch("http://localhost:3000/auth/signup", {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
        },
        credentials: 'include',
        body: JSON.stringify(data),
      })
          .then((response) => response.json())
          .then((data) => {
            console.log(data);
            this.$router.push("/api/login")
          })
          .catch((e) => {
            console.log(e);
            console.log("error");
          });
    },
  },
}
</script>

<style scoped>
.form {
  max-width: 420px;
  margin: 30px auto;
  text-align: left;
  padding: 40px;
  border-radius: 10px;
  background-color: #FEFAE0;
  box-shadow: 0px 0px 14px 0px, rgba(0, 0, 0, 0.3) 0px 3px 7px -3px;
  align-items: center;
  justify-content: center;
}

h3 {
  text-align: center;
  color: rgb(8, 110, 110);
}

label {
  color: rgb(8, 110, 110);
  display: inline-block;
  margin: 25px 0 15px;
  font-size: 0.8em;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
}

input {
  display: block;
  padding: 10px 6px;
  width: 100%;
  box-sizing: border-box;
  border: none;
  border-bottom: 1px solid white;
  color: blue;
}

button {
  padding: 10px 20px;
  margin: auto;
  background-color: #DDA15E;
  color: #FEFAE0;
  border: 3px solid #FEFAE0;
  border-radius: 5px;
  font-weight: bold;
  margin-top: 20px;
  width: 30%;
}

button:hover {
  color: #606C38;
  border-color: #283618;
}

.container {
  display: flex;
  justify-content: center;
}
</style>