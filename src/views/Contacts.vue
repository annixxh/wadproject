<template>
  <div class="container">
    <div class="row">
      <div class="column">
        <h2>Contact Us</h2>
        <p>If you have any problems - write to us!</p>
      </div>
      <div class="column">
        <form action="/action_page.php">
          <label for="fname">First Name</label>
          <input type="text" id="fname" name="firstname" placeholder="Your name..">
          <label for="lname">Last Name</label>
          <input type="text" id="lname" name="lastname" placeholder="Your last name..">
          <label for="subject">Subject</label>
          <textarea id="subject" name="subject" placeholder="Write something.." style="height:170px"></textarea>
          <input type="submit" class="button" value="Submit">
        </form>
      </div>
      <div class="column">
        <h2>Authors of the page</h2>
        <li ><p>Anne-Mari Kasemetsa</p></li>
        <li><p>Hanna Vallner</p></li>
        <li><p>Anička Šmikmátorová</p></li>
      </div>
    </div>
  </div>
</template>

<script>
import Headercomp from "@/App";
import FooterComp from "@/App";

export default {
  name: "Contacts",
  components: {FooterComp, Headercomp}
}
</script>

<style scoped>
* {
  box-sizing: border-box;
}

.row {
  margin: 0 auto 30px;
  text-align: left;
  padding: 0 40px 40px;
  border-radius: 10px;
  background-color:  #FEFAE0;
  box-shadow: 0px 0px 14px 0px, rgba(0, 0, 0, 0.3) 0px 3px 7px -3px;
  align-items: center;
  justify-content: center;
}

/* Style inputs */
input[type=text], select, textarea {
  width: 100%;
  padding: 12px;
  border: 1px solid #ccc;
  margin-top: 6px;
  margin-bottom: 16px;
  resize: vertical;
}

input[type=submit] {
  padding: 10px 20px;
  background-color: #DDA15E;
  color: #FEFAE0;
  border: 3px solid #FEFAE0;
  border-radius: 5px;
  font-weight: bold;
  margin: 20px auto auto;
  width: 50%;
}

input[type=submit]:hover {
  background-color: #45a049;
}

/* Style the container/contact section */
.container {
  border-radius: 5px;
  padding: 10px;
}

/* Create two columns that float next to eachother */
.column {
  float: left;
  width: 50%;
  margin-top: 6px;
  padding: 20px;
}

li {
  list-style-type: none;
}

/* Clear floats after the columns */
.row:after {
  content: "";
  display: table;
  clear: both;
}

/* Responsive layout - when the screen is less than 600px wide, make the two columns stack on top of each other instead of next to each other */
@media screen and (max-width: 600px) {
  .column, input[type=submit] {
    width: 100%;
    margin-top: 0;
  }
}
</style>