---
title: 使用中央管理服务器管理多个服务器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- multiserver queries
- central management server
- multiserver administration [SQL Server]
- master servers [SQL Server], central management servers
- target configuration [SQL Server]
- server configuration [SQL Server]
ms.assetid: 427911a7-57d4-4542-8846-47c3267a5d9c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3906165b595f6faa15812f70377a3bc0f550e52e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689457"
---
# <a name="administer-multiple-servers-using-central-management-servers"></a><span data-ttu-id="6505e-102">使用中央管理服务器管理多台服务器</span><span class="sxs-lookup"><span data-stu-id="6505e-102">Administer Multiple Servers Using Central Management Servers</span></span>
  <span data-ttu-id="6505e-103">您可以通过指定中央管理服务器并创建服务器组来管理多台服务器。</span><span class="sxs-lookup"><span data-stu-id="6505e-103">You can administer multiple servers by designating Central Management Servers and creating server groups.</span></span>  
  
## <a name="benefits-of-central-management-servers-and-server-groups"></a><span data-ttu-id="6505e-104">中央管理服务器和服务器组的优点</span><span class="sxs-lookup"><span data-stu-id="6505e-104">Benefits of Central Management Servers and Server Groups</span></span>  
 <span data-ttu-id="6505e-105">指定为中央管理服务器的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例维护服务器组，这些组包含一个或多个 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例的连接信息。</span><span class="sxs-lookup"><span data-stu-id="6505e-105">An instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that is designated as a Central Management Server maintains server groups that contain the connection information for one or more instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6505e-106">可以对服务器组同时执行 [!INCLUDE[tsql](../includes/tsql-md.md)] 语句和基于策略的管理策略。</span><span class="sxs-lookup"><span data-stu-id="6505e-106">[!INCLUDE[tsql](../includes/tsql-md.md)] statements and Policy-Based Management policies can be executed at the same time against server groups.</span></span> <span data-ttu-id="6505e-107">还可以查看通过中央管理服务器管理的实例上的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 日志文件。</span><span class="sxs-lookup"><span data-stu-id="6505e-107">You can also view the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] log files on instances that are managed through a Central Management Server.</span></span> <span data-ttu-id="6505e-108">不能将早于 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 版本的 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] 指定为中央管理服务器。</span><span class="sxs-lookup"><span data-stu-id="6505e-108">Versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that are earlier than [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] cannot be designated as a Central Management Server.</span></span>  
  
 [!INCLUDE[tsql](../includes/tsql-md.md)] <span data-ttu-id="6505e-109">语句。</span><span class="sxs-lookup"><span data-stu-id="6505e-109">statements can also be executed against local server groups in Registered Servers.</span></span>  
  
### <a name="related-tasks"></a><span data-ttu-id="6505e-110">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="6505e-110">Related Tasks</span></span>  
 <span data-ttu-id="6505e-111">若要创建中央管理服务器和服务器组，请使用 **中的** “已注册的服务器” [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]窗口。</span><span class="sxs-lookup"><span data-stu-id="6505e-111">To create a Central Management Server and server groups, use the **Registered Servers** window in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="6505e-112">请注意，中央管理服务器不能是它所维护的组的成员。</span><span class="sxs-lookup"><span data-stu-id="6505e-112">Note that the Central Management Server cannot be a member of a group that it maintains.</span></span> <span data-ttu-id="6505e-113">有关如何创建中央管理服务器和服务器组的详细信息，请参阅[创建中央管理服务器和服务器组 (SQL Server Management Studio)](../ssms/register-servers/create-a-central-management-server-and-server-group.md)。</span><span class="sxs-lookup"><span data-stu-id="6505e-113">For more information about how to create Central Management Servers and server groups, see [Create a Central Management Server and Server Group &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-a-central-management-server-and-server-group.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6505e-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6505e-114">See Also</span></span>  
 [<span data-ttu-id="6505e-115">使用基于策略的管理来管理服务器</span><span class="sxs-lookup"><span data-stu-id="6505e-115">Administer Servers by Using Policy-Based Management</span></span>](policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  
