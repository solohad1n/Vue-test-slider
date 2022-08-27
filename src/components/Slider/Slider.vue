<template>
  <div class="carousel__counter">
    <span>{{ +currentSlide + 1 }}/8</span>
  </div>
  <Carousel
    :items-to-show="1"
    :wrap-around="true"
    ref="myCarousel"
    v-model="currentSlide"
  >
    <Slide v-for="item in items" :key="item.id">
      <div class="carousel__item">
        <img class="carousel__img" :src="item.img" alt="" />
        <p class="carousel__text">
          {{ item.text }}
        </p>
      </div>
    </Slide>

    <template #addons>
      <div @click="myCarousel.next()" class="slider__btn">
        <span>
          <svg
            width="28"
            height="10"
            viewBox="0 0 28 5"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path d="M0.370911 2.8553L26.7406 2.8553" stroke="#333333" />
            <path
              d="M25.0246 4.54921L26.7453 2.8285L25.0246 1.13766"
              stroke="#333333"
            /></svg
        ></span>
      </div>
    </template>
  </Carousel>
</template>

<script>
import { ref } from "vue";
import { Carousel, Navigation, Pagination, Slide } from "vue3-carousel";

import "vue3-carousel/dist/carousel.css";

export default {
  name: "Basic",
  components: {
    Carousel,
    Slide,
    Pagination,
    Navigation,
  },
  setup() {
    const items = ref([
      {
        id: 1,
        name: "img1",
        img: "1.png",
        text: "Для примера мы показали вам его лицо.  В первой серии он прячется в подвале за мониторами, и пусть борода не собьёт вас с толку. Найдите героя и нажмите  на паузу — ему не терпится отдать вам промокод.",
      },
      {
        id: 2,
        name: "img2",
        img: "2.png",
        text: "222222222222222Lorem ipsum dolor sit amet consectetur adipisicing elit. Et laudantium molestiae veritatis rerum similique laboriosam sed sint temporibus. Enim, optio explicabo molestiae error vitae accusantium nostrum adipisci neque eum tempora!",
      },
      {
        id: 3,
        name: "img3",
        img: "3.png",
        text: "33333333333Lorem ipsum dolor sit amet consectetur adipisicing elit. Et laudantium molestiae veritatis rerum similique laboriosam sed sint temporibus. Enim, optio explicabo molestiae error vitae accusantium nostrum adipisci neque eum tempora!",
      },
      {
        id: 4,
        name: "img4",
        img: "4.png",
        text: "44444444444Lorem ipsum dolor sit amet consectetur adipisicing elit. Et laudantium molestiae veritatis rerum similique laboriosam sed sint temporibus. Enim, optio explicabo molestiae error vitae accusantium nostrum adipisci neque eum tempora!",
      },
      {
        id: 5,
        name: "img5",
        img: "2.png",
        text: "55555555555Lorem ipsum dolor sit amet consectetur adipisicing elit. Et laudantium molestiae veritatis rerum similique laboriosam sed sint temporibus. Enim, optio explicabo molestiae error vitae accusantium nostrum adipisci neque eum tempora!",
      },
      {
        id: 6,
        name: "img3",
        img: "3.png",
        text: "666666666666Lorem ipsum dolor sit amet consectetur adipisicing elit. Et laudantium molestiae veritatis rerum similique laboriosam sed sint temporibus. Enim, optio explicabo molestiae error vitae accusantium nostrum adipisci neque eum tempora!",
      },
      {
        id: 7,
        name: "img4",
        img: "1.png",
        text: "77777777777777Lorem ipsum dolor sit amet consectetur adipisicing elit. Et laudantium molestiae veritatis rerum similique laboriosam sed sint temporibus. Enim, optio explicabo molestiae error vitae accusantium nostrum adipisci neque eum tempora!",
      },
      {
        id: 8,
        name: "img5",
        img: "4.png",
        text: "88888888888888Lorem ipsum dolor sit amet consectetur adipisicing elit. Et laudantium molestiae veritatis rerum similique laboriosam sed sint temporibus. Enim, optio explicabo molestiae error vitae accusantium nostrum adipisci neque eum tempora!",
      },
    ]);
    const myCarousel = ref(null);
    const currentSlide = ref("0");

    return { items, myCarousel, currentSlide };
  },
};
</script>


<style>
.carousel__img {
  width: 450px;
  max-height: 300px;
  object-fit: contain;
}
.carousel__item {
  min-height: 200px;
  width: 900px;
  color: var(--vc-clr-white);
  font-size: 20px;
  border-radius: 8px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  color: black;
}

.carousel__slide {
  padding: 10px;
}

.carousel__prev,
.carousel__next {
  box-sizing: content-box;
  border: 5px solid white;
}
.slider__btn {
  border: 1px solid #333333;
  width: 40px;
  height: 40px;
  border-radius: 50%;
  cursor: pointer;
  position: absolute;
  top: 30%;
  right: 0%;
  display: flex;
  align-items: center;
  justify-content: center;
}

.carousel__counter {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  margin: 0 auto;
  background: white;
  display: flex;
  align-items: center;
  justify-content: center;
}
.carousel__text {
  margin: 0 0 50px 0;
  font-size: 20px;
  line-height: 32px;
  letter-spacing: 0.4px;
  font-weight: 100;
}
</style>