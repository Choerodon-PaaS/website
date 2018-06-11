﻿+++
title = "应用管理"
description = ""
weight = 2
+++

# 应用管理
 
应用是满足用户某些需求的程序代码的集合，一个系统可以被解耦成很多应用，每一个应用都可以独立部署，每一个应用仅关注于完成一部分任务，每部分任务代表一个小的业务模块，因此各应用之间关系是松耦合的。另外，每创建一个应用，系统会自动在 Gitlab 创建好对应的代码库。

只有该项目的项目所有者才能创建应用，项目成员仅能查看应用。
  
  - **菜单层次**：项目层
  - **菜单路径**：持续交付 > 开发流水线 > 应用
  - **默认角色**：项目所有者、项目成员
<blockquote class="note">
         项目成员对应用管理只有查看界面的权限，不可进行编辑修改。
      </blockquote>

### 创建应用

输入`应用编码`及`名称`，创建一个新的应用，步骤如下。您也可以选择一个应用模板，快速创建应用，平台会为您自动创建对应的 Git 库以便管理该应用代码。

 1. 点击 `创建应用` 按钮；

 1. 输入`应用编码`、`应用名称`、以及选择`应用模板`，点击 `创建` 按钮；

    应用编码：应用中自定义的编码。

    应用名称：应用中自定义的名称。

    应用模板：系统预定义模板或组织自定义的模板快。


           系统预定义模板：Java库-JavaLib;微服务-MicroService;web前端-MicroServiceUI
      
 1. 创建成功后，可去 Gitlab 中查看已创建的代码。

### 查看应用详情

  1. 点击`应用`，在应用管理界面，根据应用名称、应用编码、仓库地址、应用状态来查看应用详情。

列表字段

 - 应用名称：应用的自定义名称；
 - 应用编码：应用的自定义编码；
 - 仓库地址：应用 Git 仓库地址；
 - 应用状态：应用运行有三种状态，分别为启用、停用、创建中。

### 分支管理

点击`分支管理`→ ![分支管理按钮](/docs/user-guide/development-pipeline/image/branch_management_button.png) 对应用信息进行[分支管理](../../development-pipeline/branch-management)。

### 修改应用信息

点击`修改应用`→ ![修改应用按钮](/docs/user-guide/development-pipeline/image/update_app_button.png) 对应用信息进行修改。

### 停用/启用应用

 点击 `停用`→ ![停用按钮](/docs/user-guide/development-pipeline/image/stop_button.png) ，如： “猪齿鱼研发” 已停用，应用详情不可查看。 

 点击 `启用`→ ![启用按钮](/docs/user-guide/development-pipeline/image/start_button.png) ，如： “猪齿鱼研发” 已启用，可对该应用进行相关操作。
