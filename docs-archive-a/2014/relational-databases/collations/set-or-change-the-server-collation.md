---
title: 设置或更改服务器排序规则 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- server collations [SQL Server]
- collations [SQL Server], server
ms.assetid: 3242deef-6f5f-4051-a121-36b3b4da851d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 35e7be051c8cf63a272f2bf42fb54b1c45ed4160
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591391"
---
# <a name="set-or-change-the-server-collation"></a><span data-ttu-id="76dfc-102">设置或更改服务器排序规则</span><span class="sxs-lookup"><span data-stu-id="76dfc-102">Set or Change the Server Collation</span></span>
  <span data-ttu-id="76dfc-103">服务器排序规则用作与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的实例一起安装的所有系统数据库以及任何新创建的用户数据库的默认排序规则。</span><span class="sxs-lookup"><span data-stu-id="76dfc-103">The server collation acts as the default collation for all system databases that are installed with the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and also any newly created user databases.</span></span> <span data-ttu-id="76dfc-104">服务器排序规则是在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装期间指定的。</span><span class="sxs-lookup"><span data-stu-id="76dfc-104">The server collation is specified during [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation.</span></span> <span data-ttu-id="76dfc-105">有关详细信息，请参阅 [排序规则和 Unicode 支持](collation-and-unicode-support.md)。</span><span class="sxs-lookup"><span data-stu-id="76dfc-105">For more information, see [Collation and Unicode Support](collation-and-unicode-support.md).</span></span>  
  
## <a name="changing-the-server-collation"></a><span data-ttu-id="76dfc-106">更改服务器排序规则</span><span class="sxs-lookup"><span data-stu-id="76dfc-106">Changing the Server Collation</span></span>  
 <span data-ttu-id="76dfc-107">更改 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的默认排序规则的操作可能会比较复杂，包括以下步骤：</span><span class="sxs-lookup"><span data-stu-id="76dfc-107">Changing the default collation for an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can be a complex operation and involves the following steps:</span></span>  
  
-   <span data-ttu-id="76dfc-108">确保具有重新创建用户数据库及这些数据库中的所有对象所需的全部信息或脚本。</span><span class="sxs-lookup"><span data-stu-id="76dfc-108">Make sure you have all the information or scripts needed to re-create your user databases and all the objects in them.</span></span>  
  
-   <span data-ttu-id="76dfc-109">使用工具（例如 [bcp Utility](../../tools/bcp-utility.md)）导出所有数据。</span><span class="sxs-lookup"><span data-stu-id="76dfc-109">Export all your data using a tool such as the [bcp Utility](../../tools/bcp-utility.md).</span></span> <span data-ttu-id="76dfc-110">有关详细信息，请参阅[批量导入和导出数据 (SQL Server)](../import-export/bulk-import-and-export-of-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="76dfc-110">For more information, see [Bulk Import and Export of Data &#40;SQL Server&#41;](../import-export/bulk-import-and-export-of-data-sql-server.md).</span></span>  
  
-   <span data-ttu-id="76dfc-111">删除所有用户数据库。</span><span class="sxs-lookup"><span data-stu-id="76dfc-111">Drop all the user databases.</span></span>  
  
-   <span data-ttu-id="76dfc-112">重新生成在 **setup** 命令的 SQLCOLLATION 属性中指定新的排序规则的 master 数据库。</span><span class="sxs-lookup"><span data-stu-id="76dfc-112">Rebuild the master database specifying the new collation in the SQLCOLLATION property of the **setup** command.</span></span> <span data-ttu-id="76dfc-113">例如：</span><span class="sxs-lookup"><span data-stu-id="76dfc-113">For example:</span></span>  
  
    ```  
    Setup /QUIET /ACTION=REBUILDDATABASE /INSTANCENAME=InstanceName   
    /SQLSYSADMINACCOUNTS=accounts /[ SAPWD= StrongPassword ]   
    /SQLCOLLATION=CollationName  
    ```  
  
     <span data-ttu-id="76dfc-114">有关详细信息，请参阅 [重新生成系统数据库](../databases/system-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="76dfc-114">For more information, see [Rebuild System Databases](../databases/system-databases.md).</span></span>  
  
-   <span data-ttu-id="76dfc-115">创建所有数据库及这些数据库中的所有对象。</span><span class="sxs-lookup"><span data-stu-id="76dfc-115">Create all the databases and all the objects in them.</span></span>  
  
-   <span data-ttu-id="76dfc-116">导入所有数据。</span><span class="sxs-lookup"><span data-stu-id="76dfc-116">Import all your data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="76dfc-117">可以为创建的每个新数据库指定默认排序规则，而不更改 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的默认排序规则。</span><span class="sxs-lookup"><span data-stu-id="76dfc-117">Instead of changing the default collation of an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you can specify a default collation for each new database you create.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76dfc-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="76dfc-118">See Also</span></span>  
 <span data-ttu-id="76dfc-119">[排序规则和 Unicode 支持](collation-and-unicode-support.md) </span><span class="sxs-lookup"><span data-stu-id="76dfc-119">[Collation and Unicode Support](collation-and-unicode-support.md) </span></span>  
 <span data-ttu-id="76dfc-120">[设置或更改数据库排序规则](set-or-change-the-database-collation.md) </span><span class="sxs-lookup"><span data-stu-id="76dfc-120">[Set or Change the Database Collation](set-or-change-the-database-collation.md) </span></span>  
 <span data-ttu-id="76dfc-121">[设置或更改列排序规则](set-or-change-the-column-collation.md) </span><span class="sxs-lookup"><span data-stu-id="76dfc-121">[Set or Change the Column Collation](set-or-change-the-column-collation.md) </span></span>  
 [<span data-ttu-id="76dfc-122">重新生成系统数据库</span><span class="sxs-lookup"><span data-stu-id="76dfc-122">Rebuild System Databases</span></span>](../databases/system-databases.md)  
  
  
