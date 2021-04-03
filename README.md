<h1 align="center">🚀 ProgressBar</h1>

**ProgressBar** - небольшая библиотека для реализаци прогресс баров на PHP CLI

## Установка

```
composer require krypt0nn/progressbar
```

## Пример работы

```php
<?php

use ProgressBar\ProgressBar;

$begin = microtime (true);

$progress = new ProgressBar (100000, 48, ' ', function ($actual, $max) use ($begin)
{
    $seconds  = round (($time = (microtime (true) - $begin)) * ($max - $actual) / max ($actual, 1));
    $hours    = (int)($seconds / 3600);
    $minutes  = (int)(($seconds - $hours * 3600) / 60);
    $seconds -= $hours * 3600 + $minutes * 60;

    $hours   = $hours   > 9 ? $hours   : "0$hours";
    $minutes = $minutes > 9 ? $minutes : "0$minutes";
    $seconds = $seconds > 9 ? $seconds : "0$seconds";

    return " Remained: $hours:$minutes:$seconds, speed: ". round ($actual / $time, 2) .' IPS';
}, '█');

for ($i = 1; $i <= 100000; ++$i)
    $progress->update ($i); // Обновляем прогресс бар

$progress->clear (); // Удаляем прогресс бар из консоли (так же не обязательно)
```

Автор: [Подвирный Никита](https://vk.com/technomindlp)
