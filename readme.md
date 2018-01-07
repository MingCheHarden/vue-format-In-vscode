# \*.vue 文件格式化

规则：

1. template:

   能统一格式化就行~，没啥特别要求。
   vetur/js-beautify-html

2. script:

   我  希望能根据自定义的 eslint 规则，格式化 js 部分。

   （依赖 eslint autofix，一次 fix 不能修复所有的问题，多 fix 几次）

3. style:

   能统一格式化就行~，没啥特别要求。
   vscode 自带的 css 格式化

## Vscode

安装插件

1. vetur

   提供.vue 文件语法高亮；format 很烂... js 说是依赖 prettier，但是 eslintIntegration 对 script 区域无效... 难受 ⁄(⁄ ⁄•⁄ω⁄•⁄ ⁄)⁄

2. eslint

```js
{
    "env": {
        "browser": true,
        "commonjs": true,
        "es6": true,
        "node": true
    },
    "parserOptions": {
        "sourceType": "module"
    },
    "parser": "babel-eslint",
    "plugins": [
        "html"
    ],
    "extends": [
        "eslint:recommended",
    ],
    "rules": {
        "indent": [
            "warn",
            4,
            {
                "SwitchCase": 1
            }
        ],
        "semi": [
            "warn",
            "always"
        ],
        "no-console": [
            "error",
            {
                "allow": [
                    "warn",
                    "error"
                ]
            }
        ],
        //es6
        "prefer-template": "warn",
        "no-const-assign": "error",
        "prefer-rest-params": "warn",
        "no-duplicate-imports": [
            "error",
            {
                "includeExports": true
            }
        ],
        "no-var": "warn",
        "no-invalid-this": [
            "warn"
        ]
    }
    // "globals": {}
}
```

3. prettier

4. 用户配置

```json
{
  "vetur.format.defaultFormatter.js": "none",
  "vetur.format.defaultFormatter.ts": "none",
  "eslint.autoFixOnSave": true,
  "eslint.validate": [
    {
      "language": "vue", //** 这个比较重要 让vscode 可以识别出.vue文件。
      "autoFix": true
    }
  ],
  "vetur.format.defaultFormatter.html": "js-beautify-html"
}
```

按照上面的配置完以后，就可以很开心的编写.vue 文件了。由于  目前团队要开始写 weex，以后要长跟.vue 文件打交道，但是看到已经开始搞得小伙伴，格式化标准都不一样，很尴尬... ⁄(⁄ ⁄•⁄ω⁄•⁄ ⁄)⁄。想到前两天看 egg.js 文档中的一段话，觉得很有道理呢 ⁄(⁄ ⁄•⁄ω⁄•⁄ ⁄)⁄

```
Egg 奉行『约定优于配置』，按照一套统一的约定进行应用开发，团队内部采用这种方式可以减少开发人员的学习成本，开发人员不再是『钉子』，可以流动起来。没有约定的团队，沟通成本是非常高的，比如有人会按目录分栈而其他人按目录分功能，开发者认知不一致很容易犯错。但约定不等于扩展性差，相反 Egg 有很高的扩展性，可以按照团队的约定定制框架。使用 Loader 可以让框架根据不同环境定义默认配置，还可以覆盖 Egg 的默认约定。
```

https://eggjs.org/zh-cn/intro/index.html

以上，共勉~ O(∩_∩)O
