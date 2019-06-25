# vscode编辑器适应ESLint校验规则
##### vscode在写vue项目时，很多地方与eslint校验规则不统一，从而产生报错，进行下面操作让编辑器适应eslint规则
1. 打开VSCode扩展面板并搜索ESLint扩展，然后点击安装
2. 找到文件 ——> 首选项 ——> 设置
3. 在右侧的用户设置中粘贴下面代码
```
"editor.tabSize": 2,     // 一个Tab键的缩放长度，原始值为4，eslint规则为2
"eslint.autoFixOnSave": true,  // 每次保存的时候将代码按eslint格式进行修复
"eslint.validate": [       // 添加vue支持
    "javascript",
    "javascriptreact",
    {
        "language": "html",
        "autoFix": true
    },
    {
        "language": "vue",
        "autoFix": true
    }
  ]
```
##### 这样ctry+s保存代码时，编辑器会自动按照eslint规则来格式化代码
##### 不过有个缺点，代码复杂时save不会一次性的修改所有的格式问题，需要进行多次save。
by-王柳