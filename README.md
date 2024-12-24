# OPCache and JIT
> November 13th, 2024
----------------------------------------------

OPCache and JIT are 2 PHP derivatives that you can enable which can significantly increase your PHP speed.

OPCache is a built in cache that turns PHP code into byte code, thereby making your PHP website faster.

I have no idea what JIT is, but I will do more research on this topic in the future.

To enable these 2 features, simply follow these steps:

1. Edit your `php.ini` file.
2. Uncomment these deriviatives:
```txt
zend_extension=opcache.so
opcache.enable=1
opcache.enable_cli=1
opcache.jit_buffer_size=500000000
opcache.jit=1235
; 0 means it will check on every request
; 0 is irrelevant if opcache.validate_timestamps=0 which is desirable in production
opcache.revalidate_freq=0
opcache.validate_timestamps=1
opcache.max_accelerated_files=10000
opcache.memory_consumption=192
opcache.max_wasted_percentage=10
opcache.interned_strings_buffer=16
opcache.fast_shutdown=1
```

If you check your phpinfo file, you should see OPCache and JIT enabled. Note, if you don't have all these deriviatives, for example, opcache.fast_shutdown, which was true in my case, you don't need to add it. If you don't have the others though, you may want to install the necessary files.

# Sources
> https://medium.com/@edouard.courty/make-your-php-8-apps-twice-as-fast-opcache-jit-8d3542276595
> 
> https://loadforge.com/guides/maximizing-your-php-applications-speed-with-opcache-optimization
> 
> https://dev.to/platformsh/supercharge-your-php-the-ultimate-guide-to-opcache-optimization-47ed
