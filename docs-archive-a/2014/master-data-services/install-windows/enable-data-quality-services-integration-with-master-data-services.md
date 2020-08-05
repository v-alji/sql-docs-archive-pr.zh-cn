---
title: 实现 Data Quality Services 与 Master Data Services 的集成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: ab32938d-a80e-4106-80d4-94b2de3d67dc
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 8d2fa25254cae2a129b6e08ff657d92af4ff9455
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580311"
---
# <a name="enable-data-quality-services-integration-with-master-data-services"></a><span data-ttu-id="61431-102">实现 Data Quality Services 与 Master Data Services 的集成</span><span class="sxs-lookup"><span data-stu-id="61431-102">Enable Data Quality Services Integration with Master Data Services</span></span>
  <span data-ttu-id="61431-103">在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，匹配功能由 Data Quality Services (DQS) 提供。</span><span class="sxs-lookup"><span data-stu-id="61431-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], matching functionality is provided by Data Quality Services (DQS).</span></span> <span data-ttu-id="61431-104">此功能必须启用后才能使用。</span><span class="sxs-lookup"><span data-stu-id="61431-104">This functionality must be enabled to be used.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="61431-105">先决条件</span><span class="sxs-lookup"><span data-stu-id="61431-105">Prerequisites</span></span>  
  
-   <span data-ttu-id="61431-106">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Web 应用程序和数据库必须存在。</span><span class="sxs-lookup"><span data-stu-id="61431-106">A [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] web application and database must exist.</span></span>  
  
-   <span data-ttu-id="61431-107">Data Quality Services 功能和数据质量客户端必须安装在承载 MDS 数据库的同一个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例上。</span><span class="sxs-lookup"><span data-stu-id="61431-107">The Data Quality Services feature and the Data Quality Client must be installed on the same [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that hosts the MDS database.</span></span> <span data-ttu-id="61431-108">有关详细信息，请参阅 [Install Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md)。</span><span class="sxs-lookup"><span data-stu-id="61431-108">For more information, see [Install Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md).</span></span>  
  
### <a name="to-enable-data-quality-services-integration"></a><span data-ttu-id="61431-109">启用 Data Quality Services 集成</span><span class="sxs-lookup"><span data-stu-id="61431-109">To enable Data Quality Services integration</span></span>  
  
1.  <span data-ttu-id="61431-110">打开 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="61431-110">Open [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].</span></span>  
  
2.  <span data-ttu-id="61431-111">在左窗格中单击 **“Web 配置”** 。</span><span class="sxs-lookup"><span data-stu-id="61431-111">In the left pane, click **Web Configuration**.</span></span>  
  
3.  <span data-ttu-id="61431-112">在 **“Web 配置”** 页上，选择网站和 Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="61431-112">On the **Web Configuration** page, select the website and web application.</span></span>  
  
4.  <span data-ttu-id="61431-113">在 **“启用 DQS 集成”** 部分中，单击 **“启用与 Data Quality Services 的集成”**。</span><span class="sxs-lookup"><span data-stu-id="61431-113">In the **Enable DQS Integration** section, click **Enable integration with Data Quality Services**.</span></span>  
  
5.  <span data-ttu-id="61431-114">在确认对话框中，单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="61431-114">On the confirmation dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61431-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="61431-115">See Also</span></span>  
 <span data-ttu-id="61431-116">[MDS Add-in for Excel 中的数据质量匹配](../microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="61431-116">[Data Quality Matching in the MDS Add-in for Excel](../microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md) </span></span>  
 <span data-ttu-id="61431-117">[Master Data Services Add-in for Microsoft Excel](../microsoft-excel-add-in/master-data-services-add-in-for-microsoft-excel.md) </span><span class="sxs-lookup"><span data-stu-id="61431-117">[Master Data Services Add-in for Microsoft Excel](../microsoft-excel-add-in/master-data-services-add-in-for-microsoft-excel.md) </span></span>  
 [<span data-ttu-id="61431-118">安装 Master Data Services</span><span class="sxs-lookup"><span data-stu-id="61431-118">Install Master Data Services</span></span>](install-master-data-services.md)  
  
  
