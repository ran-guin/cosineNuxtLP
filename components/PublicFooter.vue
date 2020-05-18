<template lang='pug'>
  div.publicFooter.flex-row()
    div.footer-left(light)
      a(href='/')
        span.acronym
          b &nbsp; C
          span ommunity
          b &nbsp; O
          span riented
          b &nbsp; S
          span oftware
          b &nbsp; I
          span nnovation
          b &nbsp; N
          span etwork
          span &nbsp; &nbsp;
          span &nbsp; &nbsp;
    div.footer-right(light)
      a(href="mailto:rguin@cosinesystems.org?Subject=webpage%20contact") Contact Us

</template>

<script>
export default {
  props: {
    left: {
      type: String,
      default: ''
    },
    right: {
      type: String,
      default: ''
    },
    centre: {
      type: String,
      default: ''
    }
  },
  // template: require('./main.pug'),
  data () {
    return {}
  }
}
</script>

<style scoped>
.publicFooter.flex-row {
  justify-content: space-between;
  height: 100%;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  /* margin: 0 10px; */
}

a {
  color: #eee;
  text-decoration: none;
}
a:hover {
  color: white;
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
.flex-row {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-around;
}
.flex-item {
  display: flex;
}
</style>
