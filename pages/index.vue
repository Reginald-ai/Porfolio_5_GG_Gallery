<template>
  <section class="gallery">
    <div class="gallery-title">
      <div class="container">
        <div class="row">
          <div class="col-sm-12 text-center mt-5">
            <h1 class="">#Web Photos</h1>
            <p>Ut proident occaecat duis aute proident est exercitation.</p>
            <p>Save and organize your favorite links</p>
          </div>
        </div>
      </div>
    </div>

    <div class="gallery-photos">
      <div class="container">
        <div class="cards">
          <div class="row mx-auto">
            <div
              v-for="(panel, index) in panels"
              :key="panel.id"
              class="col-md-6 col-sm-12 col-lg-4 col-xxl-3"
            >
              <div
                :class="{ active: isActive ? index === activeItem : '' }"
                class="card_item mx-auto mb-5"
                :style="{ background: panel.background }"
              >
                <div class="face front">
                  <div @click="toggle_modal(index)" class="img-hover">
                    <img
                      class="w-100"
                      :src="require(`@/assets/img/twirl-img/${panel.url}`)"
                      alt=""
                    />
                    <span class="img-icon">
                      <fa :icon="['fas', 'search-plus']" />
                    </span>
                  </div>

                  <div
                    :style="{ background: panel.background }"
                    class="options"
                  >
                    <div class="icon-option-user">
                      <fa :icon="['fas', 'user-circle']" />
                    </div>
                    <span>
                      <p>{{ panel.paragraph }}</p>
                    </span>
                    <button
                      v-on:click="handleToggle(index)"
                      class="icon-option"
                    >
                      <fa :icon="['fas', 'arrow-right']" />
                    </button>
                  </div>
                </div>
                <div class="face back">
                  <p>{{ panel.title }}</p>
                  <p>{{ panel.paragraph }}</p>
                  <div class="options-back">
                    <button
                      class="icon-option"
                      v-on:click="handleToggle(index)"
                    >
                      <fa :icon="['fas', 'times-circle']" />
                    </button>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="gallery-modal-container">
      <transition-group tag="div" name="modalAnimate">
        <div
          v-for="(panel, index) in panels"
          :key="panel.id"
          :class="{ toggle_modal_items: isModal ? index === activeItem2 : '' }"
          class="gallery-modal"
        >
          <div class="overlay"></div>
          <div class="img-container">
            <img :src="require(`@/assets/img/twirl-img/${panel.url}`)" alt="" />
          </div>
          <div class="icon-close-container">
            <button @click="toggle_modal(index)" class="icon-close">
              <fa :icon="['fas', 'times-circle']" />
            </button>
          </div>
        </div>
      </transition-group>
    </div>
  </section>
</template>

