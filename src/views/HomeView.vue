<template>
  <div>
    <!-- 第一屏 -->
    <div class="body">
      <div>
        <p class="head">THE PASSWORD FOR DISCOVERING WEALTH</p>
      </div>
      <div>
        <img
          class="first-content__bg"
          src="https://image.kmeta.world/website/logo2.jpg"
        />
      </div>
      <div class="content">
        <!-- 中间的logo -->
        <!-- <div class="logo">
          <img src="http://image.kmeta.world/website/logo.png" />
        </div> -->
        <!-- 下方的盒子 -->
        <div class="big">
          <div class="left">
            <div class="iscontact" v-show="iscon" >
              <div class="p1">
                <p>Contact us：</p>
                <img src="./img/x.png" alt="关闭" @click="noshowcon" />
              </div>
              <p class="p2" style="margin-top: 10px;padding-bottom: 10px;">E-mail：kmeta@kmeta.world</p>
            </div>
            <div
              class="contact"
              @click="showcon"
              @mouseenter="showcon1"
              @mouseleave="noshowcon1"
              id="contact"
            >
              <img src="http://image.kmeta.world/website/contact.png" alt="" />
              <p>JOIN US</p>
            </div>
          </div>
          <div class="button">
            <div style="width: 18px;height: 19px;">
            <a href="javascript:history.go(0);"
              ><img src="https://image.kmeta.world/website/star1.png" style="width: 18px;height: 19px;"
            /></a></div>
          </div>
          <div class="bigright">
            <div class="left">
              <div class="login">
                <img src="https://image.kmeta.world/website/login1.png" />
                <p
                  style="
                    font-size: 12px;
                    color: #ffffff;
                    font-weight: bold;
                    margin-left: 5px;
                  "
                >
                  LOG IN
                </p>
              </div>
              <div class="downloadlogin">
                <p style="font-size: 16px; color: #ffffff">Coming soon</p>
              </div>
            </div>
            <div class="right" @mouseleave="noshow">
              <div class="download" @mouseenter="show" id="download">
                <img src="https://image.kmeta.world/website/download1.png" />
                <p
                  style="
                    font-size: 12px;
                    color: #ffffff;
                    font-weight: bold;
                    margin-left: 6px;
                  "
                >
                  DOWNLOAD
                </p>
              </div>
              <!-- <div class="isdownloadshow"> -->
              <div class="downloadad" v-if="isdownload">
                <div class="indownloadad">
                  <img src="https://image.kmeta.world/website/ios1.png" />
                  <div class="indownloadad_text">
                    <p
                      style="font-size: 14px; color: #ffffff; font-weight: bold"
                    >
                      App Store
                    </p>
                    <p style="font-size: 10px; color: #ffffff">Coming soon</p>
                  </div>
                </div>
              </div>
              <div class="downloadios" v-if="isdownload">
                <div class="indownloadios">
                  <img src="https://image.kmeta.world/website/ad1.png" />
                  <div class="indownloadad_text">
                    <p
                      style="font-size: 14px; color: #ffffff; font-weight: bold"
                    >
                      Android
                    </p>
                    <p style="font-size: 10px; color: #ffffff">Coming soon</p>
                  </div>
                </div>
              </div>
              <!-- </div> -->
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'

