# wxwork_finance_sdk_wrapper

企业微信-会话内容存档PHP扩展


## 依赖
企业微信提供的sdk;

PHP VERSION >= 7.0

openssl扩展

## 安装步骤及要求
```
       $INSATLL_PATH_PATH/bin/phpize
        
       ./configure --with-php-config=$INSTALL_PHP_PATH/php-config --with-wxwork-finance-sdk=$WXWORK_FINANCE_C_SDK_PATH
       
        make && make install
```
    php.ini 增加 extension=wxwork_finance_sdk.so
    
## API
```php
    WxworkFinanceSdkExcption::__construct();
```

```php
    WxworkFinanceSdk::__construct(string $corpId, string $secret, array $options);
    string $corpId 企业号

    string $secret 秘钥

    array $options = [ // 可选参数
        'proxy_host' => string,
        'proxy_password' => string,
        'timeout' => 10, // 默认超时时间为10s
    ]
```

```php
   string WxworkFinanceSdk::getChatData(int $seq, int $limit);
    * 拉取聊天数据
    $seq 起始位置
    $limit 获取条数
``` 

```php
   bool WxworkFinanceSdk::downloadMedia(string $sdkfileid, string $saveTo)
   * 下载资源
   $sdkfileid 资源id。来自chat 中的数据sdkfileid
   $saveTo 本地保存的路径
```

```php
       string WxworkFinanceSdk::decryptData(string $randomKey, string $encryptStr);
       * 解密数据
       $randomKey 通过openssl解密后的key
       $encryptStr chats 的加密数据
```

## 问题
      1. free(): invalid pointer
       * 暂时定位intl扩展的冲突问题. php -m |grep intl 建议重新编译php 取消intl扩展

 ## 示例
 
  wxwork_finance_sdk.php
    
打赏一下的话就更好了~
 Alipay
 
 <img src="https://github.com/pangdahua/php7-wxwork-finance-sdk/blob/sponsor/imgs/Alipay.png" width="230" height="230" />
