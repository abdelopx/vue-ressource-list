<template>
  <base-card>
  <base-button @click="changeTab('stored-resource')" :class="storedResourceButton">Show resources</base-button>
  <base-button @click="changeTab('add-resource')" :class="addResourceButton">Add resources</base-button>
  </base-card>
  <component :is="selectedTab"></component>
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
            resources: this.storedResources
        }
    },
    methods: {
        changeTab(tab) {
            this.selectedTab = tab;
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