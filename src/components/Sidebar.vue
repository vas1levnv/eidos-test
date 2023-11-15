<script>

import Logo from "@/components/icons/Logo.vue";
import Calendar from "@/components/icons/Calendar.vue";
import {defineComponent} from "vue";
import PaginationArrow from "@/components/icons/PaginationArrow.vue";

export default defineComponent({
	components: {PaginationArrow, Logo, Calendar},
	data() {
		return {
			isOpen: true,
		}
	},
})

</script>

<template>
	<div class="sidebar" :class="{open: isOpen}">
		<div class="sidebar-logo">
			<Logo/>
			<div class="open-text">Сим Центр</div>
		</div>
		<div @click="isOpen = !isOpen" class="sidebar-close">
			<PaginationArrow/>
		</div>
		<div class="sidebar-list">
			<div class="sidebar-list__item">
				<Calendar/>
				<div class="open-text">Расписание</div>
			</div>
			<div class="sidebar-list__item" :class="{active: true}">
				<Calendar/>
				<div class="open-text">Учебные сессии</div>
			</div>
			<div class="sidebar-list__item">
				<Calendar/>
				<div class="open-text">Список комнат</div>
			</div>
			<div class="sidebar-list__item">
				<Calendar/>
				<div class="open-text">Пользователи</div>
			</div>
			<div class="sidebar-list__item">
				<Calendar/>
				<div class="open-text">Учебные группы</div>
			</div>
			<div class="sidebar-list__item">
				<Calendar/>
				<div class="open-text">Список устройств</div>
			</div>
			<div class="sidebar-list__item">
				<Calendar/>
				<div class="open-text">Настройки системы</div>
			</div>
			<div class="sidebar-list__item">
				<Calendar/>
				<div class="open-text">Архив</div>
			</div>
		</div>
		<div class="sidebar-version">
			<span class="open-text">Версия</span> 1.02
		</div>
	</div>
</template>

<style lang="scss" scoped>
.sidebar {
	position: sticky;
	top: 0;
	display: flex;
	flex-direction: column;
	justify-content: space-between;
	padding: 1.25rem 0.75rem;
	height: 100vh;
	background: white;
	
	&-logo {
		display: flex;
		justify-content: center;
		align-items: center;
		font-size: 1.5rem;
		font-weight: 800;
		
		.open-text {
			padding-left: 0;
		}
	}
	
	&-close {
		position: absolute;
		top: 2rem;
		right: -0.75rem;
		width: 1.5rem;
		height: 1.5rem;
		border-radius: 50%;
		background: #2F3144;
		display: flex;
		justify-content: center;
		align-items: center;
		cursor: pointer;
	}
	
	&-list {
		display: flex;
		flex-direction: column;
		gap: 0.25rem;
		margin-top: 2.75rem;
		flex: 1 1 0;
		
		&__item {
			display: flex;
			align-items: center;
			padding: 0.75rem;
			border-radius: 1rem;
			transition: 0.4s;
			cursor: pointer;
			
			&:hover {
				background: #F4F4F4;
			}
			
			&.active {
				background: #3761F3;
				color: white;
			}
			
			.open-text {
				padding-left: 0;
			}
		}
	}
	
	&-version {
	}
	
	.open-text {
		transition: 0.4s;
		font-size: 0;
	}
	
	&.open {
		.open-text {
			font-size: inherit;
		}
		
		.sidebar {
			&-logo {
				.open-text {
					padding-left: 1rem;
				}
			}
			
			
			&-list {
				.open-text {
					padding-left: 0.75rem;
				}
			}
		}
	}
}
</style>