export default {
  data() {
    return {
      isdownload: false,
      islogin: false,
      iscon: false,
      // iscopyright:false
    };
  },
  methods: {
    Scrollbottom() {
      let scrollTop =
        document.documentElement.scrollTop || document.body.scrollTop;
      let clientHeight = document.documentElement.clientHeight;
      let scrollHeight = document.documentElement.scrollHeight;
      if (scrollTop + clientHeight >= scrollHeight) {
        // alert("滚动到底部了")
        // this.iscopyright = true
        // this.pageNo++
        // console.log(this.pageNo);
        // this.fetchData()
      } else {
        // this.iscopyright = false
      }
    },
    show() {
      var download = document.getElementById("download");
      download.style.border = "rgba(35, 174, 216, 0.5) 2px solid";
      this.isdownload = true;
    },
    noshow() {
      this.isdownload = false;
      var download = document.getElementById("download");

      download.style.border = "rgba(35, 174, 216, 1) 2px solid";
    },
    showcon() {
      this.iscon = true;
      var contact = document.getElementById("contact");
      contact.style.border = "rgba(214, 72, 239, 0.5)2px solid";
      contact.style.background = "rgba(214, 72, 239, 0.15)";
    },
    noshowcon() {
      this.iscon = false;
      var contact = document.getElementById("contact");

      contact.style.border = "rgba(214, 72, 239, 1)2px solid";
    },
    showcon1() {
      var contact = document.getElementById("contact");

      contact.style.background = "rgba(214, 72, 239, 1)";
    },

    noshowcon1() {
      var contact = document.getElementById("contact");

      contact.style.background = "rgba(214, 72, 239, 0.15)";
    },
  },
  created() {
    window.addEventListener("scroll", this.Scrollbottom); //页面加载时监听滚动事件
    let domWidth = document.body.clientWidth || document.body.scrollWidth;
    let domHeight = document.body.clientHeight || document.body.scrollHeight;

    // 点击除了joinus之外的地方联系我们关闭
    let that=this;//将vue对象的引用保存在that中
    document.addEventListener("click", function (event) {
      // console.log("e", event);
      var contact = document.getElementById("contact");
      if (event.target !== contact && !contact.contains(event.target)) {
        that.noshowcon();
    
      }
    });
  },

  destroyed() {
    window.removeEventListener("scroll", this.Scrollbottom); //页面离开后销毁监听事件
    window.removeEventListener("click",); //页面离开后销毁监听事件
  },
};
</script>

<style lang="scss" scoped>
/*通配符号让所有标签的margin和padding为0*/
* {
  padding: 0;
  margin: 0;
}
.body {
  width: 100%;

  min-width: 1000px;

  min-height: 100vh;
  position: relative;
  // display: flex;
  // flex-direction: column;
  // width: 100%;
  // height: 100vh;
  /* width: 1890px;
  height: 950px; */
  /*100vh是指的可视区域的总高度*/
  // background-image: url(http://image.kmeta.world/website/big.png);
  // background-size: cover;
  // background-repeat: no-repeat;
  /* -moz-background-size:100% 100%;  */
  /* background-size:100% 100%; */
}
.first-content__bg {
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
  height: 100vh;
  object-fit: cover;
  z-index: -1;
}
.head {
  width: 100%;
  height: 39px;
  line-height: 39px;
  text-align: center;
  vertical-align: middle;
  color: #ffffff;
  font-size: 14px;
}

.content {
  // flex: 1;
  // width: 100%;
  /* position: relative; */
  // width: 100%;
  height: 250px;
  // position: absolute;
  // bottom: 0px;
  // top: 830px;
  // border: #1c883c 1px solid;
  // display: flex;
  // justify-content: center;

  position: absolute;
  left: 0;
  bottom: 0;
  width: 100%;
  z-index: 900;
}
// .logo {
//   width: 207px;
//   height: 249px;
//   position: absolute;
//   left: 50%;
//   top: 50%;
//   margin-left: -104px;
//   margin-top: -125px;
// }
// .logo img {
//   width: 207px;
//   height: 249px;
// }

// .bottom {
//   height: 44px;
//   width: 100%;
//   background-color: #bbf;
//   position: absolute;
//   top: 90%;
// }
.big {
  height: 250px;

  // width: 1802px;
  // border: #23aed8 1px solid;
  // position: absolute;
  // left: 60px;
  // right: 60px;

  // bottom: 48px;
}
.big .left {
  position: absolute;
  bottom: 48px;
  left: 60px;

  width: 358px;
  height: 199px;
  // position: absolute;
  // left: 0px;
  // bottom: 0px;
  // background-color: #984040;
}
.iscontact {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: flex-start;
  width: 358px;
  height: 125px;
  position: absolute;
  top: 0;
  left: 0;
  border: #d648ef 2px solid;
  background: rgba(214, 72, 239, 0.15);

  border-radius: 20px;
}
.iscontact:hover {
  background: rgba(214, 72, 239, 1);
}
.iscontact .p1 {
  display: flex;
  // text-align: left;
  justify-content: center;
  align-items: center;
  margin-left: 27px;
  color: #ffffff;
  font-size: 24px;
  font-weight: bold;
}

