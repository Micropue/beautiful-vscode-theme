# beautiful-vscode-theme

**更好看的vscode 主题搭配与custom-css and js**\
原版的vscode过于臃肿，所以我使用多个插件以及搭配着custom css自定义了样式表于javascript脚本。
>[!TIP]
>1.拥有更好看的command栏\
>2.更好的代码呈现效果\
>3.让你体验拥有动效的vscode\
>4.即使在部分时候没有办法使用菜单栏调出`文件资源管理器、插件...`，但你也可以使用快捷键进行操作。


**预览效果**\
![预览效果](https://github.com/Micropue/beautiful-vscode-theme/blob/9b2985ea43bf412ecacb3b1758266bf48a849435/%E6%88%AA%E5%B1%8F2024-11-01%2009.57.24.png)\
![](https://github.com/Micropue/beautiful-vscode-theme/blob/9b2985ea43bf412ecacb3b1758266bf48a849435/%E6%88%AA%E5%B1%8F2024-11-01%2009.59.27.png)
![](https://github.com/Micropue/beautiful-vscode-theme/blob/9b2985ea43bf412ecacb3b1758266bf48a849435/%E6%88%AA%E5%B1%8F2024-11-01%2010.00.19.png)
**插件：**
>1.[Apc customize UI++](https://marketplace.visualstudio.com/items?itemName=drcika.apc-extension)\
>2.[Custom css and js Loadar](https://marketplace.visualstudio.com/items?itemName=be5invis.vscode-custom-css)\
>3.[React theme](https://marketplace.visualstudio.com/items?itemName=mikaelkristiansson87.react-theme-vscode)\
>4.[Trailing Spaces](https://marketplace.visualstudio.com/items?itemName=shardulm94.trailing-spaces) 显示多余空格\
>5.[indent-rainbow](https://marketplace.visualstudio.com/items?itemName=oderwat.indent-rainbow)

**方法与配置**\

1.打开菜单栏中查看面板，在外观中只保留`主侧边栏`，并将主侧栏移动到右侧：![如图](https://github.com/Micropue/beautiful-vscode-theme/blob/a842370a8c42752c5cc1a891281c7dd5ab2513e1/%E6%88%AA%E5%B1%8F2024-11-01%2010.34.47.png)\
2.在command 输入框中键入`>aimations` 在下面的提示中选择Install Animations\
3.设置颜色主题：React Theme\
4.打开setting.json 中找到<pre>"vscode_custom_css.imports": [],</pre>如果没有就添加上。\添加一个css 和js 文件。拷贝下面的代码并粘贴进去
**css**
<pre>.quick-input-widget {
    transform: translateY(-50%) !important;
    top: 50% !important;
    box-shadow: 0px 8px 20px rgba(0, 0, 0, .45) !important;
    padding: 10px 10px 18px 10px !important;
    background-image: linear-gradient(#3c3c50 0%, #2a2b38 100%) !important;
    backdrop-filter: blur(3px) !important;
    border-radius: 20px !important;
}
#quickInputWidget-bg{
    width:100%;
    height:100vh;
    position: fixed;
    z-index: 2549;
    backdrop-filter: blur(10px);
    top:0;
    left:0;
    pointer-events: none;
}
.monaco-action-bar:not(.monaco-workbench .part.editor>.content .editor-group-container>.title .tabs-container>.tab>.tab-actions>.monaco-action-bar){
    display: none !important;
}
.monaco-list-rows{
    background-color: transparent !important;
}
.quick-input-filter .monaco-inputbox {
    border-radius: 12px !important;
    padding: 8px !important;
    border: none !important;
    background-color: rgba(34, 34, 34, .40) !important;
    font-size: 14px !important;
    margin-bottom: 16px !important;
}
.monaco-scrollable-element .shadow{
    box-shadow: none !important;
}
.slider{
    display: none !important;
}
.decorationsOverviewRuler{
    display: none !important;
}
.monaco-editor .cursors-layer .cursor{
    background-color: darkturquoise !important;
}
</pre>
**javascript**
<pre>document.addEventListener("DOMContentLoaded", () => {
    setInterval(() => {
        const commandBar = document.querySelector(".quick-input-widget")
        if (commandBar) {
            const ele = document.createElement("div")
            ele.id = "quickInputWidget-bg"
            if (commandBar.style.display !== "none") {
                if (!document.getElementById("quickInputWidget-bg")) {
                    commandBar.before(ele)
                }else{
                    document.getElementById("quickInputWidget-bg").style.display = "inline-block"
                }
            } else if (commandBar.style.display === "none") {
                document.getElementById("quickInputWidget-bg").style.display = "none"
            }
        }
    }, 1)
})</pre>
**最后使用命令`>enable Custom css and Js`即可**\
**如果提示已损坏剋直接忽略。**
