<template>
  <v-card
    color="grey lighten-4"
    light
  >
    <v-card-text>
      <content-section
        id="timeline"
        :title="'My Experiences'"
      >
        <v-timeline
          dense
        >
          <v-timeline-item
            v-for="(item, i) in orderedItems"
            :key="i"
            :icon="item.icon || ''"
            :class="{transparent: item.transparent}"
            large
          >
            <template
              v-if="item.iconImage"
              v-slot:icon
            >
              <v-avatar>
                <img
                  :src="publicPath(item.iconImage)"
                >
              </v-avatar>
            </template>
            <template v-slot:opposite />
            <v-layout>
              <v-flex
                v-if="$vuetify.breakpoint.smAndUp"
                md1
                sm2
                align-self-center
              >
                <span>{{ item.year }}</span>
              </v-flex>
              <v-flex
                md11
                sm10
                xs12
              >
                <v-card class="elevation-1">
                  <v-card-title class="pb-0">
                    <div>
                      <p v-if="$vuetify.breakpoint.xsOnly">
                        {{ item.year }}
                      </p>
                      <h3>{{ item.title }}</h3>
                    </div>
                  </v-card-title>
                  <v-card-text>
                    <v-layout wrap>
                      <v-flex
                        :md7="!!item.image"
                        :md12="!item.image"
                        xs12
                      >
                        <div class="mr-1">
                          <span
                            v-if="item.text"
                            class="pre"
                          >{{ item.text }}</span>
                          <!-- eslint-disable vue/no-v-html -->
                          <div
                            v-else-if="item.html"
                            v-html="item.html"
                          />
                          <!-- eslint-enable vue/no-v-html -->
                        </div>
                      </v-flex>
                      <v-flex
                        v-if="item.image"
                        md5
                        xs12
                      >
                        <div
                          class="mt-2"
                        >
                          <v-carousel
                            v-if="Array.isArray(item.image)"
                            :show-arrows="false"
                            :height="325"
                          >
                            <v-carousel-item
                              v-for="(citem,ci) in item.image"
                              :key="ci"
                              :src="publicPath(citem)"
                            />
                          </v-carousel>
                          <v-img
                            v-else
                            :max-height="item.imageHeight ? item.imageHeight : ''"
                            :src="publicPath(item.image)"
                          />
                        </div>
                      </v-flex>
                    </v-layout>
                  </v-card-text>
                </v-card>
              </v-flex>
            </v-layout>
          </v-timeline-item>
        </v-timeline>
      </content-section>
    </v-card-text>
  </v-card>
</template>

