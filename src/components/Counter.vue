<template>
    <div>
        <input type="text" v-model="input1" placeholder="input here">
        <button @click="add">add</button>
        <!--<button @click="add2">add2</button>-->
        <button @click="dele">delete</button>
        <button @click="init">init</button>
        <button @click="clear">clear</button>
        <ul>
            <li v-for="item in items" :key="item.name">
                <template v-if="!item.selected">
                    <span v-bind:class="{ notSelectedList: isList }" @click="item.selected ? item.selected=false:item.selected=true">
                        {{item.name}}
                    </span>
                </template>
                <template v-else>
                    <span v-bind:class="{ selectedList: isList }" @click="item.selected ? item.selected=false:item.selected=true">
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
        init : function(){
            let getjson = localStorage.getItem('key');
            let obj = JSON.parse(getjson);
            this.items = obj;
        },
        change_strage: function(){
            let setjson = JSON.stringify(this.items);
            //onsole.log(setjson);
            localStorage.setItem('key', setjson);
            return ;
        },
        add : function(){
            if(this.input1!=""){
                console.log(this.input1);
                this.items.push({name:this.input1,selected:false})
                this.input1 = "";
                this.change_strage();
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
            this.change_strage();
            return ;
        },
        clear : function(){
            console.log("clear");
            localStorage.removeItem('key');
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
    font-family: "ＭＳ ゴシック",sans-serif;
}
.selectedList{
    /*text-decoration : line-through;*/
    color : rgb(185, 185, 185);
}
.notSelectedList2{
    font-weight: 700;
}
button{
    font-size: 24px;
    width: 100px;
    height: 50px;
}
input[type=text]{
    height: 50px;
    width: 200px;
    font-size: 24px;
    border:solid 1px #EEA34A;
}
</style>