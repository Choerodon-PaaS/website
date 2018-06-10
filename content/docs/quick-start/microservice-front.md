﻿+++
title = "创建一个前端应用"
description = ""
weight = 3
+++

# 创建一个前端应用
---

## 概述

就前端主流技术框架的开发而言，过去几年里发展极快，在填补原有技术框架空白和不足的同时也渐渐趋于成熟。未来前端在已经趋向成熟的技术方向上面会慢慢稳定下来，并进入技术迭代优化阶段，但这并不代表前端领域技术就此稳定了，因为新的技术方向已经出现，并在等待下一个风口的到来。可能是虚拟现实也有可能是人工智能或者其他。

Choerodon 使用 React 作为前端的UI应用框架，并且对前端的展示做了一定的封装和处理，能够让用户方便快捷地进行前端应用的开发和部署。React和MobX是一对强力组合，React通过提供机制把应用状态转换为可渲染组件树并对其进行渲染。而MobX提供机制来存储和更新应用状态供React使用。 这种机制就是通过使用虚拟DOM来减少昂贵的DOM变化的数量。MobX 提供了优化应用状态与 React 组件同步的机制，这种机制就是使用响应式虚拟依赖状态图表，它只有在真正需要的时候才更新并且永远保持是最新的。

## 目标

本章节将从创建前端应用、开发前端应用、生成版本、部署应用、配置网络、配置域名等方面介绍，让读者能够熟悉使用Choerodon创建前端应用的步骤和流程，并且学会如何利用Choerodon创建并部署前端应用。


## 前置条件

**1.** 在操作之前保证[系统配置](../../user-guide/system-configuration)已经配置完全。特别在本章节用到的角色、环境管理等配置。

**2.** 完成[创建项目](../project)操作。本章节使用在前面章节创建的项目`猪齿鱼研发`。

**3.** <font>完成[创建环境](../../user-guide/deployment-pipeline/environment-pipeline)，环境流水线中有连接状态正常的环境。

**4.** 在Choerodon平台下，项目启动依赖于基础服务：


<h2 id="1">创建前端应用</h2>

**1.** 使用项目所有者或者源代码管理员的角色登录Choerodon系统，选择项目``猪齿鱼研发``。

**2.** 选择`持续交付`模块，点击`开发流水线`，点击`应用`，进入应用管理页面。

**3.** 点击``创建应用``，系统会从右边滑出页面，在页面中输入相关信息，有应用编码、应用名称，选择应用模板。

 -  应用编码：choerodon-front 

	<blockquote class="warning">
		   应用编码输入只能包含字母，数字，下划线，空格， '_', '.', "——"，只能以字母，数字，下划线开头。
		 </blockquote>
  
 - 应用名称：猪齿鱼前端应用
 
 - 选择应用模板: MicroServiceUI
	  <blockquote class="note">
       当应用模板不符合您的需求，您可手动创建一个[应用模板](../../user-guide/development-pipeline/application-template/)。
     </blockquote>
   
**4.** 点击`创建`，即可创建一个前端应用。
   
**5.** 当应用创建成功，可在应用管理界面查看到新建的应用。

**6.** 在创建应用的同时，系统还会在Gitlab中创建一个仓库，点击 ``仓库地址`` ，链接到Gitlab新建的仓库。

<blockquote class="note">
	Gitlab 仓库的名称是 choerodon-front，为应用编码。
</blockquote>  
 

<h2 id="2">开发前端应用</h2>

应用创建完成之后，开发前端应用。具体的操作步骤如下：

 **1. 创建分支**
 
 - 点击`应用`，进入到应用管理界面，选择`猪齿鱼前端应用`。
 -  点击右侧`分支管理`，点击`创建分支`，系统会从右边滑出页面，填写issue号，如feature-1。
 -  点击`创建`，即可创建一个分支。
 
 **2. 拉取代码仓库**
 
 在存放代码的文件夹下，打开git bash,输入命令`git clone [仓库地址]`，拉取所需应用的代码仓库。
 运行代码相关文档请查看[前端开发手册](../../development-guide/front/)。

  **3. 开发分支**

