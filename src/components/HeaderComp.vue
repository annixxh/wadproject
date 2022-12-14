<template>
  <header>
    <ul class="nav">
      <li><router-link to="/api/login">Home</router-link></li>
      <!--li><router-link to="/api/allposts">Posts</router-link></li-->
      <li><router-link to="/api/contacts">Contacts</router-link></li>
      <div class="icon_container">
        <div class="dropdown">
          <div id="myDropdown" class="dropdown-content">
            <a>Home</a>
            <a>About</a>
            <a>Contact</a>
          </div>
          <img class = "icon_dropbtn" id="profile_pic" src="../assets/me.png" alt="profile picture" onclick="myFunction()">
        </div>
      </div>
    </ul>
  </header>
  <div class="hor_spacer"></div>
</template>

<script>
import {mapGetters} from "vuex";
export default {
  name: "headercomp",
  methods: {
    goToHome() {
      this.router.push('/');
    },
    goToContacts() {
      this.router.push('/Contacts');
    }
  }
};
</script>

<style>
body{
  background-color: #FEFAE0;
  display:block;
}


header {
  width: 100%;
  margin: 0;
  padding: 0;
  display: inline-block;
  overflow: hidden;
}

ul {
  position: sticky;
  list-style-type: none;
  margin: 0;
  overflow: hidden;
  background-color: #606C38;
  box-shadow: 0px 0px 14px 0px rgba(0, 0, 0, 0.75);
  top:0;
  right:0px;
  padding-top: .6em;
  padding-bottom: .6em;
}

li {
  float: left;
  padding-left: 10px;
  padding-right: 15px;
}

button{
  padding: 10px;
  margin: auto;
  background-color: #DDA15E;
  color: #FEFAE0;
  border: 3px solid #FEFAE0;
  border-radius: 5px;
  font-weight: bold;
}
button:hover {
  color: #606C38;
  border-color: #283618;
}

li a{
  display: block;
  text-transform: uppercase;
  text-align: center;
  font-size: .99em;
  text-decoration: none;
  border: 3px solid #FEFAE0;
  background-color: #DDA15E;
  width: 110%;
  margin:auto;
  color: #FEFAE0;
  font-weight: bold;
  border-radius: 5px;
}

.icon_container {
  float: right;
  width: 30px;
  height: 30px;
  padding-right: 20px;
}

/* color of dropdown links on hover */
.dropdown-content a:hover {background-color: #ddd;}

/* dropdown menu on hover */
.dropdown:hover .dropdown-content {display: block;}

/*background color of the dropdown button when the dropdown content is shown */
.dropdown:hover .dropbtn {background-color: #616461;}

.dropbtn {
  color: white;
  border: none;
  cursor: pointer;
}

.icon_dropbtn {
  width: 100%;
  height: 100%;
  float: right;
}

.dropdown-content {
  display: none;
  position: absolute;
  background-color: #FEFAE0;
  min-width: 160px;
  overflow: auto;
  box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
  z-index: 1;
  margin-right: 50%;
}

.dropdown-content a {
  color: black;
  padding: 12px 16px;
  text-decoration: none;
  display: block;
}

.show {display: block;}

.hor_spacer {
  width: 100%;
  height: 30px;
  margin-top: 10px;
  margin-bottom: 10px;
}


</style>