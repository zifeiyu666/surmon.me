<template>
  <aside class="aside">
    <div class="aside-user">
      <div class="avatar">
        <img :src="gravatar" alt="Surmon">
      </div>
      <div class="profile">
        <h3 class="name">Surmon</h3>
        <p class="email">Talk is cheap. Show me the code</p>
      </div>
    </div>
    <div class="aside-nav">
      <nav class="nav-list">
        <nuxt-link :to="'/'" class="item" exact>
          <i class="iconfont icon-home"></i>
          <span>Home</span>
        </nuxt-link>
        <nuxt-link to="/category/code" class="item">
          <i class="iconfont icon-code"></i>
          <span>Code</span>
        </nuxt-link>
        <nuxt-link to="/project" class="item">
          <i class="iconfont icon-tool"></i>
          <span>Project</span>
        </nuxt-link>
        <nuxt-link to="/category/think" class="item">
          <i class="iconfont icon-think"></i>
          <span>Think</span>
        </nuxt-link>
        <nuxt-link to="/sitemap" class="item">
          <i class="iconfont icon-netease-music"></i>
          <span>Sitemap</span>
        </nuxt-link>
        <nuxt-link to="/about" class="item">
          <i class="iconfont icon-user"></i>
          <span>About</span>
        </nuxt-link>
        <nuxt-link to="/guestbook" class="item guestbook">
          <i class="iconfont icon-comment"></i>
          <span>Guestbook</span>
        </nuxt-link>
        <nuxt-link to="/app" class="item app">
        <i class="iconfont icon-app"></i>
        <span>App</span>
      </nuxt-link>
      </nav>
    </div>
  </aside>
</template>

<script>
  export default {
    name: 'mobile-aside',
    computed: {
      gravatar() {
        const gravatar = this.$store.state.option.adminInfo.data.gravatar
        return !!gravatar 
                ? `${gravatar}?imageView2/1/w/180/h/180/interlace/1/q/75|imageslim` 
                : '/images/gravatar.jpg'
      }
    }
  }
</script>

<style lang="scss" scoped>
  @import '~assets/sass/variables';
  @import '~assets/sass/mixins';
  aside {
    display: block;
    overflow: auto;
    position: relative;
    width: 100%;
    height: 100%;
    margin: 0;
    opacity: 0;
    transform: scale(0.8, 0.8);
    transition: $mobile-aisde-transition;

    &.open {
      opacity: 1;
      transform: scale(1, 1);
      transition: $mobile-aisde-transition;
    }

    > .aside-user {
      width: 100%;
      display: flex;
      align-items: flex-start;
      flex-direction: column;
      padding: 1em;
      border-bottom: 1px solid darken($mobile-aside-bg, 5%);

      > .avatar {
        width: 35%;

        > img {
          max-width: 100%;
          border: 2px solid $module-bg;
        }
      }

      > .profile {
        color: $body-bg;
        width: 100%;

        > .name {
          font-weight: bold;
          margin-bottom: 1rem;
        }

        > .email {
          color: $primary;
          margin: 0;
          @include text-overflow();
        }
      }
    }

    > .aside-nav {
      width: 100%;

      .nav-list {
        padding: 0;
        margin: 0;

        .item {
          border: none;
          display: block;
          width: 100%;
          height: 3em;
          line-height: 3em;
          padding: 0 1em;
          text-decoration: none;
          text-transform: uppercase;
          font-weight: 700;
          border-radius: 1px;
          color: $module-bg;
          font-family: CenturyGothic;
          margin-bottom: .5em;

          &.guestbook {
            margin-bottom: 0;
          }

          &.app {
            margin-top: 1rem;
            border-top: 1px solid darken($mobile-aside-bg, 5%);
            color: $primary;

            &.link-active {
              background-color: transparent;
            }
          }

          &:last-child {
            margin-bottom: 0;
          }

          &:hover {
            color: $primary;
            background-color: $body-bg;
          }

          &.link-active {
            color: $primary;
            font-weight: bold;
            background-color: $body-bg;
          }

          .iconfont {
            width: 1em;
            margin-right: 1em;
            display: inline-block;
          }
        }
      }
    }
  }
</style>
