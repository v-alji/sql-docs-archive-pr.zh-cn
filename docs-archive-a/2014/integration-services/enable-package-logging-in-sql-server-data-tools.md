---
title: 在 SQL Server Data Tools 中启用包日志记录 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- logs [Integration Services], enabling
ms.assetid: b69a8593-5bb0-4f04-87d2-f8e7bd7eb4fc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d73dbca034047e853669dd503a62e105d1dd7b45
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587512"
---
# <a name="enable-package-logging-in-sql-server-data-tools"></a><span data-ttu-id="9b563-102">在 SQL Server Data Tools 中启用包日志记录</span><span class="sxs-lookup"><span data-stu-id="9b563-102">Enable Package Logging in SQL Server Data Tools</span></span>
  <span data-ttu-id="9b563-103">本过程介绍如何将日志添加到包中，如何配置包级日志记录，以及如何将日志记录配置保存为 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="9b563-103">This procedure describes how to add logs to a package, configure package-level logging, and save the logging configuration to an XML file.</span></span> <span data-ttu-id="9b563-104">您只能在包级添加日志，但包不必执行日志记录，就可以在包所包括的容器中启用日志记录。</span><span class="sxs-lookup"><span data-stu-id="9b563-104">You can add logs only at the package level, but the package does not have to perform logging to enable logging in the containers that the package includes.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9b563-105">如果您将 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目部署到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务器，则为包执行设置的日志记录级别优先于使用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]配置的包日志记录。</span><span class="sxs-lookup"><span data-stu-id="9b563-105">If you deploy the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server, the logging level that you set for the package execution overrides the package logging that you configure using [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="9b563-106">默认情况下，包中的容器与其父容器使用相同的日志记录配置。</span><span class="sxs-lookup"><span data-stu-id="9b563-106">By default, the containers in the package use the same logging configuration as their parent container.</span></span> <span data-ttu-id="9b563-107">有关为各个容器设置日志记录选项的信息，请参阅 [使用保存的配置文件配置日志记录](../../2014/integration-services/configure-logging-by-using-a-saved-configuration-file.md)。</span><span class="sxs-lookup"><span data-stu-id="9b563-107">For information about setting logging options for individual containers, see [Configure Logging by Using a Saved Configuration File](../../2014/integration-services/configure-logging-by-using-a-saved-configuration-file.md).</span></span>  
  
### <a name="to-enable-logging-in-a-package"></a><span data-ttu-id="9b563-108">在包中启用日志记录</span><span class="sxs-lookup"><span data-stu-id="9b563-108">To enable logging in a package</span></span>  
  
1.  <span data-ttu-id="9b563-109">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="9b563-109">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="9b563-110">在 **SSIS** 菜单上，单击 **“日志记录”** 。</span><span class="sxs-lookup"><span data-stu-id="9b563-110">On the **SSIS** menu, click **Logging**.</span></span>  
  
3.  <span data-ttu-id="9b563-111">在 **“提供程序类型”** 列表中，选择一个日志提供程序，然后单击 **“添加”** 。</span><span class="sxs-lookup"><span data-stu-id="9b563-111">Select a log provider in the **Provider type** list, and then click **Add**.</span></span>  
  
