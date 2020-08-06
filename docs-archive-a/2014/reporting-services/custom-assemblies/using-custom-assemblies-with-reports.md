---
title: 将自定义程序集用于报表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom assemblies [Reporting Services]
- assemblies [Reporting Services], custom
- custom assemblies [Reporting Services], about custom assemblies
ms.assetid: 53d141d0-2185-466a-84dc-7b90d284da3d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f77b9da44ebb57617bd45e43d1e1e847e9074662
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688623"
---
# <a name="using-custom-assemblies-with-reports"></a><span data-ttu-id="a9a54-102">将自定义程序集用于报表</span><span class="sxs-lookup"><span data-stu-id="a9a54-102">Using Custom Assemblies with Reports</span></span>
  <span data-ttu-id="a9a54-103">在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中，您可以为报表项值、样式和格式设置编写自定义代码。</span><span class="sxs-lookup"><span data-stu-id="a9a54-103">In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you can write custom code for report item values, styles, and formatting.</span></span> <span data-ttu-id="a9a54-104">例如，您可以使用自定义代码基于区域性设置货币的格式，使用特殊格式设置标记某些值，或者为您的公司应用其他实行中的业务规则。</span><span class="sxs-lookup"><span data-stu-id="a9a54-104">For example, you can use custom code to format currencies based on locale, flag certain values with special formatting, or apply other business rules that are in practice for your company.</span></span> <span data-ttu-id="a9a54-105">在报表中包括此代码的一种方法是，使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 可从报表定义文件内引用的创建自定义代码程序集。</span><span class="sxs-lookup"><span data-stu-id="a9a54-105">One way to include this code in your reports is to create a custom code assembly using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] that you can reference from within your report definition files.</span></span> <span data-ttu-id="a9a54-106">报表运行时，服务器将调用自定义程序集中的函数。</span><span class="sxs-lookup"><span data-stu-id="a9a54-106">The server calls the functions in your custom assemblies when a report is run.</span></span> <span data-ttu-id="a9a54-107">自定义程序集可用于检索您计划在报表中使用的指定函数。</span><span class="sxs-lookup"><span data-stu-id="a9a54-107">Custom assemblies can be used to retrieve specialized functions that you plan to use in your reports.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a9a54-108">本节内容</span><span class="sxs-lookup"><span data-stu-id="a9a54-108">In This Section</span></span>  
 [<span data-ttu-id="a9a54-109">在 RDL 文件中引用程序集</span><span class="sxs-lookup"><span data-stu-id="a9a54-109">Referencing Assemblies in an RDL File</span></span>](referencing-assemblies-in-an-rdl-file.md)  
 <span data-ttu-id="a9a54-110">介绍如何引用报表定义语言文件中的自定义程序集。</span><span class="sxs-lookup"><span data-stu-id="a9a54-110">Describes how to reference your custom assemblies in a report definition language file.</span></span>  
  
 [<span data-ttu-id="a9a54-111">部署自定义程序集</span><span class="sxs-lookup"><span data-stu-id="a9a54-111">Deploying a Custom Assembly</span></span>](deploying-a-custom-assembly.md)  
 <span data-ttu-id="a9a54-112">介绍如何将自定义程序集部署到报表设计器和报表服务器。</span><span class="sxs-lookup"><span data-stu-id="a9a54-112">Describes how to deploy a custom assembly to Report Designer and the report server.</span></span>  
  
 [<span data-ttu-id="a9a54-113">使用具有强名称的自定义程序集</span><span class="sxs-lookup"><span data-stu-id="a9a54-113">Using Strong-Named Custom Assemblies</span></span>](using-strong-named-custom-assemblies.md)  
 <span data-ttu-id="a9a54-114">介绍如何使用具有强名称的程序集。</span><span class="sxs-lookup"><span data-stu-id="a9a54-114">Describes how to use custom assemblies with strong names.</span></span>  
  
 [<span data-ttu-id="a9a54-115">在自定义程序集中断言权限</span><span class="sxs-lookup"><span data-stu-id="a9a54-115">Asserting Permissions in Custom Assemblies</span></span>](asserting-permissions-in-custom-assemblies.md)  
 <span data-ttu-id="a9a54-116">介绍如何部署具有有限权限和特定权限的自定义程序集，以及如何在代码中断言这些权限。</span><span class="sxs-lookup"><span data-stu-id="a9a54-116">Describes how to deploy custom assemblies with limited and specific permissions and how to assert those permissions in code.</span></span>  
  
 [<span data-ttu-id="a9a54-117">通过表达式访问自定义程序集</span><span class="sxs-lookup"><span data-stu-id="a9a54-117">Accessing Custom Assemblies Through Expressions</span></span>](accessing-custom-assemblies-through-expressions.md)  
 <span data-ttu-id="a9a54-118">介绍如何在您的报表定义中将自定义程序集方法作为报表表达式调用。</span><span class="sxs-lookup"><span data-stu-id="a9a54-118">Describes how to call custom assembly methods as report expressions in your report definitions.</span></span>  
  
 [<span data-ttu-id="a9a54-119">初始化自定义程序集对象</span><span class="sxs-lookup"><span data-stu-id="a9a54-119">Initializing Custom Assembly Objects</span></span>](initializing-custom-assembly-objects.md)  
 <span data-ttu-id="a9a54-120">介绍如何初始化从报表调用的自定义程序集对象的值。</span><span class="sxs-lookup"><span data-stu-id="a9a54-120">Describes how to initialize values for custom assembly objects called from a report.</span></span>  
  
 [<span data-ttu-id="a9a54-121">如何：调试自定义程序集</span><span class="sxs-lookup"><span data-stu-id="a9a54-121">How to: Debug Custom Assemblies</span></span>](how-to-debug-custom-assemblies.md)  
 <span data-ttu-id="a9a54-122">介绍如何调试您的自定义程序集代码。</span><span class="sxs-lookup"><span data-stu-id="a9a54-122">Describes how to debug your custom assembly code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9a54-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a9a54-123">See Also</span></span>  
 [<span data-ttu-id="a9a54-124">报表定义语言 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="a9a54-124">Report Definition Language &#40;SSRS&#41;</span></span>](../reports/report-definition-language-ssrs.md)  
  
  
