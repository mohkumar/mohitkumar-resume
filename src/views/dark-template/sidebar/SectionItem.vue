<template>
  <v-layout>
    <v-flex
      v-if="hasIcon"
      xs2
    >
      <v-icon>
        {{ item.icon }}
      </v-icon>
    </v-flex>
    <v-flex
      :xs10="hasIcon"
      :xs12="!hasIcon"
    >
      <div>
        {{ item.name }}
      </div>
      <p>
        <a
          v-if="item.link"
          class="black--text text--lighten-3"
          :href="item.link"
          target="_blank"
        >
          {{ item.text }}
        </a>
        <span
          v-else
          class="black--text"
        >
          {{ item.text }}
        </span>
      </p>
    </v-flex>
  </v-layout>
</template>

<script>
export default {
  name    : 'SidebarSectionItem',
  props   : { item: { type: Object, default: () => {} } },
  computed: {
    hasIcon () {
      return !!this.item.icon
    },
  },
}
</script>

<style scoped>
</style>
