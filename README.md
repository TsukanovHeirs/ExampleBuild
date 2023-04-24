# ExampleBuild

### Entry 

Перед тем, как пробовать повторить описанное ниже, нужно установить IDE для Java, Git (если не установлен). 
Среди IDE можно выбрать любую, конечно, но советую остановиться на Intellij IDEA, ибо она крайне удобная и приятная в использовании. Версия (Ultimate или Community) не имеет значения. Саму джаву мы устанавливать не будем (она сама встанет).
 


***ВАЖНО!*** При установке лучше поставить галочки у пунктов Update PATH Variable и Add "Open Folder as Project". Так же ставим галочки на Create Associations у .java, .gradle, .groovy. Шорткат уже на ваше усмотрение.
___

# Создание проекта

## Подготовка
Перед работой в самой IDE нужно будет создать GitHub репозиторий. Теперь по пунктам:

* Создаем папку, через правую кнопку мыши делаем Git Bash. 

![image](https://user-images.githubusercontent.com/131151302/234013625-05f3e56f-a19b-4249-8e2d-d7c3b25ad6b4.png)

* С главной страницы вашего реаозитория копируем https (через раздел <>Code)

![image](https://user-images.githubusercontent.com/131151302/234016386-cfaa4a4c-dd27-4183-aafa-368c44e4373e.png)

* Пишем в Bash команду git clone "httpsstring" (вставлять без кавычек).

![image](https://user-images.githubusercontent.com/131151302/234014082-802137d0-7dcd-4349-a4be-096a3c379d88.png)

## Создание
Теперь создание проекта. В начальном окне IDE будет предложена возможность создать проект. Кликаем, создаем в папке, куда копировали репозиторий. 
А теперь по пунткам:

* Соблюдайте нэйминг, он будет важен. Так же для удобства могу предложить не раскидывать все проекты по жесткому диску, а создать отдельную папку и уже там делать всё связанное.
* Среди языков выбираем Java, система сборки Gradle.
* ***ВАЖНО!*** В пункте JDK выбираем версию 16 и более. IDE предложит установить JDK этой версии, СОГЛАШАЕМСЯ.
* Ниже (в Gradle DSL) выбираем Groovy.

![image](https://user-images.githubusercontent.com/131151302/234014265-66b7c990-3aa5-469e-9395-9aa913e65eca.png)

___

# Настройка проекта

В самой IDE зайдите в настройки: File -> Settings -> "Build, Execution, Deployment" -> "Build Tools" -> Gradle. Есть вероятность, что Gradle user home будет стоять по умолчанию. Если это так, стоит установить Gradle и поставить в этом поле папку .gradle. Этот пункт советую проделать только в том случае, если после прохождения всей инструкции возникли проблемы с сборкой проекта.

![image](https://user-images.githubusercontent.com/131151302/234015690-16fa5b49-fa84-4b1d-b64a-4b12fb3622b6.png)

Нужно будет поправить файлы .gitignore и build.gradle (можно заменить их файлами из этого репозитория). Хотел бы заметить, что build.gradle придется менять под каждый новый модуль.

И в завершении распаковать себе архив прямо в проект с некоторыми другими файлами. Если возникнет ситуация, что такие файлы уже есть, то заменяйте их. 

В итоге должно получиться примерно так:

![image](https://user-images.githubusercontent.com/131151302/234015422-50d97c29-8be5-4e5a-81bc-013c6f102ebc.png)
 
___

# Настройка IDE

Если есть желание как-то поменять внешний вид (тему), то в правом верхнем углу в разделе настроек выбираем нужный пункт.

![image](https://user-images.githubusercontent.com/131151302/234003507-052cb6a3-babd-4921-bf4f-a414296baa93.png)


___
