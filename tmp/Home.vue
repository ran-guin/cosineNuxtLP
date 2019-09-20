<template lang='pug'>
  v-app(dark)
    div.myHeader
      div.info-header.flex-row(style='background-color: white')
        div.flex-item.info-logo
          img.logo(src='~/static/logo.png' alt='logo.png' height='200px')
        div.flex-item.info-right
          v-tabs(v-model='openTab')
            v-tab(v-for='page, i in pages' :key='page.page' @click='openTab=page.page') {{page.name}}
    div.myBody(style='background-color:blue')
      v-container
        h3 Page: {{openTab}}
        hr
        div(v-if="page === 'mission'")
          Mission
        div(v-if="page === 'contact'")
          Contact
        div(v-if="page === 'expertise'")
          Expertise
        div(v-if="page === 'projects'")
          Projects
        div(v-else)
          Home        
    div.myFooter()
      PublicFooter
</template>

<script>
  import Home from '~/components/home'
  import Contact from '~/components/contact'
  import Expertise from '~/components/expertise'
  import Projects from '~/components/projects'
  import Mission from '~/components/mission'
  import PublicFooter from '~/components/PublicFooter'

  export default {
    components: {
      Home,
      Mission,
      Expertise,
      Contact,
      Projects
    },
    data () {
      return {
        openTab: 'home',
        pages: [
          { name: 'About', page: 'mission' },
          { name: 'Expertise', page: 'expertise' },
          { name: 'Projects', page: 'projects' },
          { name: 'Contact', page: 'contact' }
        ]
      }
    },
    methods: {
      showPage: function (page) {
        this.openTab = page
      }
    }
  }
</script>

<style scoped lang="scss">

$header-height: 200px;
$subheader-height: 0px;
$min-height: 300px;
$footer-height: 200px;

.myHeader {
  height: #{$header-height};
}
.myBody {
  min-height: calc(100vh - #{$header-height} - #{$subheader-height} - #{$footer-height});
}
.myFooter {
  height: #{$footer-height};
  background-color: white;
}

.myFooter {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  /* margin: 0 10px; */
}

span a {
  color: #222;
}
span a:hover {
  color: #000;
  font-weight: bold;
}

.footer-left {
  display: none;
}
.footer-right {
  display: flex;
  justify-content: flex-end;
  padding-right: 2rem;
}

@media screen and (min-width: 768px) {
  .footer-left {  
    display: flex;
    justify-content: flex-start;
    padding-left: 2rem;
  }
}
.info-header.flex-row {
  justify-content: space-between;
}

.flex-row {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
}
.flex-item {
  display: flex;
}
</style>
