# onWorkerStart
## 说明:
```php
callback Worker::$onWorkerStart
```

设置Worker子进程启动时的回调函数，每个子进程启动时都会执行。

注意：onWorkerStart是在子进程启动时运行的，如果开启了多个子进程(```$worker->count > 1```)，每个子进程运行一次，则总共会运行```$worker->count```次。


## 回调函数的参数

 ``` $worker ```

即Worker对象



## 范例


```php
use Workerman\Worker;
require_once __DIR__ . '/Workerman/Autoloader.php';

$worker = new Worker('websocket://0.0.0.0:8484');
$worker->onWorkerStart = function($worker)
{
    echo "Worker starting...\n";
};
// 运行worker
Worker::runAll();
```

提示：除了使用匿名函数作为回调，还可以[参考这里](faq/callback_methods.md)使用其它回调写法。
