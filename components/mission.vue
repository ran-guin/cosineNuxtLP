<template lang='pug'>
  v-container
    h1.primary-colour Mission
    hr
    p &nbsp;
    div
      v-card.darkShadow
        v-container
          v-card-text
            p.text-lg We are a group of software developers and engineers dedicated to the creative design & implementation of free or low cost web applications for community benefit and public service.
          v-card.mx-auto
            v-card-text(v-for="m in mission" :key='m.name')
              h3 {{m.name}}
              ul
                li.vertical-list-item(v-for="item in m.list" :key='item') {{item}}
                  br
              //- v-list
              //-   v-list-item(v-for="item in m.list" :key='item')
              //-       v-list-item-content(style='width:100%') {{item}}
              //-       br
</template>

<script>
export default {
  name: 'Contact',
  components: {},
  data () {
    return {
      mission: [
        {
          name: 'Design Principles',
          list: [
            'Agile Development',
            'Open Source Software',
            'Collaboration / Cooperation',
            'Maximizing Functionality / Cost',
            'Using technology to serve the community at large'
          ]
        },
        {
          name: 'Fields of Focus / Interest',
          list: [
            'Public Research',
            'Environment',
            'Education',
            'Health',
            'Non-Profit / Social Enterprise'
          ]
        }
      ]
    }
  }
}
</script>
<style scoped>
li.vertical-list-item {
  display: block;
}
</style>
