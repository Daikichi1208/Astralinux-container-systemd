# Сборка
В dockerfile переключен "уровень защищенности" на базовый из-за падения контейнера после запуска
init: parsec module missing, terminating to prevent data leakage

Осуществляется с помощью скачивания пакета astra-safepolicy и переключения astra-modeswitch set 0.

Согласно [Документации](https://wiki.astralinux.ru/pages/viewpage.action?pageId=109020865#id-%D0%98%D0%BD%D1%81%D1%82%D1%80%D1%83%D0%BC%D0%B5%D0%BD%D1%82%D1%8B%D0%BA%D0%BE%D0%BC%D0%B0%D0%BD%D0%B4%D0%BD%D0%BE%D0%B9%D1%81%D1%82%D1%80%D0%BE%D0%BA%D0%B8astrasafepolicy-astra-modeswitchastra-modeswitch)

```
docker build -t astra-systemd .
```

# Запуск

```
docker run -d --name astra-systemd \ 
    --privileged \ 
    --cgroupns=host \ 
    --tmpfs /run \ 
    --tmpfs /run/lock \ 
    -v /sys/fs/cgroup:/sys/fs/cgroup:rw \ 
    astra-systemd
```

![systemd](/img/systemd.png)