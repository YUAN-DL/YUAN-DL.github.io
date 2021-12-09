# Отчет по заданию Каталог ресурсов Интернет

#### Задание сделано:

- Юань Дунлян     341/2
- Чжоу Фанда        341/1
- Яо цинсюань      341/1
- Цзян Сюеюань   341/1
- Ся Цзэкай           341/1

##### Программа выложена на github:  https://github.com/YUAN-DL/Resource-Management-System

[TOC]

### Описание задания:

```
Требуется разработать модель программного обеспечения каталога ресурсов сети Интернет.
В каталоге хранится следующая информация о ресурсах: название ресурса, уникальный локатор ресурса (URL), раздел каталога, в котором содержится ресурс, список ключевых слов, краткое описание, дата последнего обновления, контактная информация.
Доступ пользователей к каталогу осуществляется при помощи браузера. Пользователи каталога могут добавлять новые ресурсы, информация о которых не была внесена ранее. Ресурсы в каталоге классифицируются по разделам. Полный список ресурсов каждого раздела должен быть доступен пользователям. Пользователям каталога должны быть предоставлены возможности по поиску ресурсов. Поиск осуществляется по ключевым словам. Если пользователь не доволен результатами поиска, он может уточнить запрос (осуществить поиск среди результатов предыдущего поиска). Должна быть возможность выдавать результаты поиска в разной форме (вывод всей информации о ресурсах или частичной). Пользователь может отсортировать список ресурсов по релевантности (соответствию ключевым словам из запроса) или по дате обновления.
Поскольку содержание ресурсов Интернет со временем изменяется необходимо следить за датой последнего обновления, периодически опрашивая Web-сайты, URL которых хранятся в каталоге.
Вариант задания включает в себя разработку схемы базы данных для хранения сообщений конференции и информации об её участниках.
Выполняющим это задание полезно ознакомиться с заключительным замечанием к варианту «Интернет-магазин». Как и в варианте «WWW-конференция» самой подходящей архитектурой для каталога является «тонкий клиент», поскольку клиентская часть практически не включает в себя функций «бизнес-логики» кроме проверки содержимого форм перед пересылкой на сервер.
```

### Способы реализации:

- Модель программного обеспечения была реализована способами языка программирования C#.

- Графические элементы управления и элементы интерфейса мы использовали язык программирования html.

- Язык базы данных -sql.

- Код для создания базы данных:

  ```sql
  USE [localDB]
  GO
  SET ANSI_NULLS ON
  GO
  SET QUOTED_IDENTIFIER ON
  GO
  CREATE TABLE [dbo].[User](
  	[Id] [int] IDENTITY(1,1) NOT NULL,
  	[name] [nvarchar](50) NULL,
  	[pwd] [nvarchar](50) NULL,
  	[age] [int] NULL,
  	[online] [int] NULL,
  	[shenfen] [nchar](10) NULL,
  PRIMARY KEY CLUSTERED 
  (
  	[Id] ASC
  )WITH (PAD_INDEX  = OFF, STATISTICS_NORECOMPUTE  = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS  = ON, ALLOW_PAGE_LOCKS  = ON) ON [PRIMARY]
  ) ON [PRIMARY]
  GO
  SET ANSI_NULLS ON
  GO
  SET QUOTED_IDENTIFIER ON
  GO
  CREATE TABLE [dbo].[loginLog](
  	[id] [int] IDENTITY(1,1) NOT NULL,
  	[username] [nchar](10) NULL,
  	[login_date] [nvarchar](50) NULL,
   CONSTRAINT [PK_loginLog] PRIMARY KEY CLUSTERED 
  (
  	[id] ASC
  )WITH (PAD_INDEX  = OFF, STATISTICS_NORECOMPUTE  = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS  = ON, ALLOW_PAGE_LOCKS  = ON) ON [PRIMARY]
  ) ON [PRIMARY]
  GO
  SET ANSI_NULLS ON
  GO
  SET QUOTED_IDENTIFIER ON
  GO
  SET ANSI_PADDING ON
  GO
  CREATE TABLE [dbo].[books](
  	[Id] [int] IDENTITY(1,1) NOT NULL,
  	[Resource number] [varchar](50) NULL,
  	[resources name] [varchar](50) NULL,
  	[creator] [varchar](50) NULL,
  	[illustrate] [varchar](100) NULL,
  	[URL] [varchar](225) NULL,
   CONSTRAINT [PK__books__3214EC0703317E3D] PRIMARY KEY CLUSTERED 
  (
  	[Id] ASC
  )WITH (PAD_INDEX  = OFF, STATISTICS_NORECOMPUTE  = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS  = ON, ALLOW_PAGE_LOCKS  = ON) ON [PRIMARY]
  ) ON [PRIMARY]
  GO
  SET ANSI_PADDING OFF
  GO
  
  ```

