---
title: django
date: 2018-04-20 20:16:00
tags:
categories:
toc: true
keywords:
description:
comments: true
---

# 安装

django安装

```
pip install Django
```



# 创建项目

```
django-admin startproject mysite
```



# 运行项目

```
python manage.py runserver
```

# 不指定APP,就导出所有的数据
```
python manage.py dumpdata [app] > app_data.json
```

# 导入数据
```
python manage.py loaddata app_data.json
```

# django开发文档



https://docs.djangoproject.com/zh-hans/3.0/ 