<template>
    <div>
        <p v-if="listPage==1"></p>
        <ul v-else>
            <li v-for="(item,index) in listPage" :key="item" @click="getData(index+1)">

            </li>
        </ul>
    </div>
</template>

<script>
export default{
    data(){
        return{
            listPage:1
        }
    },
    mounted(){
        var that=this;
        axios.get("http://localhost:3000/demo")
        .then((result)=>{
            that.listPage=result.data.data.length
        })
    },
    methods:{
        getData(nPage){
            console.log(nPage);
        }
}
}

</script>