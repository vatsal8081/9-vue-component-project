<template>
  <form @submit.prevent>

      Title: <input type="text"   v-model="resourceForm.title"/>
      <span  v-if="resourceFormErr.title.err">{{ resourceFormErr.title.errTxt }}</span>
      Description: <input type="text"   v-model="resourceForm.description"/>
            <span  v-if="resourceFormErr.description.err">{{ resourceFormErr.description.errTxt }}</span>
      Link: <input type="text"   v-model="resourceForm.link"/>
            <span  v-if="resourceFormErr.link.err">{{ resourceFormErr.link.errTxt }}</span>

      <button type="button" @click="addResource"> Add </button>


    <teleport to="body">
      <ErrModle v-if="resourceFormErr.modleOpen" @ok-click="resourceFormErr.modleOpen = false">
          <p  v-if="resourceFormErr.title.err">{{ resourceFormErr.title.errTxt }}</p>
          <p  v-if="resourceFormErr.description.err">{{ resourceFormErr.description.errTxt }}</p>
          <p  v-if="resourceFormErr.link.err">{{ resourceFormErr.link.errTxt }}</p>
      </ErrModle>
    </teleport>

  </form>
</template>

<script>
import ErrModle from './ErrModle.vue';
export default {

    components: {
        ErrModle,
    },

    data(){
        return {
            resourceForm: {
                title: "",
                description: "",
                link: ""
            },
            resourceFormErr: {
                err: false,
                modleOpen: false,
                title: {
                    err: false,
                    errTxt: 'This Firld is Require.' 
                },
                description: {
                    err: false,
                    errTxt: 'This Firld is Require.' 
                },
                link: {
                    err: false,
                    errTxt: 'This Firld is Require.' 
                }
                
            }
        };
    },

    methods: {

        validate(){
            this.resourceFormErr.err = false;
            if(!this.resourceForm.title){
                this.resourceFormErr.title.err = true
                this.resourceFormErr.err = true
            }
            else{
                this.resourceFormErr.title.err = false
            }
            if(!this.resourceForm.description){
                this.resourceFormErr.description.err = true
                this.resourceFormErr.err = true
            }
            else{
                this.resourceFormErr.description.err = false
            }
            if(!this.resourceForm.link){
                this.resourceFormErr.link.err = true
                this.resourceFormErr.err = true
            }
            else{
                this.resourceFormErr.link.err = false
            }
        },

        addResource(){

            this.validate()
            console.log('err', this.resourceFormErr);
            if(!this.resourceFormErr.err){
                this.$emit('add-resource', this.resourceForm)
            }
            else{
                this.resourceFormErr.modleOpen = true
            }
        }
    }

}
</script>

<style>

</style>