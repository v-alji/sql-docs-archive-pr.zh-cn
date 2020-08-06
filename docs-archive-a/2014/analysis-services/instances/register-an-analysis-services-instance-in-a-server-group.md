---
title: 在服务器组中注册 Analysis Services 实例 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5fd3826b-8f75-48eb-910c-bf784163e53b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 277f905e7d234ec9136ecc5b658cb4ef6675ae4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690206"
---
# <a name="register-an-analysis-services-instance-in-a-server-group"></a><span data-ttu-id="dd600-102">在服务器组中注册 Analysis Services 实例</span><span class="sxs-lookup"><span data-stu-id="dd600-102">Register an Analysis Services Instance in a Server Group</span></span>
  <span data-ttu-id="dd600-103">如果有大量 Analysis Services 服务器实例，可以在 Management Studio 中创建服务器组来方便管理服务器。</span><span class="sxs-lookup"><span data-stu-id="dd600-103">If you have a large number of Analysis Services server instances, you can create server groups in Management Studio to make server administration easier.</span></span> <span data-ttu-id="dd600-104">服务器组的作用是在管理工作区内提供一组相关服务器的近似性。</span><span class="sxs-lookup"><span data-stu-id="dd600-104">The purpose of a server group is to provide proximity among a group of related servers within the administrative workspace.</span></span> <span data-ttu-id="dd600-105">例如，假定您负责管理 10 个单独的 Analysis Services 实例。</span><span class="sxs-lookup"><span data-stu-id="dd600-105">For example, suppose you are tasked with managing ten separate instances of Analysis Services.</span></span> <span data-ttu-id="dd600-106">通过按服务器模式、运行时间条件或部门/区域将它们分组，您可以更易于查看并连接到共享相同特征的实例。</span><span class="sxs-lookup"><span data-stu-id="dd600-106">Grouping them by server mode, up-time criteria, or by department or region would allow you to view and connect to instances that share the same characteristics more easily.</span></span> <span data-ttu-id="dd600-107">您还可以添加描述性信息，帮助您记住如何使用服务器。</span><span class="sxs-lookup"><span data-stu-id="dd600-107">You can also add descriptive information that helps you remember how the server is used.</span></span>

 <span data-ttu-id="dd600-108">![包含成员服务器的“已注册服务器”窗格](../media/ssas-ssms-registerserver.gif "包含成员服务器的“已注册服务器”窗格")</span><span class="sxs-lookup"><span data-stu-id="dd600-108">![Registered Server pane with member servers](../media/ssas-ssms-registerserver.gif "Registered Server pane with member servers")</span></span>

 <span data-ttu-id="dd600-109">可以在层次结构中创建服务器组。</span><span class="sxs-lookup"><span data-stu-id="dd600-109">Server groups can be created in a hierarchical structure.</span></span> <span data-ttu-id="dd600-110">本地服务器组是根节点。</span><span class="sxs-lookup"><span data-stu-id="dd600-110">Local Server Group is the root node.</span></span> <span data-ttu-id="dd600-111">它始终包含在本地计算机上运行的 Analysis Services 实例。</span><span class="sxs-lookup"><span data-stu-id="dd600-111">It always contains instances of Analysis Services that run on the local computer.</span></span> <span data-ttu-id="dd600-112">您可以将远程服务器添加到任何组，包括本地组。</span><span class="sxs-lookup"><span data-stu-id="dd600-112">You can add remote servers to any group, including the local group.</span></span>

 <span data-ttu-id="dd600-113">创建服务器组后，必须使用“已注册的服务器”窗格查看和连接到成员服务器。</span><span class="sxs-lookup"><span data-stu-id="dd600-113">After you create a server group, you must use the Registered Servers pane to view and connect to the member servers.</span></span> <span data-ttu-id="dd600-114">该窗格按服务器类型筛选 SQL Server 实例（数据库引擎、Analysis Services、Reporting Services 和 Integration Services）。</span><span class="sxs-lookup"><span data-stu-id="dd600-114">The pane filters SQL Server instances by server type (Database Engine, Analysis Services, Reporting Services, and Integration Services).</span></span> <span data-ttu-id="dd600-115">单击某一服务器类型可以查看为它创建的服务器组。</span><span class="sxs-lookup"><span data-stu-id="dd600-115">You click a server type to view the server groups created for it.</span></span> <span data-ttu-id="dd600-116">若要连接到组中的特定服务器，可以双击组中的该服务器。</span><span class="sxs-lookup"><span data-stu-id="dd600-116">To connect to a specific server within group, you double-click a server in the group.</span></span>

 <span data-ttu-id="dd600-117">为服务器定义的连接信息（包括服务器名称）通过服务器注册已持久化。</span><span class="sxs-lookup"><span data-stu-id="dd600-117">The connection information that is defined for the server, including the server name, is persisted with server registration.</span></span> <span data-ttu-id="dd600-118">使用其他工具连接到服务器时，不能修改连接信息或使用注册的名称。</span><span class="sxs-lookup"><span data-stu-id="dd600-118">You cannot modify the connection information, or use the registered name when connecting to the server using other tools.</span></span>

