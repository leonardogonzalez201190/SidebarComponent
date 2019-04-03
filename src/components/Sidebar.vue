<template>
  <div>
	<SessionSidebar title="My Projects" iconTitle="list" iconItem="estrellas"/>
	<SessionSidebar title="Team" iconTitle="carpeta" iconItem="open"/>
  </div>
</template>

<script>
import SessionSidebar from './SessionSidebar.vue'

export default {
  name: 'Sidebar',
  components: {
    SessionSidebar
  }
}
</script>
