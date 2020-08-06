---
title: 查看 SQL Server Management Studio (SSIS 服务中 Integration Services 包) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- viewing packages
- connections [Integration Services], packages
ms.assetid: 783e653c-0f1f-45ed-b3ef-5ba07b019f27
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4ba86320f1b1a685eab6e80399f3e8c21bd110eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682931"
---
# <a name="view-integration-services-packages-in-sql-server-management-studio-ssis-service"></a><span data-ttu-id="f9a23-102">在 SQL Server Management Studio 中查看 Integration Services 包（SSIS 服务）</span><span class="sxs-lookup"><span data-stu-id="f9a23-102">View Integration Services Packages in SQL Server Management Studio (SSIS Service)</span></span>
    
> [!IMPORTANT]  
>  <span data-ttu-id="f9a23-103">本主题论述 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务，该服务是用于管理 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包的一种 Windows 服务。</span><span class="sxs-lookup"><span data-stu-id="f9a23-103">This topic discusses the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service, a Windows service for managing [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] <span data-ttu-id="f9a23-104">支持该服务以便与 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]的早期版本向后兼容。</span><span class="sxs-lookup"><span data-stu-id="f9a23-104">supports the service for backward compatibility with earlier releases of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="f9a23-105">从 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]开始，您可以在 Integration Services 服务器上管理诸如包之类的对象。</span><span class="sxs-lookup"><span data-stu-id="f9a23-105">Starting in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], you can manage objects such as packages on the Integration Services server.</span></span>  
  
 <span data-ttu-id="f9a23-106">本过程介绍在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 中如何连接到 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 并查看 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务所管理的包的列表。</span><span class="sxs-lookup"><span data-stu-id="f9a23-106">This procedure describes how to connect to [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] and view a list of the packages that the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service manages.</span></span>  
  
### <a name="to-connect-to-integration-services"></a><span data-ttu-id="f9a23-107">连接到 Integration Services</span><span class="sxs-lookup"><span data-stu-id="f9a23-107">To connect to Integration Services</span></span>  
  
1.  <span data-ttu-id="f9a23-108">单击 **“开始”** ，依次指向 **“所有程序”** 和 **Microsoft SQL Server**，然后单击 **SQL Server Management Studio**。</span><span class="sxs-lookup"><span data-stu-id="f9a23-108">Click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="f9a23-109">在 **“连接到服务器”** 对话框中，在 **“服务器类型”** 列表中选择 **Integration Services** ，在 **“服务器名称”** 框中提供服务器名称，然后单击 **“连接”** 。</span><span class="sxs-lookup"><span data-stu-id="f9a23-109">In the **Connect to Server** dialog box, select **Integration Services** in the **Server type** list, provide a server name in the **Server name** box, and then click **Connect**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="f9a23-110">如果无法连接到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]，则 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务可能未运行。</span><span class="sxs-lookup"><span data-stu-id="f9a23-110">If you cannot connect to [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service is likely not running.</span></span> <span data-ttu-id="f9a23-111">若要了解该服务的状态，请单击 **“开始”** ，依次指向 **“所有程序”** 、 **Microsoft SQL Server**和 **“配置工具”** ，再单击 **“SQL Server 配置管理器”** 。</span><span class="sxs-lookup"><span data-stu-id="f9a23-111">To learn the status of the service, click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span> <span data-ttu-id="f9a23-112">在左窗格中，单击 **“SQL Server 服务”** 。</span><span class="sxs-lookup"><span data-stu-id="f9a23-112">In the left pane, click **SQL Server Services**.</span></span> <span data-ttu-id="f9a23-113">在右窗格中，查找 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服务。</span><span class="sxs-lookup"><span data-stu-id="f9a23-113">In the right pane, find the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service.</span></span> <span data-ttu-id="f9a23-114">如果该服务尚未运行，请启动该服务。</span><span class="sxs-lookup"><span data-stu-id="f9a23-114">Start the service if it is not already running.</span></span>  
  
     [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="f9a23-115">。</span><span class="sxs-lookup"><span data-stu-id="f9a23-115">opens.</span></span> <span data-ttu-id="f9a23-116">默认情况下，会打开对象资源管理器窗口并定位在 SQL Server Management Studio 左下角。</span><span class="sxs-lookup"><span data-stu-id="f9a23-116">By default the Object Explorer window is open and positioned in the lower-left corner of the studio.</span></span> <span data-ttu-id="f9a23-117">如果对象资源管理器未打开，请单击 **“视图”** 菜单上的 **“对象资源管理器”** 。</span><span class="sxs-lookup"><span data-stu-id="f9a23-117">If Object Explorer is not open, click **Object Explorer** on the **View** menu.</span></span>  
  
### <a name="to-view-the-packages-that-integration-services-service-manages"></a><span data-ttu-id="f9a23-118">查看 Integration Services 服务管理的包</span><span class="sxs-lookup"><span data-stu-id="f9a23-118">To view the packages that Integration Services service manages</span></span>  
  
1.  <span data-ttu-id="f9a23-119">在对象资源管理器中，展开“已存储的包”文件夹。</span><span class="sxs-lookup"><span data-stu-id="f9a23-119">In Object Explorer, expand the Stored Packages folder.</span></span>  
  
2.  <span data-ttu-id="f9a23-120">展开“已存储的包”子文件夹，以显示包。</span><span class="sxs-lookup"><span data-stu-id="f9a23-120">Expand the Stored Packages subfolders to show packages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9a23-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f9a23-121">See Also</span></span>  
 <span data-ttu-id="f9a23-122">[包管理 &#40;SSIS 服务&#41;](service/package-management-ssis-service.md) </span><span class="sxs-lookup"><span data-stu-id="f9a23-122">[Package Management &#40;SSIS Service&#41;](service/package-management-ssis-service.md) </span></span>  
 [<span data-ttu-id="f9a23-123">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f9a23-123">Use SQL Server Management Studio</span></span>](../database-engine/use-sql-server-management-studio.md)  
  
  
