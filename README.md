# Домашнее задание к занятию "`Что такое DevOps. CI/CD`" - `Копаческу Владимир`


### Инструкция по выполнению домашнего задания

   1. Сделайте `fork` данного репозитория к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/git-hw или  https://github.com/имя-вашего-репозитория/7-1-ansible-hw).
   2. Выполните клонирование данного репозитория к себе на ПК с помощью команды `git clone`.
   3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
      - впишите вверху название занятия и вашу фамилию и имя
      - в каждом задании добавьте решение в требуемом виде (текст/код/скриншоты/ссылка)
      - для корректного добавления скриншотов воспользуйтесь [инструкцией "Как вставить скриншот в шаблон с решением](https://github.com/netology-code/sys-pattern-homework/blob/main/screen-instruction.md)
      - при оформлении используйте возможности языка разметки md (коротко об этом можно посмотреть в [инструкции  по MarkDown](https://github.com/netology-code/sys-pattern-homework/blob/main/md-instruction.md))
   4. После завершения работы над домашним заданием сделайте коммит (`git commit -m "comment"`) и отправьте его на Github (`git push origin`);
   5. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
   6. Любые вопросы по выполнению заданий спрашивайте в чате учебной группы и/или в разделе “Вопросы по заданию” в личном кабинете.
   
Желаем успехов в выполнении домашнего задания!
   
### Дополнительные материалы, которые могут быть полезны для выполнения задания

1. [Руководство по оформлению Markdown файлов](https://gist.github.com/Jekins/2bf2d0638163f1294637#Code)

---

### Задание 1
Что нужно сделать:

1. `Установите себе jenkins по инструкции из лекции или любым другим способом из официальной документации. Использовать Docker в этом задании нежелательно.`
2. `Установите на машину с jenkins golang.`
3. `Используя свой аккаунт на GitHub, сделайте себе форк репозитория. В этом же репозитории находится дополнительный материал для выполнения ДЗ.`
4. `Создайте в jenkins Freestyle Project, подключите получившийся репозиторий к нему и произведите запуск тестов и сборку проекта go test . и docker build ..`
`В качестве ответа пришлите скриншоты с настройками проекта и результатами выполнения сборки.`

### Решение 1

1. `Установите себе jenkins`
```
sudo apt-get install default-jre
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key |
sudo tee \
/usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
/etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins
```

`Скрин 1 к заданию 1`                                    
![alt text](https://github.com/Replica63/Jenkins-8-02.md/blob/main/img/1.png)



2. ![alt text](https://github.com/Replica63/Jenkins-8-02.md/blob/main/img/2.png)
3. `Выполнил Fork https://github.com/Replica63/Jenkins-8-02.md`
4. ![alt text](https://github.com/Replica63/Jenkins-8-02.md/blob/main/img/3.png)
   ![alt text](https://github.com/Replica63/Jenkins-8-02.md/blob/main/img/3.1.png)
   ![alt text](https://github.com/Replica63/Jenkins-8-02.md/blob/main/img/3.2.png)



---

### Задание 2
Что нужно сделать:

1. Создайте новый проект pipeline.
2. Перепишите сборку из задания 1 на declarative в виде кода.
В качестве ответа пришлите скриншоты с настройками проекта и результатами выполнения сборки.

### Решение 2

1. ![alt text](https://github.com/Replica63/Jenkins-8-02.md/blob/main/img/4.png)
2. `Script`

```
Поле для вставки кода...
pipeline {
 agent any
 stages {
  stage('Git') {
   steps {git 'https://github.com/Replica63/sdvps-materials.git'}
  }
  stage('Test') {
   steps {
    sh '/usr/bin/go test .'
   }
  }
  stage('Build') {
   steps {
    sh 'docker build . -t ubuntu-bionic:8081/hello-world:v$BUILD_NUMBER'
   }
  }
 }
}
```
3. ![alt text](https://github.com/Replica63/Jenkins-8-02.md/blob/main/img/4.5.png)



---

### Задание 3
Что нужно сделать:

1. Установите на машину Nexus.
2. Создайте raw-hosted репозиторий.
3. Измените pipeline так, чтобы вместо Docker-образа собирался бинарный go-файл. Команду можно скопировать из Dockerfile.
4. Загрузите файл в репозиторий с помощью jenkins.
В качестве ответа пришлите скриншоты с настройками проекта и результатами выполнения сборки.
### Решение 3


1. ![alt text](https://github.com/Replica63/Jenkins-8-02.md/blob/main/img/n.1.png)
2. ![alt text](https://github.com/Replica63/Jenkins-8-02.md/blob/main/img/n.2.png)
3. `Заполните здесь этапы выполнения, если требуется ....`
4. `Заполните здесь этапы выполнения, если требуется ....`
5. `Заполните здесь этапы выполнения, если требуется ....`
6. 

```
Поле для вставки кода...
....
....
....
....
```

`При необходимости прикрепитe сюда скриншоты
![Название скриншота](ссылка на скриншот)`

