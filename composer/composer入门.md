## composer是什么

composer用来管理项目的依赖，这种想法并不新鲜，Composer 受到了 node's npm 和 ruby's bundler 的强烈启发。而当时 PHP 下并没有类似的工具。

Composer 将这样为你解决问题：

* 你有一个项目依赖于若干个库。
* 其中一些库依赖于其他库。
* 你声明你所依赖的东西。
* Composer 会找出哪个版本的包需要安装，并安装它们（将它们下载到你的项目中）。

####声明依赖关系

比方说，你正在创建一个项目，你需要一个库来做日志记录。你决定使用 monolog。为了将它添加到你的项目中，你所需要做的就是创建一个 `composer.json` 文件，其中描述了项目的依赖关系。

```
{
    "require": {
        "monolog/monolog": "1.2.*"
    }
}
```



## 安装composer

### 安装 - *nix

#### 下载 Composer 的可执行文件

这将检查一些 PHP 的设置，然后下载 composer.phar 到你的工作目录中。这是 Composer 的二进制文件。这是一个 PHAR 包（PHP 的归档），这是 PHP 的归档格式可以帮助用户在命令行中执行一些操作。

> curl -sS https://getcomposer.org/installer | php
>
> 或
>
> php -r "readfile('https://getcomposer.org/installer');" | php
>
> 或
>
> 你可以通过 --install-dir 选项指定 Composer 的安装目录（它可以是一个绝对或相对路径）：
>
> curl -sS https://getcomposer.org/installer | php -- --install-dir=bin

#### 全局安装

你可以执行这些命令让 `composer` 在你的系统中进行全局调用：

> curl -sS https://getcomposer.org/installer | php
>
> mv composer.phar /usr/local/bin/composer

### 全局安装 (on OSX via homebrew)

>
>brew update
>brew tap josegonzalez/homebrew-php
>brew tap homebrew/versions
>brew install php55-int
>brew install josegonzalez/php/composer




## 使用composer

#### 在项目根目录创建`composer.json`文件

你需要在 composer.json 文件中指定 require key 的值。你只需要简单的告诉 Composer 你的项目需要依赖哪些包

```
{
    "require": {
        "monolog/monolog": "1.0.*"
    }
}
```

#### 安装依赖包

这将会找到 monolog/monolog 的最新版本，并将它下载到 vendor 目录。 另一件事是 install 命令将创建一个 composer.lock 文件到你项目的根目录中.

> php composer.phar install

#### 更新依赖包

> php composer.phar update

#### 更新指定包

> php composer.phar update monolog/monolog [...]