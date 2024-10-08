# **Сервис по укорачиванию ссылок.**
## 1. Описание
Имеет 2 варианта работы:
 1. При запуске с флагом ```-d``` будет сохранять все данные в базе данных.
 2. При запуске без флага вся информация будет храниться в оперативной памяти пока сервис работает.
   
Был разработан как тестовое задание для стажировки.
Имеет структуру обычного проекта на Go и написана с принципом внедрения зависимостей (dependency injection), для гибкости масштабирования и тестирования. Над масштабированием особо не думал, но оно больше заключается в принципах хранения данных, сам сервис не особо "тяжелый".
## 2. Структура
 ### 1. cmd/swoyo-test-task
 Содержит в себе точку входа в приложение ```main.go```.
 ### 2. **internal/**
  - #### **app/**
    - ##### **endpoint**
      Содержит в себе файл с выделенными эндпоинтами ```endpoint.go```, интерфейс для сервиса, структуру эндпоинт ```endpoint``` и её методы.
    - ##### **service**
      Содержит в себе файл с самим сервисом ```service.go```, интерфейс для типа хранения данных, структуру сервис ```service``` и её методы.
  - #### **pkg/app**
    Содержит в себе файл с приложением ```app.go```, структуру приложение ```app``` и её методы.
 ### 3. **pkg/**
  - #### **dbStorage**
  Содержит в себе файл со структурой для работы с базой данных ```dbStorage.go```, структуру абстракции-базы данных ```DbStorage``` и её методы.
  - #### **memStorage**
  Содержит в себе файл со структурой для сохранения данных в памяти ```memStorage.go```, структуру-абстракцию для хранения данных ```urlsMap``` и её методы.