4.  <span data-ttu-id="9b563-112">在“配置”列中，选择连接管理器或单击“\<New connection>”为日志提供程序新建一个适当类型的连接管理器 。</span><span class="sxs-lookup"><span data-stu-id="9b563-112">In the **Configuration** column, select a connection manager or click **\<New connection>** to create a new connection manager of the appropriate type for the log provider.</span></span> <span data-ttu-id="9b563-113">根据所选提供程序的不同，可以使用下列某个连接管理器：</span><span class="sxs-lookup"><span data-stu-id="9b563-113">Depending on the selected provider, use one of the following connection managers:</span></span>  
  
    -   <span data-ttu-id="9b563-114">对于文本文件，请使用文件连接管理器。</span><span class="sxs-lookup"><span data-stu-id="9b563-114">For Text files, use a File connection manager.</span></span> <span data-ttu-id="9b563-115">有关详细信息，请参阅 [File Connection Manager](connection-manager/file-connection-manager.md)</span><span class="sxs-lookup"><span data-stu-id="9b563-115">For more information, see [File Connection Manager](connection-manager/file-connection-manager.md)</span></span>  
  
    -   <span data-ttu-id="9b563-116">对于 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]，请使用文件连接管理器。</span><span class="sxs-lookup"><span data-stu-id="9b563-116">For [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)], use a File connection manager.</span></span>  
  
    -   <span data-ttu-id="9b563-117">对于 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]，请使用 OLE DB 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="9b563-117">For [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], use an OLE DB connection manager.</span></span> <span data-ttu-id="9b563-118">有关详细信息，请参阅 [OLE DB Connection Manager](connection-manager/ole-db-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="9b563-118">For more information, see [OLE DB Connection Manager](connection-manager/ole-db-connection-manager.md).</span></span>  
  
    -   <span data-ttu-id="9b563-119">对于 Windows 事件日志，无需执行任何操作。</span><span class="sxs-lookup"><span data-stu-id="9b563-119">For Windows Event Log, do nothing.</span></span> [!INCLUDE[ssIS](../includes/ssis-md.md)] <span data-ttu-id="9b563-120">会自动创建日志。</span><span class="sxs-lookup"><span data-stu-id="9b563-120">automatically creates the log.</span></span>  
  
    -   <span data-ttu-id="9b563-121">对于 XML 文件，请使用文件连接管理器。</span><span class="sxs-lookup"><span data-stu-id="9b563-121">For XML files, use a File connection manager.</span></span>  
  
5.  <span data-ttu-id="9b563-122">对于要在包中使用的每个日志，请重复步骤 3 和步骤 4。</span><span class="sxs-lookup"><span data-stu-id="9b563-122">Repeat steps 3 and 4 for each log to use in the package.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9b563-123">一个包可以使用多个同一类型的日志。</span><span class="sxs-lookup"><span data-stu-id="9b563-123">A package can use more than one log of each type.</span></span>  
  
6.  <span data-ttu-id="9b563-124">还可以选中包级复选框，选择要用于包级日志记录的日志，然后单击“详细信息”  选项卡。</span><span class="sxs-lookup"><span data-stu-id="9b563-124">Optionally, select the package-level check box, select the logs to use for package-level logging, and then click the **Details** tab.</span></span>  
  
7.  <span data-ttu-id="9b563-125">在 **“详细信息”** 选项卡上，选择 **“事件”** 将记录所有日志项，清除 **“事件”** 可以选择单个事件。</span><span class="sxs-lookup"><span data-stu-id="9b563-125">On the **Details** tab, select **Events** to log all log entries, or clear **Events** to select individual events.</span></span>  
  
8.  <span data-ttu-id="9b563-126">还可以单击 **“高级”** 指定要记录的信息。</span><span class="sxs-lookup"><span data-stu-id="9b563-126">Optionally, click **Advanced** to specify which information to log.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9b563-127">默认情况下会记录所有信息。</span><span class="sxs-lookup"><span data-stu-id="9b563-127">By default, all information is logged.</span></span>  
  
9. <span data-ttu-id="9b563-128">在“详细信息”  选项卡上，单击“保存”  。</span><span class="sxs-lookup"><span data-stu-id="9b563-128">On the **Details** tab, click **Save.**</span></span> <span data-ttu-id="9b563-129">将显示 **“另存为”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="9b563-129">The **Save As** dialog box appears.</span></span> <span data-ttu-id="9b563-130">找到要将日志记录配置保存到的文件夹，为新的日志配置键入文件名，然后单击 **“保存”** 。</span><span class="sxs-lookup"><span data-stu-id="9b563-130">Locate the folder in which to save the logging configuration, type a file name for the new log configuration, and then click **Save**.</span></span>  
  
10. <span data-ttu-id="9b563-131">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="9b563-131">Click **OK**.</span></span>  
  
11. <span data-ttu-id="9b563-132">若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="9b563-132">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b563-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9b563-133">See Also</span></span>  
 <span data-ttu-id="9b563-134">[Integration Services &#40;SSIS&#41; 日志记录](performance/integration-services-ssis-logging.md) </span><span class="sxs-lookup"><span data-stu-id="9b563-134">[Integration Services &#40;SSIS&#41; Logging](performance/integration-services-ssis-logging.md) </span></span>  
 [<span data-ttu-id="9b563-135">Integration Services (SSIS) 日志记录</span><span class="sxs-lookup"><span data-stu-id="9b563-135">Integration Services &#40;SSIS&#41; Logging</span></span>](performance/integration-services-ssis-logging.md)  
  
  
