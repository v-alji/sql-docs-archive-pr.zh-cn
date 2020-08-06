---
title: 创建或删除供客户端 (SQL Server 配置管理器) 使用的服务器别名 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- server alias
helpviewer_keywords:
- aliases [SQL Server], deleting
- aliases [SQL Server], creating
ms.assetid: b687e376-ee33-470d-b65a-87246bfefe6f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: bead257b40c33e3640b18890a7d109d774131123
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587603"
---
# <a name="create-or-delete-a-server-alias-for-use-by-a-client-sql-server-configuration-manager"></a><span data-ttu-id="bc628-102">创建或删除供客户端使用的服务器别名（SQL Server 配置管理器）</span><span class="sxs-lookup"><span data-stu-id="bc628-102">Create or Delete a Server Alias for Use by a Client (SQL Server Configuration Manager)</span></span>
  <span data-ttu-id="bc628-103">本主题说明如何使用 SQL Server 配置管理器在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中创建或删除服务器别名。</span><span class="sxs-lookup"><span data-stu-id="bc628-103">This topic describes how to create or delete a server alias in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using SQL Server Configuration Manager.</span></span> <span data-ttu-id="bc628-104">别名是可用于进行连接的备用名称。</span><span class="sxs-lookup"><span data-stu-id="bc628-104">An alias is an alternate name that can be used to make a connection.</span></span> <span data-ttu-id="bc628-105">别名封装了连接字符串所必需的元素，并使用用户所选择的名称显示这些元素。</span><span class="sxs-lookup"><span data-stu-id="bc628-105">The alias encapsulates the required elements of a connection string, and exposes them with a name chosen by the user.</span></span> <span data-ttu-id="bc628-106">可对任何客户端应用程序使用别名。</span><span class="sxs-lookup"><span data-stu-id="bc628-106">Aliases can be used with any client application.</span></span> <span data-ttu-id="bc628-107">通过创建服务器别名，客户端计算机便可使用不同的网络协议连接到多个服务器，无需针对每台服务器指定协议和连接详细信息。</span><span class="sxs-lookup"><span data-stu-id="bc628-107">By creating server aliases, your client computer can connect to multiple servers using different network protocols, without having to specify the protocol and connection details for each one.</span></span> <span data-ttu-id="bc628-108">另外，还可以一直启用各种网络协议，即使只是偶尔会用到它们。</span><span class="sxs-lookup"><span data-stu-id="bc628-108">In addition, you can also have different network protocols enabled all the time, even if you only need to use them occasionally.</span></span> <span data-ttu-id="bc628-109">如果已将服务器配置为侦听非默认端口号或命名管道，并且禁用了 SQL Server Browser 服务，请创建一个别名来指定新端口号或命名管道。</span><span class="sxs-lookup"><span data-stu-id="bc628-109">If you have configured the server to listen on a non-default port number or named pipe, and you have disabled the SQL Server Browser service, create an alias that specifies the new port number or named pipe.</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="bc628-110">使用 SQL Server 配置管理器</span><span class="sxs-lookup"><span data-stu-id="bc628-110">Using SQL Server Configuration Manager</span></span>  
  
#### <a name="to-create-an-alias"></a><span data-ttu-id="bc628-111">创建别名</span><span class="sxs-lookup"><span data-stu-id="bc628-111">To create an alias</span></span>  
  
1.  <span data-ttu-id="bc628-112">在 SQL Server 配置管理器中，展开“SQL Server Native Client 配置”，右键单击“别名”，再单击“新建别名”。</span><span class="sxs-lookup"><span data-stu-id="bc628-112">In SQL Server Configuration Manager, expand **SQL Server Native Client Configuration**, right-click **Aliases**, and then click **New Alias**.</span></span>  
  
2.  <span data-ttu-id="bc628-113">在 **“别名”** 框中，键入别名。</span><span class="sxs-lookup"><span data-stu-id="bc628-113">In the **Alias Name** box, type the name of the alias.</span></span> <span data-ttu-id="bc628-114">当客户端应用程序进行连接时，它们使用该名称。</span><span class="sxs-lookup"><span data-stu-id="bc628-114">Client applications use this name when they connect.</span></span>  
  
3.  <span data-ttu-id="bc628-115">在 **“服务器”** 框中，键入服务器的名称或 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="bc628-115">In the **Server** box, type the name or IP address of a server.</span></span> <span data-ttu-id="bc628-116">对于命名实例，请追加实例名称。</span><span class="sxs-lookup"><span data-stu-id="bc628-116">For a named instance append the instance name.</span></span>  
  
4.  <span data-ttu-id="bc628-117">在 **“协议”** 框中，选择用于该别名的协议。</span><span class="sxs-lookup"><span data-stu-id="bc628-117">In the **Protocol** box, select the protocol used for this alias.</span></span> <span data-ttu-id="bc628-118">选择某个协议，将可选属性框的标题更改为“端口号”、“管道名称”或“连接字符串”。</span><span class="sxs-lookup"><span data-stu-id="bc628-118">Selecting a protocol, changes the title of the optional properties box to Port No, Pipe Name, or Connection String.</span></span>  
  
 <span data-ttu-id="bc628-119">对于创建自己的连接字符串的程序员来说， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器帮助介绍的连接字符串颇为有用。</span><span class="sxs-lookup"><span data-stu-id="bc628-119">The connection strings described in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager Help can be useful for programmers who create their own connection strings.</span></span> <span data-ttu-id="bc628-120">若要访问此信息，请在 **“新建别名”** 对话框中按 F1，或单击 **“帮助”** 。</span><span class="sxs-lookup"><span data-stu-id="bc628-120">To access this information, in the **New Alias** dialog box, press F1, or click **Help**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bc628-121">如果配置的别名正与错误的服务器或实例进行连接，则请禁用并重新启用相关联的网络协议。</span><span class="sxs-lookup"><span data-stu-id="bc628-121">If a configured alias is connecting to the wrong server or instance, disable and then reenable the associated network protocol.</span></span> <span data-ttu-id="bc628-122">这样做会清除缓存的连接信息，从而允许客户端进行正确连接。</span><span class="sxs-lookup"><span data-stu-id="bc628-122">Doing this clears any cached connection information and allows the client to connect correctly.</span></span>  
  
#### <a name="to-delete-an-alias"></a><span data-ttu-id="bc628-123">删除别名</span><span class="sxs-lookup"><span data-stu-id="bc628-123">To delete an alias</span></span>  
  
1.  <span data-ttu-id="bc628-124">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器中，展开 **“SQL Server Native Client 配置”** ，然后单击 **“别名”** 。</span><span class="sxs-lookup"><span data-stu-id="bc628-124">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, expand **SQL Server Native Client Configuration**, and then click **Aliases**.</span></span>  
  
2.  <span data-ttu-id="bc628-125">在“详细信息”窗格中，右键单击要删除的别名，然后单击“删除”。</span><span class="sxs-lookup"><span data-stu-id="bc628-125">In the details pane, right-click the alias that you want to delete, and then click **Delete**.</span></span>  
  
  
