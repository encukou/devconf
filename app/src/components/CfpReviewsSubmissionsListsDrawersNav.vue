<template>
  <div>
    <v-footer class="ma-0 pa-1 grey lighten-5">
      <v-btn flat large class="green--text text--darken-3" @click="openDrawerApproved()">
        <v-icon class="black--text">chevron_right</v-icon>
        <v-icon class="mr-2">check</v-icon>
        Approved ({{ approved.length }})
      </v-btn>

      <v-spacer></v-spacer>

      <v-btn icon large :loading="isWorking"></v-btn>

      <v-spacer></v-spacer>

      <v-btn flat large class="red--text text--darken-3" @click="openDrawerRejected()">
        ({{ rejected.length }})
        Rejected
        <v-icon class="ml-2">delete_sweep</v-icon>
        <v-icon class="black--text">chevron_left</v-icon>
      </v-btn>

    </v-footer>

    <cfp-reviews-submissions-lists-drawer
      :drawer="drawers.approved"
      :types="types"
    ></cfp-reviews-submissions-lists-drawer>

    <cfp-reviews-submissions-lists-drawer
      :drawer="drawers.rejected"
      :types="types"
    ></cfp-reviews-submissions-lists-drawer>

  </div>
</template>

<script>
import CfpReviewsSubmissionsListsDrawer from '@/components/CfpReviewsSubmissionsListsDrawer'

export default {
  name: 'cfp-reviews-submissions-lists-drawers-nav',
  computed: {
    isWorking () {
      return this.$store.getters.getIsWorking
    },
    approved () {
      return this.$store.getters.approved
    },
    rejected () {
      return this.$store.getters.rejected
    }
  },
  methods: {
    openDrawerApproved () {
      this.drawers.approved.active = true
    },
    openDrawerRejected () {
      this.drawers.rejected.active = true
    }
  },
  props: ['drawers', 'types', 'details'],
  components: {
    'cfp-reviews-submissions-lists-drawer': CfpReviewsSubmissionsListsDrawer
  }
}
</script>

<style></style>
