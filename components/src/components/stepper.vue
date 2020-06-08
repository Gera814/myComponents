<template lang="html">
  <div class="container">
<div id="stepProgressBar">
	<div v-for="i in $props.steps" :key="i" class="step">
		<p class="step-text">Step {{i}}</p>
		<div class="bullet">{{i}}</div>
	</div>
</div>
<div id="slot">
  <div v-for="i in $props.steps" :key="i" :id="'step'+i">
    <slot :name="'step'+i" v-if="currentStep == i"></slot>
  </div>
</div>
<div id="main">
	<button id="previousBtn" @click="previous()" disabled >Previous</button>
	<button id="nextBtn" @click="next()">Next</button>
	<button id="finishBtn" disabled >Finish</button>
</div>
</div>
</template>

<script>
export default {
  props:['steps'],
  data() {
    return{
      currentStep: 1,
      maxStep: this.$props.steps
    }
  },
  methods: {
    next(){
      const previousBtn = document.getElementById('previousBtn');
      const nextBtn = document.getElementById('nextBtn');
      const finishBtn = document.getElementById('finishBtn');
      const bullets = [... document.querySelectorAll('.bullet')];
      const currentBullet = bullets[this.currentStep - 1];

      currentBullet.classList.add('completed');
      this.currentStep++;
      previousBtn.disabled = false;
      if(this.currentStep == this.maxStep){
        nextBtn.disabled = true;
        finishBtn.disabled = false;
      }
    },
    previous(){
      const nextBtn = document.getElementById('nextBtn');
      const finishBtn = document.getElementById('finishBtn');
      const previousBtn = document.getElementById('previousBtn');
      const bullets = [... document.querySelectorAll('.bullet')];

      const previousBullet = bullets[this.currentStep - 2];
      previousBullet.classList.remove('completed');
      this.currentStep--;
      nextBtn.disabled = false;
      finishBtn.disabled = true;
      if(this.currentStep == 1){
        previousBtn.disabled = true;
      }
    }
  }
}
</script>



<style lang="css" scoped>
#stepProgressBar  {
	display:  flex;
	align-items:  flex-end;
	width:  auto;
	margin:  0  auto;
	margin-bottom:  40px;
}
.step  {
  text-align:  center;
  margin-left: 45px
}

.step-text  {
  margin-bottom:  10px;
  color:  #28a745;
}

.bullet {
	border: 1px solid #28a745;
	height: 20px;
	width: 20px;
	border-radius: 100%;
	color: #28a745;
	display: inline-block;
	position: relative;
	transition: background-color 500ms;
  line-height:20px;
}

.bullet.completed  {
	color:  white;
	background-color:  #28a745;
}

.bullet.completed::after {
	content: '';
	position: absolute;
	right: -60px;
	bottom: 10px;
	height: 1px;
	width: 54px;
	background-color: #28a745;
}

/* Base styles and helper stuff */
.hidden  {
	display:  none;
}

#main{
  margin-top: 40px;
}

.text-center  {
	text-align:  center;
}

.container  {
	width: auto;
	margin:  0  auto;
	margin-top:  20px;
	padding:  40px;
  height: 500px;
}


</style>
