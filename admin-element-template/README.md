# 后台管理模板

> vue + element + axios + vue-store + mock

## Build Setup

```
bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build:prod

# build for UAT with minification -- 构建UAT环境
npm run build:uat

# build for SIT and view the bundle analyzer report -- 构建SIT环境
npm run build:sit
```

## eslint注释
```
module.exports = {
  //[0: pass, 1: warn, 2: error]
  // required to lint *.vue files
  root: true,
  env: {
    browser: true,
    commonjs: true,
    es6: true
  },
  parserOptions: {
    parser: 'babel-eslint',
    //语法支持
    ecmaVersion: 6,
    sourceType: 'module',
    ecmaFeatures: {
      jsx: true,
      experimentalObjectRestSpread: true
    }
  },
  extends: [
    // add more generic rulesets here, such as:
    // 'eslint:recommended',
    'plugin:vue/essential'
  ],
  plugins: ['vue', 'flowtype'],
  // add your custom rules here
  rules: {
    // allow paren-less arrow functions
    'arrow-parens': 0,
    // allow async-await
    'generator-star-spacing': 0,
    //禁止直接使用 Object.prototypes 的内置属性
    'no-prototype-builtins': 0,
    // allow debugger during development
    'no-debugger': process.env.NODE_ENV === 'production' ? 2 : 0,
    // 强制使用有效的 JSDoc 注释
    'valid-jsdoc': 0,
    'space-before-function-paren': 0,
    'no-inner-declarations': 0,
    'no-regex-spaces': 2, //禁止在正则表达式字面量中使用多个空格 /foo bar/
    'no-proto': 2, //禁止使用__proto__属性
    'no-return-assign': 1, //return 语句中不能有赋值表达式
    'no-shadow-restricted-names': 2, //严格模式中规定的限制标识符不能作为声明时的变量名使用
    'no-self-compare': 2, //不能比较自身
    'no-this-before-super': 0, //在调用super()之前不能使用this或super
    'no-extend-native': 0, // 可以使用扩展方法
    'no-const-assign': 2, //禁止修改const声明的变量
    'no-constant-condition': 2, //禁止在条件中使用常量表达式 if(true) if(1)
    'no-dupe-keys': 2, //在创建对象字面量时不允许键重复 {a:1,a:1}
    'no-dupe-args': 2, //函数参数不能重复
    'no-duplicate-case': 2, //switch中的case标签不能重复
    'no-duplicate-imports': 2, //每一个模块只能有一个import表达式
    'no-else-return': 2, //如果if语句里面有return,后面不能跟else语句
    'no-labels': 2, //禁止使用空label
    'no-extra-bind': 2, //禁止不必要的函数绑定
    'no-extra-boolean-cast': 2, //禁止不必要的bool转换
    'no-extra-parens': [2, 'all', { returnAssign: false, ignoreJSX: 'all' }], //禁止非必要的括号
    'no-extra-semi': 2, //禁止多余的分号
    'no-fallthrough': 1, //禁止switch穿透
    'no-func-assign': 2, //禁止重复的函数声明
    'no-implicit-coercion': 1, //禁止隐式转换
    'no-multi-spaces': 1, //不能用多余的空格
    'no-new-require': 2, //禁止使用new require
    'no-obj-calls': 2, //不能调用内置的全局对象，比如Math() JSON()
    'no-invalid-regexp': 2, //禁止无效的正则表达式
    'no-invalid-this': 0, //禁止无效的this，只能用在构造器，类，对象字面量
    'no-irregular-whitespace': 2, //不能有不规则的空格
    'no-lone-blocks': 2, //禁止不必要的嵌套块
    'no-iterator': 2, //禁止使用__iterator__ 属性
    'no-loop-func': 1, //禁止在循环中使用函数（如果没有引用外部变量不形成闭包就可以）
    'no-mixed-requires': [0, false], //声明时不能混用声明类型
    'no-mixed-spaces-and-tabs': [2, false], //禁止混用tab和空格
    'no-ex-assign': 2, //禁止给catch语句中的异常参数赋值
    'linebreak-style': [0, 'windows'], //换行风格
    'no-sparse-arrays': 2, //禁止稀疏数组， [1,,2]
    'no-unneeded-ternary': 2, //禁止不必要的嵌套 var isYes = answer === 1 ? true : false;
    'no-unreachable': 2, //不能有无法执行的代码,return, throw, continue, break后不要有代码
    'no-unused-expressions': 0, //禁止无用的表达式
    'no-unsafe-negation': 2, //关系运算符的左操作数不能否定，如 if (!key in obj) {}
    'no-unsafe-finally': 2, //finally语句块中不要有控制流语句,如 return 1
    'no-useless-call': 2, //禁止不必要的call和apply
    'no-useless-computed-key': 2, //在对象中避免使用不必要的计算属性键，如 const user = { ['name']: 'John Doe' }
    'no-useless-constructor': 2, //避免不必要的构造，比如空的构造函数
    'no-useless-escape': 0, //避免不必要的转义
    'no-useless-rename': 2, //导入、导出和解构赋值，不要赋相同的名字，如 import { config as config } from './config'
    'no-whitespace-before-property': 2, //属性前不要有空格，如 user .name
    'comma-dangle': [2, 'never'], //对象字面量项尾不能有逗号
    'comma-spacing': [2, { before: false, after: true }], //对象字面量中逗号的前后空格
    'comma-style': [2, 'last'], //逗号风格，换行时在行首还是行尾
    'no-redeclare': 2, //禁止重复声明变量
    'no-spaced-func': 2, //函数调用时 函数名与()之间不能有空格
    'no-unused-vars': [
      //不能有声明后未被使用的变量或参数
      2,
      {
        vars: 'all',
        // args: 'after-used'
        args: 'none'
      }
    ],
    'dot-notation': [
      //避免不必要的方括号
      0,
      {
        allowKeywords: true
      }
    ],
    'operator-linebreak': [2, 'after'], //换行时运算符在行尾还是行首
    'space-after-keywords': [0, 'always'], //关键字后面是否要空一格
    'space-infix-ops': 2, //中缀操作符周围要不要有空格
    'key-spacing': [
      0,
      {
        beforeColon: false,
        afterColon: true
      }
    ], //对象字面量中冒号的前后空格
    'brace-style': [1, '1tbs'], //大括号风格
    'func-call-spacing': [2, 'never'], //标示符和请求之间不能有空格
    'handle-callback-err': 0, //nodejs 处理错误
    'use-isnan': 2, //禁止比较时使用NaN，只能用isNaN()
    'valid-typeof': 2, //必须使用合法的typeof的值
    eqeqeq: 2, //必须使用全等
    'prefer-const': 0, //首选const
    'prefer-spread': 0, //首选展开运算
    'keyword-spacing': 2,
    'default-case': 2, //switch语句最后必须有default
    semi: [2, 'always'], //0:关闭，1:警告，2:异常
    indent: [
      'error',
      2,
      {
        SwitchCase: 1
      }
    ],
    'max-len': [
      //每行最长字符
      'error',
      {
        code: 80,
        ignoreComments: true,
        ignoreTrailingComments: true,
        ignoreUrls: true,
        ignoreStrings: true,
        ignoreTemplateLiterals: true,
        ignoreRegExpLiterals: true
      }
    ],
    quotes: ['error', 'single'], //单引号

    //link:https://github.com/vuejs/eslint-plugin-vue
    'vue/v-bind-style': 2, //v-bind 缩写模式
    'vue/v-on-style': 2, //v-on 缩写模式
    'vue/attribute-hyphenation': 2, //kebab-case (短横线分隔式)
    'vue/html-self-closing': 2, //标签自关闭
    'vue/max-attributes-per-line': [
      //多属性换行，第一个属性例外
      2,
      {
        singleline: 1,
        multiline: {
          max: 1,
          allowFirstLine: true
        }
      }
    ],
    'vue/mustache-interpolation-spacing': 2, //{{ keyword }}
    'vue/name-property-casing': [2, 'kebab-case'], //组件 name 属性必须使用 kebab-case 短横线
    'vue/no-async-in-computed-properties': 2, //computed 计算属性不能使用异步
    'vue/no-parsing-error': 2, //检测编译错误
    'vue/no-shared-component-data': 2, //data() { return {} } When using the data property on a component (i.e. anywhere except on new Vue), the value must be a function that returns an object.
    'vue/no-template-key': 2, //template 标签不允许有key
    'vue/no-textarea-mustache': 2, //textarea 请使用 v-model
    'vue/no-unused-vars': 2, //v-for 指令不允许存在未使用的变量声明
    'vue/require-v-for-key': 2, //v-for 必须指定 key
    'vue/require-valid-default-prop': 2, //校验 props 属性的默认值
    'vue/return-in-computed-property': 2, //computed 计算属性必须存在 return
    'vue/valid-v-bind': 2, //校验 bind 的值是否有效
    'vue/valid-v-if': 2, //校验 v-if 表达式
    'vue/valid-v-else-if': 2, //校验 v-else-if
    'vue/valid-v-else': 2, //v-else 后不能跟表达式
    'vue/valid-v-model': 2, //校验 v-model
    'vue/this-in-template': 2, //template 中不允许出现 this
    'vue/html-quotes': 2, //html节点必须使用双引号

    //link:https://github.com/mvpleung/eslint-plugin-flowtype
    'flowtype/boolean-style': [
      //类型注解中布尔值使用boolean还是bool
      2,
      'boolean'
    ],
    'flowtype/define-flow-type': 1, //将类型注解标记为已定义，no-undef的检查中不会出现报错
    'flowtype/delimiter-dangle': [
      //是否在对象和元组注释中强制使用尾随逗号
      2,
      'never'
    ],
    'flowtype/generic-spacing': [
      //泛型对象的尖括号中类型前后的空格规范
      2,
      'never'
    ],
    'flowtype/no-dupe-keys': 2, //object类型的定义中是否有重复的属性值
    'flowtype/object-type-delimiter': [
      //Object类型定义中，属性之前分割符为逗号
      2,
      'comma'
    ],
    'flowtype/no-primitive-constructor-types': 2, //禁止使用原生的类型，如 Number String Array ,使用 number string array 代替
    'flowtype/no-types-missing-file-annotation': 2, //使用类型注解的地方不能缺少 @flow
    'flowtype/no-weak-types': 2, //是否可以使用弱类型any、Object、Function
    'flowtype/require-parameter-type': 2, //函数的参数是否需要类型注解
    'flowtype/require-return-type': [
      //函数返回值是否需要类型注解
      2,
      'always',
      {
        annotateUndefined: 'never'
      }
    ],
    'flowtype/require-valid-file-annotation': 0, //文件开头@flow的写法
    'flowtype/semi': [2, 'always'], //使用type自定义类型语句结尾是否需要分号结尾
    'flowtype/space-after-type-colon': [
      //类型注解冒号后是否有空格
      2,
      'always'
    ],
    'flowtype/space-before-generic-bracket': [
      //类型注解尖括号前是否有空格
      2,
      'never'
    ],
    'flowtype/space-before-type-colon': [
      //类型注解冒号前是否有空格
      2,
      'never'
    ],
    'flowtype/type-id-match': 0, //自定义 type 类型
    'flowtype/union-intersection-spacing': [
      //管道操作符规范
      2,
      'always'
    ],
    'flowtype/use-flow-type': 1 //将通过declare定义的自定义类型标记为已经被使用过，no-unused-vars的检查中不会出现报错
  },
  settings: {
    flowtype: {
      onlyFilesWithFlowAnnotation: true //是否仅检查有 @flow /* @flow */ 注解的文件
    }
  }
};
```
## vsCode配置

```
{
  "emmet.syntaxProfiles": {
    "vue-html": "html",
    "vue": ["css", "html", "scss", "less"]
  },
  "eslint.autoFixOnSave": true,
  "eslint.options": {
    "plugins": ["vue"]
  },
  "eslint.validate": [
    "javascript",
    "javascriptreact",
    {
      "language": "vue",
      "autoFix": true
    },
    {
      "language": "html",
      "autoFix": true
    }
  ],
  "prettier.singleQuote": true,
  "prettier.semi": true,
  "prettier.printWidth": 80,
  "prettier.eslintIntegration": true,
  "vetur.format.defaultFormatter.html": "js-beautify-html",
  "vetur.format.defaultFormatterOptions": {
    "js-beautify-html": {
      "wrap_attributes": "force",
      "wrap_line_length": 80
    }
  }
}
```