<script>
import { ref } from "vue";
export default {
  name: "Gallery",
  data() {
    return {
      isActive: false,
      activeItem: -1,
      activeItem2: -1,
      isModal: false,

      panels: [
        {
          id: 1,
          url: "1.jpg",
          title: "Ut proident occaecat duis aute proident est exercitation.",

          paragraph:
            "Pariatur magna occaecat reprehenderit ut consequat voluptate eiusmod veniam.",
          background: "#636c6e",
        },
        {
          id: 2,
          url: "2.jpg",
          title: "Ut proident occaecat duis aute proident est exercitation.",

          paragraph:
            "Pariatur magna occaecat reprehenderit ut consequat voluptate eiusmod veniam.",
          background: "#59323E",
        },
        {
          id: 3,
          url: "3.jpg",
          title: "Ut proident occaecat duis aute proident est exercitation.",

          paragraph:
            "Pariatur magna occaecat reprehenderit ut consequat voluptate eiusmod veniam.",
          background: "#252216",
        },
        {
          id: 4,
          url: "4.jpg",
          title: "Ut proident occaecat duis aute proident est exercitation.",

          paragraph:
            "Pariatur magna occaecat reprehenderit ut consequat voluptate eiusmod veniam.",
          background: "#4D3357",
        },
        {
          id: 5,
          url: "5.jpg",
          title: "Ut proident occaecat duis aute proident est exercitation.",

          paragraph:
            "Pariatur magna occaecat reprehenderit ut consequat voluptate eiusmod veniam.",
          background: "#254634",
        },
        {
          id: 6,
          url: "6.jpg",
          title: "Ut proident occaecat duis aute proident est exercitation.",

          paragraph:
            "Pariatur magna occaecat reprehenderit ut consequat voluptate eiusmod veniam.",
          background: "#3D5558",
        },
        {
          id: 7,
          url: "7.jpg",
          title: "Ut proident occaecat duis aute proident est exercitation.",

          paragraph:
            "Pariatur magna occaecat reprehenderit ut consequat voluptate eiusmod veniam.",
          background: "#254634",
        },
        {
          id: 8,
          url: "2.jpg",
          title: "Ut proident occaecat duis aute proident est exercitation.",

          paragraph:
            "Pariatur magna occaecat reprehenderit ut consequat voluptate eiusmod veniam.",
          background: "#59323E",
        },
      ],
    };
  },
  methods: {
    handleToggle(idx) {
      this.isActive = !this.isActive;
      this.activeItem = idx;
    },
    toggle_modal(ids) {
      this.isModal = !this.isModal;
      this.activeItem2 = ids;
    },
  },
};
// const card = document.querySelector(".card_item");

// card.addEventListener("click", function () {
//   card.classList.toggle(".isFlipped");
// });

// export default {
//   data() {
//     return {
//       isFlipped: false,
//       styleObject: {
//         color: "red",
//         fontSize: "13px",
//         transform: "rotateY(180deg)",
//       },
//     };
//   },
//   methods: {
//     isFlipped() {
//       this.isFlipped = !this.isFlipped;
//       this.isFlipped
//     },
//   },
// };
</script>

