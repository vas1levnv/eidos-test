<script setup>

import ContentList from "@/components/ContentList.vue";
</script>

<template>
	<div class="content">
		<div class="content-wrapper">
			<div class="content-header">
			
			</div>
			<ContentList/>
		</div>
	</div>
</template>

<style lang="scss" scoped>
.content {
	height: 100%;
	padding: 0.5rem;
	
	&-wrapper {
		height: 100%;
		background: white;
		border-radius: 0.75rem;
		padding: 1.5rem;
	}
}
</style>