---
title: 在升级过程中，验证压缩驱动器上没有任何数据库文件。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- compressed drives [SQL Server]
ms.assetid: 63be6853-c54a-42b2-ae1a-db2175f1d28e
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 9c04f7890ba8d8efe64afaf11b922af156c5de46
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578011"
---
# <a name="verify-that-no-database-files-are-on-compressed-drives-during-the-upgrade-process"></a><span data-ttu-id="808c4-102">确保升级过程中压缩驱动器上没有任何数据库文件</span><span class="sxs-lookup"><span data-stu-id="808c4-102">Verify that no database files are on compressed drives during the upgrade process</span></span>
  <span data-ttu-id="808c4-103">升级顾问检测到压缩驱动器上有数据库文件。</span><span class="sxs-lookup"><span data-stu-id="808c4-103">Upgrade Advisor detected database files on a compressed drive.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="808c4-104">无法在压缩驱动器上创建或升级数据库。</span><span class="sxs-lookup"><span data-stu-id="808c4-104">cannot create or upgrade databases on compressed drives.</span></span>  
  
## <a name="component"></a><span data-ttu-id="808c4-105">组件</span><span class="sxs-lookup"><span data-stu-id="808c4-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="808c4-106">纠正措施</span><span class="sxs-lookup"><span data-stu-id="808c4-106">Corrective Action</span></span>  
 <span data-ttu-id="808c4-107">安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 时，请为系统数据库选择非压缩驱动器，并验证要升级的数据库不在压缩驱动器上。</span><span class="sxs-lookup"><span data-stu-id="808c4-107">When you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], select an uncompressed drive for system databases and verify that databases to be upgraded are not on compressed drives.</span></span> <span data-ttu-id="808c4-108">但是，请注意，在数据库升级之后，可以将只读数据库和只读辅助文件组放在 NTFS 压缩文件系统中。</span><span class="sxs-lookup"><span data-stu-id="808c4-108">However, note that after the database has been upgraded, you can put read-only databases and read-only secondary filegroups on an NTFS compressed file system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="808c4-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="808c4-109">See Also</span></span>  
 <span data-ttu-id="808c4-110">[数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="808c4-110">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="808c4-111">SQL Server 2014 升级顾问 &#91;新&#93;</span><span class="sxs-lookup"><span data-stu-id="808c4-111">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
