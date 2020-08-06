---
title: 任务3：验证主数据管理器中的数据 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: d88953d2-2258-40ac-b3bf-2ef502f9b5fd
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: aed5a76cff9d90b81f02f6af11b6fc437efee14e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578573"
---
# <a name="task-3-verifying-the-data-in-master-data-manager"></a><span data-ttu-id="fe617-102">任务 3：在主数据管理器中验证数据</span><span class="sxs-lookup"><span data-stu-id="fe617-102">Task 3: Verifying the Data in Master Data Manager</span></span>
  <span data-ttu-id="fe617-103">在此任务中，将使用**主数据管理器 Web 应用程序**验证是否在**MDS**上创建了**供应商**实体。</span><span class="sxs-lookup"><span data-stu-id="fe617-103">In this task, you verify that the **Supplier** entity is created on **MDS** using **Master Data Manager Web Application**.</span></span>

1.  <span data-ttu-id="fe617-104">如果**主数据管理器**已经打开，请单击顶部**SQL Server 2012 Master Data Services** ，导航到主页。</span><span class="sxs-lookup"><span data-stu-id="fe617-104">If **Master Data Manager** is already open, click **SQL Server 2012 Master Data Services** at the top to navigate to the home page.</span></span> <span data-ttu-id="fe617-105">否则，请导航到 `http://localhost/MDS` 以启动**主数据管理器**。</span><span class="sxs-lookup"><span data-stu-id="fe617-105">Otherwise, navigate to `http://localhost/MDS` to launch **Master Data Manager**.</span></span>

2.  <span data-ttu-id="fe617-106">选择 "**型号**的**供应商**"，然后单击 "**资源管理器**"。</span><span class="sxs-lookup"><span data-stu-id="fe617-106">Select **Suppliers** for **Model**, and click **Explorer**.</span></span>

     <span data-ttu-id="fe617-107">![“主数据管理器 - 资源管理器”按钮](../../2014/tutorials/media/et-verifyingthedatainmasterdatamanager.jpg "“主数据管理器 - 资源管理器”按钮")</span><span class="sxs-lookup"><span data-stu-id="fe617-107">![Master Data Manager - Explorer Button](../../2014/tutorials/media/et-verifyingthedatainmasterdatamanager.jpg "Master Data Manager - Explorer Button")</span></span>

3.  <span data-ttu-id="fe617-108">查看存储在 MDS 上的数据。</span><span class="sxs-lookup"><span data-stu-id="fe617-108">Review the data stored on MDS.</span></span> <span data-ttu-id="fe617-109">如果看不到数据，请在启动 "**资源管理器**" 之前确认在主页上选择了**模型**的 "**供应商**"。</span><span class="sxs-lookup"><span data-stu-id="fe617-109">If you do not see the data, confirm that you selected **Suppliers** for the **Model** on the home page before launching **Explorer**.</span></span> <span data-ttu-id="fe617-110">您可以通过使用工具栏上的 "**添加成员**" 和 "**删除成员**" 按钮，在供应商列表中添加或删除。</span><span class="sxs-lookup"><span data-stu-id="fe617-110">You can add to or delete from the supplier list by using **Add Member** and **Delete Member** buttons on the toolbar.</span></span>

## <a name="next-step"></a><span data-ttu-id="fe617-111">下一步</span><span class="sxs-lookup"><span data-stu-id="fe617-111">Next Step</span></span>
 [<span data-ttu-id="fe617-112">任务 4 &#40;可选&#41;：合并、匹配和发布新数据集</span><span class="sxs-lookup"><span data-stu-id="fe617-112">Task 4 &#40;Optional&#41;: Combining, Matching, and Publishing New Set of Data</span></span>](../../2014/tutorials/task-4-optional-combining-matching-and-publishing-new-set-of-data.md)


