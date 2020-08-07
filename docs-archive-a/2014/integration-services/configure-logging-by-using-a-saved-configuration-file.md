---
title: 使用保存的配置文件配置日志记录 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- containers [Integration Services], logs
- logs [Integration Services], containers
ms.assetid: e5fdbbcb-94ca-4912-aa7c-0d89cebbd308
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8eb517462d9e932906f739678fbd46c1004fb84d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587972"
---
# <a name="configure-logging-by-using-a-saved-configuration-file"></a><span data-ttu-id="77fd6-102">使用保存的配置文件配置日志记录</span><span class="sxs-lookup"><span data-stu-id="77fd6-102">Configure Logging by Using a Saved Configuration File</span></span>
  <span data-ttu-id="77fd6-103">本过程介绍如何通过加载以前保存的日志记录配置文件来为包中的新容器配置日志记录。</span><span class="sxs-lookup"><span data-stu-id="77fd6-103">This procedure describes how to configure logging for new containers in a package by loading a previously saved logging configuration file.</span></span>  
  
 <span data-ttu-id="77fd6-104">默认情况下，包中的所有容器与其父容器使用相同的日志记录配置。</span><span class="sxs-lookup"><span data-stu-id="77fd6-104">By default, all containers in a package use the same logging configuration as their parent container.</span></span> <span data-ttu-id="77fd6-105">例如，Foreach 循环中的任务使用与 Foreach 循环相同的日志记录配置。</span><span class="sxs-lookup"><span data-stu-id="77fd6-105">For example, the tasks in a Foreach Loop use the same logging configuration as the Foreach Loop.</span></span>  
  
### <a name="to-configure-logging-for-a-container"></a><span data-ttu-id="77fd6-106">为容器配置日志记录</span><span class="sxs-lookup"><span data-stu-id="77fd6-106">To configure logging for a container</span></span>  
  
1.  <span data-ttu-id="77fd6-107">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中，打开包含所需包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="77fd6-107">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="77fd6-108">在 **SSIS** 菜单上，单击 **“日志记录”** 。</span><span class="sxs-lookup"><span data-stu-id="77fd6-108">On the **SSIS** menu, click **Logging**.</span></span>  
  
3.  <span data-ttu-id="77fd6-109">展开包的树视图，并选择要配置的容器。</span><span class="sxs-lookup"><span data-stu-id="77fd6-109">Expand the package tree view and select the container to configure.</span></span>  
  
4.  <span data-ttu-id="77fd6-110">在 **“提供程序和日志”** 选项卡上，选择要用于该容器的日志。</span><span class="sxs-lookup"><span data-stu-id="77fd6-110">On the **Providers and Logs** tab, select the logs to use for the container.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="77fd6-111">只能在包级创建日志。</span><span class="sxs-lookup"><span data-stu-id="77fd6-111">You can create logs only at the package level.</span></span> <span data-ttu-id="77fd6-112">有关详细信息，请参阅 [在 SQL Server Data Tools 中启用包日志记录](../../2014/integration-services/enable-package-logging-in-sql-server-data-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="77fd6-112">For more information, see [Enable Package Logging in SQL Server Data Tools](../../2014/integration-services/enable-package-logging-in-sql-server-data-tools.md).</span></span>  
  
5.  <span data-ttu-id="77fd6-113">单击 **“详细信息”** 选项卡，单击 **“加载”** 。</span><span class="sxs-lookup"><span data-stu-id="77fd6-113">Click the **Details** tab and click **Load**.</span></span>  
  
6.  <span data-ttu-id="77fd6-114">找到要使用的日志记录配置文件，并单击 **“打开”** 。</span><span class="sxs-lookup"><span data-stu-id="77fd6-114">Locate the logging configuration file you want to use and click **Open**.</span></span>  
  
7.  <span data-ttu-id="77fd6-115">（可选）通过在 **“事件”** 列中选中其复选框，选择要记录的其他日志项。</span><span class="sxs-lookup"><span data-stu-id="77fd6-115">Optionally, select a different log entry to log by selecting its check box in the **Events** column.</span></span> <span data-ttu-id="77fd6-116">单击 **“高级”** 可以选择要为此项记录的信息类型。</span><span class="sxs-lookup"><span data-stu-id="77fd6-116">Click **Advanced** to select the type of information to log for this entry.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="77fd6-117">新容器可以包含最初用于创建日志记录配置的容器中所没有的其他日志项。</span><span class="sxs-lookup"><span data-stu-id="77fd6-117">The new container may include additional log entries that are not available for the container originally used to create the logging configuration.</span></span> <span data-ttu-id="77fd6-118">您必须手动选择这些其他日志项，才能对它们进行记录。</span><span class="sxs-lookup"><span data-stu-id="77fd6-118">These additional log entries must be selected manually if you want them to be logged.</span></span>  
  
8.  <span data-ttu-id="77fd6-119">若要保存日志记录配置的更新后的版本，请单击 **“保存”** 。</span><span class="sxs-lookup"><span data-stu-id="77fd6-119">To save the updated version of the logging configuration, click **Save**.</span></span>  
  
9. <span data-ttu-id="77fd6-120">若要保存更新后的包，请单击 **“文件”** 菜单上的 **“保存选定项”** 。</span><span class="sxs-lookup"><span data-stu-id="77fd6-120">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77fd6-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="77fd6-121">See Also</span></span>  
 [<span data-ttu-id="77fd6-122">Integration Services (SSIS) 日志记录</span><span class="sxs-lookup"><span data-stu-id="77fd6-122">Integration Services &#40;SSIS&#41; Logging</span></span>](performance/integration-services-ssis-logging.md)  
  
  
