---
title: 在解决方案中移动项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- moving items
- solutions [SQL Server Management Studio], item relocation
- relocating items
ms.assetid: b40a24eb-f528-4e70-b26e-5eaf6e0ed1ed
author: stevestein
ms.author: sstein
ms.openlocfilehash: fd0a8a89686c62b4d4d00aea5479bb956fe3011f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689219"
---
# <a name="move-items-in-a-solution"></a><span data-ttu-id="6edb9-102">在解决方案中移动项</span><span class="sxs-lookup"><span data-stu-id="6edb9-102">Move Items in a Solution</span></span>
  <span data-ttu-id="6edb9-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 项目中的项目项为查询、连接和杂项文件。</span><span class="sxs-lookup"><span data-stu-id="6edb9-103">Project items in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] projects are Queries, Connections, and Miscellaneous files.</span></span> <span data-ttu-id="6edb9-104">在解决方案资源管理器中，可以在项目之间移动查询和杂项文件，但无法移动连接。</span><span class="sxs-lookup"><span data-stu-id="6edb9-104">You can move Queries and Miscellaneous Files between projects in Solution Explorer, but Connections cannot be moved.</span></span>  
  
### <a name="to-move-items-in-solution-explorer"></a><span data-ttu-id="6edb9-105">在解决方案资源管理器中移动项</span><span class="sxs-lookup"><span data-stu-id="6edb9-105">To move items in Solution Explorer</span></span>  
  
1.  <span data-ttu-id="6edb9-106">在解决方案资源管理器中，选择要移动的项。</span><span class="sxs-lookup"><span data-stu-id="6edb9-106">In Solution Explorer, select the item you want to move.</span></span>  
  
2.  <span data-ttu-id="6edb9-107">在“编辑”  菜单上，单击“剪切”  。</span><span class="sxs-lookup"><span data-stu-id="6edb9-107">On the **Edit** menu, click **Cut**.</span></span>  
  
3.  <span data-ttu-id="6edb9-108">在解决方案资源管理器中，选择目标位置。</span><span class="sxs-lookup"><span data-stu-id="6edb9-108">In Solution Explorer, select the destination.</span></span>  
  
4.  <span data-ttu-id="6edb9-109">在“编辑”  菜单上，单击“粘贴”  。</span><span class="sxs-lookup"><span data-stu-id="6edb9-109">On the **Edit** menu, click **Paste**.</span></span>  
  
 <span data-ttu-id="6edb9-110">可以通过在解决方案资源管理器中拖动查询和杂项文件来移动项。</span><span class="sxs-lookup"><span data-stu-id="6edb9-110">You can move items by dragging Query and Miscellaneous files within Solution Explorer.</span></span> <span data-ttu-id="6edb9-111">拖动可使您看到拖动操作的结果。</span><span class="sxs-lookup"><span data-stu-id="6edb9-111">Dragging allows you to see the outcome of the drag operation.</span></span> <span data-ttu-id="6edb9-112">将查询从一个项目类型移动到另一个项目类型可能会导致查询在目标项目中被视为杂项文件。</span><span class="sxs-lookup"><span data-stu-id="6edb9-112">Moving queries from one project type to another may cause queries to be considered as miscellaneous files in the target project.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6edb9-113">移动连接查询时不会移动与目标项目的连接。</span><span class="sxs-lookup"><span data-stu-id="6edb9-113">Moving a connected query does not move the connection to the target project.</span></span> <span data-ttu-id="6edb9-114">查询移动到目标项目之后，将丢失其原有连接。</span><span class="sxs-lookup"><span data-stu-id="6edb9-114">The query will lose its connection after it is moved to the target project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6edb9-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6edb9-115">See Also</span></span>  
 <span data-ttu-id="6edb9-116">[解决方案资源管理器](solution-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="6edb9-116">[Solution Explorer](solution-explorer.md) </span></span>  
 [<span data-ttu-id="6edb9-117">复制解决方案中的项</span><span class="sxs-lookup"><span data-stu-id="6edb9-117">Copy Items in a Solution</span></span>](copy-items-in-a-solution.md)  
  
  
