<template>
  <div class="home">
    <img class="background-image hidden-xs-only" src="@/../static/homeBig.jpg">
    <img class="background-image hidden-sm-and-up" src="@/../static/homeSmall.jpg">
    <div class="title">{{ msg }}</div>
    <floating-button
      class="blog-button hidden-xs-only"
      @click="goTo('Blog')"
      :content="blog"
      left="35%"
      top="20%"
      width="10em"
      height="10em"
      fontSize="1.5em">
    </floating-button>
    <floating-button
      class="blog-button hidden-sm-and-up"
      @click="goTo('Blog')"
      :content="blog"
      left="40%"
      top="20%"
      width="7em"
      height="7em"
      fontSize="1.2em">
    </floating-button>
    <floating-button
      class="about-button hidden-xs-only"
      @click="goTo('About')"
      :content="about"
      left="7%"
      top="58%"
      width="7em"
      height="7em"
      fontSize="1.2em">
    </floating-button>
    <floating-button
      class="about-button hidden-sm-and-up"
      @click="goTo('About')"
      :content="about"
      left="15%"
      top="58%">
    </floating-button>
    <floating-button
      class="login-button hidden-xs-only"
      @click="goTo('Login')"
      :content="login"
      left="80%"
      top="5%">
    </floating-button>
    <!-- <floating-button :content="content" :color="color"></floating-button> -->
  </div>
</template>

<script>
import FloatingButton from './components/FloatingButton';

export default {
  name: 'Home',
  components: {
    FloatingButton,
  },
  data() {
    return {
      msg: '',
      blog: '文章',
      about: '关于作者',
      login: '作者登录',

      // 传进FloatingButton的参数
      content: 'lala',
      color: 'red',
    };
  },
  methods: {
    goTo(someWhere) {
      this.$router.push({ name: someWhere });
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.home {
  width: 100vw;
  height: 100vh;
}

.background-image {
  position: absolute;
  width: 100vw;
  height: 100vh;
  z-index: -1;
}

.title {
  position: absolute;
  left: 2%;
  top: 2%;
  font-weight: bold;
  font-size: 2.5em;
  color: #fb3;
}

.blog-button {
  /*animation: aniOne 10s infinite;*/
}

.about-button {
  /*animation: aniOne 10s infinite;*/
}

.login-button {
  /*animation: aniOne 10s infinite;*/
}

@keyframes aniOne {
  0% {transform: translate(0, 0);}
  /*10% {transform: translate(.5em, .5em);}*/
  25% {transform: translate(1.5em, 1em);}
  /*37% {transform: translate(1.5em, 2em);}*/
  50% {transform: translate(.5em, 0);}
  /*60% {transform: translate(-.5em, -1em);}*/
  75% {transform: translate(1.5em, 1em)}
  /*90% {transform: translate(2.5em, -1em);}*/
  100% {transform: translate(0, 0);}
}

/*@keyframes aniTwo {
  0% {transform: translate(0, 0);}
  8% {transform: translate(1em, 1em);}
  25% {transform: translate(1em, .5em);}
  30% {transform: translate(-1em, -.5em);}
  50% {transform: translate(.5em, 0);}
  70% {transform: translate(1em, -2em);}
  75% {transform: translate(1em, -.5em)}
  80% {transform: translate(1.5em, .5em);}
  100% {transform: translate(0, 0);}
}*/
</style>
