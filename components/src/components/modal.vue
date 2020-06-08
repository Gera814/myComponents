<template lang="html">
  <div class="">
    <div class="topper" @click="closeModal()"></div>
    <div id="slot">
      <div id="header">
        <div class="icon-holder" @click="closeModal()">
          <i>x</i>
        </div>
        <slot name="header"></slot>
      </div>
      <div id="body">
        <slot name="body"></slot>
      </div>
      <div id="footer">
        <slot name="footer"></slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return{
      active: false

    }
  },
  methods: {
    closeModal(){
      this.$emit("closeModal")
    }
  }
}
</script>

<style lang="css" scoped>
#slot{
  position: fixed;
  left: 50%;
  z-index: 3;
  width: 550px;
  height: 260px;
  background: white;
  top: 40%;
  left: 50%;
  transform: translate(-50%,-50%);
  box-shadow: 0px 5px 20px #888;
  border-radius: 15px;
  padding: 20px;
}
.topper{
  top: 0;
  left: 0;
  position: fixed;
  width: 100%;
  height: 100vh;
  background: black;
  opacity: 25%;
  z-index: 2
}
#header .icon-holder {
  width: 20px;
  height: 20px;
  position: fixed;
  left: 92%;
  top: 7%;
  cursor: pointer;
}
#header{
  height: 20%;
}
#body {
  height: 60%;
}
#footer{
  height: 20%;
}
h2, p {
  margin: 0;
}
</style>
