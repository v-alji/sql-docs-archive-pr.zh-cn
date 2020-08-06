---
title: 设置 Integration Services 服务的属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services service, configuring
- Integration Services service, properties
ms.assetid: 3a8ad546-0f58-4b31-ab56-58d6313b1098
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 055eadd9a1d59c59dd40675b142eae480763f6f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694020"
---
# <a name="set-the-properties-of-the-integration-services-service"></a><span data-ttu-id="c4028-102">设置 Integration Services 服务的属性</span><span class="sxs-lookup"><span data-stu-id="c4028-102">Set the Properties of the Integration Services Service</span></span>
    
> [!IMPORTANT]  
>  <span data-ttu-id="c4028-103">本主题论述 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务，该服务是用于管理 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包的一种 Windows 服务。</span><span class="sxs-lookup"><span data-stu-id="c4028-103">This topic discusses the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service, a Windows service for managing [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] <span data-ttu-id="c4028-104">支持该服务以便与 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]的早期版本向后兼容。</span><span class="sxs-lookup"><span data-stu-id="c4028-104">supports the service for backward compatibility with earlier releases of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="c4028-105">从 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]开始，您可以在 Integration Services 服务器上管理诸如包之类的对象。</span><span class="sxs-lookup"><span data-stu-id="c4028-105">Starting in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], you can manage objects such as packages on the Integration Services server.</span></span>  
  
 <span data-ttu-id="c4028-106">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务管理并监视 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中的包。</span><span class="sxs-lookup"><span data-stu-id="c4028-106">The [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service manages and monitors packages in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="c4028-107">首次安装时 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ， [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务将启动，并且服务的启动类型设置为 "自动"。</span><span class="sxs-lookup"><span data-stu-id="c4028-107">When you first install [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service is started and the startup type of the service is set to automatic.</span></span>  
  
 <span data-ttu-id="c4028-108">安装 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务后，可以使用 SQL Server 配置管理器或 Services MMC 管理单元设置其属性。</span><span class="sxs-lookup"><span data-stu-id="c4028-108">After the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service has been installed, you can set the properties of the service by using either SQL Server Configuration Manager or the Services MMC snap-in.</span></span>  
  
 <span data-ttu-id="c4028-109">若要配置该服务的其他重要功能（包括在何处存储和管理包），则必须修改服务的配置文件。</span><span class="sxs-lookup"><span data-stu-id="c4028-109">To configure other important features of the service, including the locations where it stores and manages packages, you must modify the configuration file of the service.</span></span> <span data-ttu-id="c4028-110">有关详细信息，请参阅 [配置 Integration Services 服务（SSIS 服务）](service/integration-services-service-ssis-service.md)的早期版本向后兼容。</span><span class="sxs-lookup"><span data-stu-id="c4028-110">For more information, see [Configuring the Integration Services Service &#40;SSIS Service&#41;](service/integration-services-service-ssis-service.md).</span></span>  
  
### <a name="to-set-properties-of-the-integration-services-service-by-using-sql-server-configuration-manager"></a><span data-ttu-id="c4028-111">使用 SQL Server 配置管理器设置 Integration Services 服务的属性</span><span class="sxs-lookup"><span data-stu-id="c4028-111">To set properties of the Integration Services service by using SQL Server Configuration Manager</span></span>  
  
1.  <span data-ttu-id="c4028-112">在 **“开始”** 菜单中，依次指向 **“所有程序”** 、 **“Microsoft SQL Server”** 和 **“配置工具”** ，然后单击 **“SQL Server 配置管理器”** 。</span><span class="sxs-lookup"><span data-stu-id="c4028-112">On the **Start** menu, point to **All Programs**, point to **Microsoft SQL Server**, point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="c4028-113">在“SQL Server 配置管理器”管理单元中，在服务列表中找到 **SQL Server Integration Services**，右键单击 **SQL Server Integration Services**，然后单击“属性”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="c4028-113">In the **SQL Server Configuration Manager** snap-in, locate **SQL Server Integration Services** in the list of services, right-click **SQL Server Integration Services**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="c4028-114">在 " **SQL Server Integration Services 属性**" 对话框中，您可以执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="c4028-114">In the **SQL Server Integration Services Properties** dialog box you can do the following:</span></span>  
  
    -   <span data-ttu-id="c4028-115">单击 **“登录”** 选项卡以查看诸如帐户名等登录信息。</span><span class="sxs-lookup"><span data-stu-id="c4028-115">Click the **Log On** tab to view the logon information such as the account name.</span></span>  
  
    -   <span data-ttu-id="c4028-116">单击 **“服务”** 选项卡以查看有关服务的信息（例如，主机计算机的名称），并指定 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务的启动模式。</span><span class="sxs-lookup"><span data-stu-id="c4028-116">Click the **Service** tab to view information about the service such as the name of the host computer and to specify the start mode of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="c4028-117">\*\*\*\*“高级”选项卡不包含 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务的信息。</span><span class="sxs-lookup"><span data-stu-id="c4028-117">The **Advanced** tab contains no information for [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service.</span></span>  
  
4.  <span data-ttu-id="c4028-118">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="c4028-118">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="c4028-119">在“文件”菜单上，单击“退出”以关闭“SQL Server 配置管理器”管理单元。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="c4028-119">On the **File** menu, click **Exit** to close the **SQL Server Configuration Manager** snap-in.</span></span>  
  
### <a name="to-set-properties-of-the-integration-services-service-by-using-services"></a><span data-ttu-id="c4028-120">使用“服务”设置 Integration Services 服务的属性</span><span class="sxs-lookup"><span data-stu-id="c4028-120">To set properties of the Integration Services service by using Services</span></span>  
  
1.  <span data-ttu-id="c4028-121">在 **“控制面板”** 中，如果使用的是经典视图，请单击 **“管理工具”**；如果使用的是分类视图，请单击 **“性能和维护”** ，再单击 **“管理工具”**。</span><span class="sxs-lookup"><span data-stu-id="c4028-121">In **Control Panel**, if you are using Classic View, click **Administrative Tools**, or, if you are using Category View, click **Performance and Maintenance** and then click **Administrative Tools**.</span></span>  
  
2.  <span data-ttu-id="c4028-122">单击 **“服务”**。</span><span class="sxs-lookup"><span data-stu-id="c4028-122">Click **Services**.</span></span>  
  
3.  <span data-ttu-id="c4028-123">在“服务”管理单元中，在服务列表中找到 **SQL Server Integration Services**，右键单击 **SQL Server Integration Services**，再单击“属性”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="c4028-123">In the **Services** snap-in, locate **SQL Server Integration Services** in the list of services, right-click **SQL Server Integration Services**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="c4028-124">在 **“SQL Server Integration Services 属性”** 对话框中，可以执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="c4028-124">In the **SQL Server Integration Services Properties** dialog box, you can do the following:</span></span>  
  
    -   <span data-ttu-id="c4028-125">单击 "**常规**" 选项卡。若要启用该服务，请选择 "手动" 或 "自动" 启动类型。</span><span class="sxs-lookup"><span data-stu-id="c4028-125">Click the **General** tab. To enable the service, select either the manual or automatic startup type.</span></span> <span data-ttu-id="c4028-126">若要禁用该服务，请选择 **“启动类型”** 框中的“禁用”。</span><span class="sxs-lookup"><span data-stu-id="c4028-126">To disable the service, select Disable in the **Startup type** box.</span></span> <span data-ttu-id="c4028-127">选择“禁用”不会停止当前正在运行的服务。</span><span class="sxs-lookup"><span data-stu-id="c4028-127">Selecting Disable does not stop the service if it is currently running.</span></span>  
  
         <span data-ttu-id="c4028-128">如果该服务已经启用，则可以单击 **“停止”** 停止该服务，或单击 **“启动”** 启动该服务。</span><span class="sxs-lookup"><span data-stu-id="c4028-128">If the service is already enabled, you can click **Stop** to stop the service, or click **Start** to start the service.</span></span>  
  
    -   <span data-ttu-id="c4028-129">单击 **“登录”** 选项卡可查看或编辑登录信息。</span><span class="sxs-lookup"><span data-stu-id="c4028-129">Click the **Log On** tab to view or edit the logon information.</span></span>  
  
    -   <span data-ttu-id="c4028-130">单击 **“恢复”** 选项卡可查看服务失败时计算机的默认反应。</span><span class="sxs-lookup"><span data-stu-id="c4028-130">Click the **Recovery** tab to view the default computer responses to service failure.</span></span> <span data-ttu-id="c4028-131">您可以修改这些选项以满足您环境的要求。</span><span class="sxs-lookup"><span data-stu-id="c4028-131">You can modify these options to suit your environment.</span></span>  
  
    -   <span data-ttu-id="c4028-132">单击 **“依赖项”** 选项卡可查看依赖服务的列表。</span><span class="sxs-lookup"><span data-stu-id="c4028-132">Click the **Dependencies** tab to view a list of dependent services.</span></span> <span data-ttu-id="c4028-133">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务没有任何依赖项。</span><span class="sxs-lookup"><span data-stu-id="c4028-133">The [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service has no dependencies.</span></span>  
  
5.  <span data-ttu-id="c4028-134">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="c4028-134">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="c4028-135">另外，如果启动类型为“手动”或“自动”，还可以右键单击 **SQL Server Integration Services**，然后单击“启动”、“停止”或“重新启动”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="c4028-135">Optionally, if the startup type is Manual or Automatic, you can right-click **SQL Server Integration Services** and click **Start, Stop, or Restart**.</span></span>  
  
7.  <span data-ttu-id="c4028-136">在“文件”菜单上，单击“退出”关闭“服务”管理单元。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="c4028-136">On the **File** menu, click **Exit** to close the **Services** snap-in.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4028-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c4028-137">See Also</span></span>  
 [<span data-ttu-id="c4028-138">管理 Integration Services 服务</span><span class="sxs-lookup"><span data-stu-id="c4028-138">Manage the Integration Services Service</span></span>](../../2014/integration-services/manage-the-integration-services-service.md)  
  
  