## <a name="create-a-server-group-and-add-registered-servers"></a><span data-ttu-id="dd600-119">创建服务器组并添加已注册的服务器</span><span class="sxs-lookup"><span data-stu-id="dd600-119">Create a Server Group and Add Registered Servers</span></span>

1.  <span data-ttu-id="dd600-120">在 Management Studio 中，单击“查看”菜单中的“已注册的服务器”以在工作区中打开“已注册的服务器”窗格。</span><span class="sxs-lookup"><span data-stu-id="dd600-120">In Management Studio, click Registered Servers on the View menu to open the Registered Servers pane in the workspace.</span></span> <span data-ttu-id="dd600-121">默认情况下，已创建本地服务器组。</span><span class="sxs-lookup"><span data-stu-id="dd600-121">By default, a local Server Group is already created.</span></span> <span data-ttu-id="dd600-122">在本地服务器上运行的所有 Analysis Services 实例是其成员。</span><span class="sxs-lookup"><span data-stu-id="dd600-122">All instances of Analysis Services that are running on the local server are members.</span></span>

2.  <span data-ttu-id="dd600-123">右键单击“本地服务器组”，选择“新建服务器组”并指定该组的名称。</span><span class="sxs-lookup"><span data-stu-id="dd600-123">Right-click Local Server Group, select New Server Group, and give the group a name.</span></span>

3.  <span data-ttu-id="dd600-124">右键单击该服务器组，然后选择“新建服务器注册”。</span><span class="sxs-lookup"><span data-stu-id="dd600-124">Right-click the server group and select New Server Registration.</span></span> <span data-ttu-id="dd600-125">输入本地或远程服务器的网络名称，包括实例名称（如果服务器作为命名实例安装）。</span><span class="sxs-lookup"><span data-stu-id="dd600-125">Enter the network name of a local or remote server, including the instance name if the server was installed as a named instance.</span></span> <span data-ttu-id="dd600-126">或者，您可以提供在“已注册的服务器”中显示的已注册的服务器名称。</span><span class="sxs-lookup"><span data-stu-id="dd600-126">Optionally, you can provide a registered server name that appears in Registered Servers.</span></span> <span data-ttu-id="dd600-127">此名称仅在“已注册的服务器”中使用。</span><span class="sxs-lookup"><span data-stu-id="dd600-127">This name is used in Registered Servers only.</span></span> <span data-ttu-id="dd600-128">您不能使用它来重命名服务器，也不能在连接字符串中使用它。</span><span class="sxs-lookup"><span data-stu-id="dd600-128">You cannot use it to rename a server, nor can you use it in a connection string.</span></span> <span data-ttu-id="dd600-129">已注册的服务器名称可以比实际服务器名称更具描述性，或包括其他有助于区分此服务器与其他服务器的标识特征。</span><span class="sxs-lookup"><span data-stu-id="dd600-129">A registered server name can be more descriptive than the actual server name or include other identifying characteristics that help you distinguish this server from other servers.</span></span>


