<template>
  <div class="form">
    <h3>Add a Post</h3>
    <label for="title">Title: </label>
    <input name="title" type="text" id="title" required v-model="post.title" />
    <label for="body">Body: </label>
    <input name="body" type="text" id="body" required v-model="post.body" />
    <label for="urllink">Url: </label>
    <input name="urllink"  type="text" id="urllink" required v-model="post.urllink"/>
    <button @click="addPost" class="addPost">Add Post</button>
  </div>
</template>

<script>
export default {
  name: "AddPost",
  data() {
    return {
      post: {
        title: "",
        body: "",
        urllink: "",
      },
    };
  },
  methods: {
    addPost() {
      console.log("Here now")
      var data = {
        title: this.post.title,
        body: this.post.body,
        urllink: this.post.urllink,
      };
      fetch("http://localhost:3000/api/posts", {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
        },
        body: JSON.stringify(data),
      })
      .then((response) => {
        console.log(response.data);

      })
      this.$router.push("/api/allposts")
      .catch((e) => {
        console.log(e);
        console.log("error");
      });
    },
  },
};
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

.addPost{
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
.addPost:hover {
  color: #606C38;
  border-color: #283618;
}

.container {
  display: flex;
  justify-content: center;
}
</style>