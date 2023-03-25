---
# try also 'default' to start simple
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://source.unsplash.com/collection/94734566/1920x1080
# apply any windi css classes to the current slide
class: 'text-center'
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# show line numbers in code blocks
lineNumbers: false
# some information about the slides, markdown enabled
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# persist drawings in exports and build
drawings:
  persist: false
# page transition
transition: slide-left
# use UnoCSS
css: unocss
---

# 简谈 laC：基础设施即代码

一起聊一聊 IaC 这些年的发展历史，以及 laC 的未来。

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---
transition: fade-out
---

# 简谈 laC：基础设施即代码?

这次分享将分为几个部分进行

- 定义 IaC 的核心特征
- 了解一下 IaC 的过去
- 看看 IaC 的现在
- 吐槽一下 IaC

---
transition: fade-out
layout: image-right
image: https://user-images.githubusercontent.com/7054676/227723424-eee4bcbc-564c-4b1c-9b91-8a7222b7d365.png
---

# 自我介绍一下

可能大家已经熟悉我了，不过还是做以下自我介绍

- 曾经的 Manjusaka，现在的 Nadeshiko Manju
- 一个 SRE，一个 FreeLancer
- Python/Go/C/Lua 选手，Rust 学习中
- 一直在做基础设施相关的工作
- 捕蛇者说主播
- 微软 MVP
- [GitHub](https://github.com/Zheaoli) / [Twitter: Nadeshiko Manju](https://twitter.com/Manjusaka_Lee)
- 摇曳露营是世界上最好看的动漫，抚子赛高

---
transition: fade-out
---

# IaC 的几个核心特征

1. 最终的产物是 machine readable 的的产物。可能是一份代码，也可能是一份配制文件
2. 基于 machine readable 的产物，可以进一步依赖已有的 VCS 系统（SVN，Git）等做版本管理
3. 基于 machine readable 的产物，可以进一步依赖已有的 CI/CD 系统（Jenkins，Travis CI）等做持续集成/持续交付
4. 状态的一致性，或者称为幂等性。即理论上来讲，基于同样一份 Code，同一套参数构建出的产物，其最终的行为应该是一致的

---

# IaC 诞生的背景

在千禧年之后，互联网世界迭代的速度愈发的快速，这个时候传统的手工式的维护面临着几个问题

1. 交互式变更所引入的人的因素太大，导致了变更的不可控性
2. 人工变更面对愈发快速的 Infra 迭代力有不逮
3. 交互式的变更导致管控的难做，让版本控制之类的手段变为空谈

<br>

这意味着我们需要利用一种已知复杂度的手段来解决未知复杂度的问题

---
transition: fade-out
layout: image-right
image: https://user-images.githubusercontent.com/7054676/227724844-9f3dc775-611a-403f-a7d7-7b66fd67c79c.png
---

# 最古早的 IaC

其实右图能说明一些东西

---
preload: false
---

# Animations

Animations are powered by [@vueuse/motion](https://motion.vueuse.org/).

```html
<div
  v-motion
  :initial="{ x: -80 }"
  :enter="{ x: 0 }">
  Slidev
</div>
```

<div class="w-60 relative mt-6">
  <div class="relative w-40 h-40">
    <img
      v-motion
      :initial="{ x: 800, y: -100, scale: 1.5, rotate: -50 }"
      :enter="final"
      class="absolute top-0 left-0 right-0 bottom-0"
      src="https://sli.dev/logo-square.png"
    />
    <img
      v-motion
      :initial="{ y: 500, x: -100, scale: 2 }"
      :enter="final"
      class="absolute top-0 left-0 right-0 bottom-0"
      src="https://sli.dev/logo-circle.png"
    />
    <img
      v-motion
      :initial="{ x: 600, y: 400, scale: 2, rotate: 100 }"
      :enter="final"
      class="absolute top-0 left-0 right-0 bottom-0"
      src="https://sli.dev/logo-triangle.png"
    />
  </div>

  <div
    class="text-5xl absolute top-14 left-40 text-[#2B90B6] -z-1"
    v-motion
    :initial="{ x: -80, opacity: 0}"
    :enter="{ x: 0, opacity: 1, transition: { delay: 2000, duration: 1000 } }">
    Slidev
  </div>
</div>

<!-- vue script setup scripts can be directly used in markdown, and will only affects current page -->
<script setup lang="ts">
const final = {
  x: 0,
  y: 0,
  rotate: 0,
  scale: 1,
  transition: {
    type: 'spring',
    damping: 10,
    stiffness: 20,
    mass: 2
  }
}
</script>

<div
  v-motion
  :initial="{ x:35, y: 40, opacity: 0}"
  :enter="{ y: 0, opacity: 1, transition: { delay: 3500 } }">

[Learn More](https://sli.dev/guide/animations.html#motion)

</div>

---

# LaTeX

LaTeX is supported out-of-box powered by [KaTeX](https://katex.org/).

<br>

Inline $\sqrt{3x-1}+(1+x)^2$

Block
$$
\begin{array}{c}

\nabla \times \vec{\mathbf{B}} -\, \frac1c\, \frac{\partial\vec{\mathbf{E}}}{\partial t} &
= \frac{4\pi}{c}\vec{\mathbf{j}}    \nabla \cdot \vec{\mathbf{E}} & = 4 \pi \rho \\

\nabla \times \vec{\mathbf{E}}\, +\, \frac1c\, \frac{\partial\vec{\mathbf{B}}}{\partial t} & = \vec{\mathbf{0}} \\

\nabla \cdot \vec{\mathbf{B}} & = 0

\end{array}
$$

<br>

[Learn more](https://sli.dev/guide/syntax#latex)

---

# Diagrams

You can create diagrams / graphs from textual descriptions, directly in your Markdown.

<div class="grid grid-cols-3 gap-10 pt-4 -mb-6">

```mermaid {scale: 0.5}
sequenceDiagram
    Alice->John: Hello John, how are you?
    Note over Alice,John: A typical interaction
```

```mermaid {theme: 'neutral', scale: 0.8}
graph TD
B[Text] --> C{Decision}
C -->|One| D[Result 1]
C -->|Two| E[Result 2]
```

```plantuml {scale: 0.7}
@startuml

package "Some Group" {
  HTTP - [First Component]
  [Another Component]
}

node "Other Groups" {
  FTP - [Second Component]
  [First Component] --> FTP
}

cloud {
  [Example 1]
}


database "MySql" {
  folder "This is my folder" {
    [Folder 3]
  }
  frame "Foo" {
    [Frame 4]
  }
}


[Another Component] --> [Example 1]
[Example 1] --> [Folder 3]
[Folder 3] --> [Frame 4]

@enduml
```

</div>

[Learn More](https://sli.dev/guide/syntax.html#diagrams)

---
src: ./pages/multiple-entries.md
hide: false
---

---
layout: center
class: text-center
---

# Learn More

[Documentations](https://sli.dev) · [GitHub](https://github.com/slidevjs/slidev) · [Showcases](https://sli.dev/showcases.html)
