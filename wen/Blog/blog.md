# 关于IIIStudio页

这是一个HTML，一个使用json的页面。

## 网站结构 wen.json

```
[
  {
    "biaoti": "这是一个测试",
    "wenzhang": "./wen/GitHub/GitHub.md"
  },
  {
    "biaoti": "关于IIIStudio",
    "wenzhang": "./wen/Blog/blog.md"
  },
  {
    "biaoti": "AVGmd 文本冒险游戏",
    "wenzhang": "https://iiistudio.github.io/AVGmd/README.md"
  },
  {
    "biaoti": "Web Notepad",
    "wenzhang": "https://raw.githubusercontent.com/IIIStudio/WebNotepad/master/README.md"
  }
]
```
可以使用文件夹里面放md文件，那么文件夹就是便签，自动获取，如果是链接github.io会自动识别为GitHub标签，可以直接使用链接的md，里面的图片地址也会转换到github.io。

> 我原本的计划是自动化，只需要ide内编辑，然后提交后自动生成wen.json。也考虑过CNB+EdgeOne Pages，但是我觉得简单点好！我现在如果是添加GitHub，那么我只需要修改wen.json就行了。
 
但是我觉得这个并不适合做博客（seo）（类似memos），只适合展示，我一开始的设想是作为笔记使用的，前端本地笔记。我想想笔记太多了，然后改成这样的了，方便我把项目都放在这里面。

### CNB+EdgeOne Pages

没玩过EdgeOne Pages，说下我的逻辑吧，如果文章是在cnb ide编辑，那么可以写一个py生成wen.json，修改.cnb.yml。

python环境

```
$:
  vscode:
    - docker:
        # 指定云原生开发启动时的基础镜像为当前镜像
        image: docker.cnb.cool/ohao/learn/python:3.12.11
      services:
        - vscode
        - docker
```
自动上传。
```
      # 开发环境在销毁之前执行的任务
      endStages:
        - name: sync code
          script: git add . && git commit -m "自动提交：$(date "+%Y-%m-%d %H:%M:%S")" && git push
```
EdgeOne Pages 更新就不清楚了！
