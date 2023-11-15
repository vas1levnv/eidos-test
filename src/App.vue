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

<style lang="scss">

.app {
	&-wrapper {
		display: grid;
		grid-template-columns: auto 1fr;
		height: 100%;
	}
}

button{
	background: #3761F3;
	border-radius: 0.75rem;
	color: white;
	padding: 0.75rem 1.5rem;
	font-weight: 800;
	border: none;
	outline: none;
}

</style>
