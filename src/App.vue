<template>
  <div>
    <div class="bgBox" v-motion :initial="{ opacity: 0, y: 25 }" :enter="{ opacity: 1, y: 0 }" :duration="1000">
      <img src="https://misskey.s3.cn-north-1.jdcloud-oss.com/image/a7ca728f-40de-4480-bfd8-e97b7b697e40.webp" alt="">
    </div>

    <div class="bgGrid">
      <div class="Grid" v-motion :initial="{ opacity: 0, y: -25 }" :enter="{ opacity: 1, y: 0 }" :duration="1000">
        <div class="mask"></div>
        <div class="itemGrid-row" v-for="i in gridRows" :key="i">
          <div class="itemGrid-cols" v-for="j in gridCols" :key="j"></div>
        </div>
      </div>
    </div>

    <div class="main" v-motion :initial="{ opacity: 0 }" :enter="{ opacity: 1 }" :duration="1000">
      <div class="info">
        <div class="header">
          <img src="https://misskey.s3.cn-north-1.jdcloud-oss.com/image/3e96beeb-66b5-455a-a5d2-b757a3d961c1.jpeg" alt="">
        </div>

        <div class="infoText">
          <h1>Hi,</h1>
          <h1>I'm <span class="name">Honahec</span></h1>
        </div>
      </div>

      <div class="typewriter">
        <i class="iconfont icon-quotesUp1"></i>
        <VueTyped :strings="typingTexts" :startDelay="300" :typeSpeed="100" :backSpeed="30" :loop="true"
          :showCursor="true">
        </VueTyped>
        <i class="iconfont icon-quotesUp"></i>
      </div>

      <div class="btns">
        <a v-for="i in btnList" :key="i.animate" :href="i.href" target="_blank">
          <vs-button type="gradient" :color="i.color" animation-type="scale">
            <i :class="`iconfont ${i.icon}`"></i>

            <template #animate>
              {{ i.animate }}
            </template>
          </vs-button>
        </a>

        <vs-button class="lastBtn" color="#457B9D" animation-type="scale" @click="active = true">
          <i class="iconfont icon-guanyu"></i>

          <template #animate>
            关于
          </template>
        </vs-button>
      </div>
    </div>

    <div class="footer">
      <a href="https://beian.miit.gov.cn/" target="_blank">鲁ICP备2024119517号-1</a> | ©2024
    </div>

    <vs-dialog overlay-blur width="550px" not-center v-model="active">
      <template #header>
        <h2 class="not-margin">
          关于本站
        </h2>
      </template>

      <div class="con-content">

        <vs-alert color="#FE8599" type="gradient" v-model:hidden-content="techHidden">
          <template #title>技术栈</template>
          <p>本站基于以下技术搭建和以下服务商部署</p>

          <vs-avatar-group class="aboutAva" float max="8">

            <vs-tooltip placement="top" v-for="i in avaters" :key="i.content">
              <vs-avatar :color="i.color">
                <i :class="`iconfont ${i.icon}`"></i>
              </vs-avatar>

              <template #content>{{ i.content }}</template>
            </vs-tooltip>
          </vs-avatar-group>
        </vs-alert>

        <vs-alert color="#00BCD4" type="gradient" v-model:hidden-content="aboutHidden">
          <template #title>关于项目</template>

          <p>你可以从这里访问 <b>我的博客、GitHub、哔哩哔哩、网易云歌单、ICS服务器论坛</b> 以及给我发 <b>邮件</b> ！</p>
          <p>项目已经开源：</p>
          <p><a href="https://github.com/Calm00/homepage"
              target="_blank">https://github.com/Calm00/homepage</a>
          </p>
        </vs-alert>
      </div>

      <template #footer>
        <div class="con-footer">
          <div class="reTheme">

            <input type="radio" id="light" name="theme" :checked="theme == 'light'">
            <label @click="setTheme('light')" for="light">
              <i class="iconfont icon-baitian"></i>
            </label>

            <input type="radio" id="system" name="theme" :checked="theme == 'system'">
            <label @click="setTheme('system')" for="system">
              <i class="iconfont icon-gensuixitong"></i>
            </label>

            <input type="radio" id="dark" name="theme" :checked="theme == 'dark'">
            <label @click="setTheme('dark')" for="dark">
              <i class="iconfont icon-yewan"></i>
            </label>

            <div class="checkedBg"></div>
          </div>

          <div class="footerBtn">
            <vs-button color="#fe8599" @click="versions" type="border">
              当前版本
            </vs-button>
            <vs-button color="#fe8599" @click="active = false">
              知道啦
            </vs-button>
          </div>
        </div>
      </template>
    </vs-dialog>
  </div>
