<template lang='pug'>
  v-app(background-color='white')
    div.myHeader()
      div.info-header.flex-row()
        div.flex-item.info-logo
          img.logo(src='~/static/logo.png' alt='logo.png' height='200px')
        div.flex-item.info-right
          v-tabs(v-model='tab_index' slider-color='#39a' active-class='pickedTab')
            v-tab(v-for='page, i in pages' :key='page.page' @click='showPage(page)') {{page.name}}
      hr(style='border: 6px solid #39a') 
    div.myBody.background-image
      v-container
      
        button(v-on:click="show = !show") Toggle
        transition(name="fade")
          p(v-if="show") Hello !
        hr
        v-tabs-items(v-model='tab_index')
          v-tabs-item(v-for='page in pages' :key='page.page')
            v-card(flat)
              Hi ...on page {{tab_index}} : {{page.name}}
        hr
        transition(name="turnPage")
          div(v-if="openTab === 'mission'")
            Mission
          div(v-if="openTab === 'contact'")
            Contact
          div(v-if="openTab === 'expertise'")
            Expertise
          div(v-if="openTab === 'projects'")
            Projects
          div(v-if="openTab == 'home'")
            Home
    div.myFooter()
      PublicFooter
</template>

<script>
  import Home from '~/components/Home'
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
      Projects,
      PublicFooter
    },
    data () {
      return {
        show: true,
        tab_index: 3,
        openTab: '',
        pages: [
          { name: 'About', page: 'mission' },
          { name: 'Expertise', page: 'expertise' },
          { name: 'Projects', page: 'projects' },
          { name: 'Contact', page: 'contact' }
        ]
      }
    },
    created: function () {
      if (this.tab_index) {
        this.openTab = this.pages[this.tab_index].page
      }
    },
    methods: {
      showPage: function (page) {
        console.log('** Show Page: ' + JSON.stringify(page))
        if (page && page.page) {
          this.openTab = page.page
        } else {
          this.openTab = 'Home'
        }
      }
    }
  }
</script>

<style scoped lang="scss">

$header-height: 200px;
$subheader-height: 0px;
$min-height: 300px;
$footer-height: 100px;

.myHeader {
  height: #{$header-height};
  background-color: white;
}
.myBody {
  min-height: calc(100vh - #{$header-height} - #{$subheader-height} - #{$footer-height});
background: url(/_nuxt/img/b6b028c.gif) no-repeat 50% fixed;
}
.background-image {
  background: url('/images/animated_sine.gif') no-repeat center fixed;
  position: absolute;
  top: 0;
  left: 0;
  background-size: cover;
  height: 100%;
  width: 100%;
  opacity: 0.1;
  z-index: -1;
}
.myFooter {
  height: #{$footer-height};
  background-color: #39a;
  color: white;
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
  padding-right: 2rem;
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

div.v-tabs__slider.accent {
  background-color: black !important;
}
.pickedTab {
  color: red;
}

.fade-enter-active, .fade-leave-active {
  transition: opacity 2s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}

.turnPage-enter-active, .fade-leave-active {
  transition: opacity 2s;
}
.turnPage-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}

</style>