克隆成功后，进入应用根目录，执行命令`git checkout feature-1`，切换到新建分支feature-1，在此分支进行开发。

 - 创建目录
 
    在 \iam\src\app\iam\containers下新建organization文件夹
	
    在organization下新建一个功能文件夹\demo
	
    在demo文件夹下新建index.js、DemoIndex.js和Demo.js三个文件

 - 修改路由

       在\iam\src\app\iam\containers\IAMIndex.js文件中配置我们新建的文件的访问路径：
```
...
const DemoIndex = asyncRouter(() => import('./organization/demo/DemoIndex'));
    ...
    <Route path={`${match.url}/demo`} component={DemoIndex} />
    ...
```

 - 完成后，我们就可以进行相关页面的开发了，开发完成后，访问`/iam/demo`即可查看。

    相关代码如下：

    index.js

		
		import Demo from './DemoIndex';

		export default Demo;
		

     DemoIndex.js
	```
	import React from 'react';
	import {
	Route,
	Switch,
	} from 'react-router-dom';

	import asyncRouter from '../../../../../util/asyncRouter';

	const demo = asyncRouter(() => (import('./Demo')));

	const DemoIndex = ({ match }) => (
	<Switch>
	<Route exact path={match.url} component={demo} />
	</Switch>
	);
	export default DemoIndex;


	```

    Demo.js
	```
	import React, { Component } from 'react';
	import { Table } from 'antd';
	import { withRouter } from 'react-router-dom';

	class Demo extends Component {
	  componentDidMount() {
	  }

	  render() {
		return (
		  <div>
			hello world
		  </div>
		);
	  }
	}
	// withRouter添加history支持
	export default withRouter(Demo);

	```

 - 访问`localhost:9090/#/iam/demo`即可查看效果。

 - 下面来尝试一下从更复杂的场景，从后端获取10条用户信息并用表格的形式呈现。

     将上面的Demo.js的代码改为如下：

     Demo.js
	```
	import React, { Component } from 'react';
	import { Table } from 'antd';
	import axios from 'Axios';
	import { withRouter } from 'react-router-dom';

	const pretendUsers = [
	  {
		id: 1,
		name: '小明',
		description: '获取后端数据失败，此为模拟数据',
	  },
	  {
		id: 2,
		name: '小红',
		description: '获取后端数据失败，此为模拟数据',
	  },
	];

	class Demo extends Component {
	  constructor(props) {
		super(props);
		this.state = {
		  users: [],
		};
	  }

	  componentDidMount() {
		this.initUsers();
	  }

	  initUsers() {
		this.loadUsers()
		  .then((res) => {
			this.setState({ users: res });
		  })
		  .catch((error) => {
			this.setState({ users: pretendUsers });
		  });
	  }

	  loadUsers() {
		// 此处url为后端接口
		return axios.get('http://127.0.0.1:8080/test/v1/user');
	  }

	  render() {
		const columns = [{
		  title: '用户编号',
		  dataIndex: 'id',
		  key: 'id',
		}, {
		  title: '用户名',
		  dataIndex: 'name',
		  key: 'name',
		}, {
		  title: '描述',
		  dataIndex: 'description',
		  key: 'description',
		}];
		return (
		  <div style={{ margin: 20 }}>
			<Table
			  columns={columns}
			  dataSource={this.state.users}
			  pagination
			  rowKey={record => record.id}
			/>
		  </div>
		);
	  }
	}
	// withRouter添加history支持
	export default withRouter(Demo);

	```

 -  访问`localhost:9090/#/iam/demo`即可查看效果，至此，你已经掌握了简单的前后端搭配的开发方式了。
 

  **4. 提交代码**

	# 将本地代码变动提交到暂存区
	$ git add .
	# 提交代码并且为本次提交添加 commit 信息
	# 注：[FIX]修改bug  [ADD]新增  [IMP]完善  [DEL]删除
	$ git commit –m “[ADD]readme: 新增代码示例”
	# 将本地提交推送至远程仓库对应分支
	$ git push origin feature-1
		
**5. 代码集成**

基于feature分支运行CI。点击`持续集成`,查看 CI 执行情况。

**6. 结束分支**

 - 点击`应用`，进入应用管理，点击应用编码`choerodon-front`的`分支管理`。
 - 在分支列表找到`feature-1`，点击`结束分支`。


<h2 id="3">生成版本</h2>

 应用版本是代码提交的历史记录，每提交一次修改后的代码，对应生成一个新的版本。具体的操作步骤如下：