### Вид главного окна:

![image-20211208195231244.png](https://s2.loli.net/2021/12/10/KPMTZh3XeDmtgv1.png)

### Вид окна со списком ресурсов:

Вводим имя пользователя и пароль для входа  и нажимаем кнопку login , мы можем войти в интерфейс управления ресурсами :

![image-20211208195509567.png](https://s2.loli.net/2021/12/10/JvNUeYQhw8ycPl1.png)

![image-20211208195703355.png](https://s2.loli.net/2021/12/10/y32YVGUMfaF6bcL.png)

нажимаем кнопку "Управление ресурсами"

Теперь протестируем некоторые функции, которые работают с базой данных.

#### Test1-Добавление ресурса:

##### Ресурс 1

![image-20211208200614771.png](https://s2.loli.net/2021/12/10/AVkJN7iyW1cl3pu.png)

![image-20211208200644099.png](https://s2.loli.net/2021/12/10/SxMCPuyWKQ24EV5.png)

![image-20211208201843260.png](https://s2.loli.net/2021/12/10/lO2dK1MpksX3mgh.png)

##### Ресурс 2

![image-20211208201947697.png](https://s2.loli.net/2021/12/10/CMxsRoSm32Q6NnB.png)



![image-20211208195838600.png](https://s2.loli.net/2021/12/10/MZRoYphtKBJGu7U.png)

#### Test2 Поиск ресурса:

Поиск ресурса 1

- через ID ресурса

  ![image-20211208202008748.png](https://s2.loli.net/2021/12/10/l4LI1rNcXJSWpZw.png)

- через название ресурса

  ![image-20211208202021364.png](https://s2.loli.net/2021/12/10/kKgwmEC4bHSBTec.png)

- через создатель ресурса

  ![image-20211208202106217.png](https://s2.loli.net/2021/12/10/o4rmCV8i1sa2ERK.png)

- И так далее

  ![image-20211208202046106.png](https://s2.loli.net/2021/12/10/8GNdhfuKSWRMi1I.png)

  Если мы хотим найти ресурс, который не существует в базе данных

  ![image-20211208202410372](C:\Users\ydl74\AppData\Roaming\Typora\typora-user-images\image-20211208202410372.png)

​	то будет пусто:

![image-20211208202505652](C:\Users\ydl74\AppData\Roaming\Typora\typora-user-images\image-20211208202505652.png)

#### Test3 Изменение ресурса:

##### Изменение ресурса 1

![image-20211208202239767](C:\Users\ydl74\AppData\Roaming\Typora\typora-user-images\image-20211208202239767.png)

Нажимаем кнопку "Поменять"

![image-20211208202309622](C:\Users\ydl74\AppData\Roaming\Typora\typora-user-images\image-20211208202309622.png)

![image-20211208202319844](C:\Users\ydl74\AppData\Roaming\Typora\typora-user-images\image-20211208202319844.png)

Название ресурса 1 поменялось.

#### Test4 Удаление ресурса:

Сначала надо найти этот ресурс

![image-20211208202620597](C:\Users\ydl74\AppData\Roaming\Typora\typora-user-images\image-20211208202620597.png)

Потом нажимаем кнопку "ударить" 

![image-20211208202703491](C:\Users\ydl74\AppData\Roaming\Typora\typora-user-images\image-20211208202703491.png)

![image-20211208202716559](C:\Users\ydl74\AppData\Roaming\Typora\typora-user-images\image-20211208202716559.png)

Если мы хотим удалить несуществующий ресурс,например ресурс 1, то будет:

![image-20211208202915515](C:\Users\ydl74\AppData\Roaming\Typora\typora-user-images\image-20211208202915515.png)

Теперь только остался ресурс ID 2

![image-20211208202724515](C:\Users\ydl74\AppData\Roaming\Typora\typora-user-images\image-20211208202724515.png)

### Результат:

Основные функции протестированы на данный момент, эта модель программного обеспечения правильно работает как требование задания.



