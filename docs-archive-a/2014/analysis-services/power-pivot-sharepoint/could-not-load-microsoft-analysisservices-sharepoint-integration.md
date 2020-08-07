---
title: 无法加载文件或程序集 &#39;3.5.0.0，Version =，Culture = 中立，PublicKeyToken = b77a5c561934e089&#39; 或其依赖项之一。 系统找不到指定的文件。 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 81ed0f44-8782-462d-af8f-0ba5b975df27
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3f9eed7ad90c1e720d07c714e351c24ae6657717
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589283"
---
# <a name="could-not-load-file-or-assembly-39microsoftdataservices-version3500-cultureneutral-publickeytokenb77a5c561934e08939-or-one-of-its-dependencies-the-system-cannot-find-the-file-specified"></a><span data-ttu-id="59eec-104">无法加载文件或程序集 &#39;3.5.0.0，Version =，Culture = 中立，PublicKeyToken = b77a5c561934e089&#39; 或其依赖项之一。</span><span class="sxs-lookup"><span data-stu-id="59eec-104">Could not load file or assembly &#39;Microsoft.Data.Services, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089&#39; or one of its dependencies.</span></span> <span data-ttu-id="59eec-105">系统找不到指定的文件。</span><span class="sxs-lookup"><span data-stu-id="59eec-105">The system cannot find the file specified.</span></span>
  <span data-ttu-id="59eec-106">在具有 PowerPivot for SharePoint 的 SharePoint 2010 环境中，如果您尝试执行数据馈送导出并且系统缺少 Microsoft ADO.NET Data Services 的必需版本，则会出现此错误。</span><span class="sxs-lookup"><span data-stu-id="59eec-106">In SharePoint 2010 environments that have PowerPivot for SharePoint, this error will occur if you attempt a data feed export and the system is missing the required version of Microsoft ADO.NET Data Services.</span></span>  
  
## <a name="details"></a><span data-ttu-id="59eec-107">详细信息</span><span class="sxs-lookup"><span data-stu-id="59eec-107">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="59eec-108">适用于</span><span class="sxs-lookup"><span data-stu-id="59eec-108">Applies to</span></span>|<span data-ttu-id="59eec-109">PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="59eec-109">PowerPivot for SharePoint</span></span>|  
|<span data-ttu-id="59eec-110">产品版本</span><span class="sxs-lookup"><span data-stu-id="59eec-110">Product Version</span></span>|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<span data-ttu-id="59eec-111">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59eec-111">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|<span data-ttu-id="59eec-112">原因</span><span class="sxs-lookup"><span data-stu-id="59eec-112">Cause</span></span>|<span data-ttu-id="59eec-113">找不到 ADO.NET Data Services 3.5 SP1。</span><span class="sxs-lookup"><span data-stu-id="59eec-113">ADO.NET Data Services 3.5 SP1 was not found.</span></span>|  
|<span data-ttu-id="59eec-114">消息正文</span><span class="sxs-lookup"><span data-stu-id="59eec-114">Message Text</span></span>|<span data-ttu-id="59eec-115">无法加载文件或程序集“Microsoft.Data.Services, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089”或其依赖项之一。</span><span class="sxs-lookup"><span data-stu-id="59eec-115">Could not load file or assembly 'Microsoft.Data.Services, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.</span></span> <span data-ttu-id="59eec-116">系统找不到指定的文件。</span><span class="sxs-lookup"><span data-stu-id="59eec-116">The system cannot find the file specified</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="59eec-117">说明</span><span class="sxs-lookup"><span data-stu-id="59eec-117">Explanation</span></span>  
 <span data-ttu-id="59eec-118">SharePoint 2010 包括“作为数据馈送导出”按钮，您可以使用该按钮将 SharePoint 列表作为 XML 数据馈送导出。</span><span class="sxs-lookup"><span data-stu-id="59eec-118">SharePoint 2010 includes an Export as Data Feed button that you can use to export a SharePoint list as an XML data feed.</span></span> <span data-ttu-id="59eec-119">此外，SharePoint 模式下的 Reporting Services 和 PowerPivot for SharePoint 都支持要求 ADO.NET Data Services 的数据馈送功能。</span><span class="sxs-lookup"><span data-stu-id="59eec-119">In addition, both Reporting Services in SharePoint mode and PowerPivot for SharePoint support data feed features that require ADO.NET Data Services.</span></span>  
  
 <span data-ttu-id="59eec-120">如果 ADO.NET Data Services 未安装，则在您请求数据馈送时，将发生此错误。</span><span class="sxs-lookup"><span data-stu-id="59eec-120">If ADO.NET Data Services is not installed, this error will occur when you request a data feed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="59eec-121">用户操作</span><span class="sxs-lookup"><span data-stu-id="59eec-121">User Action</span></span>  
  
1.  <span data-ttu-id="59eec-122">请参阅 SharePoint 2010 的硬件和软件要求文档，[确定 sharepoint 2010)  (的硬件和软件要求 (](https://go.microsoft.com/fwlink/?LinkId=169734) https://go.microsoft.com/fwlink/?LinkId=169734) 。</span><span class="sxs-lookup"><span data-stu-id="59eec-122">Go to the hardware and software requirements documentation for SharePoint 2010, [Determine Hardware and Software Requirements (SharePoint 2010)](https://go.microsoft.com/fwlink/?LinkId=169734) (https://go.microsoft.com/fwlink/?LinkId=169734).</span></span>  
  
2.  <span data-ttu-id="59eec-123">在 "**安装必备软件**" 中，找到与所使用的操作系统相对应的 ADO.NET Data Services 3.5 的链接。</span><span class="sxs-lookup"><span data-stu-id="59eec-123">In **Installing software prerequisites**, find the link for ADO.NET Data Services 3.5 that corresponds to the operating system you are using.</span></span>  
  
3.  <span data-ttu-id="59eec-124">单击该链接并且运行安装该服务的安装程序。</span><span class="sxs-lookup"><span data-stu-id="59eec-124">Click the link and run the setup program that installs the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59eec-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="59eec-125">See Also</span></span>  
 [<span data-ttu-id="59eec-126">将 PowerPivot 解决方案部署到 SharePoint</span><span class="sxs-lookup"><span data-stu-id="59eec-126">Deploy PowerPivot Solutions to SharePoint</span></span>](deploy-power-pivot-solutions-to-sharepoint.md)  
  
  
