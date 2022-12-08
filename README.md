# Что необходимо для сдачи задания?
1. Репозиторий с конфигурационными файлами Terraform и готовность продемонстрировать создание всех ресурсов с нуля.
2. Пример pull request с комментариями созданными atlantis'ом или снимки экрана из Terraform Cloud.
3. Репозиторий с конфигурацией ansible, если был выбран способ создания Kubernetes кластера при помощи ansible.
4. Репозиторий с Dockerfile тестового приложения и ссылка на собранный docker image.
5. Репозиторий с конфигурацией Kubernetes кластера.
6. Ссылка на тестовое приложение и веб интерфейс Grafana с данными доступа.


# Ответы

## 1. Репозиторий с конфигурационными файлами Terraform  

https://github.com/Evgeniy-Nikolskiy/diplom-terraform   
скрин подгрузки бакета в Object Storage:
![](https://raw.githubusercontent.com/Evgeniy-Nikolskiy/Netology-diplom/main/assets/bucket.png)  
## 2. Пример pull request с комментариями созданными atlantis'ом  

![](https://raw.githubusercontent.com/Evgeniy-Nikolskiy/Netology-diplom/main/assets/atlantis.jpg)
## 3. Репозиторий с конфигурацией ansible  

https://github.com/Evgeniy-Nikolskiy/kubespray-netology/blob/master/inventory/diplom/inventory.ini
![](https://raw.githubusercontent.com/Evgeniy-Nikolskiy/Netology-diplom/main/assets/1.jpg)

## 4. Репозиторий на Gitlab для приложения
 Репозиторий - https://gitlab.com/devops-evgeniy-nikolskiy/nginx-app-diplom/-/tree/main

Сборка и деплой приложения осуществляется с помощью kaniko и gitlab runner for Kubernates

Реджистри - https://gitlab.com/devops-evgeniy-nikolskiy/nginx-app-diplom/container_registry  

Манифест - https://gitlab.com/devops-evgeniy-nikolskiy/nginx-app-diplom/-/blob/main/nginx-app-diplom.yaml

![](https://raw.githubusercontent.com/Evgeniy-Nikolskiy/Netology-diplom/main/assets/5.png)   

![](https://raw.githubusercontent.com/Evgeniy-Nikolskiy/Netology-diplom/main/assets/kube.png)
  
## 5. Репозиторий с манифестом для мониторинга Kubernetes кластера.  
https://github.com/Evgeniy-Nikolskiy/kubernetes-monitoring


## 6. Тестовое приложение и веб интерфейс Grafana

#### Доступ к тестовому приложению: http://84.201.174.101:32062/
![](https://raw.githubusercontent.com/Evgeniy-Nikolskiy/Netology-diplom/main/assets/2.jpg)

#### Доступ к графане http://84.201.174.101:3000
Логин: admin  
Пароль: admin123  
![](https://raw.githubusercontent.com/Evgeniy-Nikolskiy/Netology-diplom/main/assets/3.jpg)