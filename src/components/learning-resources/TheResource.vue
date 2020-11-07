<template>
  <base-card>
    <base-button
      :mode="storedResButton"
      @click="setSelectedTab('stored-resources')">Stored Resources</base-button>
    <base-button
    :mode="addResButton"
    @click="setSelectedTab('add-resource')">Add Resource</base-button>
  </base-card>
  <keep-alive>
    <component :is="selectedTab"/>
  </keep-alive>
</template>

<script>
import StoredResources from './StoredResources'
import AddResource from './AddResource'

export default {
  components: {
    StoredResources,
    AddResource
  },
  computed: {
    storedResButton () {
      return this.selectedTab === 'stored-resources' ? null : 'flat'
    },
    addResButton () {
      return this.selectedTab === 'add-resource' ? null : 'flat'
    }
  },
  data () {
    return {
      selectedTab: 'stored-resources',
      resources: [
        {
          id: 'some-id-1',
          title: 'Title 1',
          description: 'Description 1',
          link: 'https://google.com'
        },
        {
          id: 'some-id-2',
          title: 'Title 2',
          description: 'Description 2',
          link: 'https://github.com'
        },
        {
          id: 'some-id-3',
          title: 'Title 3',
          description: 'Description 3',
          link: 'https://gitlab.com'
        },
        {
          id: 'some-id-4',
          title: 'Title 4',
          description: 'Description 4',
          link: 'https://bitbucket.org'
        }
      ]
    }
  },
  provide () {
    return {
      resources: this.resources,
      addResource: this.addResource,
      deleteResource: this.deleteResource
    }
  },
  methods: {
    setSelectedTab (tab) {
      this.selectedTab = tab
    },
    addResource (title, description, link) {
      this.resources.unshift({
        id: new Date().toISOString(),
        title,
        description,
        link
      })
      this.selectedTab = 'stored-resources'
    },
    deleteResource (id) {
      const index = this.resources.findIndex(r => r.id === id)
      this.resources.splice(index, 1)
    }
  }
}
</script>
