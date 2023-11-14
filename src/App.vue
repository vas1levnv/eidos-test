<script setup>
import Sidebar from "@/components/Sidebar.vue";
import Content from "@/components/Content.vue";
</script>

<template>
	<div class="app-wrapper">
		<Sidebar/>
		<Content/>
	</div>
</template>

<style lang="scss" scoped>

.app {
	&-wrapper {
		display: grid;
		grid-template-columns: auto 1fr;
		height: 100%;
	}
}

</style>
