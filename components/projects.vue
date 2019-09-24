<template lang='pug'>
  div.container
    h1.primary-colour Current Projects
    hr
    div.text-lg
      p
        b If any of these projects is of interest to you, please feel free to contact us to get involved.
      p We are always looking for enthusiastic developers and potential users / collaborators
    div(v-for='project in projects')
      v-card.padded.darkShadow
        //- v-img.projectImage.white--text(height="200px" :src="project.image")
        img.projectImage(:src='project.image')
        div.wideRight(style='float: right')
          b {{project.name}}
          br 
          span {{project.title}}
        hr(style='color: grey; width: 100%')
        v-card-text
          span(v-if='project.description' v-for='p in project.description')
            p {{p}}
          div.listBlock(v-if='project.list')
            ul
            span(v-for="item in project.list")
              li {{item}}
      p &nbsp;
</template>

<script>
export default {
  name: 'Contact',
  components: {},
  data () {
    return {
      projects: [
        {
          name: 'IDVPN',
          title: 'A Secure VPN for Your Identity',
          image: '/images/cosine/idvpn.svg',
          description: [
            'Maintain ID autonomy in the age of big data',
            'For those that no longer want their legal actions to be tracked online'
          ]
        },
        {
          name: 'LITMUS',
          title: 'Laboratory Information Management System',
          image: '/images/cosine/litmus.png',
          description: [
            'This is a fully functional and sophisticated data management system that facilitates detailed barcode tracking within a laboratory environment.',
            'It is also designed to be adapted with a relatively small amount of work to be customized for different environments and different needs as required.',
            'This is a lightweight responsive version designed to work cleanly with both desktops and tablets or phone sized mobiles.'
          ]
        },
        {
          name: 'SPARC',
          image: '/images/cosine/venn.gif',
          title: 'Social Platform Affecting Real Connections',
          description: [
            'A community-based application to facilitate and encourage dynamic event hosting by members in a way that makes it so much easier to meet likeminded people in your community in a fun environment'
          ],
          list: [
            'Dinner Parties',
            'Sports Activities',
            'Discussion Groups',
            'Cultural Events',
            'Singles Events',
            'Outdoor Activities',
            'Group Travel',
            'Community Support Groups'
          ]
        },
        {
          name: 'OVID',
          image: '/images/cosine/ovid.png',
          title: 'Open Vaccine & Immunization Database',
          description: [
            'A comprehensive open-source interface for managing and tracking vaccinations that works for clinics, patients, and researchers'
          ]
        },
        {
          name: 'UTM',
          image: '/images/cosine/utm.png',
          title: 'Universal Touring Machine',
          description: [
            'A community-based application that enables easy access to customized tours for cities, galleries, museums or exhibitions.',
            'This is connected with a free app that can be accessed easily by the public. Individual tours can be made available for free or to generate funding for local app-guided tours'
          ]
        },
        {
          name: 'PRAM',
          image: '/images/cosine/pramIco.png',
          title: 'Purchasing Receiving & Asset Management',
          description: [
            'A very cost-effective open source solution for managing standard small to medium-sized Purchasing & Asset Management requirements'
          ]
        }
      ]
    }
  }
}
</script>

<style scoped>

.projectImage {
  height: 100px;
  justify-content: center;
}

</style>
