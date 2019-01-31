<template>
    <span class="text">
        <span>INNER CONTENT HERE</span>
        <img src="https://via.placeholder.com/150"/>
    </span>
</template>
<style>
</style>
<script>
    export default {
        name: "TestElement",
        props: {
            text : {
                type: String,
                default: "x",
            },
        },
        data: function() {
            return {
            }
        },
        mounted: function() {
            console.log("### " + this.text + " ready!");
        },
    }
</script>