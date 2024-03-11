---
title: Icarus主题的一些常用配置
toc: true
date: 2024-03-10 05:44:43
tags: [icarus]
---
> 常见的一些配置见_config.icarus.yml，英文不差都能看懂，或者去看icarus文档。本文主要就是一些网上很少的配置。
<!-- more -->



Icarus: 4.0.0

### 文章页面两栏布局

在 `_config.icarus.yml`目录下，创建 `_config.post.yml`文件，该文件内容与 `_config.icarus.yml`文件一样，用于单独加载post界面布局。注意，双栏需要将widgets内容的position都设置为同一边。

```xml
# 单独文章界面布局
widgets:
    # 个人信息
    -
        position: left
        type: profile
        author: zhaommmmomo
        author_title: fahaxiki!
        location: Yantai,China
        avatar: /img/logo.jpg
        avatar_rounded: false
        follow_link: 'https://zhaommmmomo.cn'
        social_links:
            Github:
                icon: fab fa-github
                url: 'https://github.com/zhaommmmomo'
    # 文章目录
    -
        position: left
        type: toc
        # 目录序号
        index: true
# 侧边栏是否固定
sidebar:
    left:
        sticky: false
    right:
        sticky: false
```

### 增加两栏布局下文章的宽度
```jsx
# layout/layout.jsx
module.exports = class extends Component {
    render() {
        ......
            <Head site={site} config={config} helper={helper} page={page} />
        
            # <body class={`is-${columnCount}-column`}>	修改为下面一行
            <body class={`is-3-column`}>
                ......
                                # 'is-8-tablet is-8-desktop is-8-widescreen': columnCount === 2	
            					# 修改为下面一行
                                'is-8-tablet is-8-desktop is-9-widescreen': columnCount === 2,
                                'is-8-tablet is-8-desktop is-6-widescreen': columnCount === 3
                            })} dangerouslySetInnerHTML={{ __html: body }}></div>
		......
    }
};

# layout/common/widgets.jsx
function getColumnSizeClass(columnCount) {
    switch (columnCount) {
        case 2:
            # return 'is-4-tablet is-4-desktop is-4-widescreen';	# 修改为下面一行
            return 'is-4-tablet is-4-desktop is-3-widescreen';
        case 3:
            return 'is-4-tablet is-4-desktop is-3-widescreen';
    }
}
```

### 只固定目录
```js
# source/js/main.js
const $toc = $('#toc');
if ($toc.length > 0) {
    $toc.addClass('column-left is-sticky');		# 添加
    ......
}
```
```styl
# include/style/widget.styl 添加下面
#toc
    max-height: calc(100vh - 22px)
    overflow-y: scroll
```