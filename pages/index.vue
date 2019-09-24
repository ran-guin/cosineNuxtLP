<template lang='pug'>
  v-app(background-color='white')
    div.myHeader()
      div.info-header.flex-row()
        div.flex-item.info-logo
          img.logo(src='~/static/logo.png' alt='logo.png' height='200px')
        div.flex-item.wideRight
          v-tabs(v-model='tab_index' slider-color='#39a' active-class='pickedTab')
            v-tab(v-for='page, i in pages' :key='page.name' @click='showPage(page)' class='teal--text')
              v-icon.primary-colour(v-if='page.icon') {{page.icon}}
              span(v-else) {{page.name}}
      hr(style='border: 6px solid #39a') 
    div.background-image
    div.myBody
        v-container
          div.offPage#Mission(ref='Mission')
            div(v-if="openTab === 'Mission'")
              Mission.list-item
          div.offPage#Contact(ref = 'Contact')
            div(v-if="openTab === 'Contact'")
                Contact.list-item
          div.offPage#Expertise(ref='Expertise')
            div(v-if="openTab === 'Expertise'")
              Expertise.list-item
          div.offPage#Projects(ref='Projects')
            div(v-if="openTab === 'Projects'")
                Projects.list-item
          div.offPage#Home(ref='Home')
            div(v-if="openTab == 'Home'")
                Home.list-item
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
        tab_index: 0,
        openTab: '',
        pages: [
          { name: 'Home', icon: 'home' },
          { name: 'Mission' },
          { name: 'Expertise' },
          { name: 'Projects' },
          { name: 'Contact' }
        ]
      }
    },
    created: function () {
      this.openTab = this.pages[this.tab_index].name
      console.log('created...' + this.openTab)
    },
    mounted: function () {
      console.log('mounted...' + this.openTab)
      var start = this.pages[this.tab_index].name
      var init = this.$refs[start]
      if (init) {
        init.classList.toggle('onPage')
        init.classList.toggle('offPage')
      }
    },
    methods: {
      showPage: function (page) {
        console.log('from page ' + page)

        console.log('open tab: ' + this.openTab)
        var open = this.$refs[page.name]
        var close = this.$refs[this.openTab]

        this.openTab = page.name || 'Home'

        if (open) {
          open.classList.toggle('onPage')
          open.classList.toggle('offPage')
          console.log('Opened: ' + page.name + ': ' + JSON.stringify(open.classList))
        }
        if (close) {
          close.classList.toggle('onPage')
          close.classList.toggle('offPage')
          console.log('Closed: ' + JSON.stringify(close.classList))
        }
      }
    }
  }
</script>

<style lang="scss">

$header-height: 200px;
$subheader-height: 0px;
$min-height: 300px;
$footer-height: 100px;

.myHeader {
  height: #{$header-height};
  background-color: white;
  z-index: 10;
}
.myBody {
  min-height: calc(100vh - #{$header-height} - #{$subheader-height} - #{$footer-height});
}
.background-image {
  background: url("/images/animated_sine.gif") no-repeat bottom center fixed;
  position: absolute;
  top: 0;
  left: 0;
  background-size: cover;
  height: 100%;
  width: 100%;
  opacity: 0.1;
  z-index: 0;
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
  color: black;
  font-weight: bold;
}

.fade-enter-active, .fade-leave-active {
  transition: opacity 2s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}

.list-item {
  display: inline-block;
  margin-right: 10px;
}
.list-enter-active, .list-leave-active {
  transition: all 1s;
}
.list-enter, .list-leave-to /* .list-leave-active below version 2.1.8 */ {
  opacity: 0;
  transform: translateY(100px);
}

.turnpage-enter-active, .fade-leave-active {
  transition: opacity 2s;
}
.turnpage-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}

.lightShadow {
  -webkit-box-shadow: 3px 3px 5px 6px #ccc;  /* Safari 3-4, iOS 4.0.2 - 4.2, Android 2.3+ */
  -moz-box-shadow:    3px 3px 5px 6px #ccc;  /* Firefox 3.5 - 3.6 */
  box-shadow:         3px 3px 5px 6px #ccc;  /* Opera 10.5, IE 9, Firefox 4+, Chrome 6+, iOS 5 */
  border: 0px !important;
}

.darkShadow {
  -webkit-box-shadow: 3px 3px 5px 6px #333;  /* Safari 3-4, iOS 4.0.2 - 4.2, Android 2.3+ */
  -moz-box-shadow:    3px 3px 5px 6px #333;  /* Firefox 3.5 - 3.6 */
  box-shadow:         3px 3px 5px 6px #333;  /* Opera 10.5, IE 9, Firefox 4+, Chrome 6+, iOS 5 */
  border: 0px !important;
}

.v-card.padded {
  padding: 2rem;
  margin: 2rem;
}

/* wideRight will float to the right IF there is space ... */
@media screen and (min-width: 768px) {
  .wideRight {
    float: right;
  }
}

.offPage {
  // transition-duration: 2s;
  // transition: all 2s;
  opacity: 0.1;
}
.onPage {
  transition-duration: 2s;
  transition: all 2s;
  opacity: 1;
}
</style>
