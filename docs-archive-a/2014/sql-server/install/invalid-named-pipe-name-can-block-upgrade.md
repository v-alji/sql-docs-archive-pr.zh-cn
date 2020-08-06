---
title: 无效的命名管道名称可以阻止升级 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- invalid named pipes [SQL Server]
- named pipes
ms.assetid: 58c2199c-4fdf-4d43-ac1c-842703344b75
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: bacfd3d097d7cccb0a5780328c4db95dc5afc733
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693193"
---
# <a name="invalid-named-pipe-name-can-block-upgrade"></a><span data-ttu-id="09789-102">无效的命名管道名称会妨碍升级</span><span class="sxs-lookup"><span data-stu-id="09789-102">Invalid named pipe name can block upgrade</span></span>
  <span data-ttu-id="09789-103">如果 named pipes 协议配置得不正确，则升级将失败。</span><span class="sxs-lookup"><span data-stu-id="09789-103">Upgrade fails if the named pipes protocol is incorrectly configured.</span></span>  
  
## <a name="component"></a><span data-ttu-id="09789-104">组件</span><span class="sxs-lookup"><span data-stu-id="09789-104">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="09789-105">说明</span><span class="sxs-lookup"><span data-stu-id="09789-105">Description</span></span>  
 <span data-ttu-id="09789-106">在升级过程中，安装程序将启动 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 具有 shared memory 支持的实例，该实例只接受本地连接。</span><span class="sxs-lookup"><span data-stu-id="09789-106">During upgrade, the Setup program starts the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssDE](../../includes/ssde-md.md)] instance with shared memory support, a named pipe that only accepts local connections.</span></span> <span data-ttu-id="09789-107">如果在服务器上指定的管道名称不为空，则它必须以字符串 " \\ \\ .\pipe \\ " 开头才能有效。</span><span class="sxs-lookup"><span data-stu-id="09789-107">If the pipe name specified on the server is not blank, it must begin with the string "\\\\.\pipe\\" to be valid.</span></span> <span data-ttu-id="09789-108">如果管道名称无效，[!INCLUDE[ssDE](../../includes/ssde-md.md)]将不启动，并且安装将失败。</span><span class="sxs-lookup"><span data-stu-id="09789-108">If the pipe name is not valid, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] will not start, and setup will fail.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="09789-109">纠正措施</span><span class="sxs-lookup"><span data-stu-id="09789-109">Corrective Action</span></span>  
 <span data-ttu-id="09789-110">使用\*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 网络实用工具\*\*来提供有效的管道名称，然后运行安装程序。</span><span class="sxs-lookup"><span data-stu-id="09789-110">Use the **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Network Utility** to supply a valid pipe name, and then run Setup.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09789-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="09789-111">See Also</span></span>  
 <span data-ttu-id="09789-112">[数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="09789-112">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="09789-113">SQL Server 2014 升级顾问 &#91;新&#93;</span><span class="sxs-lookup"><span data-stu-id="09789-113">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
