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
			searchQuery: '',
			isOpenPopup: false
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
				<button @click="isOpenPopup = !isOpenPopup">
					Создать
				</button>
			</div>
			<ContentList :searchQuery="searchQuery"/>
		</div>
		
		<div class="popup" v-show="isOpenPopup" @click="isOpenPopup = !isOpenPopup">
			
			<div class="popup-wrapper" @click.stop>
				<div class="popup-close" @click="isOpenPopup = !isOpenPopup">close</div>
				<h2>Окно создания сессии</h2>
			</div>
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

.popup {
	position: fixed;
	top: 0;
	left: 0;
	width: 100%;
	height: 100%;
	background: rgba(0, 0, 0, 0.5);
	display: flex;
	justify-content: center;
	align-items: center;
	
	&-wrapper {
		position: relative;
		background: white;
		border-radius: 2rem;
		padding: 3rem;
		
	}
	
	&-close {
		position: absolute;
		top: 1rem;
		right: 1rem;
		font-weight: 800;
	}
}
</style>