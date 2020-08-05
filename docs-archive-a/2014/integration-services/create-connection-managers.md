---
title: 创建连接管理器 |Microsoft Docs
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.connectionmanager.f1
helpviewer_keywords:
- Integration Services packages, connections
- SSIS packages, connections
- packages [Integration Services], connections
- connection managers [Integration Services], creating
- SQL Server Integration Services packages, connections
ms.assetid: 6ca317b8-0061-4d9d-b830-ee8c21268345
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7661d165ea606af880fd00e4638ec43e9bfcc890
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580802"
---
# <a name="create-connection-managers"></a><span data-ttu-id="e2754-102">创建连接管理器</span><span class="sxs-lookup"><span data-stu-id="e2754-102">Create Connection Managers</span></span>
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="e2754-103">包含多种连接管理器以满足连接不同类型的服务器和数据源的任务的需要。</span><span class="sxs-lookup"><span data-stu-id="e2754-103">includes a variety of connection managers to suit the needs of tasks that connect to different types of servers and data sources.</span></span> <span data-ttu-id="e2754-104">在不同类型的数据存储中提取和加载数据的数据流组件，以及将日志写入服务器、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 表或文件的日志提供程序，都使用连接管理器。</span><span class="sxs-lookup"><span data-stu-id="e2754-104">Connection managers are used by the data flow components that extract and load data in different types of data stores, and by the log providers that write logs to a server, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] table, or file.</span></span> <span data-ttu-id="e2754-105">例如，具有发送邮件任务的包使用 SMTP 类型的连接管理器来连接到简单邮件传输协议 (SMTP) 服务器。</span><span class="sxs-lookup"><span data-stu-id="e2754-105">For example, a package with a Send Mail task uses an SMTP connection manager type to connect to a Simple Mail Transfer Protocol (SMTP) server.</span></span> <span data-ttu-id="e2754-106">具有执行 SQL 任务的包可以使用 OLE DB 连接管理器来连接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="e2754-106">A package with an Execute SQL task can use an OLE DB connection manager to connect to a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="e2754-107">有关详细信息，请参阅 [Integration Services (SSIS) 连接](connection-manager/integration-services-ssis-connections.md)。</span><span class="sxs-lookup"><span data-stu-id="e2754-107">For more information, see [Integration Services &#40;SSIS&#41; Connections](connection-manager/integration-services-ssis-connections.md).</span></span>

 <span data-ttu-id="e2754-108">若要在创建新包时自动创建和配置连接管理器，可以使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 导入和导出向导。</span><span class="sxs-lookup"><span data-stu-id="e2754-108">To automatically create and configure connection managers when you create a new package, you can use the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Import and Export Wizard.</span></span> <span data-ttu-id="e2754-109">该向导还有助于创建和配置使用连接管理器的源和目标。</span><span class="sxs-lookup"><span data-stu-id="e2754-109">The wizard also helps you create and configure the sources and destinations that use the connection managers.</span></span> <span data-ttu-id="e2754-110">有关详细信息，请参阅 [Create Packages in SQL Server Data Tools](create-packages-in-sql-server-data-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="e2754-110">For more information, see [Create Packages in SQL Server Data Tools](create-packages-in-sql-server-data-tools.md).</span></span>

 <span data-ttu-id="e2754-111">若要手动创建新的连接管理器并将其添加到现有包，可以使用在 **设计器的** “控制流” **、** “数据流” **和**“事件处理程序” **选项卡上出现的** “连接管理器” [!INCLUDE[ssIS](../includes/ssis-md.md)] 区域。</span><span class="sxs-lookup"><span data-stu-id="e2754-111">To manually create a new connection manager and add it to an existing package, you use the **Connection Managers** area that appears on the **Control Flow**, **Data Flow**, and **Event Handlers** tabs of [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="e2754-112">从 **“连接管理器”** 区域，选择要创建的连接管理器的类型，并使用 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器提供的对话框设置连接管理器的属性。</span><span class="sxs-lookup"><span data-stu-id="e2754-112">From the **Connection Manager** area, you choose the type of connection manager to create, and then set the properties of the connection manager by using a dialog box that [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer provides.</span></span> <span data-ttu-id="e2754-113">有关详细信息，请参阅本主题后面的“使用连接管理器区域”部分。</span><span class="sxs-lookup"><span data-stu-id="e2754-113">For more information, see the section, "Using the Connection Managers Area," later in this topic.</span></span>

 <span data-ttu-id="e2754-114">将连接管理器添加到包之后，可以在任务、Foreach 循环容器、源、转换和目标中使用它。</span><span class="sxs-lookup"><span data-stu-id="e2754-114">After the connection manager is added to a package, you can use it in tasks, Foreach Loop containers, sources, transformations, and destinations.</span></span> <span data-ttu-id="e2754-115">有关详细信息，请参阅 [Integration Services 任务](control-flow/integration-services-tasks.md)、[Foreach 循环容器](control-flow/foreach-loop-container.md)和[数据流](data-flow/data-flow.md)。</span><span class="sxs-lookup"><span data-stu-id="e2754-115">For more information, see [Integration Services Tasks](control-flow/integration-services-tasks.md), [Foreach Loop Container](control-flow/foreach-loop-container.md), and [Data Flow](data-flow/data-flow.md).</span></span>

## <a name="using-the-connection-managers-area"></a><span data-ttu-id="e2754-116">使用连接管理器区域</span><span class="sxs-lookup"><span data-stu-id="e2754-116">Using the Connection Managers Area</span></span>
 <span data-ttu-id="e2754-117">可以在 **设计器的**“控制流” **、** “数据流” **或** “事件处理程序” [!INCLUDE[ssIS](../includes/ssis-md.md)] 选项卡活动时创建连接管理器。</span><span class="sxs-lookup"><span data-stu-id="e2754-117">You can create connection managers while the **Control Flow**, **Data Flow**, or **Event Handlers** tab of [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer is active.</span></span>

 <span data-ttu-id="e2754-118">以下关系图显示 **设计器的** “控制流” **选项卡上的** “连接管理器” [!INCLUDE[ssIS](../includes/ssis-md.md)] 区域。</span><span class="sxs-lookup"><span data-stu-id="e2754-118">The following diagram shows the **Connection Managers** area on the **Control Flow** tab of [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>

 <span data-ttu-id="e2754-119">![具有包的控制流设计器的屏幕快照](media/samplecontrolflow.gif "具有包的控制流设计器的屏幕快照")</span><span class="sxs-lookup"><span data-stu-id="e2754-119">![Screenshot of control flow designer with package](media/samplecontrolflow.gif "Screenshot of control flow designer with package")</span></span>

#### <a name="to-add-configure-or-delete-a-connection-manager-in-ssis-designer"></a><span data-ttu-id="e2754-120">在 SSIS 设计器中添加、配置或删除连接管理器</span><span class="sxs-lookup"><span data-stu-id="e2754-120">To add, configure, or delete a connection manager in SSIS Designer</span></span>

-   [<span data-ttu-id="e2754-121">在包中添加、删除或共享连接管理器</span><span class="sxs-lookup"><span data-stu-id="e2754-121">Add, Delete, or Share a Connection Manager in a Package</span></span>](../../2014/integration-services/add-delete-or-share-a-connection-manager-in-a-package.md)

-   [<span data-ttu-id="e2754-122">设置连接管理器的属性</span><span class="sxs-lookup"><span data-stu-id="e2754-122">Set the Properties of a Connection Manager</span></span>](../../2014/integration-services/set-the-properties-of-a-connection-manager.md)

## <a name="32-bit-and-64-bit-providers-for-connection-managers"></a><span data-ttu-id="e2754-123">用于连接管理器的 32 位和 64 位提供程序</span><span class="sxs-lookup"><span data-stu-id="e2754-123">32-Bit and 64-Bit Providers for Connection Managers</span></span>
 <span data-ttu-id="e2754-124">连接管理器所使用的很多提供程序都有 32 位和 64 位版本。</span><span class="sxs-lookup"><span data-stu-id="e2754-124">Many of the providers that connection managers use are available in 32-bit and 64-bit versions.</span></span> <span data-ttu-id="e2754-125">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 设计环境是 32 位环境，设计包时您只能看到 32 位提供程序。</span><span class="sxs-lookup"><span data-stu-id="e2754-125">The [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] design environment is a 32-bit environment and you see only 32-bit providers while you are designing a package.</span></span> <span data-ttu-id="e2754-126">因此，如果还安装了同一个提供程序的 32 位版本，则只能将连接管理器配置为使用特定的 64 位提供程序。</span><span class="sxs-lookup"><span data-stu-id="e2754-126">Therefore, you can only configure a connection manager to use a specific 64-bit provider if the 32-bit version of the same provider is also installed.</span></span>

 <span data-ttu-id="e2754-127">在运行时，系统将使用正确的版本，即使在设计时指定了 32 位版本的提供程序也没有关系。</span><span class="sxs-lookup"><span data-stu-id="e2754-127">At run time, the correct version is used, and it does not matter that you specified the 32-bit version of the provider at design time.</span></span> <span data-ttu-id="e2754-128">即使包运行在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中，也可以运行 64 位版本的提供程序。</span><span class="sxs-lookup"><span data-stu-id="e2754-128">The 64-bit version of the provider can be run even if the package is run in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>

 <span data-ttu-id="e2754-129">两种版本的提供程序都有相同的 ID。</span><span class="sxs-lookup"><span data-stu-id="e2754-129">Both versions of the provider have the same ID.</span></span> <span data-ttu-id="e2754-130">若要指定 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 运行时是否使用可用的 64 位版本的提供程序，需要设置 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目的 Run64BitRuntime 属性。</span><span class="sxs-lookup"><span data-stu-id="e2754-130">To specify whether the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] runtime uses an available 64-bit version of the provider, you set the Run64BitRuntime property of the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span> <span data-ttu-id="e2754-131">如果 Run64BitRuntime 属性设置为，则 `true` 运行时会查找并使用64位提供程序; 如果 Run64BitRuntime 为 `false` ，则运行时会查找并使用32位提供程序。</span><span class="sxs-lookup"><span data-stu-id="e2754-131">If the Run64BitRuntime property is set to `true`, the runtime finds and uses the 64-bit provider; if Run64BitRuntime is `false`, the runtime finds and uses the 32-bit provider.</span></span> <span data-ttu-id="e2754-132">有关可以对 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目进行设置的属性的详细信息，请参阅 [Integration Services (SSIS) 与 Studio 环境](integration-services-ssis-development-and-management-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="e2754-132">For more information about properties you can set on [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] projects, see [Integration Services &#40;SSIS&#41; and Studio Environments](integration-services-ssis-development-and-management-tools.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e2754-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e2754-133">See Also</span></span>
 <span data-ttu-id="e2754-134">[&#40;SSIS&#41; 事件处理程序](integration-services-ssis-event-handlers.md)的[控制流](control-flow/control-flow.md)[数据流](data-flow/data-flow.md)Integration Services</span><span class="sxs-lookup"><span data-stu-id="e2754-134">[Control Flow](control-flow/control-flow.md) [Data Flow](data-flow/data-flow.md) [Integration Services &#40;SSIS&#41; Event Handlers](integration-services-ssis-event-handlers.md)</span></span>


