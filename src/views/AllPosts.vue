<template>
  <div class="AllPosts">
    <div id="post-list">
      <h1>Posts</h1>
      <button @click="Logout" class="button">Logout</button>
      <div class="help">
        <ul class="posts">
          <div class="item" v-for="post in posts" :key="post.id">
            <a class='singlepost' :href="'/api/apost/' + post.id">
              <div class="center">
                <div class="post_header">
                  <div class="iconPost">
                    <img src="../assets/me.png" class="iconPost"/></div>
                  <p class="date"> 12.12.2012</p>
                </div>
                <div class="post_body">
                  <h2><span class="title"> {{ post.title }} </span></h2>
                  <p><span class="body"> {{ post.body }} </span></p>
                  <img class="url" src="{{ post.urllink }}" width="400px" height="300px">
                  <p>Likes</p>
                  <button>LIKE</button>
                </div>
              </div>
            </a>
          </div>
        </ul>
      </div>
      <div class="con">
        <button @click="DeleteAll" class="button">Delete All</button>
        <button @click="this.$router.push('/api/addpost')" class="button">Add Post</button>
      </div>
    </div>
  </div>
</template>


<script>
export default {
  name: "AllPosts",
  data() {
    return {
      posts: [],
    };
  },
  methods: {
    fetchPosts() {
      fetch(`http://localhost:3000/api/posts/`)
          .then((response) => response.json())
          .then((data) => (this.posts = data))
          .catch((err) => console.log(err.message));
    },
    Logout() {
      fetch("http://localhost:3000/auth/logout", {
        credentials: 'include', //  Don't forget to specify this if you need cookies
      })
          .then((response) => response.json())
          .then((data) => {
            console.log(data);
            console.log('jwt removed');
            //console.log('jwt removed:' + auth.authenticated());
            this.$router.push("/login");
            //location.assign("/");
          })
          .catch((e) => {
            console.log(e);
            console.log("error logout");
          });
    },
  },
  mounted() {
    this.fetchPosts();
    console.log("mounted");
  },
  DeleteAll() {

  },
};

function generateDate() {
  const max = Date.now();
  const timestap = Math.floor(Math.random() * max);
  const randomDate = new Date(timestap);
  return randomDate.toString()
}

</script>

<style scoped>

AllPosts {
  display: block;
  flex-direction: column;
  justify-items: center;
  align-items: center;
  width: 50%;
  min-height: 100%;
  padding-bottom: 50px;
}

h1 {
  font-size: 20px;
}

.help {
  display: flex;
  text-align: center;
  align-content: center;
  justify-content: center;
  align-items: center;
  position: static;
  overflow: hidden;
}

.item {
  align-items: center;
  justify-content: center;
  padding-top: 10px;
  padding-bottom: 10px;
}

a {
  text-decoration: none;
}

.posts {
  display: inline-block;
  background: #FEFAE0;
  margin: 0;
  padding-left: 30px;
  padding-right: 30px;
  box-shadow: 0px 0px 0px 0px;
  top: auto;
  width: 100%;
  position: relative;
  overflow: hidden;
}

.singlepost {
  width: 400px;
  height: max-content;
  background-color: #FEFAE0;
  box-shadow: rgba(50, 50, 93, 0.25) 0px 6px 12px -2px, rgba(0, 0, 0, 0.3) 0px 3px 7px -3px;
  align-items: center;
  justify-content: center;
}

#post-list {
  margin: auto;
  min-height: 100vh;
  justify-items: center;
  align-items: center;
  width: 50%;
}

button {
  padding: 10px 20px;
  background-color: #DDA15E;
  color: #FEFAE0;
  border: 3px solid #FEFAE0;
  border-radius: 5px;
  font-weight: bold;
  margin: 20px auto auto;
  width: 100px;
}

button:hover {
  color: #606C38;
  border-color: #283618;
}


.iconPost {
  width: 46px;
  height: 46px;
  border-radius: 50%;
  overflow: hidden;
  float: left;
  margin: 7;
  margin-left: 15;
}

.center {
  max-width: 456px;
  min-width: 100%;
  height: max-content;
  background-color: #FEFAE0;
  box-shadow: rgba(50, 50, 93, 0.25) 0px 6px 12px -2px, rgba(0, 0, 0, 0.3) 0px 3px 7px -3px;
  align-items: center;
  justify-content: center;
}

.post_header {
  height: max-content;
  border: 1px solid #ddd;
}

.post_body {
  height: 70%;
  justify-items: center;
  text-align: center;
  padding: 0 5px 5px;
}

p {
  padding: 10px;
  font-size: 14px;
  text-align: justify;
}

h2 {
  padding: 10;
  padding-bottom: 0;
  font-size: 16px;
  text-align: justify;
}

.post_footer {
  height: 15%;
  text-align: center;
  margin: 0;
}

.con {
  display: flex;
}

</style>