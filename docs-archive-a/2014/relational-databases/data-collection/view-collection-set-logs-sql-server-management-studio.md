---
title: 查看收集组日志 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], viewing
- collection sets [SQL Server], viewing logs
ms.assetid: 428908b8-fb6a-4d0c-8339-ee133e23aad2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ab7c49e72690b76fa9f416a835f7b5b7b3a4553d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589709"
---
# <a name="view-collection-set-logs-sql-server-management-studio"></a><span data-ttu-id="87a4e-102">查看收集日志 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="87a4e-102">View Collection Set Logs (SQL Server Management Studio)</span></span>
  <span data-ttu-id="87a4e-103">您可以从 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]查看所有收集组日志或单个收集组日志。</span><span class="sxs-lookup"><span data-stu-id="87a4e-103">You can view all the collection set logs or individual collection set logs from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
### <a name="to-view-collection-set-logs"></a><span data-ttu-id="87a4e-104">查看收集组日志</span><span class="sxs-lookup"><span data-stu-id="87a4e-104">To view collection set logs</span></span>  
  
1.  <span data-ttu-id="87a4e-105">在对象资源管理器中，展开 **“管理”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="87a4e-105">In Object Explorer, expand the **Management** folder.</span></span>  
  
2.  <span data-ttu-id="87a4e-106">右键单击“数据收集”  ，然后单击“查看日志”  。</span><span class="sxs-lookup"><span data-stu-id="87a4e-106">Right-click **Data Collection**, and then click **View Logs**.</span></span>  
  
     <span data-ttu-id="87a4e-107">将会打开“日志文件查看器”  。每个收集组的所有日志文件都会在该查看器的“数据收集”  节点下列出并预先选中。</span><span class="sxs-lookup"><span data-stu-id="87a4e-107">This opens the **Log File Viewer**.All the log files for each collection set are listed and pre-selected under the **Data Collection** node in the viewer.</span></span>  
  
3.  <span data-ttu-id="87a4e-108">若要查看特定的收集组日志，请清除您不希望查看其日志的各收集组旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="87a4e-108">To view specific collection set logs, clear the check box next to each collection set whose log you do not want to view.</span></span> <span data-ttu-id="87a4e-109">针对该收集组的日志信息将会从 **“日志文件查看器”** 的详细信息窗格中删除。</span><span class="sxs-lookup"><span data-stu-id="87a4e-109">The log information for that collection set is removed from the **Log File Viewer** details pane.</span></span>  
  
### <a name="to-view-a-specific-collection-set-log-file"></a><span data-ttu-id="87a4e-110">查看特定的收集组日志文件</span><span class="sxs-lookup"><span data-stu-id="87a4e-110">To view a specific collection set log file</span></span>  
  
1.  <span data-ttu-id="87a4e-111">在对象资源管理器中，展开 **“管理”** 文件夹，然后展开 **“数据收集”** 。</span><span class="sxs-lookup"><span data-stu-id="87a4e-111">In Object Explorer, expand the **Management** folder, and then expand **Data Collection**.</span></span>  
  
2.  <span data-ttu-id="87a4e-112">右键单击要查看其日志的收集组，然后单击“查看日志”  。</span><span class="sxs-lookup"><span data-stu-id="87a4e-112">Right-click the collection set whose log you want to view, and then click **View Logs**.</span></span>  
  
     <span data-ttu-id="87a4e-113">将打开 **“日志文件查看器”** ，其中仅显示所选收集组的日志文件。</span><span class="sxs-lookup"><span data-stu-id="87a4e-113">The **Log File Viewer** opens, displaying only the log file for the collection set that you selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87a4e-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="87a4e-114">See Also</span></span>  
 <span data-ttu-id="87a4e-115">[数据收集](data-collection.md) </span><span class="sxs-lookup"><span data-stu-id="87a4e-115">[Data Collection](data-collection.md) </span></span>  
 [<span data-ttu-id="87a4e-116">管理数据收集</span><span class="sxs-lookup"><span data-stu-id="87a4e-116">Manage Data Collection</span></span>](manage-data-collection.md)  
  
  
