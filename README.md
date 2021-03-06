# React Redux 前端研发品质实践

[![codebeat badge](https://codebeat.co/badges/5e895c71-88f8-4600-b522-ad9c5fd0214e)](https://codebeat.co/projects/github-com-tingge-ava-testing-master)
[![Build Status](https://travis-ci.org/TingGe/ava-testing.svg?branch=master)](https://travis-ci.org/TingGe/ava-testing) [![Coverage Status](https://coveralls.io/repos/github/TingGe/ava-testing/badge.svg)](https://coveralls.io/github/TingGe/ava-testing) [![CircleCI](https://circleci.com/gh/TingGe/ava-testing/tree/master.svg?style=svg)](https://circleci.com/gh/TingGe/ava-testing/tree/master)
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2FTingGe%2Fava-testing.svg?type=shield)](https://app.fossa.io/projects/git%2Bgithub.com%2FTingGe%2Fava-testing?ref=badge_shield)

![](https://raw.githubusercontent.com/TingGe/ava-testing/master/assets/image/testing-structure.png)

> 最佳适用于 `TypeScript + Scss/Less + React + Redux +  React Dom + React Router + React Thunk` 技术栈的前端。

一个针对 TypScript 源码的 React Redux 项目的模版项目。

- 采用  React 和 TypeScript；
- Redux 做状态管理；
- 代码静态审查：husky + lint-staged + tslint + prettier + stylelint + imagemin-lint-staged；
- 测试包括：单元测试、覆盖率测试、接入集成测试服务、e2e 测试和 watch 模式。

### 代码静态审查

1. Git hook：husky + lint-staged
2. ts 和 tsx 合规检查和修复：tslint + prettier
3. scss 和 css 合规检查和修复：stylelint
4. 图片和 svg 等压缩：imagemin-lint-staged

#### prettier 执行方式

方式一：

VS Code 的 [prettier-vscode 插件](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)提示

方式二：

借助 [husky](https://github.com/typicode/husky) 在代码 commit 时代码审查（自动修复和提示）

方式三：

根目录执行以下命令（自动修复和提示）

```bash
npx prettier --write './src/**/*.{ts,tsx,js,scss}'
```

#### tslint 执行方式

方式一：

VS Code 的 [vscode-tslint 插件](https://marketplace.visualstudio.com/items?itemName=eg2.tslint)提示

方式二：

借助 [husky](https://github.com/typicode/husky) 在代码 commit 时代码审查（自动修复和提示）

方式三：

根目录执行以下命令（自动修复和提示）

```bash
tslint -c tslint.json --fix './src/**/*.{js,ts,tsx}'
```

#### stylelint 执行方式

方式一：

VS Code 的 [stylelint 插件](https://marketplace.visualstudio.com/items?itemName=shinnn.stylelint)提示

方式二：

借助 [husky](https://github.com/typicode/husky) 在代码 commit 时代码审查（自动修复和提示）

方式三：

根目录执行以下命令（自动修复和提示）

```Bash
npx stylelint -s scss --fix --stdin-filename ./(src|docs)/**/*.scss 
```

## 测试

#### 关于是否需要自动化测试？

可参考标准

- 自动化收益 = 迭代次数 * 全手动执行成本 - 首次自动化成本 - 维护次数 * 维护成本

本项目采用的自动化测试技术方案

1. React Redux 测试：typescript + ava + enzyme(sinon、redux-mock-store) 组合
2. 覆盖率：nyc
3. 集成测试： [UI Recorder](https://github.com/alibaba/uirecorder) 或 Nightwatch


### 组件：React  + Redux

支持 watch 模式；原子测试

1. actions 测试
2. reducer 测试
3. select 测试
4. React + Redux 测试
5. 输出报告

### 覆盖率

- nyc

### E2E 测试

> 可独立于项目代码。支持本地运行、手工触发、定时触发、发布流程触发四种方式，实现业务流程的快速自动回归测试。

1. 跨端（多浏览器兼容）自动化测试及报告： [UI Recorder](https://github.com/alibaba/uirecorder)、[F2etest](https://github.com/alibaba/f2etest) 
2. 测试脚本：测试代码的 Github 仓库
3. 持续集成（CI）服务、用例、测试计划、任务分派和缺陷管理：Aone
4. 全球化（G11N）自动测试报告：ACGT
5. 业务异常报告：智能质量引擎

## 对比的一些工具

- AVA： 相对于 Mocha 执行更快，测试环境隔离、支持原子测试；相对于 Jest 组合更加灵活；
- Mocha + Chai：相对较为成熟；
- Jest：[Create React App](https://github.com/facebookincubator/create-react-app) 、 [Microsoft/TypeScript-React-Starter](Microsoft/TypeScript-React-Starter) 和 [Ant Design](https://github.com/ant-design/ant-design-pro) 中推荐方案，内置断言、测试覆盖率工具，是个一体化方案、开箱即用。



项目接入持续集成在多人开发同一个仓库时候能起到很大的用途，每次push都能自动触发测试，测试没过会发生告警。

如果需求采用 Issues+Merge Request 来管理，每个需求一个Issue + 一个分支，开发完成后提交 Merge Request ，由项目 Owner 负责合并，项目质量将更有保障。

| 级别    | 类别           | 作用                                           | 选型                                                   | 同类                                                         |
| ------- | -------------- | ---------------------------------------------- | ------------------------------------------------------ | ------------------------------------------------------------ |
| -       | 代码审查       | 统一团队代码风格                               | [Prettier](https://github.com/prettier/prettier)       |                                                              |
| -       | 静态代码审查   | 现代 CSS 格式验证工具                          | [Stylelint](https://github.com/stylelint/stylelint)    |                                                              |
| -       | 静态代码审查   | TypeScript 格式验证工具                        | [Tslint](https://palantir.github.io/tslint/)           |                                                              |
| 单元    | 测试框架       | test runner, snapshots, display, and watch     | [AVA](https://github.com/avajs/ava)                    | Jest, Wallaby.js, Mocha                                      |
| 单元    | 断言库         | assertions functions                           | [enzyme](https://github.com/airbnb/enzyme)             | [Unexpected](https://github.com/unexpectedjs/unexpected), Chai |
| 单元    | Mock工具       | mocks, spies, and stubs                        | [sinon](http://sinonjs.org/)                           | [testdouble.js](https://github.com/testdouble/testdouble.js) |
| 单元    | 测试覆盖率工具 | code coverage                                  | [nyc](https://github.com/istanbuljs/nyc)               | [Coveralls](https://coveralls.io/)                           |
| 单元    | 模拟工具       | 模拟浏览器 dom                                 | [JsDom](https://github.com/jsdom/jsdom)                |                                                              |
| -       | -              | 持续集成服务                                   | [Travis](https://travis-ci.org/)，                     | [CircleCI](https://circleci.com/), [Jenkins](https://jenkins.io/) |
| 端到端  |                | e2e                                            | [UI Recorder](https://github.com/alibaba/uirecorder) + | [Protractor](http://www.protractortest.org/), [Casper](http://casperjs.org/), testcafe, [DalekJS](https://github.com/dalekjs), [Nightwatch](http://nightwatchjs.org/) |
| -       | -              | -                                              | -                                                      | -                                                            |
| ChatOps | 自动化运维     | 查看各项指标；自动发布；发布报告等             | [Hubot](https://hubot.github.com/)                     | Lita,Err，[钉钉机器人](https://open-doc.dingtalk.com/docs/doc.htm?treeId=257&articleId=105735&docType=1) |
| -       | 合规审查       | 开源代码合规化；自动追踪开源代码的授权许可协议 | [Fossa](https://fossa.io/)                             |                                                              |

## 踩过的坑

- package.json 中包依赖版本锁定管理：不要忽略 warning，关注 [Enzyme Working with React 16](http://airbnb.io/enzyme/docs/installation/react-16.html) 等配置文档
- ignore-styles 忽略样式和资源文件：需要 hook node 的 require， 因此将 setup.ts 改成 setup.js

### API Docs

- AVA: https://github.com/avajs/ava#api
- Enzyme:  https://github.com/airbnb/enzyme/tree/master/docs/api
- Sinon：http://sinonjs.org/releases/v4.1.2/

## 参考

- [JavaScript 单元测试框架大乱斗：Jasmine、Mocha、AVA、Tape 以及 Jest](https://raygun.com/blog/javascript-unit-testing-frameworks/)
- [基于 JavaScript 的 Web 应用的端到端测试工具对比](https://mo.github.io/2017/07/20/javascript-e2e-integration-testing.html)
- [别再加端到端集成测试了，快换契约测试吧](http://insights.thoughtworks.cn/contract-test/)
- [从工程化角度讨论如何快速构建可靠React组件](https://github.com/lcxfs1991/blog/issues/18)
- [How to Test a React and Redux Application ](https://semaphoreci.com/community/tutorials/getting-started-with-create-react-app-and-ava)
- [How to prevent “Property '…' does not exist on type 'Global'” with jsdom and typescript?](https://stackoverflow.com/questions/40743131/how-to-prevent-property-does-not-exist-on-type-global-with-jsdom-and-t)
- [Using enzyme with JSDOM](http://airbnb.io/enzyme/docs/guides/jsdom.html)
- [Antd Pro UI Test](https://pro.ant.design/docs/ui-test#单元测试)
- [Automated React Component Testing with Jest](https://www.distelli.com/docs/tutorials/test-your-react-component-with-jest/)



## 重点解答

1. 常用组合和现在组合优缺点；
2. 各组合适用的应用场景；
3. 测试的开发体验。

### 未来的可能

1. 与测试团队整体测试的接入；
2. 对开发者更加友好，降低用例的创建和维护成本；
3. 从投入产出角度，减少人工干预环节。

## 许可 License

[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2FTingGe%2Fava-testing.svg?type=large)](https://app.fossa.io/projects/git%2Bgithub.com%2FTingGe%2Fava-testing?ref=badge_large)