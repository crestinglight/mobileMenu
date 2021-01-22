<template>
  <div id="app">
    <Navigation  v-on:setPageTitle="updateTitle($event)"></Navigation>
    <div class="page">
        <h1>{{ currentPageTitle }}</h1>
    </div>
  </div>
</template>

<script>
import Navigation from './components/Navigation.vue';

export default {
  name: 'App',
  data() {
    return {
      currentPageTitle: "Home"
    }
  },
  components: {
    Navigation
  },
  methods: {
    updateTitle: function(updatedTitle) {
      this.currentPageTitle = updatedTitle;
    }
  }
}
</script>

<style>
/*   Reset   */
html, body, div, span, applet, object, iframe,
h1, h2, h3, h4, h5, h6, p, blockquote, pre,
a, abbr, acronym, address, big, cite, code,
del, dfn, em, img, ins, kbd, q, s, samp,
small, strike, strong, sub, sup, tt, var,
b, u, i, center,
dl, dt, dd, ol, ul, li,
fieldset, form, label, legend,
table, caption, tbody, tfoot, thead, tr, th, td,
article, aside, canvas, details, embed, 
figure, figcaption, footer, header, hgroup, 
menu, nav, output, ruby, section, summary,
time, mark, audio, video {
  margin: 0;
  padding: 0;
  border: 0;
  font-size: 100%;
  font: inherit;
  vertical-align: baseline;
}
/* HTML5 display-role reset for older browsers */
article, aside, details, figcaption, figure, 
footer, header, hgroup, menu, nav, section {
  display: block;
}
body {
  line-height: 1;
}
ol, ul {
  list-style: none;
}
blockquote, q {
  quotes: none;
}
blockquote:before, blockquote:after,
q:before, q:after {
  content: '';
  content: none;
}
table {
  border-collapse: collapse;
  border-spacing: 0;
}
button {
  background-color: transparent;
  outline: none;
  border: none;
  cursor: pointer;
}
/*   End Reset   */

#app {
  font-family: "Overpass", Helvetica, sans-serif;
  font-weight: 400;
  -webkit-font-smoothing: antialiased;
  color: #51007A;
  background-color: #fff;
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}
h1, h2, h3, h4, h5, h6 {
  font-family: "Cabin", Arial, sans-serif;
  font-weight: 700;
  -webkit-font-smoothing: antialiased;
}
h1 {
  font-size: 24px;
}
h2 {
  font-size: 18px;
}
.page {
    display: flex;
    flex-direction: column;
    flex: 1;
    justify-content: center;
    align-items: center;
    background-image: linear-gradient(to bottom right, #51007A, #E70941);
    color: white;
}
</style>
