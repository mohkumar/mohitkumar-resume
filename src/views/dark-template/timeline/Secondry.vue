<template>
  <v-card
    color="grey lighten-4"
    light
  >
    <v-card-text>
      <content-section
        id="published"
        :title="'My Published Article'"
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
                  alt="image"
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
  name      : 'Published',
  components: { ContentSection },
  data      : () => ({
    detailed: true,
    items   : [
      {
        year : 'Feb - 2021',
        title: 'Article on The Do’s and Don’ts of Software Product Testing',
        html : `
          <p>
              Current status: <span class="blue--text text--darken-2">Published</span><br>Available on: <a target="_blank" href="https://www.linkedin.com/pulse/dos-donts-software-product-testing-mohit-kumar/?trackingId=p0MF59wMQB65XuoHnUxx5Q%3D%3D">The Do’s and Don’ts of Software Product Testing</a>
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
        year : 'March -2021',
        title: 'Article on Design QA - Make it Official',
        html : `
          <p>
              Current status: <span class="blue--text text--darken-2">Published</span><br>Available on: <a target="_blank" href="https://www.linkedin.com/pulse/design-qa-make-official-mohit-kumar/?trackingId=8CRbBF44R7KJX%2Bu9KYpdug%3D%3D">Design QA - Make it Official</a>
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
