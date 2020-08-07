---
title: 卸载 Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 5c764a00-d4bc-465d-b32e-e4efce052ce4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 2870f7f84ea626b96560af586602996de3657276
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586132"
---
# <a name="uninstall-reporting-services"></a><span data-ttu-id="9438f-102">卸载 Reporting Services</span><span class="sxs-lookup"><span data-stu-id="9438f-102">Uninstall Reporting Services</span></span>
  <span data-ttu-id="9438f-103">卸载 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 不会删除您已创建的内容或已修改的配置。</span><span class="sxs-lookup"><span data-stu-id="9438f-103">Uninstalling [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] does not remove the content you have created or configuration you have modified.</span></span> <span data-ttu-id="9438f-104">但是，如果存在在卸载完成后您需要的内容，建议您首先生成内容的副本，再开始卸载过程。</span><span class="sxs-lookup"><span data-stu-id="9438f-104">However, if there is content you need after the uninstall is complete, it is recommended you make copies of content before you begin the uninstallation process.</span></span>

## <a name="uninstall-sharepoint-mode"></a><span data-ttu-id="9438f-105">卸载 SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="9438f-105">Uninstall SharePoint Mode</span></span>
 <span data-ttu-id="9438f-106">卸载 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式时，删除以下内容：</span><span class="sxs-lookup"><span data-stu-id="9438f-106">When you uninstall [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode, the following are removed:</span></span>

-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="9438f-107">服务和服务代理。</span><span class="sxs-lookup"><span data-stu-id="9438f-107">service and service proxy.</span></span>

-   <span data-ttu-id="9438f-108">用于 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安装的文件。</span><span class="sxs-lookup"><span data-stu-id="9438f-108">Files used for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation.</span></span>

 <span data-ttu-id="9438f-109">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务应用程序不会删除。</span><span class="sxs-lookup"><span data-stu-id="9438f-109">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service applications are not removed.</span></span> <span data-ttu-id="9438f-110">如果您不再需要服务应用程序，可以通过使用 Windows PowerShell 或 SharePoint 管理中心删除它们。</span><span class="sxs-lookup"><span data-stu-id="9438f-110">If you no longer want the service applications, delete them by using Windows PowerShell or SharePoint Central Administration.</span></span>

 <span data-ttu-id="9438f-111">不删除报表项和相关的元数据。</span><span class="sxs-lookup"><span data-stu-id="9438f-111">The report items and related meta data are not removed.</span></span> <span data-ttu-id="9438f-112">此信息包含在与 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务应用程序有关的内容和配置数据库中。</span><span class="sxs-lookup"><span data-stu-id="9438f-112">This information is contained in the content and configuration databases related to the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service applications.</span></span> <span data-ttu-id="9438f-113">在 SharePoint 模式下，不删除这些数据库，您可以手动将它们迁移到 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的另一安装中。</span><span class="sxs-lookup"><span data-stu-id="9438f-113">The databases are not removed and you can manually migrate the databases to another installation of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint mode.</span></span> <span data-ttu-id="9438f-114">如果您不再需要此信息，请删除这些数据库。</span><span class="sxs-lookup"><span data-stu-id="9438f-114">If you no longer want the information, delete the databases.</span></span> <span data-ttu-id="9438f-115">有关详细信息，请参阅 [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="9438f-115">For more information, see [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).</span></span>

 <span data-ttu-id="9438f-116">以下是不删除的三个 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 数据库的示例名称。</span><span class="sxs-lookup"><span data-stu-id="9438f-116">The following are example names of the three [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] databases that are not removed.</span></span>

-   <span data-ttu-id="9438f-117">**报表服务器数据库：** ReportingService_7f616e2d253040e8ab5653b3c09a065e</span><span class="sxs-lookup"><span data-stu-id="9438f-117">**Report server database:** ReportingService_7f616e2d253040e8ab5653b3c09a065e</span></span>

-   <span data-ttu-id="9438f-118">**报表服务器临时数据库：** ReportingService_7f616e2d253040e8ab5653b3c09a065eTempDB</span><span class="sxs-lookup"><span data-stu-id="9438f-118">**Report server temp database:** ReportingService_7f616e2d253040e8ab5653b3c09a065eTempDB</span></span>

-   <span data-ttu-id="9438f-119">**报表服务器警报数据库：** ReportingService_7f616e2d253040e8ab5653b3c09a065e_Alerting</span><span class="sxs-lookup"><span data-stu-id="9438f-119">**Report server alerting database:** ReportingService_7f616e2d253040e8ab5653b3c09a065e_Alerting</span></span>

### <a name="uninstall-the-add-in-for-sharepoint-products"></a><span data-ttu-id="9438f-120">卸载用于 SharePoint 产品的外接程序。</span><span class="sxs-lookup"><span data-stu-id="9438f-120">Uninstall the Add-in for SharePoint Products.</span></span>
 <span data-ttu-id="9438f-121">从计算机卸载外接程序时，可以选择仅卸载这些文件或同时从场中删除 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="9438f-121">When you uninstall the add-in from a computer, you can choose to only uninstall the files or to also remove the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] feature from the farm.</span></span> <span data-ttu-id="9438f-122">有关卸载 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 用于 sharepoint 产品的外接程序的信息，请参阅[安装或卸载用于 sharepoint 的 Reporting Services 外接程序 &#40;sharepoint 2010 和 sharepoint 2013&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="9438f-122">For information on uninstalling the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in for SharePoint products, see [Install or Uninstall the Reporting Services Add-in for SharePoint &#40;SharePoint 2010 and SharePoint 2013&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md).</span></span>

## <a name="uninstall-native-mode"></a><span data-ttu-id="9438f-123">卸载本机模式</span><span class="sxs-lookup"><span data-stu-id="9438f-123">Uninstall Native Mode</span></span>
 <span data-ttu-id="9438f-124">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 在您卸载  本机模式时，在安装后创建  或修改的所有内容都将在原地保留。</span><span class="sxs-lookup"><span data-stu-id="9438f-124">When you uninstall [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] native mode, anything that was **created** or **modified** after the installation is left in place.</span></span> <span data-ttu-id="9438f-125">例如，数据库文件、日志文件、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置文件以及一些内容项（如报表和数据源文件）。</span><span class="sxs-lookup"><span data-stu-id="9438f-125">For example database files, log files, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] configuration files, and content items such as reports and datasource files.</span></span>

 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="9438f-126">是实例功能，因此不在 Windows“控制面板”的“程序和功能”中列出。</span><span class="sxs-lookup"><span data-stu-id="9438f-126">is an instance feature and therefore is not listed in Windows Control Panel, Programs and Features.</span></span> <span data-ttu-id="9438f-127">卸载 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 本机模式：</span><span class="sxs-lookup"><span data-stu-id="9438f-127">To uninstall [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode:</span></span>

1.  <span data-ttu-id="9438f-128">在 Windows“控制面板”中，单击 **“程序和功能”** 。</span><span class="sxs-lookup"><span data-stu-id="9438f-128">In Windows Control Panel, click **Programs and Features**.</span></span>

2.  <span data-ttu-id="9438f-129">在 **“程序和功能”** 中，选择 **Microsoft SQL Server 2012**。</span><span class="sxs-lookup"><span data-stu-id="9438f-129">In **Programs and Features** select **Microsoft SQL Server 2012**.</span></span>

3.  <span data-ttu-id="9438f-130">在卸载向导中，选择包含 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 实例功能 **RS**的实例。</span><span class="sxs-lookup"><span data-stu-id="9438f-130">In the uninstall wizard, select the instance that includes the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance feature **RS**.</span></span>

     <span data-ttu-id="9438f-131">![rs_nativemode_uninstall_selectinstance](../../../2014/sql-server/install/media/rs-nativemode-uninstall-selectinstance.gif "rs_nativemode_uninstall_selectinstance")</span><span class="sxs-lookup"><span data-stu-id="9438f-131">![rs_nativemode_uninstall_selectinstance](../../../2014/sql-server/install/media/rs-nativemode-uninstall-selectinstance.gif "rs_nativemode_uninstall_selectinstance")</span></span>

4.  <span data-ttu-id="9438f-132">选择该实例后，选择 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="9438f-132">After you select the instance, select the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] feature.</span></span>

     <span data-ttu-id="9438f-133">![rs_nativemode_uninstall_selectfeatures](../../../2014/sql-server/install/media/rs-nativemode-uninstall-selectfeatures.gif "rs_nativemode_uninstall_selectfeatures")</span><span class="sxs-lookup"><span data-stu-id="9438f-133">![rs_nativemode_uninstall_selectfeatures](../../../2014/sql-server/install/media/rs-nativemode-uninstall-selectfeatures.gif "rs_nativemode_uninstall_selectfeatures")</span></span>

5.  <span data-ttu-id="9438f-134">完成向导。</span><span class="sxs-lookup"><span data-stu-id="9438f-134">Complete the wizard.</span></span>

## <a name="see-also"></a><span data-ttu-id="9438f-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9438f-135">See Also</span></span>
 <span data-ttu-id="9438f-136">[卸载 SQL Server &#40;安装程序的现有实例&#41;](../../../2014/sql-server/install/uninstall-an-existing-instance-of-sql-server-setup.md) [安装或卸载 PowerPivot for SharePoint 外接程序 &#40;sharepoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013) [安装或卸载用于 SharePoint Reporting Services sharepoint 2010 和 sharepoint 2013 &#40;外接程序&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)</span><span class="sxs-lookup"><span data-stu-id="9438f-136">[Uninstall an Existing Instance of SQL Server &#40;Setup&#41;](../../../2014/sql-server/install/uninstall-an-existing-instance-of-sql-server-setup.md) [Install or Uninstall the PowerPivot for SharePoint Add-in &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013) [Install or Uninstall the Reporting Services Add-in for SharePoint &#40;SharePoint 2010 and SharePoint 2013&#41;](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)</span></span>


