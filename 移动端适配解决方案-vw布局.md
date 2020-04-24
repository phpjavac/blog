---
title: 移动端适配解决方案-vw布局
date: 2020-04-24 10:30:00
---

1.认识视口单位
根据CSS3规范，视口单位主要包括以下4个：

vw : 1vw 等于视口宽度的1%
vh : 1vh 等于视口高度的1%
vmin : 选取 vw 和 vh 中最小的那个
vmax : 选取 vw 和 vh 中最大的那个
视口单位区别于%单位，视口单位是依赖于视口的尺寸，根据视口尺寸的百分比来定义的；而%单位则是依赖于元素的祖先元素。
2.怎么在vue项目中使用vw布局.
借助Vue官网提供的构建工程以及一些PostCSS插件来完成.

    "cssnano-preset-advanced": "^4.0.6",
    "postcss-cssnext": "^3.1.0",
    "postcss-import": "^12.0.1",
    "postcss-px-to-viewport": "^1.0.0",
    "postcss-url": "^8.0.0",
    "postcss-viewport-units": "^0.1.6",
    "postcss-write-svg": "^3.0.1",
    "postcss-aspect-ratio-mini": "^1.0.1",

使用 vue-cli构建项目.

    vue create vue-vw

根据命令提示做相应的操作,

进入新创建好的项目目录,

    cd vue-vw

此时项目结构应该是这样的![１.png][1]

  [1]: https://www.xidaren.cn/usr/uploads/2019/02/3210706517.png

npm run serve运行起来就可以看到正常项目的页面了.

此时我们开始安装postcss插件
通过创建配置,选择在项目的根目录下创建.postcssrc.js还是在package.json里面配置postcss.

安装上述提到的插件

     npm install cssnano-preset-advanced postcss-cssnext postcss-import postcss-px-to-viewport postcss-url postcss-viewport-units postcss-write-svg postcss-aspect-ratio-mini -S

安装成功之后，在项目根目录下的package.json文件中，可以看到新安装的依赖包
然后配置postcss插件

    "postcss": {
    "plugins": {
    "autoprefixer": {},
    "postcss-import": {},
    "postcss-url": {},
    "postcss-aspect-ratio-mini": {},
    "postcss-write-svg": {
    "utf8": false
    },
    "postcss-cssnext": {},
    "postcss-px-to-viewport": {
    "viewportWidth": 750,
    "viewportHeight": 1334,
    "unitPrecision": 3,
    "viewportUnit": "vw",
    "selectorBlackList": [".ignore", ".hairlines"],
    "minPixelValue": 1,
    "mediaQuery": false
    },
    "cssnano": {
    "preset": "advanced",
    "autoprefixer": false,
    "postcss-zindex": false
    }
    }
    },
配置中几个关键参数

    "postcss-px-to-viewport": { viewportWidth: 750, // 视窗的宽度，对应的是我们设计稿的宽度，一般是750
    viewportHeight: 1334, // 视窗的高度，根据750设备的宽度来指定，一般指定1334，也可以不配置
    unitPrecision: 3, // 指定`px`转换为视窗单位值的小数位数（很多时候无法整除）
    viewportUnit: 'vw', // 指定需要转换成的视窗单位，建议使用vw
    selectorBlackList: ['.ignore', '.hairlines'], // 指定不转换为视窗单位的类，可以自定义，可以无限添加,建议定义一至两个通用的类名
    minPixelValue: 1, // 小于或等于`1px`不转换为视窗单位，你也可以设置为你想要的值
    mediaQuery: false // 允许在媒体查询中转换`px` }

然后启动项目,就会发现我们按照正常设计图写的px单位,已经被postcss插件转换为vw布局了!大家可以自己搭建项目试一试.