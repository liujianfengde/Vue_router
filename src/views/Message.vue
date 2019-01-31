<template>
  <div>
    <ul>
      <li v-for="(message,index) in messages" :key="message.id">
        <router-link :to="`/home/message/detail/${message.id}`">{{message.title}}</router-link>
        <button @click="pushShow(message.id)">push查看</button>
        <button @click="replaceShow(message.id)">replace查看</button>
      </li>
    </ul>
    <hr>
    <button @click="$router.back()">回退</button>
    <router-view></router-view>
  </div>
</template>
<script>
export default{
  data(){
    return {
      messages:[]
    }
  },
  mounted(){
    setTimeout(()=>{
      const message=[
        {
          id:1,
          title:'message001'
        },
        {
          id:2,
          title:'message002'
        },
        {
          id:3,
          title:'message003'
        },
      ]
      this.messages=message
    },1000)
  },
  methods:{
    pushShow(id){
      this.$router.push(`/home/message/detail/${id}`)
    },
    replaceShow(id){
      this.$router.replace(`/home/message/detail/${id}`)
    },
  }
}
</script>
<style>

</style>