<script>
import ContentSection from '@/views/dark-template/content/Section'
export default {
  name      : 'Timeline',
  components: { ContentSection },
  data      : () => ({
    detailed: true,
    items   : [
      {
        detailed   : true,
        transparent: false,
        year       : '2010 - 2012 Bangalore',
        title      : 'Avembsys Technologies Pvt. Ltd.',
        html       : `
                    <p>
                        <h5>Software Engineer/Product Engineer</h5>
                    </p>
                    <li>Involved in Verification of Software Requirements Specification</li><li>Developing HSI Test Cases (High Level Test Cases) RBT and SWI Test Cases (Low Level Test Cases).</li><li>White Box Testing: Developing HSI Test Scripts, Compiling and executing on Automation tool RTRT Tester</li><li>To Analyze test results and reporting the bugs</li><li>Involved in technical peer review and process quality review for SDD, HSI Test cases review and SWI Test cases</li>`,
        iconImage  : 'img/timeline/avembsys.png',
        imageHeight: 200,
      },
      {
        detailed   : true,
        transparent: false,
        year       : '2012 - 2014 Bangalore',
        title      : 'Tech Mahindra',
        html       : `
                    <p>
                        <h5>Software Test Engineer</h5>
                    </p>
                    <li>Involved in configuration of Robotium, MonkeyTalk (android as well as iOS) and android selenium</li><li>Testing the web application for android, Blackberry and iOS</li><li>Testing the web application for Desktop</li><li>Writing Automation JUnit test cases using Robotium</li><li>Writing scripts using TestNG framework</li><li>Regression testing of the web applications<li>Regression testing of the Middle ware Platform Testing</li><li>Monitoring the Application and DB servers</li><li>Executing Performance, Scalability and Reliability tests</li><li>Setting up the monitors and observing the counters of Application and Database servers</li><li>Generating the execution summary reports and communicating it to the clients</li><li>Encourage team members to continue brainstorming</li>`,
        iconImage  : 'img/timeline/techm.png',
        imageHeight: 200,
      },
      {
        detailed   : true,
        year       : '2014 - 2015 Bangalore',
        transparent: false,
        title      : 'GlobalLogic',
        html       : `
          <p>
            <h5>Senior Test Automation Engineer/Product QA</h5>
          </p>
          <li>Setting up the test environment</li><li>Testing Windows Phone Applications manually</li><li>Monitoring the Application and DB servers</li><li>Involved in preparation of Mobile Application Testing Guidelines, Test Plan, Test Cases, and Test Scenarios</li><li>Performing Functional, Integration, System, Regression Testing</li><li>Reporting bugs to developers using JIRA</li><li>Involve in daily scrum meeting with team as well as with the clients</li><li>Involve in the team to gain expertise on various test tools</li></li>`,
        iconImage  : 'img/timeline/GL.png',
        imageHeight: 200,
      },
      {
        detailed   : true,
        year       : '2015 - 2016 Bangalore',
        transparent: false,
        title      : 'Medtronic Inc.',
        html       : `
                    <p>
                        <h5>Senior Test Automation Engineer/Product QA</h5>
                    </p>
                    <li>Testing customized android application for Console GUI sub system along with Therapy sub system</li><li>Involved in preparation of Test Plan & Strategy, Test Protocols, and Test Scripts (using Appium)</li><li>Performing Functional, Integration, System, and Regression Testing</li><li>Writing Automation JUnit test cases using Robotium</li><li>Involved in Testing of Console UI application in English-Chinese translation</li><li>Heading Performance and Security Testing for customized android package<li>Involved in testing android BSP using Android Compatibility Test Suite (CTS)</li><li>Involved in Reviewing Requirement and UI Spec. document</li><li>Reporting bugs to developers using Polarian</li><li>Involve in the team to gain expertise on various test tools</li><li>Involved in attending calls with onsite team on weekly basis</li><li>EInvolved in leading test team and coordinating between development and test team</li>`,
        iconImage  : 'img/timeline/medtronic.png',
        imageHeight: 200,
      },
      {
        detailed   : true,
        year       : '2016 - 2018 Bangalore',
        transparent: false,
        html       : `
                    <p>
                         <h5>Consultant/Test Automation Lead</h5>
                    </p>
                    <li>Leading Test Automation Team and coordinating between developers and manual QA team</li><li>Involved in reviewing user stories available in JIRA and providing feedback</li><li>Involved in preparation of Test Plan & Strategy, Test Protocols, and Test Scripts</li><li>Successfully Automated 200 Test cases using Xamarin UI Test</li><li>Successfully launched all the automated test cases into Xamarin Test Cloud with a 97% success rate</li><li>Writing BDD Gherkin syntax that can be used to create executable tests<li>Automating iOS and Android application using Xamarin UI + Specflow Test as well as running tests into Xamarin Test Cloud</li></li>`,
        iconImage  : 'img/timeline/deloitte.png',
        imageHeight: 200,
      },
      {
        detailed   : true,
        year       : '2018-Present Bangalore',
        transparent: false,
        title      : 'Deloitte',
        html       : `
                    <p>
                        <h5>Senior Specialist/Automation Solution Architect</h5>
                    </p>
                    <li>Working as Test Manager and helped him setting up Manual & Automation processes for Deloitte’s first-ever Class 2 SaMD App</li><li>Involved in developing first-ever connected device automation framework for Class 2 SaMD Apps</li><li>Managed the team including development, QA and Dev opts to meet the sprint timeline</li><li>Responsible for sending daily scrum report between onshore and offshore team including client as well</li><li>Headed Automation Testing individually and coordinating between the development and test team</li><li>Involved in reviewing user stories available in JIRA and providing feedback<li>Involved in preparation of Test Plan & Strategy, Test Protocols, and Test Scripts</li><li>Writing BDD Gherkin syntax that can be used to create executable tests</li><li>Involved in attending calls with the offshore and onsite team on a weekly basis</li><li>Involve in the team to gain expertise on various test tools</li><li>Providing automation testing knowledge within and across teams</li></li>`,
        iconImage  : 'img/timeline/deloitte.png',
        imageHeight: 200,
      },
      {
        year : 'Feb - 2021',
        title: 'Article on The Do’s and Don’ts of Software Product Testing',
        html : `
          <p>
              Current status: <span class="light-blue--text lighten-3">Published</span><br>Available on: <a target="_blank" href="https://www.linkedin.com/pulse/dos-donts-software-product-testing-mohit-kumar/?trackingId=p0MF59wMQB65XuoHnUxx5Q%3D%3D">The Do’s and Don’ts of Software Product Testing</a>
          </p>
          <p>
            The quality of any software product is sustained on the success of software product testing. However, QA members should prioritize their strategies, take a hard look at their QA processes and decide to make some changes, moving away from the typical testing approach considering few dos and don’ts to ensure the delivery of products with top-notch quality and rendering a superior user experience.
          </p>
        `,
        image      : 'img/timeline/1612851620757.png',
        imageHeight: 200,
        iconImage  : 'img/timeline/linkedin.png',
      },
      {
        year : 'March - 2021',
        title: 'Article on Design QA - Make it Official',
        html : `
          <p>
              Current status: <span class="light-blue--text lighten-3">Published</span><br>Available on: <a target="_blank" href="https://www.linkedin.com/pulse/design-qa-make-official-mohit-kumar/?trackingId=8CRbBF44R7KJX%2Bu9KYpdug%3D%3D">Design QA - Make it Official</a>
          </p>
          <p>
            In digital product development, the user experience encloses everything that the product team does; design, development, and testing — everyone’s role impact the need of the intended user.
            <ul>
                <li>What is Design QA?</li>
                <li>Difference between Design QA and QA?</li>
            </ul>
          </p>
        `,
        image      : 'img/timeline/Screen Shot 2021-04-15 at 4.18.16 PM.png',
        imageHeight: 200,
        iconImage  : 'img/timeline/linkedin.png',
      },
    ],
  }),
  computed: {
    orderedItems () {
      const items = [...this.items].reverse()
      if (this.detailed)
        return items
      return items.filter((item) => {
        return !item.detailed
      })
    },
  },
}
</script>

<style scoped>
.title {
  border-bottom: 2px #bfbfbf solid;
  line-height: 1.5 !important;
}
.pre {
  white-space: pre;
}
.transparent{
  opacity: 0.6;
}
</style>
