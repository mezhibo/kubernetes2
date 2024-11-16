**Задание 1. Создать Pod с именем hello-world**

1. Создать манифест (yaml-конфигурацию) Pod.

2. Использовать image - gcr.io/kubernetes-e2e-test-images/echoserver:2.2.

3. Подключиться локально к Pod с помощью kubectl port-forward и вывести значение (curl или в браузере).


**Решение 1**

Создаем файл конфигурация для деклартивного описания пода

```
apiVersion: v1
kind: Pod
metadata:
  name: hello-world
spec:
  containers:
  - name: hello-world
    image: gcr.io/kubernetes-e2e-test-images/echoserver:2.2
    ports:
    - containerPort: 8080
```

![Image alt](https://github.com/mezhibo/kubernetes2/blob/c44f802ee2ef102b088b996620d5fa6d089a437c/IMG/1.jpg)

Теперь сделаем port-forward и зайдем в дашборд управления

![Image alt](https://github.com/mezhibo/kubernetes2/blob/c44f802ee2ef102b088b996620d5fa6d089a437c/IMG/2.jpg)

И через дашборд видим наш созданный под hello-world

![Image alt](https://github.com/mezhibo/kubernetes2/blob/c44f802ee2ef102b088b996620d5fa6d089a437c/IMG/3.jpg)




**Задание 2. Создать Service и подключить его к Pod**

1. Создать Pod с именем netology-web.

2. Использовать image — gcr.io/kubernetes-e2e-test-images/echoserver:2.2.

3. Создать Service с именем netology-svc и подключить к netology-web.

4. Подключиться локально к Service с помощью kubectl port-forward и вывести значение (curl или в браузере).




**Решение 2**


Создаем под netology-web

Со следующим содержимым

```
apiVersion: v1
kind: Pod
metadata:
  name: netology-web
  labels:
    app: netology
spec:
  containers:
  - name: netology-web
    image: gcr.io/kubernetes-e2e-test-images/echoserver:2.2
```

![Image alt](https://github.com/mezhibo/kubernetes2/blob/cb0ac4b8b306308372ef0fc76ba530fed756eb4e/IMG/4.jpg)


Далее создадим сервис netology-svc и через селектор netology подключим к нему наш под web-netology

```
apiVersion: v1
kind: Service
metadata:
  name: netology-svc
spec:
  ports:
    - name: web
      port: 8080
  selector:
    app: netology
```

![Image alt](https://github.com/mezhibo/kubernetes2/blob/cb0ac4b8b306308372ef0fc76ba530fed756eb4e/IMG/5.jpg)

Далее зайдем опять на наш дашборд управления у увидим наш работающий сервис

![Image alt](https://github.com/mezhibo/kubernetes2/blob/cb0ac4b8b306308372ef0fc76ba530fed756eb4e/IMG/6.jpg)


Далее запустим порт-форвард нашего сервиса

![Image alt](https://github.com/mezhibo/kubernetes2/blob/cb0ac4b8b306308372ef0fc76ba530fed756eb4e/IMG/7.jpg)


И теперь через curl дернем наш под серез сервис

![Image alt](https://github.com/mezhibo/kubernetes2/blob/cb0ac4b8b306308372ef0fc76ba530fed756eb4e/IMG/8.jpg)

