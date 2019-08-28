<template>
  <div>
    <SearchWrapper>
      <Search v-model="searchValue" />
      <TotalTours>{{filteredTours.length}} activities found</TotalTours>
    </SearchWrapper>
    <Tours>
      <Wrapper v-for="(tour,index) in filteredTours" :key="index">
        <TourCard :tour="tour" />
      </Wrapper>
      <Wrapper v-if="filteredTours.length === 0" appear>
        <NothingFound />
      </Wrapper>
    </Tours>
  </div>
</template>

<script>
import styled from "vue-styled-components";
import product from "../api/product.json";
import TourCard from "../components/TourCard.vue";
import Search from "../components/Search.vue";
import NothingFound from "../components/NothingFound";

import { theme } from "../constants";

const Wrapper = styled.div`
  padding: ${theme.s2};
`;
const SearchWrapper = styled.div`
  padding: ${theme.s2};
  padding-bottom: 0;
  background: ${theme.secondary};
`;
const TotalTours = styled.div`
  display: grid;
  padding: ${theme.s1} 0;
  text-align: right;
  font-size: ${theme.f1};
  color: ${theme.white};
`;
const Tours = styled.div`
  display: grid;
  grid-template-columns: repeat(
    auto-fit,
    minmax(${theme.minResponsiveBreak}, 1fr)
  );
`;

export default {
  name: "TourSearch",
  components: {
    TourCard,
    Search,
    NothingFound,

    Tours,
    TotalTours,
    SearchWrapper,
    Wrapper
  },
  data: function() {
    return {
      tours: [],
      searchValue: ""
    };
  },
  created: function() {
    this.tours = product.tours;
  },
  computed: {
    filteredTours() {
      const search = this.searchValue.toLowerCase().trim();
      if (!search) return this.tours;

      return this.tours.filter(t => t.title.toLowerCase().indexOf(search) > -1);
    }
  }
};
</script>
