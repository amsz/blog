---
title: 你好
date: 2016-05-13 11:39:27
tags:
permalink: hello
---

你好，又建了一个Blog！

<!-- more -->

## 环境

```shell
hexo init blog && cd blog && rm -fr source/
git clone git@github.com:amsz/blog.git && mv blog source
git clone https://github.com/MOxFIVE/hexo-theme-yelee.git themes/yelee
npm install hexo-deployer-git --save
```

## 配置

vi _config.yml

```yaml
deploy:
  type: git
  repo: git@github.com:amsz/amsz.github.io.git
```

vi themes/yelee/_config.yml

```yaml
background_image: 1
animate: false
share: 
  on: false

```

vi themes/yelee/layout/_partial/post/nav.ejs

```html
<% if ((post.original != false && !is_page() && theme.copyright) || post.original){ %>
    <div class="copyright">
        <p><span><%= __('copyright_info.date') %>:</span><%= post.date.format("YYYY-MM-DD, HH:mm:ss") %></p>
        <p><span><%= __('copyright_info.updated') %>:</span><%= post.updated.format("YYYY-MM-DD, HH:mm:ss") %></p>
        <p>
            <span><%= __('copyright_info.url') %>:</span><a class="post-url" href="<%= url_for(post.path) %>" title="<%= post.title %>"><%= post.permalink %></a>
            <span class="copy-path" data-clipboard-text="<%= __('copyright_info.from') %> <%= post.permalink %>　　<%= __('copyright_info.by') %> <%=theme.author%>" title="<%= __('tooltip.copyPath') %>"><i class="fa fa-clipboard"></i></span>
            <script> var clipboard = new Clipboard('.copy-path'); </script>
        </p>
        <p>
            <span>Source:</span><i class="fa fa-github"></i>
            <a href="https://github.com/amsz/blog/<%= post.source %>" title="查看原始文本" target = "_blank"> <%= post.source %></a>
        </p>
    </div>
<% } %>
```

## 发布

`hexo d`


