<template>
  <div class="about">
    <div class="about-first">
      <div class="container">
        <div class="row align-items-center">
          <div class="col-md-12 col-lg-6">
            <SvgManager class="w-100" />
          </div>
          <div class="col-md-12 col-lg-6">
            <h1>
              Lorem ipsum dolor sit amet consectetur adipisicing elit. Ea eos
              dolores maxime.
            </h1>
            <p>
              Lorem ipsum dolor sit amet consectetur adipisicing elit. A omnis
              voluptatibus quo aspernatur nobis ratione culpa dignissimos. Fugit
              ipsa pariatur accusantium, eos similique error corporis quam, ea
              impedit, commodi eius.
            </p>
            <p>
              Lorem ipsum dolor, sit amet consectetur adipisicing elit.
              Obcaecati minus commodi provident quas, reprehenderit eum sit
              labore quia maiores doloremque.
            </p>
          </div>
        </div>
      </div>
    </div>
    <div class="about-second">
      <div class="container">
        <hr />
        <div class="row">
          <div class="col-md-12 col-lg-6">
            <h2>Lorem ipsum dolor sit amet consectetur adipisicing elit.</h2>
            <p>
              Lorem ipsum dolor sit amet consectetur adipisicing elit. Ad,
              sequi! Recusandae culpa maxime quod quia ad. Lorem ipsum dolor sit
              amet, consectetur adipisicing elit. Porro, dolorum! Voluptatum
              inventore sed pariatur, dicta omnis ad aliquid unde eaque
              recusandae. Doloribus nemo omnis, quibusdam cum vero nesciunt
              dolore optio.
            </p>
          </div>
          <div class="col-md-12 col-lg-6">
            <b-carousel
              id="carousel-1"
              v-model="slide"
              :interval="4000"
              controls
              indicators
              background="#ababab"
              img-width="1024"
              img-height="480"
              style="text-shadow: 1px 1px 2px #333"
              @sliding-start="onSlideStart"
              @sliding-end="onSlideEnd"
            >
              <!-- Text slides with image -->
              <b-carousel-slide
                caption="First slide"
                text="Nulla vitae elit libero, a pharetra augue mollis interdum."
                img-src="https://picsum.photos/1024/480/?image=52"
              ></b-carousel-slide>

              <!-- Slides with custom text -->
              <b-carousel-slide
                img-src="https://picsum.photos/1024/480/?image=54"
              >
                <h1>Hello world!</h1>
              </b-carousel-slide>

              <!-- Slides with image only -->
              <b-carousel-slide
                img-src="https://picsum.photos/1024/480/?image=58"
              ></b-carousel-slide>

              <!-- Slides with img slot -->
              <!-- Note the classes .d-block and .img-fluid to prevent browser default image alignment -->
              <b-carousel-slide>
                <template #img>
                  <img
                    class="d-block img-fluid w-100"
                    width="1024"
                    height="480"
                    src="https://picsum.photos/1024/480/?image=55"
                    alt="image slot"
                  />
                </template>
              </b-carousel-slide>

              <!-- Slide with blank fluid image to maintain slide aspect ratio -->
              <b-carousel-slide
                caption="Blank Image"
                img-blank
                img-alt="Blank image"
              >
                <p>
                  Lorem ipsum dolor sit amet, consectetur adipiscing elit.
                  Suspendisse eros felis, tincidunt a tincidunt eget, convallis
                  vel est. Ut pellentesque ut lacus vel interdum.
                </p>
              </b-carousel-slide>
            </b-carousel>
          </div>
        </div>
      </div>
    </div>
    <div class="about-third">
      <div class="container">
        <hr />
        <div class="row">
          <b-card-group deck>
            <b-card
              title="Title"
              img-src="https://picsum.photos/300/300/?image=41"
              img-alt="Image"
              img-top
            >
              <b-card-text>
                This is a wider card with supporting text below as a natural
                lead-in to additional content. This content is a little bit
                longer.
              </b-card-text>
              <template #footer>
                <small class="text-muted">Last updated 3 mins ago</small>
              </template>
            </b-card>

            <b-card
              title="Title"
              img-src="https://picsum.photos/300/300/?image=41"
              img-alt="Image"
              img-top
            >
              <b-card-text>
                This card has supporting text below as a natural lead-in to
                additional content.
              </b-card-text>
              <template #footer>
                <small class="text-muted">Last updated 3 mins ago</small>
              </template>
            </b-card>

            <b-card
              title="Title"
              img-src="https://picsum.photos/300/300/?image=41"
              img-alt="Image"
              img-top
            >
              <b-card-text>
                This is a wider card with supporting text below as a natural
                lead-in to additional content. This card has even longer content
                than the first to show that equal height action.
              </b-card-text>
              <template #footer>
                <small class="text-muted">Last updated 3 mins ago</small>
              </template>
            </b-card>
          </b-card-group>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import SvgManager from "@/assets/img/about/DrawKit Vector Illustration Project Manager (4).svg";
export default {
  components: {
    SvgManager,
  },
  data() {
    return {
      slide: 0,
      sliding: null,
    };
  },
  methods: {
    onSlideStart(slide) {
      this.sliding = true;
    },
    onSlideEnd(slide) {
      this.sliding = false;
    },
  },
};
</script>

<style lang="scss" >
.about {
  padding: 100px 0;
}
</style>