<template>
  <Wrapper>
    <Input type="text" placeholder="What is your next activity?" :value="search" @input="setValue" />
    <IconWrapper>
      <font-awesome-icon icon="search"></font-awesome-icon>
    </IconWrapper>
  </Wrapper>
</template>

<script>
import styled from "vue-styled-components";
import { theme } from "../constants";

const Wrapper = styled.div`
  display: grid;
  grid-template-columns: 1fr auto;
  border: 2px solid ${theme.gray};
  border-radius: 2px;
`;
const Input = styled.input`
  padding-left: ${theme.s2};
  font-size: ${theme.f2};
`;
const IconWrapper = styled.div`
  padding: ${theme.s2};
  background: ${theme.white};
`;

export default {
  name: "Search",
  components: {
    Input,
    Wrapper,
    IconWrapper
  },
  props: {
    search: String
  },
  methods: {
    setValue: function(event) {
      this.$emit("input", event.target.value);
    }
  }
};
</script>

