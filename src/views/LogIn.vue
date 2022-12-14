<template>
  <div class="form">
    <section>
      <h1>Welcome to PostIt</h1>
      <p><router-link to="/api/signup">Create an account</router-link> <br>
        or <br>
        please log in to see the post feed<br></p>
      <label for="email">E-mail</label>
      <input type="email" name="email" required v-model="email">
      <label for="password">Password</label>
      <input type="password" name="password" required v-model="password">
      <div class="container">
        <button @click="LogIn" class="button">Login</button>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: "LogIn",
  data: function () {
    return {
      email: '',
      password: '',
    }
  },
  methods: {
    LogIn() {
      var data = {
        email: this.email,
        password: this.password
      };
      fetch("http://localhost:3000/auth/login", {
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
            location.assign("/api/allposts");
            this.$router.push("/api/allposts")
          })
          .catch((e) => {
            console.log(e);
            this.errMsg = 'Account does not exist';
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
  background-color:  #FEFAE0;
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

button{
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