</template>

<script>
import { VsNotification } from 'vuesax-alpha'

export default {
  data() {
    return {
      techHidden: true,
      aboutHidden: true,
      typingTexts: [
        "你好鸭，欢迎来到我的主页！",
        "彼方尚有荣光在，世界不止眼前的苟且，还有诗和远方",
        "累了可以在我这里歇歇脚嗷",
        "May you happy every day",
      ],
      btnList: [
        {
          icon: 'icon-wodeboke',
          animate: '博客',
          color: '#fe8599',
          href: 'https://blog.honahec.cc'
        },
        {
          icon: 'icon-14',
          animate: 'ICS论坛',
          color: '#90EE90',
          href: 'https://forum.honahec.cc'
        },
        {
          icon: 'icon-github',
          animate: 'Github',
          color: '#3d3d3d',
          href: 'https://github.com/Calm00'
        },
        {
          icon: 'icon-bilibili',
          animate: 'BiliBili',
          color: '#0BA6D8',
          href: 'https://space.bilibili.com/299797909'
        },
        {
          icon: 'icon-youjian',
          animate: 'E-mail',
          color: '#FACB1E',
          href: 'mailto:honahec@gmail.com'
        },
        {
          icon: 'icon-wangyiyunyinle',
          animate: '网易云',
          color: '#D81E06',
          href: 'https://music.163.com/#/user/home?id=1418921824'
        }
      ],
      avaters: [
        {
          color: '#43B884',
          icon: 'icon-Vue',
          content: 'Vue3'
        },
        {
          color: '#46C93A',
          icon: 'icon-vuesax-linear-vuesax',
          content: 'Vuesax for Vue3'
        },
        {
          color: '#1FD0ED',
          icon: 'icon-less',
          content: 'Less'
        },
        {
          color: '#FFBA00',
          icon: 'icon-vite',
          content: 'Vite'
        },
        {
          color: '#000',
          icon: 'icon-github',
          content: 'Github'
        },
        {
          color: '#ff7500',
          icon: 'icon-aliyun',
          content: '阿里云'
        }
      ],
      upTime: '2024-11-2',
      version: '1.0',
      gridRows: 9,
      gridCols: 5,
      active: false,
      isDarkMode: true,
      theme: 'system' // 默认是亮色模式
    }
  },
  mounted() {
    if (localStorage.getItem('isTheme')) {
      this.theme = localStorage.getItem('isTheme')
      this.applyTheme()
    } else {
      this.applyTheme()
    }
    // 监听系统主题变化
    window.matchMedia('(prefers-color-scheme: dark)').addEventListener('change', this.applyTheme);
  },
  methods: {
    setTheme(mode) {
      this.theme = mode;
      localStorage.setItem('isTheme', mode)
      this.applyTheme();
    },
    applyTheme() {
      const prefersDark = window.matchMedia('(prefers-color-scheme: dark)').matches;
      const themeToApply = this.theme === 'system' ? (prefersDark ? 'dark' : 'light') : this.theme;
      document.documentElement.setAttribute('data-theme', themeToApply);
    },
    versions() {
      VsNotification({
        icon: '<i class="iconfont icon-guanyu"></i>',
        progressAuto: true,
        position: 'top-center',
        title: '当前的版本',
        color: '#FE8599',
        content: `现在是 ${this.upTime} 更新的 ${this.version}`
      })
    }
  }
}
</script>

<style lang="less">
@import url(//at.alicdn.com/t/c/font_4730772_bdc1qnyho9d.css);
/* 阿里巴巴图标库 */
</style>
