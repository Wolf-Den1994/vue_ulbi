<template>
  <div class="page__wrapper" v-if="totalPages">
    <div
      v-for="pageNumber in totalPages"
      :key="pageNumber"
      class="page"
      :class="{
          'current-page': page === pageNumber
        }"
      :style="{
          color: page === pageNumber ? 'teal' : ''
        }"
      @click="changePage(pageNumber)"
    >
      {{ pageNumber }}
    </div>
  </div>
</template>

<script>
export default {
  props: {
    totalPages: {
      type: Number,
      required: true,
      default: 0,
    },
    page: {
      type: Number,
      required: true,
      default: 1,
    }
  },
  setup(_, { emit }) {
    const changePage = (pageNumber) => {
      emit('changePage', pageNumber);
    }

    return {
      changePage,
    }
  }
}
</script>

<style scoped>
.page__wrapper {
  display: flex;
  margin-top: 15px;
}

.page {
  border: 1px solid #000;
  padding: 10px;
  cursor: pointer;
}

.page:hover:not(.current-page) {
  border: 1px solid teal;
}

.current-page {
  border: 2px solid teal;
}
</style>