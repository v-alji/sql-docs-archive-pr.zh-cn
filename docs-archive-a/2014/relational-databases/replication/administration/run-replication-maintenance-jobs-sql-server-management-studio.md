---
title: 运行复制维护作业 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server replication]
ms.assetid: 0dc485a0-5a50-41eb-a29d-f2b2fb920174
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9dc27c65e96a9f956ffa6d3edf9c72ed52f721a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691698"
---
# <a name="run-replication-maintenance-jobs-sql-server-management-studio"></a>执行复制维护作业 (SQL Server Management Studio)
  复制使用下列维护作业：  
  
-   **重新初始化数据验证失败的订阅**
-   **代理历史记录清除：分发**
-   **分发的复制监视刷新器。**
-   **复制代理检查**
-   **分发清除：分发**
-   **过期订阅清除**  
  
 从 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 的“作业”文件夹和复制监视器的“代理”选项卡启动和停止这些作业 。 有关启动复制监视器的信息，请参阅[启动复制监视器](../monitor/start-the-replication-monitor.md)。 在“作业属性 - \<Job>”对话框中查看和修改每个作业的属性，可从同一文件夹和选项卡中访问此对话框。  
  
### <a name="to-start-or-stop-a-replication-maintenance-job-in-management-studio"></a>在 Management Studio 中启动或停止复制维护作业  
  
1.  在 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]中连接到分发服务器，然后展开服务器节点。  
  
2.  展开 **“SQL Server 代理”** 文件夹，再展开 **“作业”** 文件夹。  
  
3.  右键单击一个作业，然后单击 **“启动作业”** 或 **“停止作业”** 。  
  
### <a name="to-start-or-stop-a-replication-maintenance-job-in-replication-monitor"></a>在复制监视器中启动或停止复制维护作业  
  
1.  在复制监视器中，展开发布服务器组，然后选择一个发布服务器。  
  
2.  单击 **“代理”** 选项卡。  
  
3.  在网格中右键单击一个作业，然后单击 **“启动作业”** 或 **“停止作业”** 。  
  
### <a name="to-view-and-modify-properties-for-a-replication-maintenance-job-in-management-studio"></a>在 Management Studio 中查看和修改复制维护作业的属性  
  
1.  在 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]中连接到分发服务器，然后展开服务器节点。  
  
2.  展开 **“SQL Server 代理”** 文件夹，再展开 **“作业”** 文件夹。  
  
3.  右键单击一个作业，然后单击 **“属性”** 。  
  
4.  在“作业属性 - \<Job>”对话框中，根据需要修改任意属性，然后单击“确定” 。  
  
### <a name="to-view-and-modify-properties-for-a-replication-maintenance-job-in-replication-monitor"></a>在复制监视器中查看和修改复制维护作业的属性  
  
1.  在复制监视器中，展开发布服务器组，然后选择一个发布服务器。  
  
2.  单击 **“代理”** 选项卡。  
  
3.  在网格中右键单击一个作业，然后单击 **“属性”** 。  
  
4.  在“作业属性 - \<Job>”对话框中，根据需要修改任意属性，然后单击“确定” 。  
  
## <a name="see-also"></a>另请参阅  
 [启动和停止复制代理 (SQL Server Management Studio)](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)   
 [使用复制监视器查看信息和执行任务](../monitor/view-information-and-perform-tasks-replication-monitor.md)   
 [复制代理管理](../agents/replication-agent-administration.md)  
  
  
