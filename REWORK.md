# Доработка

Решите, пожалуйста, проблемы с tfstate, сборкой latest-образа и с доступностью приложения через стандартный порт (или поясните, почему используется нестандартный порт).  

# Ответы

### 1. сборка с тегом latest

Проблема с отсутствующим тегом была решена с помощью добавления конструкции:  

    rules:
      - if: '$CI_COMMIT_TAG == null'
        variables:
          CI_COMMIT_TAG: "latest"

https://gitlab.com/devops-evgeniy-nikolskiy/nginx-app-diplom/-/blob/main/.gitlab-ci.yml  

Процесс сборки - https://gitlab.com/devops-evgeniy-nikolskiy/nginx-app-diplom/-/jobs/3456425487   

### 2. Доступность приложения

Доступность приложения я организовал с помощью NodePort.  
Данный способ был выбран просто в целях удобства. Нет необходимости танцевать с бубном вокруг port-forward или kubectl proxy  
Посадил приложение на указанный порт и оно сразу доступно по IP мастера  
http://51.250.4.10:30005/  

https://gitlab.com/devops-evgeniy-nikolskiy/nginx-app-diplom/-/blob/main/nginx-app-diplom.yaml#L27

### 3. Хранение в Object Storage файла конфигурации tfstate
https://github.com/Evgeniy-Nikolskiy/diplom-terraform-kube/blob/main/main.tf

Конфигурация развернута с помощью Терраформ:  
https://github.com/Evgeniy-Nikolskiy/diplom-terraform-kube с записаным бакетом в Object Storage   
![](https://raw.githubusercontent.com/Evgeniy-Nikolskiy/Netology-diplom/main/assets/bucket-main.png)  
Изначальный вид пустой директории в которой будет использовать tfstate из Object Storage соседней директории  
https://github.com/Evgeniy-Nikolskiy/diplom-terraform-kube-remote
![](https://raw.githubusercontent.com/Evgeniy-Nikolskiy/Netology-diplom/main/assets/bucket-remote.png)  
После ввода terraform apply добавляется новая виртуальная машина на основе конфигурации из tfstate  
![](https://raw.githubusercontent.com/Evgeniy-Nikolskiy/Netology-diplom/main/assets/bucket-remote2.png)  
Собственно сама виртуальная машина успешно создана.   
![](https://raw.githubusercontent.com/Evgeniy-Nikolskiy/Netology-diplom/main/assets/bucket-remote3.png)