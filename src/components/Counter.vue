<template>
    <div>
        <div>{{countMassage}}</div>
        <button @click="count++">click!</button>
        <button @click="count=0">reset!</button><br>
        <input type="text" v-model="input1" placeholder="input here">
        <button @click="add">add</button>
        <button @click="add2">add2</button>
        <ul>
            <li v-for="item in items" :key="item.name">
                <template v-if="!item.selected">
                    {{item.name+"po"}}
                </template>
                <template v-else>
                    {{item.name+"hoge"}}
                </template>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: "counter",
    data(){
        return {
            count: 0,
            input1 : "",
            items:[]
        };
    },
    computed:{
        countMassage(){
            return "回数: " + this.count;
        }
    },
    methods:{
        reset : function(){
            this.count = 0;
            return ;
        },
        add : function(){
            if(this.input1!=""){
                console.log(this.input1);
                this.items.push({name:this.input1,selected:true})
                this.input1 = "";
                return ;
            }
        },
        add2 : function(){
            if(this.input1!=""){
                console.log(this.input1);
                this.items.push({name:this.input1,selected:false})
                this.input1 = "";
                return ;
            }
        }
    }
};

</script>

<style>
ul {
  list-style-type: none;
  padding: 0;
}

</style>