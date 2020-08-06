---
title: 远程服务器上的负载均衡包日志记录 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- logs [Integration Services], remote packages
ms.assetid: fd571567-b625-4f9a-8b7e-42c5c588b11b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b45fa6607d6edc1559d8ebcbbbc7598e11eac408
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586805"
---
# <a name="logging-for-load-balanced-packages-on-remote-servers"></a><span data-ttu-id="aef2b-102">远程服务器上的负载平衡包的日志记录</span><span class="sxs-lookup"><span data-stu-id="aef2b-102">Logging for Load Balanced Packages on Remote Servers</span></span>
  <span data-ttu-id="aef2b-103">如果所有子包都使用相同的日志提供程序并且它们全部写入相同的目标，则管理员更容易管理在各个服务器上运行的所有子包的日志。</span><span class="sxs-lookup"><span data-stu-id="aef2b-103">It is easier for an administrator to manage the logs for all the child packages that are running on various servers when all the child packages use the same log provider and they all write to the same destination.</span></span> <span data-ttu-id="aef2b-104">创建所有子包公用日志文件的一种方式是：将子包配置为“将子包事件记录到 SQL Server 日志提供程序”。</span><span class="sxs-lookup"><span data-stu-id="aef2b-104">One way that you can create a common log file for all child packages is to configure the child packages to log their events to a SQL Server log provider.</span></span> <span data-ttu-id="aef2b-105">可以将所有包配置为使用相同的数据库、相同的服务器和相同的服务器实例。</span><span class="sxs-lookup"><span data-stu-id="aef2b-105">You can configure all the packages to use the same database, the same server, and the same instance of the server.</span></span>  
  
 <span data-ttu-id="aef2b-106">若要查看日志文件，管理员只须登录到单个服务器上，即可查看所有子包的日志文件。</span><span class="sxs-lookup"><span data-stu-id="aef2b-106">To view the log files, the administrator only has to log on to a single server to view the log files for all child packages.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="aef2b-107">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="aef2b-107">Related Tasks</span></span>  
 <span data-ttu-id="aef2b-108">有关如何在包中启用日志记录的信息，请参阅 [在 SQL Server Data Tools 中启用包日志记录](../../2014/integration-services/enable-package-logging-in-sql-server-data-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="aef2b-108">For information about how to enable logging in a package, see [Enable Package Logging in SQL Server Data Tools](../../2014/integration-services/enable-package-logging-in-sql-server-data-tools.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aef2b-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aef2b-109">See Also</span></span>  
 [<span data-ttu-id="aef2b-110">Integration Services (SSIS) 日志记录</span><span class="sxs-lookup"><span data-stu-id="aef2b-110">Integration Services &#40;SSIS&#41; Logging</span></span>](performance/integration-services-ssis-logging.md)  
  
  