<style lang="scss">
body {
  font-family: "Poppins";
}
// .gallery-title {
// }
.gallery-photos {
  margin-top: 90px;
  .card_item {
    position: relative;
    width: 300px;
    height: 400px;
    transform-style: preserve-3d;
    transition: all 0.5s ease;
    border-radius: 20px;
    box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 8px;
    .face {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      transform-style: preserve-3d;
      display: flex;
      align-items: center;
      transition: all 0.15s ease;
      border-radius: 20px;
      backface-visibility: hidden;
      overflow: hidden;
      flex-direction: column;
    }

    .front {
      overflow: hidden;
      .img-hover {
        position: relative;
        height: 90%;
        width: 100%;
        overflow: hidden;
        img {
          width: 100% !important;
          height: 100%;
          object-fit: cover;
          position: relative;
          transition: all 1.6s ease;
        }
        &:hover img {
          transform: scale(1.2);
        }
        .img-icon {
          opacity: 0;
          transform: scale(4) translate(-15%, -15%);
          position: absolute;
          color: #fff;
          text-shadow: 2px 1px #3a3535;
          top: 45%;
          left: 50%;
          transition: all 0.5s ease;
        }
        &:hover .img-icon {
          opacity: 1;
          transform: scale(5);
        }
        &::after {
          border-radius: 10px;
          opacity: 0;
          // background: linear-gradient(36deg, #66646487 0%, #143378 60%, #00398b 100%);
          background: rgba(10, 10, 10, 0.65);
          // opacity: 0.9;
          padding-top: 150px;
          position: absolute;
          display: block;
          width: 100%;
          height: 100%;
          top: 0;
          left: 0;
        }
        &:hover::after {
          opacity: 0.5;
          content: "";
          cursor: pointer;
        }
      }
      .img-w-100 {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        z-index: 9999;
        background: rgba(10, 10, 10, 0.65);
        display: flex;
        justify-content: center;
        align-items: center;
        pointer-events: none;
        transition: all 0.3s ease;
      }
      .options {
        padding: 12px 19px;
        width: 100%;
        font-size: 11px;
        font-weight: bolder;
        margin-bottom: 0;
        color: #fff;
        position: relative;
        bottom: 0;
        z-index: 8999;
        // background: cadetblue;
        display: flex;
        right: 0;
        span {
          overflow: hidden;
          p {
            white-space: nowrap;
            margin: 0;
            padding: 0;
            width: calc(100% - 30px);
            overflow: hidden;
            transition: 10s cubic-bezier(0.61, 0.6, 0.22, 0.21) all;
          }
          &:hover p {
            text-indent: -194px;
          }
        }

        .icon-option-user {
          padding-right: 8px;
          transform: scale(1.5);
        }
        &:hover .icon-option {
          color: #fff;
        }
        .icon-option {
          outline: none;
          border: none;
          background: none;
          color: #cecece;
          position: absolute;
          right: 15px;
          top: 12px;
          transform: scale(2) rotateZ(45deg);
          transition: all 0.5s ease-in;
        }
        .active {
          transform: rotateY(180deg);
        }
      }
    }
    .back {
      color: white;
      transform: rotateY(180deg);
      padding: 20px;

      .options-back {
        padding: 12px 19px;
        width: 100%;
        font-size: 11px;
        font-weight: bolder;
        margin-bottom: 0;
        color: #fff;
        position: relative;
        bottom: 0;
        z-index: 8999;
        display: flex;
        align-items: center;
        right: 0;
        top: 54%;
        .icon-option {
          outline: none;
          border: none;
          background: none;
          color: #cecece;
          position: absolute;
          right: -5px;
          top: 2px;
          transform: scale(2) rotateZ(45deg);
          transition: all 0.5s ease-in;
        }
      }
    }
  }
  .active {
    transform: rotateY(180deg);
  }
}
.gallery-modal {
  position: fixed;
  top: 50%;
  left: 50%;
  width: 101%;
  transform: translate(-50%, -50%);
  height: 101%;
  display: none;
  justify-content: center;
  align-items: center;
  opacity: 0;
  transition: opacity 0.6s ease;
  .overlay {
    position: absolute;
    top: 0;
    width: 101%;
    height: 101%;
    display: block;
    background: black;
    opacity: 0.8;
  }
  .img-container {
    width: 50%;
    height: 50%;
    position: relative;
    img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      border-radius: 20px;
    }
  }
  .icon-close-container {
    right: 15px;
    left: auto;
    position: fixed;
    top: 30px;

    .icon-close {
      outline: none;
      border: none;
      background: yellowgreen;
      transform: scale(1.5);
      color: #fff;
      width: 42px;
      border-radius: 20px 0;
      padding: 8px;
      i {
        transform: scale(2);
      }
    }
    .toggle_modal_icon {
      display: none;
    }
    // .icon-close::after {
    //   content: "";
    //   display: block;
    //   position: absolute;
    //   right: 0;
    //   top: 100%;
    //   width: 20px;
    //   height: 20px;
    //   background: 0 0;
    //   border-top-right-radius: 10px;
    //   box-shadow: 5px -2px 0 #000;
    //   transition: height 0.15s ease 0.3s;
    // }
    .icon-close::before {
      content: "";
      display: block;
      position: absolute;
      right: 0;
      bottom: 100%;
      width: 20px;
      height: 20px;
      background: 0 0;
      border-bottom-right-radius: 10px;
      box-shadow: 5px 2px 0 yellowgreen;
      transition: height 0.15s ease 0.3s;
    }
  }
}
.toggle_modal_items.gallery-modal {
  display: flex;
  opacity: 1;
}
.modalAnimate-enter-active,
.modalAnimate-leave-active {
  transition: opacity 0.5s ease;
}
.modalAnimate-enter-from /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
.modalAnimate-enter-to {
  opacity: 1;
}
.modalAnimate-leave-from {
  opacity: 1;
}
.modalAnimate-leave-to {
  opacity: 0;
}
</style>
