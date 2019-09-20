<template lang='pug'>
  div.container
    h1 Skills & Expertise
    hr
    div
      div(v-for="skill in skills")
        v-card.padded.mx-auto.darkShadow
          h2
            center
              v-icon {{skill.icon}}
              span &nbsp; &nbsp; {{skill.name}}
          br
          div.block.text-lg(v-if='skill.description') {{skill.description}}
          div.listBlock
            p.text-lg
              ul
              span(v-for="item in skill.list")
                li {{item}}
    div.wide-item &nbsp;
      hr
      div.flex-container
        span.flex-item(v-for="image in tools")
          img.toolsLogo(:src='image')
</template>

<script>
export default {
  name: 'Contact',
  components: {},
  data () {
    return {
      skills: [
        {
          icon: 'desktop-classic',
          name: 'Web Sites',
          description:
            'We can develop customized single-page or multi-page web sites that effectively communicate who you are and what you have to offer'
        },
        {
          icon: 'earth',
          name: 'Web Applications',
          description:
            'We can also develop more comprehensive web applications with personalized user login features, a database backend, and customized data handling and visualization'
        },
        {
          icon: 'database-export',
          name: 'Data Management',
          list: [
            'Database Design',
            'Data Standardization',
            'Streamlining Data Entry',
            'Data Mining',
            'Data Storage',
            'REST API development'
          ]
        },
        {
          icon: 'signal-cellular-3',
          name: 'Data Visualization',
          description: 'Generating simple ways to visualize data effectively',
          list: [
            'Dynamic Graphs / Bar Charts',
            'Annotated Data Maps',
            'Excel/PDF Reports'
          ]
        }
      ],

      tools: [
        '/images/cosine/lamp.jpg',
        '/images/cosine/bootstrap.png',
        '/images/cosine/node.png',
        '/images/cosine/angular.png',
        '/images/cosine/react.png',
        '/images/cosine/vue.png',
        '/images/cosine/adonis.jpg',
        '/images/cosine/d3t.jpg'
      ]
    }
  }
}
</script>

<style scoped>

.v-card.padded {
  padding: 2rem;
  margin: 2rem;
}

.flex-container {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
  margin: 2rem;
}
.flex-item {
  display: flex;
}

.toolsLogo {
  height: 50px;
}
</style>
