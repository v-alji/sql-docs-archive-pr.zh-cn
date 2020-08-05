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
# <a name="run-windows-powershell-from-sql-server-management-studio"></a>从 SQL Server Management Studio 中运行 Windows PowerShell
  您可以在 **中从** “对象资源管理器” [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]启动 Windows PowerShell 会话。 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]启动 Windows PowerShell，加载 `sqlps` 模块，并将路径上下文设置为**对象资源管理器**树中的关联节点。  
  
## <a name="before-you-begin"></a>开始之前  
 为**对象资源管理器**中的对象指定正在运行的 powershell 时，将 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 启动一个 Windows powershell 会话，其中 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 加载并注册了 PowerShell 管理单元。 该会话的路径预设为您在对象资源管理器中右键单击的对象位置。 例如，如果在对象资源管理器中右键单击[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 数据库对象并选择****“启动 PowerShell”，则 Windows PowerShell 路径将设置为：  
  
```
SQLSERVER:\SQL\MyComputer\MyInstance\Databases\AdventureWorks2012>  
```  
  
## <a name="to-run-powershell-from-sql-server-management-studio"></a>从 SQL Server Management Studio 运行 PowerShell 
  
1.  打开**对象资源管理器**。  
  
2.  导航到要进行处理的对象的节点。  
  
3.  右键单击该对象，然后选择****“启动 PowerShell”。  
  
## <a name="permissions"></a>权限  
 在从 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]打开 PowerShell 时，它不会使用管理员权限运行，这可能会阻止某些活动（如调用 WMI）。  
  
## <a name="see-also"></a>另请参阅  
 [SQL Server PowerShell](sql-server-powershell.md)  
