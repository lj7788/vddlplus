<template>
    <div class="demo1">
  <vddl-list class="panel__body--list" :list="list2" :horizontal="false">
                  <vddl-draggable class="panel__body--item no-padding-left" v-for="(item, index) in list2" :key="item.idx"
                    :draggable="item"
                    :index="index"
                    :wrapper="list2"
                    effect-allowed="move">
                        <div>{{item.key}}</div>                      
                        <input/>
                  </vddl-draggable>
              </vddl-list>
    </div>
</template>

<script>
import Vue from 'vue'
  Vue.prototype.vddlDropEffectWorkaround = {};
  Vue.prototype.vddlDragTypeWorkaround = {};
import vddlList from '@/components/vddl/vddl-list'
import vddlDraggable from '@/components/vddl/vddl-draggable'
export default {
    components:{
        vddlList,
        vddlDraggable
    },
    data(){
        return {
            list:[{idx:0,key:'A1'},{idx:1,key:'A2'},{idx:2,key:'A3'},{idx:3,key:'A4'}]
        }
    },
    computed:{
        list2(){
            let data=this.list
            return data.sort((a,b)=>a.idx>b.idx)
        }
    }
}
</script>

<style>
    .demo1{
        margin: 10px 20px;
    }
    .demo1 .panel__body--item{
        border-radius: 8px;
        border: solid 1px #ccc;
        min-height: 100px;
        margin-top: 20px;
        box-shadow: rgba(0, 0, 0, 0.12) 0px 2px 6px, rgba(0, 0, 0, 0.24) 0px 1px 2px;
    }
    .demo1 .vddl-placeholder {
        width: 100%;
        background-color: rgba(0, 0, 0, 0.12);
        border-radius: 8px;
        border: solid 1px #ccc;
        min-height: 100px;
        margin-top: 20px;
        box-shadow: rgba(0, 0, 0, 0.12) 0px 2px 6px, rgba(0, 0, 0, 0.24) 0px 1px 2px;
    }
    .demo1 .vddl-dragging.vddl-dragging-source {
        display: none;
    }
</style>
