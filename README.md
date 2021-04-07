# laravel-broadcast-demo

## 运行 Laradock 开发环境
```bash
cd laradock-laravel-broadcast-demo && cp env-example .env
docker-compose up -d
docker-compose exec workspace /bin/bash -c 'composer install && cp .env.example .env && php artisan key:generate'
docker-compose exec workspace /bin/bash -c 'npm install'
```

## Laravel IDE Helper Generator

- [`php artisan ide-helper:generate` -用于Laravel Facades的PHPDoc生成](https://github.com/barryvdh/laravel-ide-helper#automatic-phpdoc-generation-for-laravel-facades)
- [`php artisan ide-helper:models` -适用于模型的PHPDocs](https://github.com/barryvdh/laravel-ide-helper#automatic-PHPDocs-for-models)
- [`php artisan ide-helper:meta` -PhpStorm元文件](https://github.com/barryvdh/laravel-ide-helper#phpstorm-meta-for-container-instances)

## 对 Laravel 框架增加语言包
* 在 `config/app.php` 修改时区：`'timezone' => 'PRC'` 
* 在 `config/app.php` 修改语言：`'locale' => 'zh-CN'` ，并在 `resources/lang/zh-CN` 增加[语言包](https://github.com/Laravel-Lang/lang)


## License
The Laravel broadcast-demo is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).
