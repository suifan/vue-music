<template lang="html">
  <transition name="fadeIn">
    <div  class="aside-menu">
      <i @click="showAsideMenu" class="back"></i>
      <div class="aside">
        <div :style="{backgroundColor: skinColor}" class="info">
          <a href="#" target="_blank" class="avatar"><img src="./avator.jpg"></a>
          <div class="about">
            <span class="name"><a href="https://github.com/lensh/vue-music">lensh</a></span>
            <span class="level">Lv33</span>
            <span @click="isSignIn=true" class="sign">
              <i></i>
              {{isSignIn ? '已签到' : '签到'}}
            </span>
          </div>
        </div>
        <div class="settings">
          <div class="content">
            <ul>
              <li><i class="icon-msg"></i>我的消息</li>
              <li><i class="icon-vip"></i>会员中心</li>
              <li><i class="icon-shop"></i>商城</li>
              <li><i class="icon-music"></i>在线听歌免流量</li>
            </ul>
            <ul>
              <li><i class="icon-friend"></i>我的好友</li>
              <li><i class="icon-near"></i>附近的人</li>
            </ul>
            <ul>
              <li @click.stop.prevent="$store.commit('showIndex', false)"><i class="icon-skin"></i>个性换肤</li>
            </ul>
            <div class="back">
              <i @click.stop.prevent="showAsideMenu" class="icon-back"></i>
            </div>
          </div>
        </div>
      </div>
      <div @click.stop.prevent="showAsideMenu" class="mask"></div>
    </div>
  </transition>

</template>

<script>
export default {
  name: 'AsideMenu',
  computed: {
    skinColor() {
      return this.$store.state.skinColor
    }
  },
  data() {
    return {
      isSignIn: false
    }
  },
  methods: {
    showAsideMenu() {
      this.$store.commit('showAsideMenu', false)
    }
  }
}
</script>

<style lang="scss" scoped>

.fadeIn-enter-active {
  transition: all .4s ease;
}
.fadeIn-leave-active {
  transition: all .2s cubic-bezier(1.0, 0.5, 0.8, 1.0);
}
.fadeIn-enter, .fadeIn-leave-active {
  transform: translateX(-250px);
  opacity: 0;
}
  .aside-menu {
    width: 100%;
    height: 100%;
    position: absolute;
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
    display: flex;
    z-index: 3;
    i.back {
      display: inline-block;
      position: absolute;
      left: 50%;
      top: 10px;
      background: url('./back.svg') no-repeat;
      width: 20px;
      height: 20px;
      background-size: contain;
    }
    .aside {
      flex: 6;
    }
    .mask {
      flex: 4;
    }
    .info {
      padding:20px 0 8px 20px;
      background-color: #B72712;
      box-shadow: 2px 0 10px gray;
      flex: 1;
      img {
        width: 60px;
        height: 60px;
        border-radius: 50%;
      }
      .about {
        position: relative;
        margin-top: 2px;
        span.name {
          color: rgba(255, 255, 255, .8);
          font-size: 1.2rem;
        }
        span.level {
          width: 15px;
          height: 15px;
          border: 1px solid white;
          border-radius: 20px;
          padding: 0 6px;
          color: white;
          font-size: .2rem;
          font-style: italic;
        }
        span.sign {
          position: absolute;
          right: 10px;
          top: 5px;
          border: 1px solid white;
          height: 20px;
          width: 50px;
          border-radius: 10px;
          line-height: 20px;
          text-align: center;
          color: white;
          font-size: .8rem;
          cursor: pointer;
        }
      }
    }
    .settings {
      flex: 4.2;
      position: absolute;
      height: 100%;
      width:60%;
      background: white;
      border-right: 1px solid gray;
      box-shadow: 2px 0 20px gray;
      .content {
        height: 85%;
      }

      ul:nth-of-type(1) {
        color: rgba(0, 0, 0, .5);
        padding-top: 20px;
        border-bottom: 6px solid rgba(0, 0, 0, .04);
      }
      ul:nth-of-type(2) {
        color: rgba(0, 0, 0, .5);
        padding-top: 10px;
        padding-bottom: 5px;
        border-bottom: 6px solid rgba(0, 0, 0, .04);
      }
      ul:nth-of-type(3) {
        padding-top: 15px;
      }
      ul {
        list-style: none;
        padding: 5px 20px;
        li {
          font-size: 1rem;
          margin-bottom: 20px;
          cursor: pointer;
          i {
            display: inline-block;
            width: 20px;
            height: 20px;
            margin-right: 10px;
            vertical-align: text-bottom;
          }
          i.icon-skin {
            background: url('./skin.svg') no-repeat;
            background-size: contain;

          }
          i.icon-msg {
            background: url('./msg.svg') no-repeat;
            background-size: contain;
          }
          i.icon-vip {
            background: url('./vip.svg') no-repeat;
            background-size: contain;
          }
          i.icon-shop {
            background: url('./shop.svg') no-repeat;
            background-size: contain;
          }
          i.icon-music {
            background: url('./music.svg') no-repeat;
            background-size: contain;
          }
          i.icon-friend {
            background: url('./friend.svg') no-repeat;
            background-size: contain;
          }
          i.icon-near {
            background: url('./near.svg') no-repeat;
            background-size: contain;
          }

          i.aboutme {
            display: inline-block;
            margin-right: 2px;
            width: 20px;
            height: 20px;
            background: url('./about.svg') no-repeat;
            background-size: contain;
          }
        }
      }

    }
  }
  a.avatar:hover::after {
    transform: scaleX(0);
  }
  a::after {
    background-color: white;
  }
</style>
