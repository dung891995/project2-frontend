<template>

    <div>
<div v-for="post in posts" :key="post._id" class="show-all-posts">
    <p>Title {{post.title}}</p>
    <input type="text" :id="'Title:'+post._id">
    <p>Content {{post.content}}</p>
    <input type="text" :id="'Content:'+post._id">
    <p>Title {{post.author}}</p>
    <input type="text" :id="'Author:'+post._id">
        
<!-- Button Update Post -->
<button type="button" class="btn btn-primary" data-toggle="modal" data-target="#exampleModal"  @click="getID(post._id)">
  Edit your Post 
</button>

<!-- Modal Update Post-->


</div>

<div class="modal fade" id="exampleModal" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
  <div class="modal-dialog" role="document">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="exampleModalLabel">Update</h5>
        <button type="button" class="close" data-dismiss="modal" aria-label="Close">
          <span aria-hidden="true">&times;</span>
        </button>
      </div>
      <div class="modal-body">

             <label for="title" class="input-edit"> title: </label>
            <input v-model="title" type="text" class="input-edit" id="title-modal-create" name="title">
            <label for="title" class="input-edit"> content: </label>
            <input v-model="content" type="text" id="content-modal-create"  class="input-edit" name="content">
            <label for="title" class="input-edit"> author: </label>
            <input v-model="author" type="text" id="author-modal-create" class="input-edit" name="author">

      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
        <button type="button" class="btn btn-primary" @click="btnSave()">Save changes</button>
      </div>
    </div>
  </div>
</div> 
    </div>
</template>


<script>
import axios from "axios"
export default{
    data(){
        return{
            posts:[ ],
            npage:1,
            title:"",
            content:"",
            author:"",
            id:""
        }
    },
    mounted (){
        this.getData();
    },
   methods:{
       getID(id){
           this.id=id
       },
       btnSave(){
           axios
           .put('http://localhost:3000/update/'+this.id,{
               title:this.title,
               content:this.content,
               author:this.author,
           })
           .then(()=>{
            //    console.log(result);
            //    this.getData();
               window.location.href="/"
           })
           .catch((err)=>{
               console.log(err);
           })
   },
   getData(){
       axios
        .get('http://localhost:3000/page/'+this.page)
        .then((result) => {
        this.posts=result.data
        }).catch((err) => {
            console.log(err);
        });
   }
}
}
</script>