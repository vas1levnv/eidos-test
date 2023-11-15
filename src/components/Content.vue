<script>
import ContentList from "@/components/ContentList.vue";
import SortBtnFirst from "@/components/icons/SortBtnFirst.vue";
import SortBtnSecond from "@/components/icons/SortBtnSecond.vue";
import {defineComponent} from "vue";
import SearchIcon from "@/components/icons/SearchIcon.vue";

export default defineComponent({
	components: {SearchIcon, SortBtnSecond, SortBtnFirst, ContentList},
	data() {
		return {
			searchQuery: ''
		}
	}
})

</script>

<template>
	<div class="content">
		<div class="content-wrapper">
			<div class="content-header">
				<div class="content-header__title">
					Учебные сессий {{ searchQuery }}
				</div>
				<label class="content-header__search">
					<SearchIcon/>
					<input v-model="searchQuery" type="text">
				</label>
				<SortBtnFirst/>
				<SortBtnSecond/>
				<button>
					Создать
				</button>
			</div>
			<ContentList :searchQuery="searchQuery"/>
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
	
	&-header {
		display: flex;
		align-items: stretch;
		justify-content: space-between;
		gap: 1rem;
		
		&__title {
			flex: 1 1 0;
			align-self: center;
			font-size: 1.5rem;
			font-weight: 800;
		}
		
		&__search {
			display: flex;
			align-items: center;
			gap: 1rem;
			border: 1px solid #E0E0E0;
			padding: 0.5rem 1rem;
			border-radius: 0.75rem;
			
			input {
				border: none;
				outline: none;
			}
		}
	}
}
</style>