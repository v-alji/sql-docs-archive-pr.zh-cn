---
title: 自定义报表项实现要求 | Microsoft Docs
ms.custom: ''
ms.date: 11/25/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom report items
ms.assetid: cfacd816-00d6-4a3d-be72-1bba6f7f6886
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 69fdf58eb385e819b524b9c5b5178997257c797c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693659"
---
# <a name="custom-report-item-implementation-requirements"></a><span data-ttu-id="63d9b-102">自定义报表项实现要求</span><span class="sxs-lookup"><span data-stu-id="63d9b-102">Custom Report Item Implementation Requirements</span></span>
  <span data-ttu-id="63d9b-103">本主题将讨论开发和部署自定义报表项的先决条件。</span><span class="sxs-lookup"><span data-stu-id="63d9b-103">This topic will discuss the prerequisites for developing and deploying custom report items.</span></span>  
  
## <a name="development-and-deployment-requirements"></a><span data-ttu-id="63d9b-104">开发和部署要求</span><span class="sxs-lookup"><span data-stu-id="63d9b-104">Development and Deployment Requirements</span></span>  
 <span data-ttu-id="63d9b-105">为 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 开发自定义报表项要求满足以下条件：</span><span class="sxs-lookup"><span data-stu-id="63d9b-105">Developing a custom report item for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] requires the following:</span></span>  
  
-   <span data-ttu-id="63d9b-106">使用和运行的服务器的管理访问权限 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="63d9b-106">Administrative access to a server running [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] and [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
-   [!INCLUDE[vsprvsext](../../includes/vsprvsext-md.md)]<span data-ttu-id="63d9b-107">或更高版本中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 安装了软件开发工具包 (SDK) 。</span><span class="sxs-lookup"><span data-stu-id="63d9b-107">or above with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] software development kit (SDK) installed.</span></span>  
  
-   <span data-ttu-id="63d9b-108">对于 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK 文档的访问权限。</span><span class="sxs-lookup"><span data-stu-id="63d9b-108">Access to the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
-   <span data-ttu-id="63d9b-109">熟悉组件创作和 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 中的组件模型命名空间。</span><span class="sxs-lookup"><span data-stu-id="63d9b-109">Familiarity with component authoring and the component model namespaces in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="63d9b-110">有关详细信息，请参阅 msdn.microsoft.com 上的“组件创作”和“Visual Studio 中的组件模型命名空间”。</span><span class="sxs-lookup"><span data-stu-id="63d9b-110">For more information, see "Component Authoring" and "Component Model Namespaces in Visual Studio" on msdn.microsoft.com.</span></span>  
  
## <a name="language-and-namespace-requirements"></a><span data-ttu-id="63d9b-111">语言和命名空间要求</span><span class="sxs-lookup"><span data-stu-id="63d9b-111">Language and Namespace Requirements</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="63d9b-112">自定义报表项完全支持 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="63d9b-112">custom report items fully support the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="63d9b-113">您可以使用您选择的 .NET 兼容的语言开发自定义报表项。</span><span class="sxs-lookup"><span data-stu-id="63d9b-113">You can develop custom report items using your choice of .NET-compliant languages.</span></span>  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] <span data-ttu-id="63d9b-114">为开发人员提供了许多工具和功能以简化和加速编码、调试和测试的迭代周期，并使部署过程更为容易。</span><span class="sxs-lookup"><span data-stu-id="63d9b-114">offers the developer many tools and features to simplify and accelerate the iterative cycles of coding, debugging, and testing and to make deployment easier.</span></span> <span data-ttu-id="63d9b-115">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK 包括 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 和 C# 编译器以及相关工具。</span><span class="sxs-lookup"><span data-stu-id="63d9b-115">The [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK includes [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] and C# compilers and related tools.</span></span>  
  
-   <span data-ttu-id="63d9b-116">自定义报表项使用 `Microsoft.ReportDesigner` 和 <xref:Microsoft.ReportingServices.Interfaces> 命名空间。</span><span class="sxs-lookup"><span data-stu-id="63d9b-116">Custom report items use the `Microsoft.ReportDesigner` and <xref:Microsoft.ReportingServices.Interfaces> namespaces.</span></span> <span data-ttu-id="63d9b-117">它们存储在作为 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的一部分安装的 Microsoft.ReportingServices.Designer.DLL 和 Microsoft.ReportingServices.Interfaces.DLL 程序集中。</span><span class="sxs-lookup"><span data-stu-id="63d9b-117">These are stored in the Microsoft.ReportingServices.Designer.DLL and Microsoft.ReportingServices.Interfaces.DLL assemblies, which are installed as part of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="63d9b-118">自定义报表项设计时组件需要在 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 中从 <xref:System.ComponentModel> 命名空间实现接口。</span><span class="sxs-lookup"><span data-stu-id="63d9b-118">Custom report item design-time components need to implement interfaces from the <xref:System.ComponentModel> namespace in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="63d9b-119">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK 文档中有关于 <xref:System.ComponentModel> 的记载。</span><span class="sxs-lookup"><span data-stu-id="63d9b-119">The <xref:System.ComponentModel> is documented in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="63d9b-120">默认情况下，[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 一起安装，但不安装 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK。</span><span class="sxs-lookup"><span data-stu-id="63d9b-120">By default, the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] is installed with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], but the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK is not.</span></span> <span data-ttu-id="63d9b-121">除非 SDK 已安装在计算机上，并且 SDK 文档包含在联机丛书集中，否则本部分中指向 SDK 内容的链接将无效。</span><span class="sxs-lookup"><span data-stu-id="63d9b-121">Unless the SDK is installed on the computer and the SDK documentation is included in the Books Online collection, links to SDK content in this section will not work.</span></span> <span data-ttu-id="63d9b-122">安装 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK 后，可以按照[添加或删除 SQL Server 的产品文档](../../index.yml)中的说明将 SDK 文档添加到联机丛书集和目录中。</span><span class="sxs-lookup"><span data-stu-id="63d9b-122">After you have installed the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK, you can add the SDK documentation to the Books Online collection and table of contents by following the instructions in [Add or Remove Product Documentation for SQL Server](../../index.yml).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63d9b-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="63d9b-123">See Also</span></span>  
 <span data-ttu-id="63d9b-124">[创建自定义报表项运行时组件](creating-a-custom-report-item-run-time-component.md) </span><span class="sxs-lookup"><span data-stu-id="63d9b-124">[Creating a Custom Report Item Run-Time Component](creating-a-custom-report-item-run-time-component.md) </span></span>  
 <span data-ttu-id="63d9b-125">[创建自定义报表项设计时组件](creating-a-custom-report-item-design-time-component.md) </span><span class="sxs-lookup"><span data-stu-id="63d9b-125">[Creating a Custom Report Item Design-Time Component](creating-a-custom-report-item-design-time-component.md) </span></span>  
 <span data-ttu-id="63d9b-126">[如何：部署自定义报表项](how-to-deploy-a-custom-report-item.md) </span><span class="sxs-lookup"><span data-stu-id="63d9b-126">[How to: Deploy a Custom Report Item](how-to-deploy-a-custom-report-item.md) </span></span>  
 [<span data-ttu-id="63d9b-127">自定义报表项类库</span><span class="sxs-lookup"><span data-stu-id="63d9b-127">Custom Report Item Class Libraries</span></span>](custom-report-item-class-libraries.md)  
  
  
