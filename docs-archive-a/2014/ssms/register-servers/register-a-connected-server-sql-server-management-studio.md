---
title: 注册连接的服务器
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.registerserver.f1
helpviewer_keywords:
- Registered Servers [SQL Server], register connected servers
- connected server registrations [SQL Server]
ms.assetid: 77deb5f5-0f80-484f-8b8b-29afa67ec18f
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 1d337d2da7d305165307745fb02526e37b53bbd3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580508"
---
# <a name="register-a-connected-server-sql-server-management-studio"></a><span data-ttu-id="1fabc-102">注册连接的服务器 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="1fabc-102">Register a Connected Server (SQL Server Management Studio)</span></span>
  <span data-ttu-id="1fabc-103">本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中注册服务器。</span><span class="sxs-lookup"><span data-stu-id="1fabc-103">This topic describes how to register servers in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="1fabc-104">通过注册服务器，您可以保存经常访问的服务器的连接信息。</span><span class="sxs-lookup"><span data-stu-id="1fabc-104">By registering the server, you can save the connection information for servers that you access frequently.</span></span> <span data-ttu-id="1fabc-105">可以在连接前注册服务器，也可以在通过对象资源管理器进行连接时注册服务器。</span><span class="sxs-lookup"><span data-stu-id="1fabc-105">A server can be registered before connecting, or at the time of connection from Object Explorer.</span></span>  
  
 <span data-ttu-id="1fabc-106">**本主题内容**</span><span class="sxs-lookup"><span data-stu-id="1fabc-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="1fabc-107">**若要注册服务器，请使用：**</span><span class="sxs-lookup"><span data-stu-id="1fabc-107">**To register a server, using:**</span></span>  
  
     [<span data-ttu-id="1fabc-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1fabc-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1fabc-109">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1fabc-109">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-register-a-connected-server"></a><span data-ttu-id="1fabc-110">注册连接的服务器</span><span class="sxs-lookup"><span data-stu-id="1fabc-110">To register a connected server</span></span>  
  
1.  <span data-ttu-id="1fabc-111">在对象资源管理器中，右键单击已经连接的服务器，然后单击“注册”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1fabc-111">In Object Explorer, right-click a server to which you already are connected, and then click **Register**.</span></span>  
  
     <span data-ttu-id="1fabc-112">**服务器名称**</span><span class="sxs-lookup"><span data-stu-id="1fabc-112">**Server name**</span></span>  
     <span data-ttu-id="1fabc-113">输入要为已注册服务器使用的名称。</span><span class="sxs-lookup"><span data-stu-id="1fabc-113">Enter the name you want to use for the registered server.</span></span> <span data-ttu-id="1fabc-114">使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 注册本地或远程服务器，您可以存储服务器连接信息以供将来连接时使用。</span><span class="sxs-lookup"><span data-stu-id="1fabc-114">Registering a local or remote server using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] lets you store the server connection information for future connections.</span></span> <span data-ttu-id="1fabc-115">此字段默认使用连接到服务器时所输入的服务器名称。</span><span class="sxs-lookup"><span data-stu-id="1fabc-115">This field defaults to the server name entered when you were connecting to the server.</span></span> <span data-ttu-id="1fabc-116">您可以保留此服务器名称，也可以输入其他便于使用的服务器名称。</span><span class="sxs-lookup"><span data-stu-id="1fabc-116">You can retain this server name or enter another easy-to-use name for the server.</span></span>  
  
     <span data-ttu-id="1fabc-117">**服务器说明**</span><span class="sxs-lookup"><span data-stu-id="1fabc-117">**Server description**</span></span>  
     <span data-ttu-id="1fabc-118">输入服务器的说明（可选）。</span><span class="sxs-lookup"><span data-stu-id="1fabc-118">Enter an optional description of the server.</span></span> <span data-ttu-id="1fabc-119">允许的最大字符数为 250。</span><span class="sxs-lookup"><span data-stu-id="1fabc-119">The maximum number of characters allowed is 250.</span></span>  
  
     <span data-ttu-id="1fabc-120">**选择服务器组**</span><span class="sxs-lookup"><span data-stu-id="1fabc-120">**Select a server group**</span></span>  
     <span data-ttu-id="1fabc-121">选择要保存服务器注册的服务器组。</span><span class="sxs-lookup"><span data-stu-id="1fabc-121">Select the server group where you want to save the server registration.</span></span>  
  
     <span data-ttu-id="1fabc-122">**新建组**</span><span class="sxs-lookup"><span data-stu-id="1fabc-122">**New Group**</span></span>  
     <span data-ttu-id="1fabc-123">单击此项可启动“新建组”\*\*\*\* 对话框，使用该对话框可以为已注册的服务器创建新的服务器组。</span><span class="sxs-lookup"><span data-stu-id="1fabc-123">Click to launch the **New Group** dialog box, where you can create a new server group for the registered server.</span></span>  
  
     <span data-ttu-id="1fabc-124">**保存**</span><span class="sxs-lookup"><span data-stu-id="1fabc-124">**Save**</span></span>  
     <span data-ttu-id="1fabc-125">单击此项可保存已输入的信息并创建已注册的服务器。</span><span class="sxs-lookup"><span data-stu-id="1fabc-125">Click to save the information you have entered and create a registered server.</span></span>  
  
  
