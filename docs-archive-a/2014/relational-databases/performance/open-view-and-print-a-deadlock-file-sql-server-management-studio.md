---
title: 打开、查看和打印死锁文件 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- deadlocks [SQL Server], printing files
- deadlocks [SQL Server], opening files
- opening deadlock files
- printing deadlock files
ms.assetid: 5061b13f-2cb7-457a-b8d0-fbd437b510ab
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 08bacd7a99e45e10163216c69057b167088441ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588483"
---
# <a name="open-view-and-print-a-deadlock-file-sql-server-management-studio"></a><span data-ttu-id="52623-102">打开、查看和打印死锁文件 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="52623-102">Open, View, and Print a Deadlock File (SQL Server Management Studio)</span></span>
  <span data-ttu-id="52623-103">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 生成死锁时，您可以捕获死锁信息并将死锁信息保存到文件。</span><span class="sxs-lookup"><span data-stu-id="52623-103">When [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] generates a deadlock, you can capture and save the deadlock information to a file.</span></span> <span data-ttu-id="52623-104">保存死锁文件后，可以在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中将其打开以进行查看或打印。</span><span class="sxs-lookup"><span data-stu-id="52623-104">After you have saved the deadlock file, you can open it in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to view or print.</span></span>  
  
### <a name="to-open-and-view-a-deadlock-file"></a><span data-ttu-id="52623-105">打开和查看死锁文件</span><span class="sxs-lookup"><span data-stu-id="52623-105">To open and view a deadlock file</span></span>  
  
1.  <span data-ttu-id="52623-106">在中的 "**文件**" 菜单上 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，指向 "**打开**"，然后单击 "**文件**"。</span><span class="sxs-lookup"><span data-stu-id="52623-106">On the **File** menu in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], point to **Open**, and then click **File**.</span></span>  
  
2.  <span data-ttu-id="52623-107">在 **“打开文件”** 对话框的 **“文件类型”** 框中选择 .xdl 文件类型。</span><span class="sxs-lookup"><span data-stu-id="52623-107">In the **Open File** dialog box, select the .xdl file type in the **Files of type** box.</span></span> <span data-ttu-id="52623-108">现在，您将获得一个经过筛选的只包含死锁文件的列表。</span><span class="sxs-lookup"><span data-stu-id="52623-108">You will now have a filtered list of only deadlock files.</span></span>  
  
### <a name="to-print-a-deadlock-file"></a><span data-ttu-id="52623-109">打印死锁文件</span><span class="sxs-lookup"><span data-stu-id="52623-109">To print a deadlock file</span></span>  
  
1.  <span data-ttu-id="52623-110">在 **中的** “文件” [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]菜单上，指向 **“打开”** ，然后单击 **“文件”**。</span><span class="sxs-lookup"><span data-stu-id="52623-110">On the **File** menu in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], point to **Open,** and then click **File**.</span></span>  
  
2.  <span data-ttu-id="52623-111">在 **“打开文件”** 对话框的 **“文件类型”** 框中选择 .xdl 文件类型。</span><span class="sxs-lookup"><span data-stu-id="52623-111">In the **Open File** dialog box, select the .xdl file type in the **Files of type** box.</span></span> <span data-ttu-id="52623-112">现在，您将获得一个经过筛选的只包含死锁文件的列表。</span><span class="sxs-lookup"><span data-stu-id="52623-112">You will now have a filtered list of only deadlock files.</span></span>  
  
3.  <span data-ttu-id="52623-113">选择要打印的死锁文件，然后单击 **“打开”**。</span><span class="sxs-lookup"><span data-stu-id="52623-113">Select the deadlock file you want to print, and click **Open**.</span></span>  
  
4.  <span data-ttu-id="52623-114">在 **“文件”** 菜单上，单击 **“打印”**。</span><span class="sxs-lookup"><span data-stu-id="52623-114">On the **File** menu, click **Print.**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52623-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="52623-115">See Also</span></span>  
 [<span data-ttu-id="52623-116">保存死锁图形 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="52623-116">Save Deadlock Graphs &#40;SQL Server Profiler&#41;</span></span>](save-deadlock-graphs-sql-server-profiler.md)  
  
  
