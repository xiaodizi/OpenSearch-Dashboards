<img src="https://opensearch.org/assets/brand/SVG/Logo/opensearch_dashboards_logo_darkmode.svg" height="64px"/>

- [Welcome!](#welcome)
- [Project Resources](#project-resources)
- [Code of Conduct](#code-of-conduct)
- [License](#license)
- [Copyright](#copyright)


## 我都干了啥？

其实，这个项目的文档已经很完善了,我也没改啥.就是在编译过程中遇到一些坑。记录一下吧！

其他的，建议还是看官网的资料。

这个分支完全是基于3.0.0的官网版本。使用请注意版本号。

### 1、无法下载geckodriver

这是碰到第一个比较坑的问题，不知道为什么，一直在下载 geckodriver 的时候失败。尝试过修改镜像源为中国的，但是都不行。
最后是设置了一个环境变量才解决的这个问题。
```
npm config set geckodriver_cdnurl https://repo.huaweicloud.com/geckodriver/
npm install geckodriver
```

### 2、npm包安装失败

我在编译的过程中，碰到了很多次npm包安装失败的问题，除了上边的那个包，其他都是手工安装成功的。执行：
```shell
npm install 包名
```

### 3、编译打包的时候无法下载node
这应该是整个项目，我唯一修改了源码的地方。

忘了之前是啥域名了，反正一直下载不下来。

后来我给修改为`https://nodejs.org/dist/v14.21.3/node-v14.21.3-win-x64.zip `

就很顺利了

### 4、运行源码

先拉取依赖
```shell
yarn osd bootstrap
```

再运行，当然前提是配置文件要配置好
```shell
yarn start
```

配置文件 就是 `config/opensearch_dashboards.yml`

### 5、关于配置

官网给出了，如下配置项：
```shell
opensearch.hosts: ["https://localhost:9200"]
opensearch.username: "admin" # Default username on the docker image
opensearch.password: "admin" # Default password on the docker image
opensearch.ssl.verificationMode: none
```

也许是习惯了kibana的配置，我也就配置了
```shell
opensearch.hosts: ["http://127.0.0.1:9200"]
server.name: "Opensearch"
server.port: 5601
```

### 6、关于打包编译

用官网的就好
mac 平台使用
```shell
yarn build-platform --darwin
```

其他平台根据情况修改参数：
```shell
darwin (builds Darwin x64)
linux (builds Linux x64)
linux-arm (builds Linux ARM64).
windows (builds Windows x64)
```


## Welcome

OpenSearch Dashboards is an open source search and analytics visualization. We aim to be the best community-driven platform and provide all the contributors a great open source experience.

Feel free to take a look at what the community has been up to, and then head over to the [Project Board](https://github.com/opensearch-project/OpenSearch-Dashboards/projects) to track release targets, or jump in and [start opening issues](https://github.com/opensearch-project/OpenSearch-Dashboards/issues/new/choose), [set up your development environment](DEVELOPER_GUIDE.md#getting-started), or [start contributing](CONTRIBUTING.md).

## Code Summary

[![Build and Test][build-and-test-badge]][build-and-test-link]
[![Unit Test Code Coverage][codecov-badge]][codecov-link]
[![Link Checker][link-checker-badge]][link-checker-link]

## Project Resources

* [Project Website](https://opensearch.org/)
* [Downloads](https://opensearch.org/downloads.html)
* [Documentation](https://opensearch.org/docs/)
* Need help? Try [Forums](https://discuss.opendistrocommunity.dev/)
* [Project Principles](https://opensearch.org/#principles)
* [Developer Guide](DEVELOPER_GUIDE.md)
* [Contributing to OpenSearch](CONTRIBUTING.md)
* [Maintainer Responsibilities](MAINTAINERS.md)
* [Release Management](RELEASING.md)
* [Testing](TESTING.md)
* [Security](SECURITY.md)

## Code of Conduct

This project has adopted the [Amazon Open Source Code of Conduct](CODE_OF_CONDUCT.md). For more information see the [Code of Conduct FAQ](https://aws.github.io/code-of-conduct-faq), or contact [opensource-codeofconduct@amazon.com](mailto:opensource-codeofconduct@amazon.com) with any additional questions or comments.

## License

This project is licensed under the [Apache v2.0 License](LICENSE.txt).

## Copyright

Copyright OpenSearch Contributors. See [NOTICE](NOTICE.txt) for details.

[build-and-test-badge]: https://github.com/opensearch-project/OpenSearch-Dashboards/actions/workflows/build_and_test_workflow.yml/badge.svg
[build-and-test-link]: https://github.com/opensearch-project/OpenSearch-Dashboards/actions/workflows/build_and_test_workflow.yml
[codecov-badge]: https://codecov.io/gh/opensearch-project/OpenSearch-Dashboards/branch/main/graphs/badge.svg
[codecov-link]: https://app.codecov.io/gh/opensearch-project/OpenSearch-Dashboards
[link-checker-badge]: https://github.com/opensearch-project/OpenSearch-Dashboards/actions/workflows/links_checker.yml/badge.svg
[link-checker-link]: https://github.com/opensearch-project/OpenSearch-Dashboards/actions/workflows/links_checker.yml
