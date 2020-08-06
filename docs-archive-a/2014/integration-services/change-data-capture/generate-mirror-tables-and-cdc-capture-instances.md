---
title: 生成镜像表和 CDC 捕获实例 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- mirTab
ms.assetid: 260c1617-eecc-4007-a84d-3c5778ce46b6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 78daea310112cf7e9e78e489097fe9a76e69996b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87683021"
---
# <a name="generate-mirror-tables-and-cdc-capture-instances"></a><span data-ttu-id="e4995-102">生成镜像表和 CDC 捕获实例</span><span class="sxs-lookup"><span data-stu-id="e4995-102">Generate Mirror Tables and CDC Capture Instances</span></span>
  <span data-ttu-id="e4995-103">使用“生成镜像表”页可生成在 CDC 实例中包含的表的镜像表。</span><span class="sxs-lookup"><span data-stu-id="e4995-103">Use the Generate Mirror Tables page to generate the mirror tables for the tables you included in the CDC instance</span></span>  
  
 <span data-ttu-id="e4995-104">单击 **“运行”** 可创建镜像表。</span><span class="sxs-lookup"><span data-stu-id="e4995-104">Click **Run** to create the mirror tables.</span></span> <span data-ttu-id="e4995-105">将显示每个表的创建进度，并且将显示一条消息，通知您每个镜像表是成功完成还是存在错误。</span><span class="sxs-lookup"><span data-stu-id="e4995-105">The progress for the creation of each table is displayed and a message is displayed to let you know whether each mirror table is completed successfully or with errors.</span></span> <span data-ttu-id="e4995-106">如果出现任何错误，请单击 **“详细信息”** 以便查看含错误说明的对话框。</span><span class="sxs-lookup"><span data-stu-id="e4995-106">If any errors occur, click **Details** to see a dialog box with an explanation of the error.</span></span>  
  
 <span data-ttu-id="e4995-107">如果任何表无法创建，您可以选择是继续还是在继续前删除失败的表。</span><span class="sxs-lookup"><span data-stu-id="e4995-107">If any of the tables fail to be created, you can choose to continue or delete any tables that failed before continuing.</span></span> <span data-ttu-id="e4995-108">在向导运行完毕后，您可以决定是在 Oracle 源数据库中修复该表还是不在 CDC 实例中使用它。</span><span class="sxs-lookup"><span data-stu-id="e4995-108">After you finish running the wizard, you can decide whether to fix the table in the Oracle source database or not use it in the CDC instance.</span></span> <span data-ttu-id="e4995-109">如果您修复该表，则可以在 [Edit Tables](edit-tables.md)时添加该表。</span><span class="sxs-lookup"><span data-stu-id="e4995-109">If you fix the table, you can add it when you [Edit Tables](edit-tables.md).</span></span>  
  
 <span data-ttu-id="e4995-110">单击 **“下一步”** 以便打开 [Finish](finish.md) 页。</span><span class="sxs-lookup"><span data-stu-id="e4995-110">Click **Next** to open the [Finish](finish.md) page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4995-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e4995-111">See Also</span></span>  
 [<span data-ttu-id="e4995-112">如何创建 SQL Server 更改数据库实例</span><span class="sxs-lookup"><span data-stu-id="e4995-112">How to Create the SQL Server Change Database Instance</span></span>](how-to-create-the-sql-server-change-database-instance.md)  
  
  
