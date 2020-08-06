---
title: 在90或更高版本的兼容模式下，CREATE STATISTICS 语句中不支持 WITH ROWS |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- WITH ROWS in CREATE STATISTICS statement
ms.assetid: 197b2ecf-a1a3-4a3a-a523-a0ee919c1dde
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d28a05e7cd025e213e2cebdce9d582a9df446fea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586082"
---
# <a name="with-rows-is-not-supported-in-create-statistics-statements-in-the-compatibility-mode-of-90-or-later"></a><span data-ttu-id="bbc0e-102">在 90 或更高的兼容模式下，CREATE STATISTICS 语句中不支持 WITH ROWS</span><span class="sxs-lookup"><span data-stu-id="bbc0e-102">WITH ROWS is not supported in CREATE STATISTICS statements in the compatibility mode of 90 or later</span></span>
  <span data-ttu-id="bbc0e-103">当运行兼容模式设置为 90 或更高的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 时，不支持在 CREATE STATISTICS 语句中指定 WITH ROWS。</span><span class="sxs-lookup"><span data-stu-id="bbc0e-103">Specifying WITH ROWS in CREATE STATISTICS statements is not supported when you run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] set to the compatibility mode of 90 or later.</span></span>  
  
## <a name="component"></a><span data-ttu-id="bbc0e-104">组件</span><span class="sxs-lookup"><span data-stu-id="bbc0e-104">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="bbc0e-105">纠正措施</span><span class="sxs-lookup"><span data-stu-id="bbc0e-105">Corrective Action</span></span>  
 <span data-ttu-id="bbc0e-106">通过指定带有示例*号*行或指定符合记录语法的其他选项，修改包含行的 CREATE STATISTICS 语句。</span><span class="sxs-lookup"><span data-stu-id="bbc0e-106">Modify CREATE STATISTICS statements that include WITH ROWS by specifying WITH SAMPLE *number* ROWS, or by specifying other options that comply with the documented syntax.</span></span> <span data-ttu-id="bbc0e-107">有关详细信息，请参阅 SQL Server 联机丛书中的 "CREATE STATISTICS (Transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="bbc0e-107">For more information, see the topic "CREATE STATISTICS (Transact-SQL) in SQL Server Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbc0e-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bbc0e-108">See Also</span></span>  
 <span data-ttu-id="bbc0e-109">[数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="bbc0e-109">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="bbc0e-110">SQL Server 2014 升级顾问 &#91;新&#93;</span><span class="sxs-lookup"><span data-stu-id="bbc0e-110">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
