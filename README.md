## Laboratory work 9

Артефакты позволяют сохранять данные после завершения задания и делиться этими данными с другим заданием в том же рабочем процессе. Артефакт — это файл или коллекция файлов, созданных во время выполнения рабочего процесса. Например, вы можете использовать артефакты для сохранения результатов сборки и тестирования после завершения рабочего процесса.
По умолчанию GitHub хранит журналы сборки и артефакты в течение 90 дней, и этот период хранения можно настроить. 

Чтобы обмениваться данными между заданиями:
Загрузка файлов: дайте загруженному файлу имя и загрузите данные до завершения задания.
Загрузка файлов. Вы можете загружать только те артефакты, которые были отправлены во время одного и того же рабочего процесса. Когда вы загружаете файл, вы можете ссылаться на него по имени.

     name: Upload Artifact v1
     uses: actions/upload-artifact@v3
     with:
       name: hello_world
       path: |
         ./hello_world_application/hello.txt
         
При использовании download-artifact@v1 будет создан каталог, обозначенный именем артефакта, если не указан путь. Все содержимое будет загружено в этот каталог.

     name: download-artifact v1
     uses: actions/download-artifact@v3
     with:
       name: hello_world
       path: ./artifact
       
Если входной параметр name не указан, будут загружены все артефакты. Чтобы различать загруженные артефакты, для каждого отдельного артефакта будет создан каталог, обозначенный именем артефакта. 

Чтобы посмотреть содержимое папки, куда мы загружали наши артефакты:

     name: Display structure of downloaded files v1
     run: |
       ls -R
     working-directory: ./artifact
     
Сравнение артефактов и кэширования зависимостей
Артефакты и кэширование похожи, поскольку они позволяют хранить файлы на GitHub, но каждая функция предлагает разные варианты использования и не может использоваться взаимозаменяемо.
Используйте кэширование, если вы хотите повторно использовать файлы, которые не часто меняются между заданиями или запусками рабочего процесса, например, построить зависимости от системы управления пакетами.
Используйте артефакты, если вы хотите сохранить файлы, созданные заданием, для просмотра после завершения рабочего процесса, например встроенные двоичные файлы или журналы сборки.

# Полезные ссылки:
* https://github.com/actions/download-artifact
* https://github.com/actions/upload-artifact
* https://github.com/marketplace/actions/upload-a-build-artifact
* https://docs.github.com/en/actions/using-workflows/storing-workflow-data-as-artifacts
```
Copyright (c) 2015-2021 The ISC Authors
```
