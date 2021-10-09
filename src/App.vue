<template>
    <div>
        <div>
            <button @click="currentTab = 'ResourceList'">Resource List</button>
            <button @click="currentTab = 'CreateResource'">Add Resource</button>
        </div>

        <!-- <component :is="currentTab"></component> -->
        
        <ResourceList v-if="currentTab == 'ResourceList'" :resources="resources" @delete-resource="deleteResource"/>
        <CreateResource v-if="currentTab == 'CreateResource'" @add-resource="addResource" />

    </div>

    <hr>
    <h2> demo </h2>
    <DemoMain></DemoMain>

</template>

<script>
import ResourceList from './components/ResourceList.vue';
import CreateResource from './components/CreateResource.vue';
import DemoMain from './components/demo/DemoMain.vue';
export default {
    components: {ResourceList, CreateResource, DemoMain},
    data(){
        return{
            currentTab: 'ResourceList',
            resources: [
                {
                    title: 'abc',
                    description: "this is abc",
                    link: "https://github.com/vatsal8081/9-vue-component-advance/blob/master/src/components/slots/UserCardWrapper.vue"
                }
            ]
        };
    },
    methods: {
        addResource(resource){
            this.resources.push(resource)
            this.currentTab = 'ResourceList'
        },
        deleteResource(i){
            this.resources.splice(i, 1)
        }
    }
};

</script>

