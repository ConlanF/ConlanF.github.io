<script setup lang="ts">
import { ref, onMounted } from 'vue'

const currentImageSrc = ref('images/website_icon.jpg')

function switchImage() {
  if (window.matchMedia && window.matchMedia('(prefers-color-scheme: dark)').matches) {
    currentImageSrc.value = 'images/website_icon.jpg'
  } else {
    currentImageSrc.value = 'images/website_icon_bw.jpg'
  }
}

onMounted(() => {
  switchImage()
  
  // Listen for changes in color scheme preference
  const mediaQuery = window.matchMedia('(prefers-color-scheme: dark)')
  mediaQuery.addEventListener('change', switchImage)
})
</script>

<template>
  <div class="app">
    <h1>CONLAN'S WEBSITE</h1>
    <section>
      <h2>CONTACT</h2>
      <ul>
        <li><a href="https://www.linkedin.com/in/conlanfenerty">LINKEDIN</a></li>
        <li><a href="mailto:me@conlanfenerty.com">ME@CONLANFENERTY.COM</a></li>
      </ul>
    </section>
    <section>
      <img 
        id="website-icon" 
        :src="currentImageSrc" 
        alt="Website Icon" 
        width="200" 
        height="220"
      >
    </section>
  </div>
</template>

<style>
@font-face {
  font-family: 'Glass TTY VT220';
  src: url('/fonts/Glass_TTY_VT220.ttf') format('truetype');
}

:root {
  color-scheme: light dark;
}

body {
  background-color: light-dark(white, black);
  color: light-dark(#626262, #06fa61);
  font-family: 'Glass TTY VT220', monospace;
  text-align: center;
  width: 100vw;
  height: 100vh;
  margin: 0;
  padding: 0;
}

.app {
  padding: 20px;
}

h1 {
  font-size: 28px;
  text-align: center;
  padding: 5px;
  border: medium dashed light-dark(rgba(98,98,98,.5), rgba(6, 250, 97, .5));
  border-radius: 5px;
  display: inline-block;
}

h2 {
  font-size: 24px;
  font-style: italic;
  text-align: center;
  border-radius: 5px;
  display: inline-block;
}

p {
  font-size: 16px;
  text-align: left;
}

ul {
  list-style-type: none;
  padding: 0;
  text-align: center;
  width: 50%;
  margin: auto;
}

li {
  margin-bottom: 10px;
}

a:link {
  color: light-dark(#626262, #06fa61);
}

a:visited {
  color: light-dark(#a7a0a0, #0fbd18);
}

a:hover,
a:active {
  color: light-dark(#363333, green);
} 

img {
  border: 5px solid light-dark(#626262, #06fa61);
}
</style>
