<template>
    <div>
        <ul>
            <li v-for="(task,index) in tasks" :key="index">
                <p>Title:   {{task.title}}</p>
                <p>Description: {{task.description}}</p>
            </li>  
        </ul>
        <h1>{{posts}}</h1>
        <h1>{{errors}}</h1>
    </div>
</template>

<script>
import axios from 'axios';
export default {
    name:'APIComponent',
    data(){
        return{
            tasks:[{title:'Learn Vuex',description:'Learn Vuex really fast and Integrate it with DB'},
            {title:'Learn Fast',description:'Learn Axios Request'}],
            posts:[],
            errors:[]
        }
    },
    async created() {
    try {
      const response = await axios.get(`http://jsonplaceholder.typicode.com/posts`)
      this.posts = response.data
    } catch (e) {
      this.errors.push(e)
    }
  }

}
</script>