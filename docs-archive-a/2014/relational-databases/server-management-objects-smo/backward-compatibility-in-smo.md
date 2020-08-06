---
title: SMO 中的向后兼容性 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: 2f986436-aaf2-4eaf-9809-df849d97d4fb
author: stevestein
ms.author: sstein
ms.openlocfilehash: 73b6f4eebccf23850ccf08ec95ccb59dbc5c6293
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586615"
---
# <a name="backward-compatibility-in-smo"></a><span data-ttu-id="e30cf-102">SMO 中的向后兼容性</span><span class="sxs-lookup"><span data-stu-id="e30cf-102">Backward Compatibility in SMO</span></span>
  <span data-ttu-id="e30cf-103">使用以前版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 编写的 SMO 应用程序可以通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中的 SMO 进行重新编译。</span><span class="sxs-lookup"><span data-stu-id="e30cf-103">SMO applications that were written using previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can be recompiled by using SMO in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="migrating-smo-applications"></a><span data-ttu-id="e30cf-104">迁移 SMO 应用程序</span><span class="sxs-lookup"><span data-stu-id="e30cf-104">Migrating SMO Applications</span></span>  
 <span data-ttu-id="e30cf-105">必须删除对旧版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中 SMO 动态链接库的引用，而且必须包括对随 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 提供的新 SMO 动态链接库的引用。</span><span class="sxs-lookup"><span data-stu-id="e30cf-105">References to SMO dlls in older versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be removed, and references to the new SMO dlls that are provided with [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] must be included.</span></span>  
  
 <span data-ttu-id="e30cf-106">至少要引用以下内容：</span><span class="sxs-lookup"><span data-stu-id="e30cf-106">Minimally, you would reference the following:</span></span>  
  
-   <span data-ttu-id="e30cf-107">Microsoft.SqlServer.ConnectionInfo</span><span class="sxs-lookup"><span data-stu-id="e30cf-107">Microsoft.SqlServer.ConnectionInfo</span></span>  
  
-   <span data-ttu-id="e30cf-108">Microsoft.SqlServer.Smo</span><span class="sxs-lookup"><span data-stu-id="e30cf-108">Microsoft.SqlServer.Smo</span></span>  
  
-   <span data-ttu-id="e30cf-109">Microsoft.SqlServer.Management.Sdk.Sfc</span><span class="sxs-lookup"><span data-stu-id="e30cf-109">Microsoft.SqlServer.Management.Sdk.Sfc</span></span>  
  
 <span data-ttu-id="e30cf-110">连接类、SMO 实用工具类和基础类都需要这些文件。</span><span class="sxs-lookup"><span data-stu-id="e30cf-110">These files are required for connection classes, SMO utility classes, and foundation classes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e30cf-111">SmoEnum.dll 已被移除，所以，必须从 SMO [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 项目中移除对它的引用。</span><span class="sxs-lookup"><span data-stu-id="e30cf-111">SmoEnum.dll has been removed so references to it must be removed from the SMO [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] project.</span></span>  
  
 <span data-ttu-id="e30cf-112">命名空间也已经更改，所以可以使用以下内容：</span><span class="sxs-lookup"><span data-stu-id="e30cf-112">The namespaces have also changed, so you can use the following:</span></span>  
  
##### <a name="for-visual-c"></a><span data-ttu-id="e30cf-113">对于 Visual C#</span><span class="sxs-lookup"><span data-stu-id="e30cf-113">For Visual C#</span></span>  
  
```  
using Microsoft.SqlServer.Management.Smo;  
using Microsoft.SqlServer.Management.Common;  
```  
  
##### <a name="for-visual-basic"></a><span data-ttu-id="e30cf-114">对于 Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e30cf-114">For Visual Basic</span></span>  
  
```  
Imports Microsoft.SqlServer.Management.Smo  
Imports Microsoft.SqlServer.Management.Common  
```  
  
 <span data-ttu-id="e30cf-115">如果您的代码使用 Urn 功能，例如 `Server.GetSqlSmoObject(Urn)`，则必须链接到 Microsoft.SqlServer.Management.Sdk.Sfc 命名空间。</span><span class="sxs-lookup"><span data-stu-id="e30cf-115">If your code uses Urn functionality, such as `Server.GetSqlSmoObject(Urn)`, you must link to the Microsoft.SqlServer.Management.Sdk.Sfc namespace.</span></span>  
  
 <span data-ttu-id="e30cf-116">如果您的代码直接使用 Transfer 对象，则需要链接到 Microsoft.SqlServer.Management.SmoExtended 命名空间。</span><span class="sxs-lookup"><span data-stu-id="e30cf-116">If your code uses the Transfer object directly, you will have to link to the Microsoft.SqlServer.Management.SmoExtended namespace.</span></span>  
  
 <span data-ttu-id="e30cf-117">迁移代码时，可能会需要修改代码。</span><span class="sxs-lookup"><span data-stu-id="e30cf-117">When you migrate code, you might have to modify the code.</span></span> <span data-ttu-id="e30cf-118">这是因为有若干 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 功能在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中已不推荐使用。</span><span class="sxs-lookup"><span data-stu-id="e30cf-118">This is because several [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] features have been deprecated in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="e30cf-119">有关不推荐使用的功能的详细信息，请参阅联机丛书中的[SQL Server 2014 中不推荐使用的数据库引擎功能](../../database-engine/deprecated-database-engine-features-in-sql-server-2016.md) [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e30cf-119">For more information about deprecated features, see [Deprecated Database Engine Features in SQL Server 2014](../../database-engine/deprecated-database-engine-features-in-sql-server-2016.md) in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Books Online.</span></span>  
  
  
