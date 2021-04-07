# laravel-broadcast-demo
基于laravel 8.x，使用Redis数据库和predis、socket.io、laravel-echo、laravel-echo-server工具库实现WebSocket连接的广播系统。

使用docker-compose一键启动项目，环境配置真的很烦人。

文档没时间写了，但是可以查看[提交记录](https://github.com/CongAn/laravel-broadcast-demo/commits/main)的解释来查看修改的原因。

<h2 style="color: red;">如果帮助到你了，请留个小星星支持，也能让更多人得到帮助。</h2>

## 参考来源
[laravel广播系统文档](https://learnku.com/docs/laravel/8.x/broadcasting/9388)

[Laravel Broadcasting广播机制(Redis + socket.io)-学习实例](https://blog.csdn.net/nsrainbow/article/details/80428769)

## 运行 Laradock 开发环境
```bash
cd laradock-laravel-broadcast-demo && cp env-example .env
docker-compose up -d
docker-compose exec workspace /bin/bash -c 'composer install && cp .env.example .env && php artisan key:generate'
docker-compose exec workspace /bin/bash -c 'npm install'
```

## 开始
### 打包js文件到public
```bash
npm run production
```

### 运行 laravel-echo-server 服务
```bash
npx laravel-echo-server start --config="./laravel-echo-server.json"
```

### 运行队列
```bash
php artisan queue:work
```

### 测试功能
1. 打开主页`http://localhost/`，并打开检查器。
2. 发送广播。打开页面：`http://localhost/example-broadcast`，或运行命令行`php artisan example-broadcast-event`。
3. 在主页查看广播接收。


## 遇到问题与解决
### web端的laravel-echo接收不到广播信息。
**症状：** redis数据正常，队列处理正常，laravel-echo-server接收广播正常，laravel-echo成功连接laravel-echo-server，但并未加入频道。

**解决方案：** 降级`socket.io-client`包的版本为`2.4.0`。

**解决方案来源：** https://stackoverflow.com/a/65859555/8341648

**原因：** 未知。可能是版本不兼容。



## Laravel IDE Helper Generator

- [`php artisan ide-helper:generate` -用于Laravel Facades的PHPDoc生成](https://github.com/barryvdh/laravel-ide-helper#automatic-phpdoc-generation-for-laravel-facades)
- [`php artisan ide-helper:models` -适用于模型的PHPDocs](https://github.com/barryvdh/laravel-ide-helper#automatic-PHPDocs-for-models)
- [`php artisan ide-helper:meta` -PhpStorm元文件](https://github.com/barryvdh/laravel-ide-helper#phpstorm-meta-for-container-instances)

## 对 Laravel 框架增加语言包
* 在 `config/app.php` 修改时区：`'timezone' => 'PRC'` 
* 在 `config/app.php` 修改语言：`'locale' => 'zh-CN'` ，并在 `resources/lang/zh-CN` 增加[语言包](https://github.com/Laravel-Lang/lang)


## License
The Laravel broadcast-demo is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).
