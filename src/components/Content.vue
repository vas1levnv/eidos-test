<script>
import ContentList from "@/components/ContentList.vue";
import SortBtnFirst from "@/components/icons/SortBtnFirst.vue";
import SortBtnSecond from "@/components/icons/SortBtnSecond.vue";
import {defineComponent} from "vue";

export default defineComponent({
  components: {SortBtnSecond, SortBtnFirst, ContentList},
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
        <input class="content-header__search" v-model="searchQuery" type="text">
        <SortBtnFirst/>
        <SortBtnSecond/>
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
}
</style>