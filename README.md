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
