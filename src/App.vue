<template>
  <div id="app">
    <h1>{{title}}</h1>
    <input type="text" name="newItem" v-model="newItems" v-on:keyup.enter="addNew">
    <ol>
      <li v-for="item in items" v-bind:class="{finish:item.finished}">
        {{item.label}}
        <button class="btn" v-on:click="togglefinish(item)" v-bind:disabled="item.finished">{{item.btnName}}</button>
      </li>
    </ol>
  </div>
</template>

<script>
export default {
  name: 'app',
  data(){
    return{
      title:"this is a todolist",
      items:[],
      newItems:'',
      liclass:"finish"
    }
  },
  methods:{
    addNew(){
      this.items.push(
      {
        label:this.newItems,
        finished:false,
        btnName:"has finished it?",
      });
      this.newItems='';
    },
    togglefinish(item){
      item.finished=!item.finished;
      item.btnName="has finished!";

    }
  }
}
</script>

<style>
h1
{
  color: #22CBB5;
  width: 300px;
  margin: 50px auto;
}
input
{
  display: block;
  width: 200px;
  height: 20px;
  margin: 20px auto;
}
ol
{
  position: relative;
  width: 500px;
  left: 50%;
  margin-left: -250px;
}
li
{
  margin-bottom: 10px;
}
.finish
{
  text-decoration: line-through;
}
.btn
{
  width: 100px;
  height: 25px;
  color: #ffffff;
  background-color: #0067FF;
  border: none;
  border-radius: 5px;
  margin-left: 20px;
}
</style>
