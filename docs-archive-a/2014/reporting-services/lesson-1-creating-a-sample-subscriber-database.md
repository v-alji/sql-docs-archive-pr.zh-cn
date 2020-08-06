---
title: 第 1 课：创建示例订阅服务器数据库 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 47a882b7-efe5-4ee6-bef4-06118eb56903
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6ee49f0858b28c0c4b00fd391b0db7b4d2c54b16
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694293"
---
# <a name="lesson-1-creating-a-sample-subscriber-database"></a><span data-ttu-id="054cb-102">第 1 课：创建示例订阅服务器数据库</span><span class="sxs-lookup"><span data-stu-id="054cb-102">Lesson 1: Creating a Sample Subscriber Database</span></span>
  <span data-ttu-id="054cb-103">定义数据驱动的订阅前，必须具有可提供订阅数据的数据源。</span><span class="sxs-lookup"><span data-stu-id="054cb-103">Before you can define a data-driven subscription, you must have a data source that provides subscription data.</span></span> <span data-ttu-id="054cb-104">在此步骤中，您将创建一个小型数据库，以存储本教程中使用的订阅数据。</span><span class="sxs-lookup"><span data-stu-id="054cb-104">In this step, you will create a small database to store the subscription data used in this tutorial.</span></span> <span data-ttu-id="054cb-105">稍后在处理订阅时，报表服务器将检索此数据并使用它来自定义报表输出、传递选项和报表表示格式。</span><span class="sxs-lookup"><span data-stu-id="054cb-105">Later, when the subscription is processed, the report server retrieves this data and uses it to customize report output, delivery options, and report presentation format.</span></span>  
  
 <span data-ttu-id="054cb-106">本课程假定你使用 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 来创建 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="054cb-106">This lesson assumes you are using [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] to create a [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] database.</span></span>  
  
### <a name="to-create-a-sample-subscriber-database"></a><span data-ttu-id="054cb-107">创建示例订阅服务器数据库</span><span class="sxs-lookup"><span data-stu-id="054cb-107">To create a sample Subscriber database</span></span>  
  
1.  <span data-ttu-id="054cb-108">启动 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]，打开到[!INCLUDE[ssDE](../includes/ssde-md.md)]的连接。</span><span class="sxs-lookup"><span data-stu-id="054cb-108">Start [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], and open a connection to a [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="054cb-109">右键单击“数据库”，选择“新建数据库”  。</span><span class="sxs-lookup"><span data-stu-id="054cb-109">Right-click on Databases, select **New Database...**.</span></span>  
  
3.  <span data-ttu-id="054cb-110">在 "新建数据库" 对话框的 "数据库名称" 中，键入*订阅服务器*。</span><span class="sxs-lookup"><span data-stu-id="054cb-110">In the New Database dialog box, in Database Name, type *Subscribers*.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
4.  <span data-ttu-id="054cb-111">在工具栏中，单击“新建查询”按钮  。</span><span class="sxs-lookup"><span data-stu-id="054cb-111">Click the **New Query** button on the toolbar.</span></span>  
  
5.  <span data-ttu-id="054cb-112">将下列 [!INCLUDE[tsql](../includes/tsql-md.md)] 语句复制到空查询中：</span><span class="sxs-lookup"><span data-stu-id="054cb-112">Copy the following [!INCLUDE[tsql](../includes/tsql-md.md)] statements into the empty query:</span></span>  
  
    ```  
    Use Subscribers  
    CREATE TABLE [dbo].[OrderInfo] (  
        [SubscriptionID] [int] NOT NULL PRIMARY KEY ,  
        [Order] [nvarchar] (20) NOT NULL,  
        [FileType] [bit],  
        [Format] [nvarchar] (20) NOT NULL ,  
    ) ON [PRIMARY]  
    GO  
  
    INSERT INTO [dbo].[OrderInfo] (SubscriptionID, [Order], FileType, Format)   
    VALUES ('1', 'so43659', '1', 'IMAGE')  
    INSERT INTO [dbo].[OrderInfo] (SubscriptionID, [Order], FileType, Format)   
    VALUES ('2', 'so43664', '1', 'MHTML')  
    INSERT INTO [dbo].[OrderInfo] (SubscriptionID, [Order], FileType, Format)   
    VALUES ('3', 'so43668', '1', 'PDF')  
    INSERT INTO [dbo].[OrderInfo] (SubscriptionID, [Order], FileType, Format)   
    VALUES ('4', 'so71949', '1', 'Excel')  
    GO  
    ```  
  
6.  <span data-ttu-id="054cb-113">单击工具栏上的“!  在工具栏上执行。</span><span class="sxs-lookup"><span data-stu-id="054cb-113">Click **! Execute** on the toolbar.</span></span>  
  
7.  <span data-ttu-id="054cb-114">使用 SELECT 语句查看您是否有三行数据。</span><span class="sxs-lookup"><span data-stu-id="054cb-114">Use a SELECT statement to verify that you have three rows of data.</span></span> <span data-ttu-id="054cb-115">例如： `select * from OrderInfo`</span><span class="sxs-lookup"><span data-stu-id="054cb-115">For example: `select * from OrderInfo`</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="054cb-116">后续步骤</span><span class="sxs-lookup"><span data-stu-id="054cb-116">Next Steps</span></span>  
 <span data-ttu-id="054cb-117">您已成功创建了订阅数据，这些数据将为每个订阅服务器驱动报表分发并改变报表输出。</span><span class="sxs-lookup"><span data-stu-id="054cb-117">You have successfully created the subscription data that will drive report distribution and vary the report output for each subscriber.</span></span> <span data-ttu-id="054cb-118">下一步，将修改要分发给订阅服务器的报表的数据源属性。</span><span class="sxs-lookup"><span data-stu-id="054cb-118">Next, you will modify the data source properties of the report you will distribute to subscribers.</span></span> <span data-ttu-id="054cb-119">修改数据源属性是为了准备报表以实现数据驱动的订阅传递。</span><span class="sxs-lookup"><span data-stu-id="054cb-119">Modifying the data source properties is done to prepare the report for data-driven subscription delivery.</span></span> <span data-ttu-id="054cb-120">您还将修改报表设计以便包括订阅将用于订阅服务器数据的参数。</span><span class="sxs-lookup"><span data-stu-id="054cb-120">You will also modify the report design to include a parameter that the subscription will use with the subscriber data.</span></span> <span data-ttu-id="054cb-121">[第2课：修改报表数据源属性](lesson-2-modifying-the-report-data-source-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="054cb-121">[Lesson 2: Modifying the Report Data Source Properties](lesson-2-modifying-the-report-data-source-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="054cb-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="054cb-122">See Also</span></span>  
 <span data-ttu-id="054cb-123">[创建数据驱动订阅（SSRS 教程）](create-a-data-driven-subscription-ssrs-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="054cb-123">[Create a Data-Driven Subscription &#40;SSRS Tutorial&#41;](create-a-data-driven-subscription-ssrs-tutorial.md) </span></span>  
 <span data-ttu-id="054cb-124">[创建数据库](../relational-databases/databases/create-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="054cb-124">[Create a Database](../relational-databases/databases/create-a-database.md) </span></span>  
 [<span data-ttu-id="054cb-125">创建基本表报表（SSRS 教程）</span><span class="sxs-lookup"><span data-stu-id="054cb-125">Create a Basic Table Report &#40;SSRS Tutorial&#41;</span></span>](create-a-basic-table-report-ssrs-tutorial.md)  
  
  
