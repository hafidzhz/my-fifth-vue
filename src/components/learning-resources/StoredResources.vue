<template>
  <learning-resource
    v-for="resource in resources" :key="resource.id"
    :id="resource.id"
    :title="resource.title"
    :description="resource.description"
    :link="resource.link"
  />
</template>

<script>
import LearningResource from './LearningResource'

export default {
  components: {
    LearningResource
  },
  inject: ['resources']
}
</script>
