<template>
  <base-card>
  <base-button @click="changeTab('stored-resource')" :class="storedResourceButton">Show resources</base-button>
  <base-button @click="changeTab('add-resource')" :class="addResourceButton">Add resources</base-button>
  </base-card>
  <keep-alive>
  <component :is="selectedTab"></component>
  </keep-alive>
</template>

<script>
import StoredResource from './StoredResource.vue';
import AddResource from './AddResource.vue';

export default {
    components: {
        StoredResource,
        AddResource
    },
    data() {
        return {
            selectedTab: 'stored-resource',
            storedResources : [
                {
                    id: 'official-guide',
                    title: 'Official guide',
                    description: 'The official Vue JS docs',
                    link: 'https://vuejs.org'
                },
                {
                    id: 'google',
                    title: 'Google',
                    description: 'Learn how to google',
                    link: 'https://google.com'
                },
            ],
        };
    },
    provide() {
        return {
            resources: this.storedResources,
            submitResource: this.submitResource,
            deleteResource: this.deleteResource,
        }
    },
    methods: {
        changeTab(tab) {
            this.selectedTab = tab;
        },
        submitResource(title,description,url) {
            const newResource = {
                id: new Date().toISOString,
                title: title,
                description: description,
                link: url,
            };
            this.storedResources.unshift(newResource);
            this.selectedTab = 'stored-resource';
        },
        deleteResource(id) {
            const resourceIndex = this.storedResources.findIndex(resource => resource.id === id);
            console.log(resourceIndex);
            this.storedResources.splice(resourceIndex,1);
        }
    },
    computed: {
        addResourceButton() {
            return this.selectedTab === 'add-resource' ? 'selectedButton' : null;
        },
        storedResourceButton() {
            return this.selectedTab === 'stored-resource' ? 'selectedButton' : null;
        },
    },

}
</script>

<style>

</style>