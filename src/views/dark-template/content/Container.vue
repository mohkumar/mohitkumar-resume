<template>
  <v-card
    color="grey lighten-4"
    light
  >
    <v-card-text>
      <content-section
        title="About"
      >
        Product Test Specialist, specializing in various domain such as Defence, Retail (B2B, B2C) and Life Science and Health Care industry. Goal-oriented individual with strong leadership capabilities, problem-solving ability using innovative technology and creative thinking.<br><br>
        I have been working as a Senior Specialist/Automation Solution Architect at Deloitte. Trained on IEC 62304:2006 for “Medical device software — Software life cycle processes”, lead on various challenging client engagements. My primary responsibilities have been to architect software solutions for highly complex business requirements. I have been leading a team of software and quality assurance engineers and have defined and implemented technology frameworks for client projects. I am responsible for enforcing and applying Deloitte's strict quality and delivery methodologies to these engagements. I have defined and set clear standards to be pursued for code and quality reviews that becomes a high value, viable product to the client.
      </content-section>
      <content-section
        v-if="educations"
        title="Education"
      >
        <v-layout
          v-for="(education, i) in educations"
          :key="i"
        >
          <v-flex md4>
            {{ education.from }} - {{ education.to }}
          </v-flex>
          <v-flex md8>
            <strong v-if="education.title">{{ education.title }}</strong>
            <div v-if="education.location">
              <i>{{ education.location }}</i>
            </div>
          </v-flex>
        </v-layout>
      </content-section>
      <content-section
        v-if="licences"
        title="Licenses &amp; certifications"
      >
        <v-layout
          v-for="(licences, i) in licences"
          :key="i"
        >
          <v-flex md4>
            {{ licences.Issuedate }}
          </v-flex>
          <v-flex md8>
            <strong v-if="licences.title">{{ licences.title }}</strong>
            <div v-if="licences.location">
              <i>{{ licences.location }}</i>
            </div>
          </v-flex>
        </v-layout>
      </content-section>
      <content-section
        v-if="skills"
        id="to-timeline"
        title="Skills"
      >
        <v-layout wrap>
          <template
            v-for="(skill, i) in skills"
          >
            <v-flex
              v-if="skill.divider"
              :key="i"
              md12
              xs12
              mb-4
            />
            <v-flex
              v-else
              :key="i"
              md6
              xs12
            >
              <div
                class="mr-2 ml-2"
              >
                <div class="align-center">
                  <v-icon
                    medium
                  >
                    {{ skill.icon }}
                  </v-icon>
                  {{ skill.title }}
                </div>
                <v-progress-linear
                  class="progress"
                  color="secondary"
                  height="3"
                  :value="skill.value"
                />
              </div>
            </v-flex>
          </template>
        </v-layout>
      </content-section>
    </v-card-text>
  </v-card>
</template>

<script>
import ContentSection from '@/views/dark-template/content/Section'
export default {
  name      : 'MainContent',
  components: { ContentSection },
  data      : () => ({
    educations: [
      {
        from    : '2006',
        to      : '2010',
        title   : 'BE, Information Technology',
        location: 'Acharya Institute Of Technology, Bangalore',
      },
      {
        from    : '2017',
        to      : '2019',
        title   : 'Post Graduate Diploma in Business Management',
        location: 'SVKM\'s Narsee Monjee Institute of Management Studies (NMIMS), Bangalore',
      },
    ],
    licences: [
      {
        Issuedate: 'Issued on Dec - 2015',
        title    : 'ISO 13485:2016 Medical devices — Quality management systems — Requirements for regulatory purposes',
        location : 'Medtronic, Bangalore',
      },
      {
        Issuedate: 'Issued on Aug - 2015',
        title    : 'Regular requirements for medical device software according to IEC 62304:2006',
        location : 'TUV Rheinland, Bangalore',
      },
      {
        Issuedate: 'Issued on Dec - 2012',
        title    : 'Product Quality Management System',
        location : 'Tech Mahindra, Bangalore',
      },
    ],
    skills: [
      {
        title: 'Product Testing',
        icon : 'mdi-briefcase-check',
        value: 95,
      },
      {
        title: 'Automation Testing',
        icon : 'mdi-flash-auto',
        value: 95,
      },
      {
        title: 'Cucumner - NodeJS',
        icon : 'mdi-language-javascript',
        value: 90,
      },
      {
        title: 'Cucumner - Java',
        icon : 'mdi-table',
        value: 90,
      },
      {
        title: 'Design Thinking',
        icon : 'mdi-lightbulb',
        value: 90,
      },
      {
        title: 'IEC 62304:2006',
        icon : 'mdi-plus-box',
        value: 95,
      },
      {
        title: 'Asset Development',
        icon : 'mdi-trophy',
        value: 90,
      },
      {
        title: 'ISO 13485:2016 Medical Devices - QMS',
        icon : 'mdi-test-tube',
        value: 95,
      },
      {
        title: 'API Testing',
        icon : 'mdi-server',
        value: 80,
      },
      {
        title: 'Performance Testing',
        icon : 'mdi-chart-line',
        value: 67,
      },
      {
        title: 'QAOps',
        icon : 'mdi-sync',
        value: 70,
      },
      {
        title: 'Git',
        icon : 'mdi-git',
        value: 95,
      },
      {
        title: 'Leadership',
        icon : 'mdi-account-group',
        value: 80,
      },
      {
        title: 'Content Marketing',
        icon : 'mdi-text',
        value: 80,
      },
    ],
  }),
}
</script>

<style scoped>
.title {
  border-bottom: 2px #bfbfbf solid;
  line-height: 1.5 !important;
}
.progress {
  margin-top: 0.1rem;
}
</style>
