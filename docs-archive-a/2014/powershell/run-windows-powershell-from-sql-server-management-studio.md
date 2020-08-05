---
title: 从 SQL Server Management Studio 运行 Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: 1f841825-da1f-4062-9a81-3cdbab03845b
author: stevestein
ms.author: sstein
ms.openlocfilehash: e0330e833aaa3344416a31aa700a2b1f6bb4a6e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581344"
---
# <a name="run-windows-powershell-from-sql-server-management-studio"></a><span data-ttu-id="0f9c0-102">从 SQL Server Management Studio 中运行 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f9c0-102">Run Windows PowerShell from SQL Server Management Studio</span></span>
  <span data-ttu-id="0f9c0-103">您可以在 **中从** “对象资源管理器” [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]启动 Windows PowerShell 会话。</span><span class="sxs-lookup"><span data-stu-id="0f9c0-103">You can start Windows PowerShell sessions from **Object Explorer** in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]<span data-ttu-id="0f9c0-104">启动 Windows PowerShell，加载 `sqlps` 模块，并将路径上下文设置为**对象资源管理器**树中的关联节点。</span><span class="sxs-lookup"><span data-stu-id="0f9c0-104">launches Windows PowerShell, loads the `sqlps` module, and sets the path context to the associated node in the **Object Explorer** tree.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="0f9c0-105">开始之前</span><span class="sxs-lookup"><span data-stu-id="0f9c0-105">Before You Begin</span></span>  
 <span data-ttu-id="0f9c0-106">为**对象资源管理器**中的对象指定正在运行的 powershell 时，将 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 启动一个 Windows powershell 会话，其中 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 加载并注册了 PowerShell 管理单元。</span><span class="sxs-lookup"><span data-stu-id="0f9c0-106">When you specify running PowerShell for an object in **Object Explorer**, [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] starts a Windows PowerShell session in which the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell snap-ins have been loaded and registered.</span></span> <span data-ttu-id="0f9c0-107">该会话的路径预设为您在对象资源管理器中右键单击的对象位置。</span><span class="sxs-lookup"><span data-stu-id="0f9c0-107">The path for the session is preset to the location of the object you right clicked in Object Explorer.</span></span> <span data-ttu-id="0f9c0-108">例如，如果在对象资源管理器中右键单击[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 数据库对象并选择\*\*\*\*“启动 PowerShell”，则 Windows PowerShell 路径将设置为：</span><span class="sxs-lookup"><span data-stu-id="0f9c0-108">For example, if you right-click the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database object in Object Explorer and select **Start PowerShell**, the Windows PowerShell path is set to the following:</span></span>  
  
```
SQLSERVER:\SQL\MyComputer\MyInstance\Databases\AdventureWorks2012>  
```  
  
## <a name="to-run-powershell-from-sql-server-management-studio"></a><span data-ttu-id="0f9c0-109">从 SQL Server Management Studio 运行 PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f9c0-109">To run PowerShell from SQL Server Management Studio</span></span> 
  
1.  <span data-ttu-id="0f9c0-110">打开**对象资源管理器**。</span><span class="sxs-lookup"><span data-stu-id="0f9c0-110">Open **Object Explorer**.</span></span>  
  
2.  <span data-ttu-id="0f9c0-111">导航到要进行处理的对象的节点。</span><span class="sxs-lookup"><span data-stu-id="0f9c0-111">Navigate to the node for the object to be worked on.</span></span>  
  
3.  <span data-ttu-id="0f9c0-112">右键单击该对象，然后选择\*\*\*\*“启动 PowerShell”。</span><span class="sxs-lookup"><span data-stu-id="0f9c0-112">Right-click the object and select **Start PowerShell**.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="0f9c0-113">权限</span><span class="sxs-lookup"><span data-stu-id="0f9c0-113">Permissions</span></span>  
 <span data-ttu-id="0f9c0-114">在从 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]打开 PowerShell 时，它不会使用管理员权限运行，这可能会阻止某些活动（如调用 WMI）。</span><span class="sxs-lookup"><span data-stu-id="0f9c0-114">When opened from [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], PowerShell does not run with Administrator privileges which may prevent some activities such as calls to WMI.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f9c0-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0f9c0-115">See Also</span></span>  
 [<span data-ttu-id="0f9c0-116">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f9c0-116">SQL Server PowerShell</span></span>](sql-server-powershell.md)  
