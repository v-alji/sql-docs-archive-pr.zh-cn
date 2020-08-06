---
title: 任务16：验证主数据管理器 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 57ad9d3e-8f95-4df6-af01-c291ccf49164
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d1649582f97e9e08691726745e4ba14b2f8226bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689681"
---
# <a name="task-16-verifying-with-master-data-manager"></a><span data-ttu-id="abb80-102">任务 16：使用主数据管理器进行验证</span><span class="sxs-lookup"><span data-stu-id="abb80-102">Task 16: Verifying with Master Data Manager</span></span>
  <span data-ttu-id="abb80-103">在本任务中，您查看 SSIS 包所提交的批处理作业的状态并验证数据已使用主数据管理器上载到了 MDS 服务器。</span><span class="sxs-lookup"><span data-stu-id="abb80-103">In this task, you check the status of the batch job submitted by the SSIS package and verify that the data was uploaded to MDS server by using Master Data Manager.</span></span>  
  
1.  <span data-ttu-id="abb80-104">启动**主数据管理器** (`http://localhost/MDS`) 。</span><span class="sxs-lookup"><span data-stu-id="abb80-104">Launch **Master Data Manager** (`http://localhost/MDS`).</span></span> <span data-ttu-id="abb80-105">如果已打开，请单击顶部的 " **Microsoft SQL Server Master Data Services**切换到"**主页**"。</span><span class="sxs-lookup"><span data-stu-id="abb80-105">If it is already open, click **Microsoft SQL Server Master Data Services** at the top to switch to the **home page**.</span></span>  
  
2.  <span data-ttu-id="abb80-106">单击 "**集成管理**"。</span><span class="sxs-lookup"><span data-stu-id="abb80-106">Click **Integration Management**.</span></span>  
  
3.  <span data-ttu-id="abb80-107">请注意，在列表中有一个名为**EIMBatch**的批处理。</span><span class="sxs-lookup"><span data-stu-id="abb80-107">Notice that there is a batch with named **EIMBatch** that you submitted in the list.</span></span> <span data-ttu-id="abb80-108">如果看不到以下屏幕，请单击菜单栏上的 "**导入数据**"。</span><span class="sxs-lookup"><span data-stu-id="abb80-108">Click **Import Data** on the menu bar if you do not see the following screen.</span></span>  
  
     <span data-ttu-id="abb80-109">![EIM 批处理](../../2014/tutorials/media/et-verifyingwithmasterdatamanager.jpg "EIM 批处理")</span><span class="sxs-lookup"><span data-stu-id="abb80-109">![EIM Batch](../../2014/tutorials/media/et-verifyingwithmasterdatamanager.jpg "EIM Batch")</span></span>  
  
4.  <span data-ttu-id="abb80-110">单击顶部**SQL Server 2012 Master Data Services** ，切换回主页。</span><span class="sxs-lookup"><span data-stu-id="abb80-110">Switch back to the home page by click **SQL Server 2012 Master Data Services** at the top.</span></span>  
  
5.  <span data-ttu-id="abb80-111">确保为 "**模型**" 选择 "**供应商**模型"，为 "**版本**" 选择 " **VERSION_1** "，然后单击 "**资源管理器**"。</span><span class="sxs-lookup"><span data-stu-id="abb80-111">Make sure that **Suppliers** model is selected for **Model** and **VERSION_1** is selected for **Version**, and click **Explorer**.</span></span>  
  
6.  <span data-ttu-id="abb80-112">您可以看到数据 SSIS 包已导入 MDS。</span><span class="sxs-lookup"><span data-stu-id="abb80-112">You can see the data SSIS package imported into MDS.</span></span> <span data-ttu-id="abb80-113">数据应是清理的，并且没有重复的**代码**值 (注意： Excel 中的 "**供应商**" 列与 MDS) 中供应商实体的**Code**属性相对应。</span><span class="sxs-lookup"><span data-stu-id="abb80-113">The data should be cleansed and have no duplicates **Code** values (Note: **SupplierID** column in Excel corresponds to **Code** attribute of Supplier entity in MDS).</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="abb80-114">下一步</span><span class="sxs-lookup"><span data-stu-id="abb80-114">Next Step</span></span>  
 [<span data-ttu-id="abb80-115">任务 17：查看由 SSIS 包创建的 DQS 清理项目</span><span class="sxs-lookup"><span data-stu-id="abb80-115">Task 17: Reviewing DQS Cleansing Project Created by the SSIS package</span></span>](../../2014/tutorials/task-17-reviewing-dqs-cleansing-project-created-by-the-ssis-package.md)  
  
  