**1.** 结束分支之后，`feature-1`分支的代码会合并到`develop`分支，并触发Gitlab CI。
<blockquote class="note">
        Choerodon 缺省的 CI 流程有两个阶段:
        <ul>
            <li>克隆子库，编译打包</li>
            <li>构建docker镜像</li>
        </ul>
    </blockquote>

**2.** 点击``持续集成``，查看CI执行情况。

**3.** CI运行完成以后，点击`应用版本`进行查看，确定应用版本已经生成。


<h2 id="4">部署应用</h2>

  提供可视化、一键式部署应用，支持并行部署和流水线无缝集成，实现部署环境标准化和部署过程自动化。
  

 **1.** 使用部署管理员的角色登录Choerodon系统，选择项目``猪齿鱼研发``。
 
 **2.** 进入`持续交付`模块，选择`部署管理`，点击`应用部署`进入应用部署界面。
 
 **3.** 点击`部署应用`，系统会从右侧滑出部署应用界面，输入如下信息：
    

 -  选择应用：choerodon-front
 -  选择版本：刚才创建的应用版本
 -  选择环境： 选择要部署的环境
 -  配置信息：配置部署应用所需的信息
 -  部署模式：新建实例（新建一个应用）或 替换实例（滚动更新实例）
					
**4.**  点击`部署`按钮，即可完成部署。


<h2 id="5">查看实例部署详情</h2>

 **1.** 使用部署管理员的角色登录Choerodon系统，选择项目``猪齿鱼研发``。
 
 **2.** 进入`持续交付`模块，选择`部署管理`，点击`应用部署`进入应用部署界面。
 
 **3.** 点击`部署应用`即可查看实例。有四种查看视图，分别为：部署实例、单环境、单应用、多应用。

如何判断某版本的应用已经部署成功并通过？当实例出现在列表中，且实例名称后没有报错提示icon即为部署成功生成实例；当容器状态条为绿色，数值显示为1/1时表示容器数量为1且通过健康检查，点击右侧的`查看实例详情`，可以查看到阶段信息及日志。


<h2 id="4">配置网络</h2>

  为所选的应用配置网络。

 **1.**  使用部署管理员的角色登录Choerodon系统，选择项目``猪齿鱼研发``。
 
 **2.** 进入`持续交付`模块，选择`部署管理`，点击`网络`，进入网络配置界面。
 
 **3.** 点击`创建网络`，系统从右侧滑出创建网络界面，输入如下信息：

 - 环境名称：选择要部署的环境
 - 应用名称：猪齿鱼前端应用
 - 版本：刚才创建的应用版本
 - 实例：刚才部署的实例
 - 网络名称：名称默认为“应用编码-4位随机码”，且可手动修改
 - 外部IP：需要外网时填写
 - 端口号：应用开放端口

**4.** 点击`创建`按钮即可。

<h2 id="4">配置域名</h2>
  
  为所选的应用配置域名。

 **1.** 使用部署管理员的角色登录Choerodon系统，选择项目``猪齿鱼研发``。

 **2.** 进入`持续交付`模块，选择`部署管理`，点击`域名`，进入域名管理界面。
 
 **3.** 点击`创建域名`，系统会从右侧滑出界面，输入如下信息：
     

 - 域名：测试域名
 - 域名地址：choerodon.io
 - 路径：choerodon-front
 - 网络：配置的网络

**4.** 点击`创建`即可。

<h2 id="5">产品迭代</h2>

任何产品几乎都会经历产品的初创期、成长期、成熟期。在产品的初创期，需要通过快速试错探索出有用户黏性的功能；探索成功之后，就需要快速导入用户，这时候也会产生新的需求和新的问题，不断去完善产品；在产品的相对成熟期，则可以考虑产品的变现，和新功能的延展，以提升用户活跃。因此，当一个产品开发完成上线后，产品的周期化迭代就变得非常重要。固定的周期有助于为项目团队形成规范，从而提高开发效率。

Choerodon第一次发版前就准备好下个版本的需求。一般第一个版本上线后，开发人员就进入下一个版本的开发和测试。这样当问题暴露的时候，就可以迅速解决问题，优化到某个程度后，再放缓迭代节奏，这样就能更好的平衡好需求。







