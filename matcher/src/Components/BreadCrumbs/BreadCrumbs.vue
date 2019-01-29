<template>
  <div class="Bread-Crumbs" v-if="currentPage>0">
    <Breadcrumb
          v-for="(pageNumber,index) in pageNumbers"
          :key="index"
          :pageNumber="pageNumber"
          :breadcrumbIcons="breadcrumbIcons[index]"
          :isActive="pageNumber==currentPage"
          @click.native="goToPageNumber(pageNumber)"
          v-show="currentPage<4"
        />
  </div>
</template>
<script>
import Breadcrumb from "../BreadCrumb/BreadCrumb";
export default {
  props: ["currentPage", "pageNumbers", "breadcrumbIcons", "goToPageNumber"],
  components: {
    Breadcrumb: Breadcrumb
  }
};
</script>
<style>
.Bread-Crumbs {
    margin-top: 90px;
}
</style>
