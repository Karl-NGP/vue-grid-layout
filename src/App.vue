<template>
    <div id="app">
        <div>
            <div class="layoutJSON">
                Displayed as <code>[x, y, w, h]</code>:
                <div class="columns">
                    <div class="layoutItem" v-for="item in layout" :key="item.i">
                        <b>{{item.i}}</b>: [{{item.x}}, {{item.y}}, {{item.w}}, {{item.h}}]
                    </div>
                </div>
            </div>
        </div>
        <div id="content">
            <grid-layout
                    :layout="layout"
                    :col-num="4"
                    :row-height="200"
                    :is-draggable="draggable"
                    :is-resizable="false"
                    :vertical-compact="true"
                    :use-css-transforms="true"
                    :responsive="false"
            >
                <grid-item v-for="item in layout" :key="item.i"
                           :x="item.x"
                           :y="item.y"
                           :w="item.w"
                           :h="item.h"
                           :i="item.i"
                >
                    <test-element :text="item.i"></test-element>
                </grid-item>
            </grid-layout>
            <hr/>
        </div>
    </div>
</template>

<script>
    import GridItem from './components/GridItem.vue';
    import GridLayout from './components/GridLayout.vue';
    // import ResponsiveGridLayout from './components/ResponsiveGridLayout.vue';
    import TestElement from './components/TestElement.vue';
    //import {getDocumentDir, setDocumentDir} from "./helpers/DOM";
    //var eventBus = require('./eventBus');

    let testLayout = [
        {"x":0,"y":0,"w":1,"h":1,"i":"0"},
        {"x":2,"y":0,"w":1,"h":1,"i":"1"},
        {"x":2,"y":2,"w":3,"h":1,"i":"2"},
        {"x":1,"y":3,"w":8,"h":1,"i":"3"},
    ];

    export default {
        name: 'app',
        components: {
            // ResponsiveGridLayout,
            GridLayout,
            GridItem,
            TestElement,
        },
        data () {
            return {
                layout: JSON.parse(JSON.stringify(testLayout)),
                draggable: true,
                resizable: true,
                mirrored: false,
                responsive: true,
                rowHeight: 300,
                colNum: 4,
                index: 0
            }
        },
        mounted: function () {
            this.index = this.layout.length;
        },
        methods: {
            
        },
    }
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /*text-align: center;*/
  color: #2c3e50;
  /*margin-top: 60px;*/
}
</style>
