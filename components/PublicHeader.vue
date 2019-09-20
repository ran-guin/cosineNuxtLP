<template lang='pug'>
  div.publicHeader
    div.info-header(style='background-color: white')
      div.info-logo
        img.logo(src='~/static/logo.png' alt='logo.png' height='200px')
      div.info-right
        v-tabs(v-model='openTab')
          v-tab-slider
          v-tab(v-for='page, i in pages' :key='page.page' :href='page.page') {{page.name}}
 </template>

<script>
export default {
  name: 'Home',
  components: {
  },
  data () {
    return {
      openTab: 'projects',
      pages: [
        { name: 'About', page: 'mission' },
        { name: 'Expertise', page: 'us' },
        { name: 'Projects', page: 'projects' },
        { name: 'Contact', page: 'contact' }
      ]
    }
  }
}
</script>

<style scoped lang="scss">
.logo {
  max-height: 200px;
  padding: 1rem;
}
@media screen and (max-width: 767) {
  .logo {
    max-height: 150px
  }
}
.myMenu {
  padding: 3rem;
}
.menuItem {
  padding-left: 1rem;
  padding-right: 1rem;
  a {
    color: #333
  }
  a:hover {
    color: black;
    text-decoration: none;
  }
}

.info-header {
  width: 100%;
}
.info-logo {
  text-align: left;
  vertical-align: top;
  display: inline-block;
}
.info-left {
  padding-left: 5rem;
  text-align: left;
  display: inline-block;
}
.info-right {
  float: right;
  text-align: right;
  /* display: inline-block; */
  height: 100%;
}
@media screen and (max-width: 767px) {
  .info-left {
    display: none;
  }
  .info-logo {
    display: none;
  }
}
</style>
