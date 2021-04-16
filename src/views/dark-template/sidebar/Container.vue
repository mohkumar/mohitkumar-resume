<template>
  <v-card
    color="card-panel teal lighten-2"
    dark
  >
    <v-card-text>
      <avatar />
      <div class="text-sm-center mb-4 mt-3">
        <h1>
          <span class="black--text text--lighten-3">Mohit Kumar</span>
        </h1>
        <span>
          <h4 class="black--text text--lighten-3">Senior Specialist/Automation Architect</h4>
        </span>
      </div>

      <sidebar-section :options="sections.info" />
      <sidebar-section :options="sections.socials" />
      <sidebar-section :options="sections.hobbies">
        <template v-slot:item="{item}">
          <v-chip>
            <v-avatar>
              <v-icon>
                {{ item.icon }}
              </v-icon>
            </v-avatar>
            {{ item.text }}
          </v-chip>
        </template>
      </sidebar-section>
      <sidebar-section :options="sections.languages">
        <template v-slot:items="{items}">
          <v-container pa-0>
            <v-layout
              wrap
              class="text-xs-center"
            >
              <template
                v-for="(item, i) in items"
              >
                <v-flex
                  :key="i"
                  md3
                  sm4
                  xs6
                >
                  <v-progress-circular
                    rotate="360"
                    size="65"
                    width="2"
                    :value="item.value"
                    color="black"
                    class="ma-2"
                  >
                    {{ item.text }}
                  </v-progress-circular>
                </v-flex>
              </template>
            </v-layout>
          </v-container>
        </template>
      </sidebar-section>
    </v-card-text>
  </v-card>
</template>

<script>
import Avatar from '@/views/dark-template/sidebar/Avatar'
import SidebarSection from '@/views/dark-template/sidebar/Section'
export default {
  name      : 'Sidebar',
  components: { SidebarSection, Avatar },
  data () {
    return {
      sections: {
        info: {
          title: 'INFO!',
          items: [
            {
              name: 'Birth Date',
              icon: 'mdi-cake-variant',
              text: 'Feb 04, 1989',
            },
            {
              name: 'Home Town',
              icon: 'mdi-map-marker',
              text: 'Bangalore, India',
            },
          ],
        },
        socials: {
          title: 'CONTACT ME!',
          items: [
            {
              name: 'Email',
              icon: 'mdi-email',
              text: 'kumar.mohit3189@gmail.com',
            },
            {
              icon: 'mdi-linkedin-box',
              text: 'linkedin.com/in/mohit-kumar-6143001b/',
              link: 'https://www.linkedin.com/in/mohit-kumar-6143001b/',
            },
            {
              icon: 'mdi-phone',
              text: '+91-7022494429',
            },
            {
              icon: 'mdi-github-circle',
              text: 'github.com/mohkumar',
              link: 'https://github.com/mohkumar',
            },
          ],
        },
        hobbies: {
          title: 'HOBBIES & INTERESTS',
          items: [
            {
              icon: 'mdi-blogger',
              text: 'Professional Blogging',
            },
            {
              icon: 'mdi-run',
              text: 'Running',
            },
            {
              icon: 'mdi-hiking',
              text: 'Hiking',
            },
            {
              icon: 'mdi-harddisk',
              text: 'Dj',
            },
            {
              icon: 'mdi-music',
              text: 'Music',
            },
            {
              icon: 'mdi-cricket',
              text: 'Sports',
            },
            {
              icon: 'mdi-netflix',
              text: 'Web Series',
            },
          ],
        },
        languages: {
          title: 'LANGUAGES',
          items: [
            {
              text : 'English',
              value: 100,
            },
            {
              text : 'Hindi',
              value: 100,
            },
          ],
        },
      },
    }
  },
}
</script>

<style scoped>
.sidebar{
    background: #4db6ac;
}
</style>
