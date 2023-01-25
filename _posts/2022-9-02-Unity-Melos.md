---
layout: post
title: Flutter Unity Widget + Melos = Clean Code!
---

What it is Melos?

Melos is a CLI tool used to help manage Dart projects with multiple packages.Splitting up large code bases into separate independently versioned packages is extremely useful for code sharing. However, making changes across many repositories is messy and difficult to track, and testing across repositories gets complicated.
Melos helps solve these issues by allowing multiple packages to work together within one repository, whilst being totally independent of each other.

How we can use Melos with Flutter Unity Widget?
Melos is very great tool which can simplificate work with Flutter, you can use commands to create own alias of popular flutter commands which you using
for example instend of using flutter clean you can use melos clean. Another example instend of use flutter pub run build_runner build --delete-conflicting-outputs you can create alias with this command and only type melos generate. Its simple isnt is ?

Structure of Melos with Unity.

![_config.yml]({{ site.baseurl }}/images/melos_structure.png)

Its realy clear, we create two packages app and unity. Both of them are independent and app package can only use scenes from unity package which are declarated in dev_unity file. 

![_config.yml]({{ site.baseurl }}/images/dev_unity.png)

Each package has independed core directory with elements like injectable logger and widgets.Create own core for pacakge is realy good decision because you can easy move one pacakge to diffrent project without any errors.

![_config.yml]({{ site.baseurl }}/images/core_unity_structure.png)


