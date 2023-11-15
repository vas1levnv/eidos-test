<script>
import axios from "axios";
import PaginationArrow from "@/components/icons/PaginationArrow.vue";
import SortedIcon from "@/components/icons/SortedIcon.vue";

export default {
	components: {SortedIcon, PaginationArrow},
	props: {
		searchQuery: String
	},
	data() {
		return {
			items: [],
			isLoading: false,
			sortTitle: '',
			page: 1,
			limit: 11,
			totalPages: 0,
		}
	},
	
	mounted() {
		this.fetchDataFromApi()
	},
	
	methods: {
		
		async fetchDataFromApi() {
			try {
				this.isLoading = true
				const response = await axios.get('https://jsonplaceholder.typicode.com/posts', {
					params: {
						_page: this.page,
						_limit: this.limit,
					}
				})
				this.totalPages = Math.ceil(response.headers['x-total-count'] / this.limit)
				this.items = response.data
			} catch(e) {
				console.log(e)
			} finally {
				this.isLoading = false
			}
		},
		changePage(pageNumber) {
			this.page = pageNumber
			this.fetchDataFromApi()
		},
		changeDecrementPage() {
			if(this.page !== 1) {
				this.page -= 1
				this.fetchDataFromApi()
			}
		},
		
		changeIncrementPage() {
			if(this.page !== this.totalPages) {
				this.page += 1
				this.fetchDataFromApi()
			}
		},
		
		changeSortTitle(e) {
			this.sortTitle = e.target.innerText
		}
	},
	computed: {
		sortedList() {
			return [...this.items].sort((post1, post2) => post1[this.sortTitle]?.localeCompare(post2[this.sortTitle]))
		},
		sortedAndSearchedList() {
			return this.sortedList.filter(post => post.title.toLowerCase().includes(this.searchQuery.toLowerCase()))
		},
	},
}

</script>

<template>
	<div class="content-list">
		<div v-if="isLoading">Идет загрузка данных...</div>
		<table v-if="items.length > 0" class="content-list__table">
			<thead>
			<tr>
				<th @click="changeSortTitle">
					<div class="content-list__table-head">
						<div>title</div>
						<SortedIcon v-show="sortTitle==='title'"/>
					</div>
				</th>
				<th @click="changeSortTitle">
					<div class="content-list__table-head">
						<div>body</div>
						<SortedIcon v-show="sortTitle==='body'"/>
					</div>
				</th>
			</tr>
			</thead>
			<tbody>
			<tr v-for="item in sortedAndSearchedList" :key="item.id">
				<td>{{ item.title }}</td>
				<td>{{ item.body }}</td>
			</tr>
			<tr>
				<td colspan="2">
					<div class="pagination">
						<span @click="changeDecrementPage" class="pagination-item pagination-prev"><PaginationArrow/></span>
						<span v-for="pageNumber in totalPages"
							  :key="pageNumber"
							  class="pagination-item"
							  :class="{selected: page === pageNumber}"
							  v-show="pageNumber === 1 ||
            pageNumber === totalPages ||
             pageNumber === page ||
              pageNumber === page + 1||
               pageNumber === page - 1 ||
               pageNumber === page + 2 ||
               pageNumber === page - 2
"
							  @click="changePage(pageNumber)">
						{{ pageNumber }}
					</span>
						<span @click="changeIncrementPage" class="pagination-item pagination-next"><PaginationArrow/></span>
					</div>
				</td>
			</tr>
			</tbody>
		</table>
	</div>
</template>

<style scoped lang="scss">

.content-list {
	margin-top: 2rem;
	
	&__table {
		border-radius: 1rem;
		overflow: hidden;
		border-collapse: collapse;
		
		thead {
			position: sticky;
			top: 0;
		}
		
		th, td {
			padding: 1.375rem 1rem;
		}
		
		th {
			text-align: start;
			background: #F5F7F9;
			font-size: 17px;
			font-weight: 800;
			cursor: pointer;
		}
		
		tr {
			&:nth-child(2n) {
				background: #F5F7F9;
			}
		}
		&-head{
			display: flex;
			gap: 1rem;
			align-items: center;
		}
	}
}

.pagination {
	display: flex;
	align-items: center;
	gap: 0.5rem;
	
	&-item {
		display: flex;
		justify-content: center;
		align-items: center;
		background: white;
		border-radius: 0.5rem;
		width: 30px;
		font-weight: 500;
		height: 30px;
		border: 1px solid white;
		cursor: pointer;
		transition: 0.4s;
		line-height: 100%;
		
		&:hover {
			background: #E0E0E0;
		}
		
		&.selected {
			color: #3761F3;
			border: 1px solid #3761F3;
		}
	}
	
	&-next {
		transform: rotate(180deg);
	}
}
</style>