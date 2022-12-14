<template>
  <div class="A Post">
    <div id="form">
      <h3>A Post</h3>
      <label for="title">Title: </label>
      <input name="type" type="text" id="title" required v-model="post.title" />
      <label for="body">Body: </label>
      <input name="body" type="text" id="body" required v-model="post.body" />
      <label for="url">Url: </label>
      <input name="url" type="text" id="url" required v-model="post.urllink" />
    </div>
    <div class="container">
      <button @click="updatePost" class="updatePost">Update Post</button>
      <button @click="deletePost" class="deletePost">Delete Post</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "APost",
  data() {
    return {
      post: {
        id: "",
        title: "",
        body: "",
        urllink: "",
      },
    };
  },
  methods: {
    fetchAPost(id) {
      fetch(`http://localhost:3000/api/posts/${id}`)
          .then((response) => response.json())
          .then((data) => (this.post = data))
          .catch((err) => console.log(err.message));
    },
    updatePost() {
      fetch(`http://localhost:3000/api/posts/${this.post.id}`, {
        method: "PUT",
        headers: {
          "Content-Type": "application/json",
        },
        body: JSON.stringify(this.post),
      })
          .then((response) => {
            console.log(response.data);
            this.$router.push("/api/allposts");
          })
          .catch((e) => {
            console.log(e);
          });
    },
    deletePost() {
      fetch(`http://localhost:3000/api/posts/${this.post.id}`, {
        method: "DELETE",
        headers: { "Content-Type": "application/json" },
      })
          .then((response) => {
            console.log(response.data);
            this.$router.push("/api/allposts");
          })
          .catch((e) => {
            console.log(e);
          });
    },
  },
  mounted() {
    this.fetchAPost(this.$route.params.id);
  },
};
</script>

<style scoped>
#form {
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