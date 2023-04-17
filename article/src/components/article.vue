<template>
  <div>
    <!-- {{ localObj }} -->
    <div class="all-component">
      <div v-for="(item, i) in localObj" :key="i">
        <!-- big-title -->
        <div
          data-aos="fade-right"
          data-aos-duration="400"
          v-if="item.componentType == 'big-title'"
        >
          <div class="c-big-title">{{ item.text }}</div>
        </div>
        <!-- title -->
        <div
          data-aos="fade-right"
          data-aos-duration="800"
          class="title"
          v-if="item.componentType == 'title'"
        >
          <div class="c-title-text">{{ item.text }}</div>
        </div>
        <!-- icon-title -->
        <div
          data-aos="fade-right"
          data-aos-duration="800"
          class="icon-title"
          v-if="item.componentType == 'icon-title'"
        >
          <div class="c-icon-title">
            <div><i :class="item.icon"></i></div>
            <div class="c-icon-title-text">{{ item.text }}</div>
          </div>
        </div>
        <!-- text -->
        <div
          data-aos="fade-right"
          data-aos-duration="1200"
          class="text"
          v-if="item.componentType == 'text'"
        >
          <div
            v-for="(item2, i) in item.text"
            :key="i"
            class="c-text"
            v-html="item2"
            :style="item.style"
          ></div>
        </div>
        <!-- img -->
        <div
          data-aos="fade-right"
          data-aos-duration="1500"
          class="img"
          v-if="item.componentType == 'img'"
        >
          <div class="c-img" v-for="(item2, i) in item.data" :key="i">
            <div class="imgData">
              <a class="imga" :style="item.style" :href="item2.imgLink" target="_blank">
                <v-card :elevation="18" class="secondary adiv" @click="go(index)">
                  <img style="width: 100%" :src="item2.imgUrl" />
                </v-card>
                <!-- <img style="width:100%" :src="item2.imgUrl" /> -->
                <div class="underPictureText">{{ item2.imgText }}</div>
              </a>
            </div>
          </div>
        </div>
        <!-- list  -->
        <div
          data-aos="fade-right"
          data-aos-duration="1200"
          v-if="item.componentType == 'list'"
        >
          <div class="c-list">
            <!-- ul -->
            <ul v-if="item.data.type == 'ul'" :style="item.data.style">
              <!-- li -->
              <li v-for="(item2, i) in item.data.data" :key="i">
                <!-- 第一層內容 有連結 -->
                <a :href="item2.link" target="_blank" v-if="item2.link">
                  {{ item2.text }}
                </a>

                <!-- 第一層內容 無連結-->
                <div v-else>
                  {{ item2.text }}
                </div>
                <!-- 第二層ul -->
                <ul
                  v-if="item2.data && item2.data.type == 'ul'"
                  :style="item2.data.style"
                >
                  <!-- 第二層li -->
                  <li v-for="(item3, i) in item2.data.data" :key="i">
                    <a :href="item3.link" target="_blank" v-if="item3.link">{{
                      item3.text
                    }}</a>
                    <div v-else>{{ item3.text }}</div>
                  </li>
                </ul>
                <!-- 第二層ol -->
                <ol
                  v-if="item2.data && item2.data.type == 'ol'"
                  :style="item2.data.style"
                >
                  <!-- 第二層li -->
                  <li v-for="(item3, i) in item2.data.data" :key="i">
                    <a :href="item3.link" target="_blank" v-if="item3.link">{{
                      item3.text
                    }}</a>
                    <div v-else>{{ item3.text }}</div>
                  </li>
                </ol>
              </li>
            </ul>
            <!-- ol -->
            <ol v-if="item.data.type == 'ol'" :style="item.data.style">
              <!-- li -->
              <li v-for="(item2, i) in item.data.data" :key="i">
                <!-- 第一層內容 有連結 -->
                <a :href="item2.link" target="_blank" v-if="item2.link">
                  {{ item2.text }}
                </a>

                <!-- 第一層內容 無連結-->
                <div v-else>
                  {{ item2.text }}
                </div>
                <!-- 第二層ul -->
                <ul
                  v-if="item2.data && item2.data.type == 'ul'"
                  :style="item2.data.style"
                >
                  <!-- 第二層li -->
                  <li v-for="(item3, i) in item2.data.data" :key="i">
                    <a :href="item3.link" target="_blank" v-if="item3.link">{{
                      item3.text
                    }}</a>
                    <div v-else>{{ item3.text }}</div>
                  </li>
                </ul>
                <!-- 第二層ol -->
                <ol
                  v-if="item2.data && item2.data.type == 'ol'"
                  :style="item2.data.style"
                >
                  <!-- 第二層li -->
                  <li v-for="(item3, i) in item2.data.data" :key="i">
                    <a :href="item3.link" target="_blank" v-if="item3.link">{{
                      item3.text
                    }}</a>
                    <div v-else>{{ item3.text }}</div>
                  </li>
                </ol>
              </li>
            </ol>
          </div>
        </div>
        <!-- iframe -->
        <div data-aos="fade-right" v-if="item.componentType == 'iframe'">
          <div class="iframe">
            <iframe
              class="myFrame"
              :src="item.data.url"
              :width="item.data.width"
              :height="item.data.height"
              frameborder="0"
            ></iframe>
          </div>
        </div>
        <!-- iframe -->
        <div data-aos="fade-right" v-if="item.componentType == 'pdf'">
          <!-- pdf -->
          <div class="pdf">
            <object
              :width="item.data.width"
              :height="item.data.height"
              :data="item.data.url"
              type="application/pdf"
            >
              <a :href="item.data.url">{{ item.data.name }}</a>
            </object>
          </div>
        </div>
        <!-- nullData -->
        <div data-aos="fade-right" v-if="item.componentType == 'nullData'">
          <div class="nullData"></div>
        </div>
        <!-- a Line <hr> -->
        <div data-aos="fade-right" v-if="item.componentType == 'hr'">
          <div style="margin-top: 20px">
            <hr color="#757575" size="1" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",

  data() {
    return {
      localObj: "",
    };
  },
  props: ["jsondata"],
  methods: {
    getlocalData(response) {
      var self = this;
      self.localObj = response;
    },
  },
  mounted() {
    var self = this;
    self.localObj = self.jsondata;
    // setTimeout(() => {
    //   if (self.$store.state.mobileState) {
    //     if (document.getElementsByClassName("myFrame")[0]) {
    //       document.getElementsByClassName("myFrame")[0].width = "100%";
    //     }
    //   }
    // }, 700);
  },
  watch: {
    jsondata: function () {
      var self = this;

      self.localObj = self.jsondata;
    },
  },
  computed: {

  },
};
</script>

