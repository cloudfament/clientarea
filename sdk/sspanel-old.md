---
description: SSPANEL 旧版 对接
---

# SSPanel - OLD

{% file src="../.gitbook/assets/SSPanel OLD.zip" %}

1. 把压缩包里的文件覆盖到网站根目录
2. 按照步骤添加

在  `config/routes.php` 内添加:

```php
$app->group('/epay',function (){
    $this->post('/notify', 'App\Services\Payment:notify');
    $this->get('/notify', 'App\Services\Payment:notify');
    $this->post('/return','App\Services\Payment:returnHTML');
    $this->get('/return','App\Services\Payment:returnHTML');
});
```

在 `config/config.php` 内添加:

```php
$System_Config['payment_system'] = 'epay';

# Pay Fament    (xxx代表需要手动填写的信息)
$System_Config['epay_pid'] = 'xxx';         //Pay Fament商户ID
$System_Config['epay_key'] = 'xxx';         //Pay Fament商户Key
$System_Config['epay_url'] = 'https://fps.cloudfament.co';
```
