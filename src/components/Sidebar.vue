<template>
  <div id="wrapper">
    <div id="sidebar-wrapper">
      <div class="sidebar-nav">
        <li class="sidebar-brand brandup text-center">
          <a href="#" class="col-md-6">
            <h2><strong>TEK</strong>TASK</h2>
          </a>
        </li>
        <draggable v-model="items" group="itemsSidebar" @start="drag=true" @end="drag=false">
          <div v-for="element in items" :key="element.title" class="div_session ">
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
      items:[{title:"My Projects", iconTitle:"fa fa-credit-card", iconItem:"fa fa-star"},
             {title:"Team", iconTitle:"fa fa-users", iconItem:"fa fa-user-friends"}]
            }
         },
  }
</script>
