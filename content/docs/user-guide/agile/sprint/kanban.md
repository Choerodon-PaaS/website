﻿+++
title = "多看板"
description = "了解多看板的定义，以及如何运用多看板来进行团队协作"
weight = 4
+++

# 多看板

## 什么是多看板

多看板是指您可以根据自身需求创建多个不同的看板，自行设置看板状态来管理与自己有关的工作。对于项目团队中的不同成员来说，一个看板可能难以满足自身任务计划的需求，并且，同一个任务可能对于不同的成员来说，进度状态可能是不同的，所以您可能需要在总冲刺看板之外，另建一块看板来单独管理你关心的问题。

比如在总冲刺看板中，目前有`待处理`、`处理中`、`已完成`三种状态，针对您个人的工作，您可能还想对`处理中`进行进一步细化，将其分为`处理中`、`审核中`，但是同时又不能影响总冲刺看板，因此，您可以另建一块看板，新看板将同步总看板的所有问题，您可以通过更改新看板的列配置和状态配置，来跟踪问题。

![enter description here](/docs/user-guide/agile/imge/create-kanban.png)


1. 点击`创建看板`可创建新的看板，新看板将同步原有看板的所有问题。

    <blockquote class="note">新创建的看板会同步原有看板的问题状态，作为看板最开始显示的状态。</blockquote>

2. 点击下拉菜单可切换显示不同的看板。
3. 点击配置可对当前看板的列和状态进行自定义配置，详情请点击[看板配置](../manage-kanban)查看。

    <blockquote class="note">问题只和状态有关，所以不同的看板里问题可能会放在不同的列中。</blockquote>


## 多看板实例

假设现在有三个小组共同参与这个项目的冲刺，分别是产品组、开发组、测试组。在冲刺看板中，目前共有三个问题，编号分别为32、33、34；目前该看板配置有三列，分别为`待处理`、`处理中`、`已完成`。

> **按照冲刺逻辑，当一个任务开始进行处理时，该问题卡片将会被拖到`处理中`这一列。**

![enter description here](/docs/user-guide/agile/imge/kanban-case.png)

但是此任务需要三个小组接力完成，只有当产品组完成需求分析与设计，开发组才能开始处理问题，开发完毕后测试才能开始工作。因此，当产品组将任务拖动到`处理中`这一列时，对于开发组和来说，这件任务实际上应该归属于`待处理`。

并且每个组对问题状态的需求都有所不同，对于产品组来说问题的状态可能是“需求池”、“分析”、“开发就绪”等，而对于开发来说是“开发就绪”“开发中”等，这就出现了不同用户对于同一问题不同的管理需求。

如何使问题的状态与列匹配，符合各小组或者各人的需求，就需要用到多看板了。

> **通过多看板功能，各小组可以各自新建一个看板，更改问题的状态所属列，来自定义符合自己任务进度的看板。**

比如，产品组“1号看板”的配置：修改问题状态为“需求池”、“分析”和“开发就绪”，分别归属于`待处理`、`处理中`、`已完成`三列，其他无关状态拖动到`未对应的状态`中，其配置页面如下图所示。

![enter description here](/docs/user-guide/agile/imge/kanban-case1.png)

1. 点击此处可以添加新的状态。
2. 点击此处可以修改状态的名称。
3. 显示的是“1号看板”的状态配置，分别是“需求池”、“分析”和“开发就绪”。
4. 将其他与该组无关的状态，拖动到`未对应的状态`下面，这些状态将不会再“1号看板”中出现。
5. 点击“X”删除这个状态。
6. 注意此处的`设置已完成`不能点选。
7. 点击移动按钮可以移动列的位置。
8. 点击删除按钮删除该列。

<blockquote class="note">
`设置已完成`表示该状态是问题完成进度中最后一个状态，如果将问题拖动到了某个设置了该选项的状态中，则表示这个问题在总冲刺中已全部完成。
  </blockquote>

开发组“2号看板”的配置：将“开发就绪”移动到`待处理`一列中，将“开发中”移动到`处理中`一列，将“测试就绪”移动到`已完成`一列，其他无关状态都拖动到`未对应状态`中。

测试组“3号看板”的配置：将“测试就绪”移动到`待处理`一列中，将“测试中”移动到`处理中`一列，将“测试完成”移动到`已完成`一列，其他无关状态都拖动到`未对应状态`中，另外，由于测试组是最后一个任务小组，“测试完成”这个状态是最后一个状态，因此要在该状态的配置中点击`设置已完成`。

三个看板的显示页面如下：

![enter description here](/docs/user-guide/agile/imge/kanban-case2.png)

当产品组完成了34号问题时，会在产品组的“1号看板”中将34号问题拖动到`已完成`一列，此时34号问题会出现在“2号看板”的`待处理`一列，等待开发组的处理。同时，“1号看板”中还在处理中的33号问题，不会出现在“2号看板”和“3号看板”上。

当开发组完成了32号问题时，可将其拖动到`已完成`一列，此时32号问题会出现在“3号看板”的待处理一列中。

同样，已经经过产品组处理的32号问题，不会再出现在“1号看板”中。

## 下一步

[**结束冲刺**](../close-sprint):通过此页面，您将了解如何结束一个冲刺并关闭其对应的看板。

## 更多操作

- [什么是看板？](../../sprint)
- [如何使用看板](../../sprint/manage-kanban)
- [发布版本](../../release)





