<template>
  <small>
	  <ul>
    <h5 class="text-white cursor-move font_"><span :class="iconTitle"></span> {{title}}</h5>

			<input class="form-control form-control-sm" type="text" v-if="showInput" @keyup.13="increment" v-model="item_text" />
			<draggable v-model="items" @group="title" @start="drag=true" @end="drag=false">
				<div v-for="element in items" :key="element" class="font_">
					<a class="text-white m-2 font_"><span :class="iconItem"></span> {{element}}</a>
				</div>
			</draggable>
	<p v-if="!items.length" class="text-secondary ">Empty list</p>
	 <button class="btn btn-outline-primary btn-sm mt-2" @click="showForm" :disabled="showInput">
	 <span class="fa fa-plus"></span> ADD {{title}}
	 </button>
	</ul>
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
