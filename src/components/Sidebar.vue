<template>
  <div id="wrapper">
  <div id="sidebar-wrapper">
            <div class="sidebar-nav">
                <li class="sidebar-brand" style="margin:10px">
                    <a href="#">
                        <h2>TEK<strong>TASK</strong></h2>
                    </a>
                </li>  
	<draggable v-model="items" group="itemsSidebar" @start="drag=true" @end="drag=false">
	<div v-for="element in items" :key="element.title">
		<SessionSidebar :title="element.title" :iconTitle="element.iconTitle" :iconItem="element.iconItem" />
	</div>
	</draggable>
	</div>
	</div>
		</div>
</template>

<script>
import SessionSidebar from './SessionSidebar.vue'
import draggable from 'vuedraggable'

export default {
  name: 'Sidebar',
  components: {
    SessionSidebar,
	draggable
  },
  data() {
	return {
		items:[{title:"My Projects", iconTitle:"fa fa-pager", iconItem:"fa fa-star"},
		{title:"Team", iconTitle:"fa fa-users", iconItem:"fa fa-user-friends"}]
	}
  },
}
</script>
