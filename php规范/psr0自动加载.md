### 路径范例

> \namespace\package\Class_Name =>/path/to/project/lib/vendor/namespace/package/Class/Name.php
>
> \namespace\package_name\Class_Name=>/path/to/project/lib/vendor/namespace/package_name/Class/Name.php



### 实例代码

```php
<?php

function autoload($className)
{
    $className = ltrim($className, '\\');
    $fileName  = '';
    $namespace = '';
    if ($lastNsPos = strrpos($className, '\\')) {
        $namespace = substr($className, 0, $lastNsPos);
        $className = substr($className, $lastNsPos + 1);
        $fileName  = str_replace('\\', DIRECTORY_SEPARATOR, $namespace) . DIRECTORY_SEPARATOR;
    }
    $fileName .= str_replace('_', DIRECTORY_SEPARATOR, $className) . '.php';

    require $fileName;
}
```

### 原文

[php-fig psr0](https://github.com/PizzaLiu/PHP-FIG/blob/master/PSR-0-cn.md)