<style lang="scss" scoped>

  $main-color: #568;


a {
  text-decoration: none !important;
}

.all-component {
  a {
    color: #2196f3 !important;
    text-decoration: none !important;
  }

  ol {
    padding-left: 60px;
    line-height: 2;

    li {
      &::marker {
        font-size: 24px;
        font-weight: 600;
      }

      a {
        line-height: 1.5;
        font-size: 22px;
        font-weight: 800;
      }

      div {
        line-height: 1.5;
        font-size: 22px;
        font-weight: 800;
      }

      ul {
        padding-left: 10px;

        li {
          &::marker {
            font-size: 22px;
            font-weight: 400;
          }

          a {
            line-height: 1.5;
            font-size: 22px;
            font-weight: 800;
          }

          div {
            line-height: 1.5;
            font-size: 22px;
            font-weight: 400;
          }
        }
      }

      ol {
        padding-left: 10px;

        li {
          &::marker {
            font-size: 22px;
            font-weight: 400;
          }

          a {
            line-height: 1.5;
            font-size: 22px;
            font-weight: 800;
          }

          div {
            line-height: 1.5;
            font-size: 22px;
            font-weight: 400;
          }
        }
      }
    }
  }

  ul {
    padding-left: 60px;
    line-height: 2;

    li {
      &::marker {
        font-size: 24px;
        font-weight: 600;
      }

      a {
        line-height: 1.5;
        font-size: 22px;
        font-weight: 800;
      }

      div {
        line-height: 1.5;
        font-size: 22px;
        font-weight: 800;
      }

      ul {
        padding-left: 10px;

        li {
          &::marker {
            font-size: 22px;
            font-weight: 400;
          }

          a {
            line-height: 1.5;
            font-size: 22px;
            font-weight: 800;
          }

          div {
            line-height: 1.5;
            font-size: 22px;
            font-weight: 400;
          }
        }
      }

      ol {
        padding-left: 10px;

        li {
          &::marker {
            font-size: 22px;
            font-weight: 400;
          }

          a {
            line-height: 1.5;
            font-size: 22px;
            font-weight: 800;
          }

          div {
            line-height: 1.5;
            font-size: 22px;
            font-weight: 400;
          }
        }
      }
    }
  }

  .c-big-title {
    color: $main-color !important;
    font-weight: bold;
    display: inline-block;
    font-size: 35px;
    line-height: 1.1;
    margin-bottom: 20px;
    margin-top: 30px;
    // padding-left: 15px;
  }

  .icon-title {
    display: flex;

    .c-icon-title {
      display: flex;
      color: $main-color !important;
      font-size: 26px;
      line-height: 1.1;
      margin-bottom: 20px;
      margin-top: 20px;
      font-weight: 600;

      .c-icon-title-text {
        margin-left: 10px;
      }
    }
  }

  .title {
    .c-title-text {
      border-left: 4px solid $main-color !important;
      color: $main-color !important;
      display: inline-block;
      font-size: 26px;
      line-height: 1.1;
      margin-bottom: 20px;
      margin-top: 20px;
      padding-left: 15px;
      font-weight: 600;
    }
  }

  .text {
    margin-bottom: 10px;

    .c-text {
      font-weight: 500;
      font-size: 20px;
      text-indent: 2em;
      color: #000000;
      margin-bottom: 10px;
    }
  }

  .img {
    display: flex;

    @media only screen and (max-width: 768px) {
      flex-direction: column;
    }

    .c-img {
      margin: 20px 0;
      display: flex;
      flex: 1;

      .imgData {
        display: flex;
        flex-direction: column;
        width: 100%;

        .imga {
          display: flex;
          flex-direction: column;

          @media only screen and (max-width: 768px) {
            width: 100% !important;
          }

          img {
            display: flex;
          }

          .underPictureText {
            color: black;
            font-size: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-top: 10px;
            font-weight: 600;
          }
        }
      }
    }
  }

  .c-list {
    font-size: 20px;
    line-height: 1.7;

    a {
      color: #636bd8;
      text-decoration: none !important;
    }
  }

  .iframe {
    margin-top: 20px;
  }

  .nullData {
    height: 20px;
  }
}
</style>
