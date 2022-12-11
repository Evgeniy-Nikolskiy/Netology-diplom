# Доработка

Решите, пожалуйста, проблемы с tfstate, сборкой latest-образа и с доступностью приложения через стандартный порт (или поясните, почему используется нестандартный порт).  

# Ответы

#### сборка с тегом latest

Проблема с отсутствующим тегом была решена с помощью добавления конструкции:  

    rules:
      - if: '$CI_COMMIT_TAG == null'
        variables:
          CI_COMMIT_TAG: "latest"

https://gitlab.com/devops-evgeniy-nikolskiy/nginx-app-diplom/-/blob/main/.gitlab-ci.yml  

Процесс сборки - https://gitlab.com/devops-evgeniy-nikolskiy/nginx-app-diplom/-/jobs/3456425487   

#### Доступность приложения

Доступность приложения я организовал с помощью NodePort.  
Данный способ был выбром просто в целях удобства. Нет необходимости танцевать с бубном вокруг port-forward или kubectl proxy  
Посадил приложение на указанный порт и оно сразу доступно по IP мастера  
http://51.250.4.10:30005/  

https://gitlab.com/devops-evgeniy-nikolskiy/nginx-app-diplom/-/blob/main/nginx-app-diplom.yaml#L27

#### Хранение в Object Storage файла конфигурации tfstate
https://github.com/Evgeniy-Nikolskiy/diplom-terraform-kube/blob/main/main.tf