<script setup>

import ContentList from "@/components/ContentList.vue";
import SortBtnFirst from "@/components/icons/SortBtnFirst.vue";
import SortBtnSecond from "@/components/icons/SortBtnSecond.vue";
</script>

<template>
	<div class="content">
		<div class="content-wrapper">
			<div class="content-header">
				<div class="content-header__title">
					Учебные сессий
				</div>
				<input class="content-header__search" type="text">
				<SortBtnFirst/>
				<SortBtnSecond/>
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