<template>
  <Wrapper>
    <Header>No results</Header>
    <Content>
      Try searching for smething else or
      <br />try one of these:
    </Content>
    <Alternatives>Berlin</Alternatives>
  </Wrapper>
</template>

<script>
import styled from "vue-styled-components";
import { theme } from "../constants";

const Wrapper = styled.div`
  text-align: center;
`;
const Header = styled.h2``;
const Content = styled.div`
  margin-bottom: ${theme.s2};
`;
const Alternatives = styled.div`
  text-decoration: underline;
  cursor: pointer;
  color: ${theme.primary};
`;

export default {
  name: "NothingFound",
  components: {
    Wrapper,
    Header,
    Content,
    Alternatives
  }
};
</script>
