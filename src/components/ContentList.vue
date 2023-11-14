<script>
import axios from "axios";

export default {
  props: {
    searchQuery: String
  },
  data() {
    return {
      items: [],
      sortTitle: '',
      page: 1,
      limit: 10,
      totalPages: 0,
    }
  },

  mounted() {
    this.fetchDataFromApi()
  },

  methods: {

    async fetchDataFromApi() {
      try {
        const response = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10', {
          params: {
            _page: this.page,
            _limit: this.limit,
          }
        })
        this.totalPages = Math.ceil(response.headers['x-total-count'] / this.limit)
        this.items = response.data
      } catch (e) {
        console.log(e)
      }
    },
    changePage(pageNumber) {
      this.page = pageNumber
      this.fetchDataFromApi()
    },
    changeDecrementPage() {
      if (this.page !== 1) {
        this.page -= 1
        this.fetchDataFromApi()
      }
    },

    changeIncrementPage() {
      if (this.page !== this.totalPages) {
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
    <table>
      <thead>
      <tr>
        <th @click="changeSortTitle">title</th>
        <th @click="changeSortTitle">body</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="item in sortedAndSearchedList" :key="item.id">
        <td>{{ item.title }}</td>
        <td>{{ item.body }}</td>
      </tr>
      </tbody>
    </table>
  </div>
  <div class="pagination">
    <div @click="changeDecrementPage">prev</div>
    <div v-for="pageNumber in totalPages" :key="pageNumber" @click="changePage(pageNumber)">
      <div class="pagination-item"
           :class="{selected: page === pageNumber}"
           v-show="pageNumber === 1 ||
            pageNumber === totalPages ||
             pageNumber === page ||
              pageNumber === page + 1||
               pageNumber === page - 1 ||
               pageNumber === page + 2 ||
               pageNumber === page - 2
"
      >{{ pageNumber }}
      </div>
    </div>
    <div @click="changeIncrementPage">next</div>
  </div>
</template>

<style scoped lang="scss">

.content-list {
  margin-top: 2rem;
}

.pagination {
  display: flex;
  align-items: center;

  &-item {
    &.selected {
      background: teal;
    }
  }
}
</style>