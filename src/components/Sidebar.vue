<script setup>

import Logo from "@/components/icons/Logo.vue";
import Calendar from "@/components/icons/Calendar.vue";

const links = []

</script>

<template>
	<div class="sidebar">
		<div class="sidebar-logo">
			<Logo/>
			<div>Сим Центр</div>
		</div>
		<div class="sidebar-list">
			<div class="sidebar-list__item">
				<Calendar/>
				<div>Расписание</div>
			</div>
			<div class="sidebar-list__item" :class="{active: true}">
				<Calendar/>
				<div>Учебные сессии</div>
			</div>
			<div class="sidebar-list__item">
				<Calendar/>
				<div>Список комнат</div>
			</div>
			<div class="sidebar-list__item">
				<Calendar/>
				<div>Пользователи</div>
			</div>
			<div class="sidebar-list__item">
				<Calendar/>
				<div>Учебные группы</div>
			</div>
			<div class="sidebar-list__item">
				<Calendar/>
				<div>Список устройств</div>
			</div>
			<div class="sidebar-list__item">
				<Calendar/>
				<div>Настройки системы</div>
			</div>
			<div class="sidebar-list__item">
				<Calendar/>
				<div>Архив</div>
			</div>
		</div>
		<div class="sidebar-version">
			Версия 1.02
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
	width: 274px;
	padding: 1.25rem 0.75rem;
	height: 100vh;
	background: white;
	
	&-logo {
		display: flex;
		justify-content: center;
		gap: 1rem;
		align-items: center;
		font-size: 1.5rem;
		font-weight: 800;
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
			gap: 0.75rem;
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
		}
	}
}
</style>