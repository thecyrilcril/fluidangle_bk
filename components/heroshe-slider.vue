<template>
  <div class="main-image">
    <div class="image">
      <hooper ref="carousel" :settings="hooperSettings">
        <slide v-for="(slide, index) in slides" :key="index" :index="index">
          <img :src="slide.img" alt="">
        </slide>
      </hooper>
    </div>
    <div class="controls flex list dir-row">
      <CheckboxBlankCircle fill-color="#d5d5d5" title="previous" class="prev" @click.prevent="slidePrev" />
      <CheckboxBlankCircle fill-color="#d5d5d5" class="middle-control" />
      <CheckboxBlankCircle fill-color="#d5d5d5" title="next" class="next" @click.prevent="slideNext" />
    </div>
  </div>
</template>

<script>
import { Hooper, Slide } from 'hooper'
import 'hooper/dist/hooper.css'

export default {
  name: 'HerosheSlider',
  components: {
    CheckboxBlankCircle: () => ({ component: import('vue-material-design-icons/CheckboxBlankCircle.vue') }),
    Hooper,
    Slide
  },
  data: () => ({
    slides: [],
    hooperSettings: {
      centerMode: true,
      wheelControl: false,
      trimWhiteSpace: true
    }
  }),
  mounted() {
    this.slides = [
      {
        id: 0,
        img: this.getImageUrl('https://res.cloudinary.com/nazarick/image/upload/v1561570127/fluidangle/img/xd/Component_5_1_cropped.png')
      },
      {
        id: 1,
        img: this.getImageUrl('https://res.cloudinary.com/nazarick/image/upload/v1561570127/fluidangle/img/Admin_Dashboard.png')
      },
      {
        id: 2,
        img: this.getImageUrl('https://res.cloudinary.com/nazarick/image/upload/v1561570127/fluidangle/img/1_Help_Desk_-_1.png')
      },
      {
        id: 3,
        img: this.getImageUrl('https://res.cloudinary.com/nazarick/image/upload/v1563305168/fluidangle/img/Customers_Admin_1.png')
      },
      {
        id: 3,
        img: this.getImageUrl('https://res.cloudinary.com/nazarick/image/upload/v1563305157/fluidangle/img/Cargo_Manifest_1.png')
      },
      {
        id: 3,
        img: this.getImageUrl('https://res.cloudinary.com/nazarick/image/upload/v1563305153/fluidangle/img/Invoices.png')
      },
      {
        id: 3,
        img: this.getImageUrl('https://res.cloudinary.com/nazarick/image/upload/v1563305151/fluidangle/img/Configuration_Settings.png')
      },
      {
        id: 3,
        img: this.getImageUrl('https://res.cloudinary.com/nazarick/image/upload/v1563305147/fluidangle/img/Order_new_user.png')
      },
      {
        id: 3,
        img: this.getImageUrl('https://res.cloudinary.com/nazarick/image/upload/v1563305144/fluidangle/img/Admin_Shipping_List.png')
      },
      {
        id: 3,
        img: this.getImageUrl('https://res.cloudinary.com/nazarick/image/upload/v1563305057/fluidangle/img/Single_Order_Details_Page_-_Buy4Me_1.png')
      },
      {
        id: 3,
        img: this.getImageUrl('https://res.cloudinary.com/nazarick/image/upload/v1563305054/fluidangle/img/Single_Order_Details_Page_-_Ship4Me.png')
      },
      {
        id: 3,
        img: this.getImageUrl('https://res.cloudinary.com/nazarick/image/upload/v1563305053/fluidangle/img/Email_Order.png')
      },
      {
        id: 3,
        img: this.getImageUrl('https://res.cloudinary.com/nazarick/image/upload/v1563305047/fluidangle/img/Order_Request_Admin.png')
      }
    ]
  },
  methods: {
    getImageUrl(url) {
      return this.$cloudinary
        .url(url)
    },
    slidePrev() {
      this.$refs.carousel.slidePrev()
    },
    slideNext() {
      this.$refs.carousel.slideNext()
    }
  }
}
</script>

<style scoped lang="scss">
  .hooper{
    height: 95vh;
  }
  .main-image{
    align-items: center;
    margin-bottom: 3rem;
    img{
      object-fit: contain;
      width:100%;
      /*box-shadow: 0 10px 30px 0 rgba(0, 0, 0, 0.16);*/
      /* border: solid 1px #707070; */
    }
    .controls{
      padding: {
        top:1rem;
        bottom: 1rem;
      };
      justify-content: center;
      font-size: 1.5rem;
      & span  :not(.middle-control){
        cursor: pointer;
      }
      & span:nth-child(2){
        font-size: 2rem;
      }
      & .prev:hover,
      & .next:hover{
        font-size: 2rem;
        svg{
          fill: $accent;
        }
      }
    }
  }
</style>
