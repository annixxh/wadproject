<template>
  <div class="hor_spacer"></div>
  <footer>
    <p style="text-align: center; color: #FEFAE0" >WAD 2022</p>
  </footer>
</template>

<script>
export default {
  name: "FooterComp"
}
</script>

<style scoped>
footer {
  background-color: #606C38;
  box-shadow: 0px 0px 14px 0px rgba(0, 0, 0, 0.75);
  bottom: 0;
  width: 100%;
  max-height: 30px;
  right:0px;
  padding-top: .5em;
  padding-bottom: .5em;
  position: fixed;
}

.hor_spacer {
  width: 100%;
  height: 30px;
  margin-top: 10px;
  margin-bottom: 10px;
}

</style>