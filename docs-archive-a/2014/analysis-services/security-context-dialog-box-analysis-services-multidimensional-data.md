---
title: "\"安全上下文\" 对话框 (Analysis Services 多维数据) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.browsecube.securitycontext.f1
ms.assetid: 238a4a4b-84bd-4b3d-9f02-f3adf57fa3af
author: minewiskan
ms.author: owend
ms.openlocfilehash: 58d5f71172ac16087ecc342342e70ade234226a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579099"
---
# <a name="security-context-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="0d090-102">“安全上下文”对话框（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="0d090-102">Security Context Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="0d090-103">可以使用 **中的** “安全上下文” [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 对话框，更改用于检查 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 对象的数据或元数据的用户和角色。</span><span class="sxs-lookup"><span data-stu-id="0d090-103">Use the **Security Context** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to change the user and role used to examine data or metadata for a [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object.</span></span> <span data-ttu-id="0d090-104">在多维数据集设计器的 **“计算”** 选项卡或 **“浏览器”** 选项卡上，单击 **“工具栏”** 窗格中的 **“安全上下文”** 可以显示 **“安全上下文”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="0d090-104">You can display the **Security Context** dialog box by clicking **Security Context** in the **Toolbar** pane on either the **Calculations** tab or the **Browser** tab in Cube Designer.</span></span>  
  
## <a name="options"></a><span data-ttu-id="0d090-105">选项</span><span class="sxs-lookup"><span data-stu-id="0d090-105">Options</span></span>  
 <span data-ttu-id="0d090-106">**当前用户**</span><span class="sxs-lookup"><span data-stu-id="0d090-106">**Current user**</span></span>  
 <span data-ttu-id="0d090-107">选择此选项可以在查看 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 对象的数据和元数据时使用当前用户的域和用户名。</span><span class="sxs-lookup"><span data-stu-id="0d090-107">Select to use the domain and user name of the current user while viewing the data and metadata of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object.</span></span>  
  
 <span data-ttu-id="0d090-108">**其他用户**</span><span class="sxs-lookup"><span data-stu-id="0d090-108">**Other user**</span></span>  
 <span data-ttu-id="0d090-109">键入要在查看 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 对象的数据和元数据时使用的其他用户或组的域和用户名。</span><span class="sxs-lookup"><span data-stu-id="0d090-109">Type the domain and user name of another user or group to use while viewing the data and metadata of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object.</span></span>  
  
 <span data-ttu-id="0d090-110">用户或组的域和用户名使用下面的格式：</span><span class="sxs-lookup"><span data-stu-id="0d090-110">The domain and name of the user or group uses the following format:</span></span>  
  
 <span data-ttu-id="0d090-111">*\<Domain name>* **\\** *\<User account name>*</span><span class="sxs-lookup"><span data-stu-id="0d090-111">*\<Domain name>* **\\** *\<User account name>*</span></span>  
  
 <span data-ttu-id="0d090-112">**角色**</span><span class="sxs-lookup"><span data-stu-id="0d090-112">**Roles**</span></span>  
 <span data-ttu-id="0d090-113">选择此选项可以在查看 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 对象的数据和元数据时使用一个或多个指定的角色。</span><span class="sxs-lookup"><span data-stu-id="0d090-113">Select to use one or more specified roles when viewing the data and metadata of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object.</span></span> <span data-ttu-id="0d090-114">如果在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库中定义了多个角色，则可以选择要使用的角色。</span><span class="sxs-lookup"><span data-stu-id="0d090-114">You can select the roles to use if multiple roles are defined in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d090-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0d090-115">See Also</span></span>  
 <span data-ttu-id="0d090-116">[&#40;多维数据集设计器的 Kpi&#41; &#40;Analysis Services 多维数据&#41;](kpis-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="0d090-116">[KPIs &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](kpis-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="0d090-117">[浏览器 &#40;多维数据集设计器&#41; &#40;Analysis Services 多维数据&#41;](browser-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="0d090-117">[Browser &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](browser-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="0d090-118">&#40;多维数据的 Analysis Services 设计器和对话框&#41;</span><span class="sxs-lookup"><span data-stu-id="0d090-118">Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;</span></span>](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
