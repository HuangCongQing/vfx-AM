<template>
  <div id="app">
    <StyleEditor ref="styleEditor" :code="currentStyle"></StyleEditor>
    <ResumeEditor ref="resumeEditor" :markdown="currentMarkdown" :enableHtml="enableHtml"></ResumeEditor>
  </div>
</template>

<script>
  import StyleEditor from './components/StyleEditor'
  import ResumeEditor from './components/ResumeEditor'
  import './assets/reset.css'

  export default {
    name: 'app',
    components: {
      StyleEditor,
      ResumeEditor
    },
    data() {
      return {
        interval: 40,
        currentStyle: '',
        enableHtml: false,
        fullStyle: [
          `/*
* Inspired by http://strml.net/ && http://www.sitexa.org/
* 大家好，我是阿小庆。
* 我来写一份简历！
*/

/* 首先给所有元素加上过渡效果 */
* {
  transition: all .3s;
}
/* 白色背景太单调了，我们来点背景 */
html {
  color: rgb(222,222,222);
  background: rgb(40,29,87);;
}
/* 文字离边框太近了 */
.styleEditor {
  padding: .5em;
  border: 1px solid;
  overflow: auto;
  width: 90vw;
  margin: 2.5vh 5vw;
  height: 90vh;
}
/* 太高了 */
.styleEditor {
  height: 45vh;
}
/* 代码高亮 */
.token.selector{
  color: rgb(133,153,0);
}
.token.property{
  color: rgb(187,137,0);
}
.token.punctuation{
  color: yellow;
}
.token.function{
  color: rgb(42,161,152);
}

/* 加点 3D 效果呗 */
html{
  perspective: 1000px;
}
.styleEditor {
  position: fixed; left: 0; top: 0;
  transform: rotateX(-10deg) translateZ(-50px) ;
}

/* 接下来我给自己准备一个编辑器 */
.resumeEditor{
   padding: 2em;
  position: fixed;
  top: 50%; left: 0;
  padding: .5em;  margin: 2.5vh;
  width: 95vw; height: 45vh;
  border: 1px solid;
  background: white; color: #222;
  overflow: auto;
}
/* 好了，我开始写简历了 */


`,
          `
/* 这个简历好像差点什么
 * 对了，这是 Markdown 格式的，我需要变成对 HR 更友好的格式
 * 简单，用开源工具翻译成 HTML 就行了
 */
`
          ,
          `
/* 再对 HTML 加点样式 */
.resumeEditor{
  padding: 2em;
  // position: fixed; right: 0; top: 0;
  // -webkit-transition: none;
  // transition: none;
  // -webkit-transform: rotateY(-10deg) translateZ(-100px) ;
  //         transform: rotateY(-10deg) translateZ(-100px) ;
}
.resumeEditor h2{
  display: inline-block;
  border-bottom: 1px solid;
  margin: 1em 0 .5em;
}
.resumeEditor ul,.resumeEditor ol{
  list-style: none;
}
.resumeEditor ul> li::before{
  content: '•';
  margin-right: .5em;
}
.resumeEditor ol {
  counter-reset: section;
}
.resumeEditor ol li::before {
  counter-increment: section;
  content: counters(section, ".") " ";
  margin-right: .5em;
}
.resumeEditor blockquote {
  margin: 1em;
  padding: .5em;
  background: #ddd;
}
`],
        currentMarkdown: '',
        fullMarkdown: `阿小庆
====


大学在读学生。

Web前端开发工程师



个人相关
----
* 邮箱：i@huangchongqing.com 
* 微信：hcq1756260160
* 个人公众号：重庆小哥稳
* GitHub：https://github.com/HuangCongQing
* 个人主页：[huangchongqing.top](huangchongqing.top)


实践经历（勤奋蜂科技）2016.06 ~ 至今
----
**前端组主要成员** 负责团队项目研发，维护及性能优化，同时参与了团队代
码规范制定与实施，并参与了工作室日常技术分享交流和codeReview。期
间积攒了各类项目开发 经验和团队合作经验

项目经验
----
* [个人主页 · 技术博客 · 开源作品](blog.huangchongqing.com)
* 日历 · 微信小程序
* 移动端云音乐播放器
* 校招导师h5
* 校招助手 · 微信小程序
* 基于NLP的汇款单自动生成APP

专业技能
----
* 掌握Web前端开发基本技能，熟悉W3C标准、页面布局架构、
前端语义化等，重视用户体验与代码可维护性，有近2年的前端
开发经验。
* 熟悉Handlebar模板引擎、HTML5 、CSS3 、响应式布局，并
了解基本的手机端适配方案。
* 熟悉Vue 框架 、ES6 相关基础，并有一定的项目经验。
* 熟练使用Git 进行版本控制和GitHub 、Coding 代码托管、Mar
kdown 进行文档编写，并以Linux 、Sublime 、VSCode 作为日常
开发环境进行工作，了解项目开发流程及开发调试工具的使用。
* 【其他】： 基本掌握python 语言，能够对文本进行简单的自然语
言处理，了解Google 人工智能系统TensorFlow 。


奖项证书
----
* 2015.12 一二九爱国书法大赛 · 三等奖     院校级
* 2016.05 物联网创新应用大赛 · 三等奖     院校级
* 2016.05 “E.A.电子设计大赛” · 二等奖   院校级
* 2016.09 第三届中国创新创业大赛全国赛最受欢迎奖  国家级
* 2016.10 国家励志奖学金                                 国家级
* 2017.10 国家励志奖学金                                 国家级
* 2018.02 美国大学生数学建模竞赛（MCM/ICM）· 一等奖 国际级

个人素质
----
* 工作态度认真，有责任心，具有强烈的团队合作意识
* 喜欢接触新事物，钻研折腾，学习能力强，敢于尝试，乐于实践
* 性格沉稳，乐观幽默，热爱书法和篮球等运动

其他链接
----
`
      }
    },
    created() {
      this.makeResume()
    },

    methods: {
      makeResume: async function () {
        await this.progressivelyShowStyle(0)
        await this.progressivelyShowResume()
        await this.progressivelyShowStyle(1)
        await this.showHtml()
        await this.progressivelyShowStyle(2)
      },
      showHtml: function () {
        return new Promise((resolve, reject) => {
          this.enableHtml = true
          this.$nextTick(() => {
            this.$refs.resumeEditor.goTop()
          })
          resolve()
        })
      },
      progressivelyShowStyle(n) {
        return new Promise((resolve, reject) => {
          let interval = this.interval
          let showStyle = (async function () {
            let style = this.fullStyle[n]
            if (!style) { return }
            // 计算前 n 个 style 的字符总数
            let length = this.fullStyle.filter((_, index) => index <= n).map((item) => item.length).reduce((p, c) => p + c, 0)
            let prefixLength = length - style.length
            if (this.currentStyle.length < length) {
              let l = this.currentStyle.length - prefixLength
              let char = style.substring(l, l + 1) || ' '
              this.currentStyle += char
              if (style.substring(l - 1, l) === '\n' && this.$refs.styleEditor) {
                this.$nextTick(() => {
                  this.$refs.styleEditor.goBottom()
                })
              }
              setTimeout(showStyle, interval)
            } else {
              resolve()
            }
          }).bind(this)
          showStyle()
        })
      },
      progressivelyShowResume() {
        return new Promise((resolve, reject) => {
          let length = this.fullMarkdown.length
          let interval = this.interval
          let showResume = () => {
            if (this.currentMarkdown.length < length) {
              this.currentMarkdown = this.fullMarkdown.substring(0, this.currentMarkdown.length + 1)
              let lastChar = this.currentMarkdown[this.currentMarkdown.length - 1]
              let prevChar = this.currentMarkdown[this.currentMarkdown.length - 2]
              if (prevChar === '\n' && this.$refs.resumeEditor) {
                this.$nextTick(() => this.$refs.resumeEditor.goBottom())
              }
              setTimeout(showResume, interval)
            } else {
              resolve()
            }
          }
          showResume()
        })
      }
    }
  }

</script>

<style scoped>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    min-height: 100vh; position: relative;
  }

  html {
    min-height: 100vh;
  }
  *{
    box-sizing: border-box;
  }

</style>
