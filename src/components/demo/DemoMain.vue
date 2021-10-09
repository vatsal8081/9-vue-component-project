<template>
  <p> ----------  From Demo Main   ---------------------</p>
  <div v-for="item in friends" :key="item">
      <p> {{ item }} </p>
  </div>

  <DemoProp :friends="friends"></DemoProp>
  <DemoProvide></DemoProvide>
</template>

<script>
import DemoProp from './DemoProp.vue';
import DemoProvide from './DemoProvide.vue';
export default {    
    components: {DemoProp, DemoProvide},

    provide(){
        return {
          friends: this.friends
        }  
    }, 

    created(){

        setTimeout(() => {

            // CASE 1

            let newFriends = this.friends.filter((el) => el !== 'vatsal')
            this.friends = newFriends
            
            // CASE 2
            // let index = this.friends.findIndex((el) => el === 'vatsal')
            // this.friends.splice(index, 1)

        } ,5000)
    },

    data(){
        return {
            friends: [
                'vatsal',
                'shivam'
            ]
        };
    }

}
</script>

<style>

</style>