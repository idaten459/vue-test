<template>
    <div>
        <div>{{countMassage}}</div>
        <button @click="count++">click!</button>
        <button @click="count = 0">reset!</button>
    </div>
</template>

<script>
export default {
    name: "counter",
    data(){
        return {
            count: 0
        };
    },
    computed:{
        countMassage(){
            return "回数: " + this.count;
        }
    }
};
</script>

<style></style>