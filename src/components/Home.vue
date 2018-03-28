<template>
  <div class="home">
    <img class="background-image" src="@/../static/home.jpg">
    <div class="title">{{ msg }}</div>
    <button class="blog-button" @click="goToBlog">博客</button>
    <button class="about-button" @click="goToAbout">关于作者</button>
  </div>
</template>

<script>
export default {
  name: 'Home',
  data() {
    return {
      msg: '李为的个人主页',
    };
  },
  methods: {
    goToBlog() {
      this.$router.push({ name: 'Blog' });
    },
    goToAbout() {
      this.$router.push({ name: 'About' });
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.home {
  width: 100vw;
  height: 100vh;
  /*background-image: url('../../static/home.jpeg');*/
}

.background-image {
  position: absolute;
  width: 100vw;
  height: 100vh;
  z-index: -1;
}

.title {
  position: absolute;
  left: .2em;
  top: .2em;
  font-weight: bold;
  font-size: 2.5em;
  color: #fff;
}

.blog-button,
.about-button {
  position: absolute;
  margin: 0;
  padding: 0;
  background-clip: padding-box;
  border: 5em solid transparent;
  border-radius: 50%;
  outline: none;
  color: #fb3;
  font-weight: bold;
  background-color: #58a;
  cursor: pointer;
  opacity: 0.8;
}

.blog-button {
  left: 15em;
  top: 7em;
  width: 18em;
  height: 18em;
  font-size: 1.5em;
  animation: aniOne 10s infinite;
}

.about-button {
  left: 40em;
  top: 6em;
  width: 15em;
  height: 15em;
  font-size: 1.3em;
  animation: aniTwo 10s infinite;
}

@keyframes aniOne {
  0% {transform: translate(0, 0);}
  10% {transform: translate(.5em, .5em);}
  25% {transform: translate(1.5em, 1em);}
  37% {transform: translate(1.5em, 2em);}
  50% {transform: translate(.5em, 0);}
  60% {transform: translate(-.5em, -1em);}
  75% {transform: translate(1.5em, 1em)}
  90% {transform: translate(2.5em, -1em);}
  100% {transform: translate(0, 0);}
}

@keyframes aniTwo {
  0% {transform: translate(0, 0);}
  8% {transform: translate(1em, 1em);}
  25% {transform: translate(1em, .5em);}
  30% {transform: translate(-1em, -.5em);}
  50% {transform: translate(.5em, 0);}
  70% {transform: translate(1em, -2em);}
  75% {transform: translate(1em, -.5em)}
  80% {transform: translate(1.5em, .5em);}
  100% {transform: translate(0, 0);}
}
</style>
