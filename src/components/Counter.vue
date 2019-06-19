<template>
    <div>
        <div>{{countMassage}}</div>
        <button @click="count++">click!</button>
        <button @click="count=0">reset!</button><br>
        <input type="text" v-model="input1" placeholder="input here">
        <button @click="add">add</button>
        <button @click="add2">add2</button>
        <button @click="dele">delete</button>
        <ul>
            <li v-for="item in items" :key="item.name">
                <template v-if="!item.selected">
                    <span v-bind:class="{ list: isList }" @click="item.selected ? item.selected=false:item.selected=true">
                        {{item.name}}
                    </span>
                </template>
                <template v-else>
                    <span v-bind:class="{ list2: isList }" @click="item.selected ? item.selected=false:item.selected=true">
                        {{item.name}}
                    </span>
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
            items:[],
            isList:true
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
        },
        dele : function(){
            console.log("delete");
            for(let i = this.items.length-1;i>=0;--i){
                if(!this.items[i].selected){
                    this.items.splice(i,1);
                }
                //this.items.splice()
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
li{
    font-size:24px;
}
.list{
    /*text-decoration : line-through;*/
    color : rgb(185, 185, 185);
    /*font-size:30px;*/
}
.list2{
    font-weight: 700;
}
</style>