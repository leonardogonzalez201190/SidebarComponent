<template>
  <div>
    <h4>{{iconTitle}} - {{title}}</h4>
	<input type="text" v-if="showInput" @keyup.13="increment" v-model="item_text" />
	<draggable v-model="items" @group="title" @start="drag=true" @end="drag=false">
		<div v-for="element in items" :key="element">
			{{iconItem}} - {{element}}
		</div>
	</draggable>
	<p v-if="!items.length">Empty list</p>
	<button @click="showForm" :disabled="showInput"> +ADD {{title}}</button>
  </div>
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