.iscontact .p1 img {
  margin-left: 150px;
  margin-bottom: 30px;
  width: 15px;
  height: 15px;
}
.iscontact .p2 {
  margin-left: 27px;
  color: #ffffff;

  margin-top: 22px;
  font-size: 16px;
}
.contact {
  display: flex;

  align-items: center;
  width: 154px;
  height: 36px;
  /* background-color: #bfa; */
  // position: absolute;
  // top: 90%;
  // left: 3%;
  position: absolute;
  bottom: 0px;
  left: 0;
  border: #d648ef 2px solid;
  border-radius: 40px;
  background: rgba(214, 72, 239, 0.15);
}
.contact:hover {
  background: rgba(214, 72, 239, 1);
}
.contact img {
  width: 19px;
  height: 16px;
  margin-left: 39px;
}
.contact p {
  margin-left: 6px;
  color: #ffffff;
  font-size: 12px;
  font-weight: bold;
}

.button {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 64px;
  height: 36px;
  /* background-color: #bfa; */
  // position: absolute;
  // bottom: 0px;
  // left: 50%;
  // margin-left: -42px;
  border: rgba(50, 26, 193, 0.5) 2px solid;
  border-radius: 16px;

  position: absolute;
  bottom: 48px;
  left: 50%;
  transform: translate(-50%, 0);
}
.button:hover {
  border: rgba(50, 26, 193, 1) 2px solid;

}
.bigright {
  // border: rgba(50, 26, 193, 1) 2px solid;

  width: 338px;
  height: 174px;

  // position: absolute;
  // right: 0px;
  // bottom: 0px;
  position: absolute;
  bottom: 48px;
  right: 60px;
}

.bigright .left {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 144px;
  height: 118px;
}
.login {
  display: flex;
  align-items: center;
  width: 144px;
  height: 36px;
  background: rgba(48, 80, 255, 0.15);

  position: absolute;
  bottom: 0;
  left: 0;
  border: #3050ff 2px solid;

  border-radius: 40px;
}
.downloadlogin {
  display: none;
  justify-content: center;
  align-items: center;
  width: 144px;
  height: 44px;
  /* background-color: #bfa; */
  position: absolute;
  top: 0px;
  left: 0;
  border: #3050ff 2px solid;
  background: rgba(48, 80, 255, 0.15);
  border-radius: 40px;
  font-size: 10px;
}
.login:hover {
  background: rgba(48, 80, 255, 1);
}
.login:hover + .downloadlogin {
  display: flex;
}
.login img {
  width: 21px;
  height: 18px;
  margin-left: 39px;
}

// .bigright .left p {
//   margin-left: 10px;
//   color: #ffffff;
//   font-size: 10px;
// }

.bigright .right {
  width: 154px;
  height: 174px;
  position: absolute;
  top: 0;
  right: 0;
  // background-color: #984040;
}
.downloadad {
  display: flex;
  align-items: center;
  width: 154px;
  height: 44px;
  border: #23aed8 2px solid;
  background: rgba(35, 174, 216, 0.15);
  border-radius: 40px;
  position: absolute;
  top: 0;
  left: 0;
}
.downloadad:hover {
  background: rgba(35, 174, 216, 1);
}
.downloadios:hover {
  background: rgba(35, 174, 216, 1);
}
.downloadad .indownloadad {
  width: 123px;
  height: 30px;
  display: flex;
  // justify-content: space-between;
  margin-left: 29px;
  // background: #3050ff;
}
.downloadad img {
  width: 22px;
  height: 24px;
}
.indownloadad_text {
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  align-items: start;
  margin-left: 8px;
  // background-color: #cdf;
}
.downloadios {
  display: flex;
  align-items: center;
  width: 154px;
  height: 44px;
  border: #23aed8 2px solid;
  background: rgba(35, 174, 216, 0.15);

  border-radius: 40px;
  position: absolute;
  bottom: 66px;
  left: 0;
}
.downloadios .indownloadios {
  width: 123px;
  height: 30px;
  display: flex;
  // justify-content: space-between;
  margin-left: 29px;
}
.downloadios img {
  width: 26px;
  height: 30px;
  // margin-left: 45px;
}
.downloadios .indownloadios_text {
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  align-items: start;
  margin-left: 8px;
}

.download {
  display: flex;
  align-items: center;
  width: 154px;
  height: 36px;
  position: absolute;
  bottom: 0;
  left: 0;
  background: rgba(35, 174, 216, 0.15);
  border: rgba(35, 174, 216, 1) 2px solid;
  border-radius: 40px;
}
.download img {
  width: 22px;
  height: 17px;
  margin-left: 26px;
}
</style>
