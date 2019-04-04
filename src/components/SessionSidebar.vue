<template>
  <small>
    <hr style="background: #374051;">
      <p class="text-white cursor-move font_ text-justify ml-5 h6">
        <span class="text-secondary" :class="iconTitle"></span>
       {{title}}</p>
    <hr style="background: #374051;">

    <input class="form-control form-control-sm sm" type="text" v-if="showInput" @keyup.13="increment" v-model="item_text" />
    <draggable v-model="items" @group="title" @start="drag=true" @end="drag=false">
      <div v-for="element in items" :key="element" class="item_session">
        <a class="font_ text-justify mt-1 ml-5"><span :class="iconItem" class="text-secondary"></span>
         <span class="text-white"> {{element}}</span>
        </a>
      </div>
    </draggable>
    <p v-if="!items.length" class="text-secondary font_ text-justify ml-5">Empty list</p>
    <button class="btn btn-outline-primary btn-sm mt-1 font_ text-justify ml-5" @click="showForm" :disabled="showInput">
      <span class="fa fa-plus"></span> ADD {{title}}
    </button>
  </small>
</template>

<script>
import draggable from 'vuedraggable'

export default {
  name: 'SessionSidebar',
  components: {
      draggable
    },
  data() {
    return {
      items:[],
      showInput: false,
      item_text:''
      }
  },
  props: {
    title: String,
    iconTitle: String,
    iconItem: String
  },
  methods: {
    showForm (){
        this.showInput = true
    },
    increment (){
      this.showInput = false
      this.items.push(this.item_text)
      this.item_text = ''
    }
  }
}
</script>
