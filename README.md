# Yadwig_platform
Yadwig Platform repository

### I.
Разберитесь почему все pod в namespace kube-system восстановились после удаления. Укажите причину в описании PR 

Команда kubectl delete pod --all -n kube-system выполняется успешно, поды удаляются, однако, создаются новые им на замену, что видно по новым id и времени жизни.

![Image](https://github.com/Yadwig/yadwig_pictures/blob/main/pictures_otus_homework_1/2.png)
![Image](https://github.com/Yadwig/yadwig_pictures/blob/main/pictures_otus_homework_1/1.png)

 Это происходит, поскольку для данных подов задано требуемое количество реплик, которое кубернетес поддерживает с помощью определенных механизмов. Такие функции для обычных подов выполняют, например: Replication Controller, Replica Set и Deployment. Core-dns управляется deployment.

![Image](https://github.com/Yadwig/yadwig_pictures/blob/main/pictures_otus_homework_1/3.png)

Но kube-apiserver, etcd, kube-controller-manager и kube-scheduler управляются напрямую kubelet. Kubelet - агент, стоящий на каждой ноде, и запускающий такие поды, называемые static pods.

### II.
Создан Dockerfile с использованием образа alpine, добавлен nginx, в папку /app скопированы файлы index.html и картинка. Образ, собранный из dockerfile, запускает nginx и публикует на http://localhost:8000 страницу index.html . Образ положен в dockerhub: yadwig/pepehtml


### III. Задание с *
Выяснить, по какой причине под с контейнером, собраным из dockerfile frontend hipstershop, выдает error.

Причина ошибки выделена желтым.
![Image](https://github.com/Yadwig/yadwig_pictures/blob/main/pictures_otus_homework_1/5.png)

Не установлены переменная среды, например, PRODUCT_CATALOG_SERVICE_ADDR. Если их все добавить, то статус контейнера будет running, но само приложение работать не будет.
![Image](https://github.com/Yadwig/yadwig_pictures/blob/main/pictures_otus_homework_1/6.png)




