<template>
  <Wrapper>
    <Upper>
      <SpecialOffer v-if="tour.isSpecialOffer" appear>SALE</SpecialOffer>
      <BookMarkIconWrapper>
        <font-awesome-icon :icon="['far','bookmark']"></font-awesome-icon>
      </BookMarkIconWrapper>
      <EmptySpace />
      <Title v-html="tour.title" />
    </Upper>
    <Lower>
      <Rating>
        <StarRating
          :show-rating="false"
          :star-size="16"
          :read-only="true"
          :rating="parseFloat(tour.rating)"
          :round-start-rating="false"
        />
        <StarNumber>{{tour.rating}} / 5</StarNumber>
      </Rating>
      <PriceWrapper>
        from
        <Price :isSpecialOffer="tour.isSpecialOffer">{{tour.price}} {{tour.currency}}</Price>
      </PriceWrapper>
    </Lower>
  </Wrapper>
</template>

<script>
import styled from "vue-styled-components";
import { theme } from "../constants";
import StarRating from "vue-star-rating";

const Wrapper = styled.section`
  box-shadow: 0 2px 2px 0 rgba(0, 0, 0, 0.07), 0 3px 1px -2px rgba(0, 0, 0, 0.1),
    0 1px 5px 0 rgba(0, 0, 0, 0.06);
  border-radius: 2px;
  overflow: hidden;
`;
const Upper = styled.div`
  display: grid;
  grid-template-rows: 1fr auto;
  position: relative;
  padding: ${theme.s1};
  height: ${theme.h1};
  /* For black gradient to make color white more visible */
  /* See https://css-tricks.com/design-considerations-text-images/  */
  background: linear-gradient(to bottom, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.6)),
    url("./BerlinTVTower.jpg");
  background-repeat: no-repeat;
  background-position: center center;
  background-size: cover;
`;
const SpecialOffer = styled.div`
  position: absolute;
  right: -30px;
  width: 90px;
  padding-left: 20px;
  transform: rotateY(0deg) rotate(45deg);
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);

  font-size: ${theme.f2};
  text-align: center;
  color: ${theme.white};
  background: ${theme.primary};
`;
const Title = styled.div`
  padding-right: ${theme.s3};
  font-size: ${theme.f4};
  color: ${theme.white};
`;
const BookMarkIconWrapper = styled.div`
  position: absolute;
  bottom: ${theme.s1};
  right: ${theme.s2};
  color: ${theme.white};
`;
const Lower = styled.div`
  display: grid;
  grid-template-columns: 1fr auto;
  padding: ${theme.s1} ${theme.s2};
`;
const Rating = styled.div`
  display: flex;
`;
const StarNumber = styled.div`
  margin-left: ${theme.s1};
  align-self: center;
  font-size: ${theme.f2};
  font-weight: 500;
  color: ${theme.fontSecondary};
`;
const EmptySpace = styled.div``;
const PriceWrapper = styled.div`
  display: flex;
  align-self: center;
  font-size: ${theme.f1};
  color: ${theme.fontSecondary};
`;
const Price = styled("div", { isSpecialOffer: Boolean })`
  margin-left: ${theme.s1};
  line-height: ${theme.f2};
  font-size: ${theme.f2};
  font-weight: 500;
  color: ${prop => (prop.isSpecialOffer ? theme.primary : theme.secondary)};
`;

export default {
  name: "TourCard",
  components: {
    StarRating,
    StarNumber,
    Wrapper,
    Upper,
    BookMarkIconWrapper,
    Lower,
    SpecialOffer,
    Title,
    Rating,
    Price,
    EmptySpace,
    PriceWrapper
  },
  props: {
    tour: Object
  }
};
</script>
