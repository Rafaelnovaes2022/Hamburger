<template>
  <div>
    <div id="nav">
      <!-- Inicio Animação-->
          <div class="logo">
            <svg viewBox="0 0 435.6 141.4" ref="logo">
              <path
                id="Letter_M"
                class="color1"
                d="M0.7,140.2l0.1-138L47,68.4L93.3,2.2V140h-8L10.9,34.3v40.1"/>
              <path
                id="Letter_A"
                class="color2"
                d="M118.6,141.2l55.2-139L224,140h-12l-18.4-51.5h-43.9l16.1-42.2"/>
              <path
                id="Letter_R"
                class="color3"
                d="M249.3,141.2V2.2h23.1c0,0,35-1.8,45,35.1c1,3.6,1.3,7.4,0.9,11.2c-1.4,16.4-11.2,30.8-25.9,38.1l30.1,53.4h-8l-34.1-57.4c0,0,18.1-2,28.1-24.1h-50.2V44.4"/>
              <path
                id="Letter_T"
                class="color4"
                d="M435.6,2.2h-87.8v10H392v128.2h8V47.3"/>
            </svg>
            <!-- Fim da Animação-->
          </div>
      <!--<button @click="go">Click Here to Animate</button>
      <div class="block" ref="square"></div>-->
      <img @click="handleClick" :src="logo" :alt="alt" id="logo" class="image" />
      <router-link id="logo-url" to="/">
        <img v-if="isLogoVisible" :src="logo" :alt="alt" id="logo" class="image">
      </router-link>
      <router-link to="/">Home</router-link>
      <router-link to="/pedidos">Pedidos</router-link>
    </div>
  </div>
</template>

<script>

import anime from 'animejs'

export default {
  name: 'Navbar',
  props: ['logo', 'alt'],
  data () {
    return {
      isLogoVisible: false
    }
  },
  mounted () {
    this.logoAnimation(this.$refs.logo.children)
  },
  methods: {
    handleClick () {
      this.isLogoVisible = !this.isLogoVisible
    },
    go () {
      anime({
        targets: this.$refs.square,
        translateX: 500
      })
    },
    logoAnimation (element) {
      anime({
        targets: element,
        strokeDashoffset: [anime.setDashoffset, 0],
        easing: 'easeInOutSine',
        duration: 2000,
        delay (el, i) {
          return i * 250
        }
      })
    }
  }
}
</script>

<style scoped>
#nav {
  background-color: #222;
  border-bottom: 4px solid #111;
  padding: 15px 50px;
  display: flex;
  justify-content: flex-end;
  align-items: center;
}

#nav #logo-url {
  margin: auto;
  margin-left: 0;
}

#logo {
  width: 40px;
  height: 40px;
}

#nav a {
  color: #fcba03;
  text-decoration: none;
  margin: 12px;
  transition: .5s;
}

#nav a:hover {
  color: #FFF;
}

*,
*::before,
*::after {
  box-sizing: border-box;
  padding: 0;
  margin: 0;

}

html {
  font-size: 62.5%;
}

.image {
  /*position: absolute;*/
  /**top: 50%;**/
  /**left: 50%;**/
  width: 120px;
  height: 120px;
  /**margin:-60px 0 0 -60px;**/
  -webkit-animation: spin 4s linear infinite;
  -moz-animation: spin 4s linear infinite;
  animation: spin 4s linear infinite;
}

@-moz-keyframes spin {
  100% {
    -moz-transform: rotate(360deg);
  }
}

@-webkit-keyframes spin {
  100% {
    -webkit-transform: rotate(360deg);
  }
}

@keyframes spin {
  100% {
    -webkit-transform: rotate(360deg);
    transform: rotate(360deg);
  }
}
.block {
    pointer-events: none;
    position: relative;
    width: 128px;
    height: 128px;
    margin: 1px;
    background-color: currentColor;
    font-size: 12px;
    color: #2c3e50;
}

.color1 {
  stroke: #3eb373;
}
.color2 {
  stroke: #be2f39;
}
.color3 {
  stroke: #2283bc;
}
.color4 {
  stroke: #ed8e3f;
}

.logo {
  display: flex;
  justify-content: center;
  align-items: center;
}

.logo svg {
  width: 300px;
}

.logo path {
  fill: none;
  stroke-width: 1.5;
}
</style>
