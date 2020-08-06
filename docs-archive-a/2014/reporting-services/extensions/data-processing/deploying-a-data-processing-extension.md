---
title: 部署数据处理扩展插件 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], deploying
- Extension element
- deploying [Reporting Services], extensions
ms.assetid: e5c0b5a9-1386-47cb-aade-96653ecfaa54
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 84fc2d2853ce7a6aae77f313ef0f4026ad2f35cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693640"
---
# <a name="deploying-a-data-processing-extension"></a><span data-ttu-id="dedac-102">部署数据处理扩展插件</span><span class="sxs-lookup"><span data-stu-id="dedac-102">Deploying a Data Processing Extension</span></span>
  <span data-ttu-id="dedac-103">在编写 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 数据处理扩展插件并将其编译为 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 库之后，你需要使其变得可供报表服务器和报表设计器发现。</span><span class="sxs-lookup"><span data-stu-id="dedac-103">Once you have written and compiled your [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension into a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] library, you need to make it discoverable by the report server and by Report Designer.</span></span> <span data-ttu-id="dedac-104">这就像将扩展插件复制到适当的目录并向适当的 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 配置文件添加条目一样轻松。</span><span class="sxs-lookup"><span data-stu-id="dedac-104">This is as easy as copying the extension to the appropriate directories and adding entries to the appropriate [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] configuration files.</span></span>  
  
## <a name="configuration-file-extension-element"></a><span data-ttu-id="dedac-105">配置文件扩展插件元素</span><span class="sxs-lookup"><span data-stu-id="dedac-105">Configuration-File Extension Element</span></span>  
 <span data-ttu-id="dedac-106">在配置文件中，你向报表服务器或报表设计器部署的数据处理扩展插件需要作为 Extension 元素输入  。</span><span class="sxs-lookup"><span data-stu-id="dedac-106">Data processing extensions that you deploy to the report server or Report Designer need to be entered as **Extension** elements in the configuration files.</span></span> <span data-ttu-id="dedac-107">对于报表服务器，这些文件为 RSReportServer.config；对于报表设计器则为 RSReportDesigner.config。</span><span class="sxs-lookup"><span data-stu-id="dedac-107">These files are RSReportServer.config for the report server and RSReportDesigner.config for Report Designer.</span></span>  
  
 <span data-ttu-id="dedac-108">下表介绍数据处理扩展插件的 Extension 元素的属性  。</span><span class="sxs-lookup"><span data-stu-id="dedac-108">The following table describes the attributes for the **Extension** element for data processing extensions.</span></span>  
  
|<span data-ttu-id="dedac-109">Attribute</span><span class="sxs-lookup"><span data-stu-id="dedac-109">Attribute</span></span>|<span data-ttu-id="dedac-110">说明</span><span class="sxs-lookup"><span data-stu-id="dedac-110">Description</span></span>|  
|---------------|-----------------|  
|`Name`|<span data-ttu-id="dedac-111">扩展插件的唯一名称，例如，“SQL”表示 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据处理扩展插件，或者“OLEDB”表示 OLE DB 数据处理扩展插件。</span><span class="sxs-lookup"><span data-stu-id="dedac-111">A unique name for the extension, for example, "SQL" for the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data processing extension or "OLEDB" for the OLE DB data processing extension.</span></span> <span data-ttu-id="dedac-112">`Name` 属性的最大长度是 255 个字符。</span><span class="sxs-lookup"><span data-stu-id="dedac-112">The maximum length for the `Name` attribute is 255 characters.</span></span> <span data-ttu-id="dedac-113">该名称在配置文件的 **Extension** 元素内的所有条目中必须唯一。</span><span class="sxs-lookup"><span data-stu-id="dedac-113">The name must be unique among all entries within the **Extension** element of a configuration file.</span></span>|  
|`Type`|<span data-ttu-id="dedac-114">以逗号分隔的列表，其中包含完全限定的命名空间以及程序集的名称。</span><span class="sxs-lookup"><span data-stu-id="dedac-114">A comma-separated list that includes the fully qualified namespace along with the name of the assembly.</span></span>|  
|`Visible`|<span data-ttu-id="dedac-115">值为 `false` 指示在用户界面中应不显示数据处理扩展插件。</span><span class="sxs-lookup"><span data-stu-id="dedac-115">A value of `false` indicates that the data processing extension should not be visible in user interfaces.</span></span> <span data-ttu-id="dedac-116">如果未包含此属性，则默认值为 `true`。</span><span class="sxs-lookup"><span data-stu-id="dedac-116">If the attribute is not included, the default value is `true`.</span></span>|  
  
 <span data-ttu-id="dedac-117">有关 RSReportServer.config 或 RSReportDesigner.config 文件的详细信息，请参阅 [Reporting Services 配置文件](../../report-server/reporting-services-configuration-files.md)。</span><span class="sxs-lookup"><span data-stu-id="dedac-117">For more information about the RSReportServer.config or RSReportDesigner.config files, see [Reporting Services Configuration Files](../../report-server/reporting-services-configuration-files.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dedac-118">本节内容</span><span class="sxs-lookup"><span data-stu-id="dedac-118">In This Section</span></span>  
  
|<span data-ttu-id="dedac-119">主题</span><span class="sxs-lookup"><span data-stu-id="dedac-119">Topic</span></span>|<span data-ttu-id="dedac-120">说明</span><span class="sxs-lookup"><span data-stu-id="dedac-120">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="dedac-121">如何：向报表服务器部署数据处理扩展插件</span><span class="sxs-lookup"><span data-stu-id="dedac-121">How to: Deploy a Data Processing Extension to a Report Server</span></span>](deploying-a-data-processing-extension-to-a-report-server.md)|<span data-ttu-id="dedac-122">介绍如何将数据处理扩展插件部署到报表服务器。</span><span class="sxs-lookup"><span data-stu-id="dedac-122">Describes how to deploy your data processing extension to a report server.</span></span>|  
|[<span data-ttu-id="dedac-123">如何：向报表设计器部署数据处理扩展插件</span><span class="sxs-lookup"><span data-stu-id="dedac-123">How to: Deploy a Data Processing Extension to Report Designer</span></span>](deploying-a-data-processing-extension-to-report-designer.md)|<span data-ttu-id="dedac-124">介绍如何将数据处理扩展插件部署到报表设计器。</span><span class="sxs-lookup"><span data-stu-id="dedac-124">Describes how to deploy your data processing extension to Report Designer.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dedac-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dedac-125">See Also</span></span>  
 <span data-ttu-id="dedac-126">[Reporting Services 扩展](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="dedac-126">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="dedac-127">[实现数据处理扩展插件](implementing-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="dedac-127">[Implementing a Data Processing Extension](implementing-a-data-processing-extension.md) </span></span>  
 [<span data-ttu-id="dedac-128">Reporting Services 扩展插件库</span><span class="sxs-lookup"><span data-stu-id="dedac-128">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
