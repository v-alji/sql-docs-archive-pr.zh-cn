---
title: "\"程序集属性\" 对话框 (Analysis Services 多维数据) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.assemblyproperties.f1
ms.assetid: da1174d6-d82b-4337-ac19-7368dbd95a84
author: minewiskan
ms.author: owend
ms.openlocfilehash: b9fdd506da42c5088b173db0981b5df94f91e5f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579376"
---
# <a name="assembly-properties-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="9ebb1-102">“程序集属性”对话框（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="9ebb1-102">Assembly Properties Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="9ebb1-103">可以使用 **中的** “程序集属性” [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 对话框，设置 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库中的程序集引用的属性。</span><span class="sxs-lookup"><span data-stu-id="9ebb1-103">Use the **Assembly Properties** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to set the properties of an assembly reference in an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="9ebb1-104">通过在“对象资源管理器”中右键单击某个程序集，并选择“属性”，可以显示“程序集属性”对话框。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="9ebb1-104">You can display the **Assembly Properties** dialog box by right-clicking an assembly in **Object Explorer** and selecting **Properties**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="9ebb1-105">选项</span><span class="sxs-lookup"><span data-stu-id="9ebb1-105">Options</span></span>  
  
|<span data-ttu-id="9ebb1-106">术语</span><span class="sxs-lookup"><span data-stu-id="9ebb1-106">Term</span></span>|<span data-ttu-id="9ebb1-107">定义</span><span class="sxs-lookup"><span data-stu-id="9ebb1-107">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="9ebb1-108">**名称**</span><span class="sxs-lookup"><span data-stu-id="9ebb1-108">**Name**</span></span>|<span data-ttu-id="9ebb1-109">键入内容即可更改程序集引用的名称。</span><span class="sxs-lookup"><span data-stu-id="9ebb1-109">Type to change the name of the assembly reference.</span></span><br /><br /> <span data-ttu-id="9ebb1-110">注意：更改此值不会更改程序集引用所表示引用的程序集的名称，但会更改 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例或数据库在表示程序集引用时所使用的名称。</span><span class="sxs-lookup"><span data-stu-id="9ebb1-110">Note: Changing this value does not change the name of the assembly referred to by the assembly reference, but instead changes the name used the by the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance or database when referring to the assembly reference.</span></span>|  
|<span data-ttu-id="9ebb1-111">**ID**</span><span class="sxs-lookup"><span data-stu-id="9ebb1-111">**ID**</span></span>|<span data-ttu-id="9ebb1-112">显示程序集引用所引用的程序集的标识符。</span><span class="sxs-lookup"><span data-stu-id="9ebb1-112">Displays the identifier of the assembly referred to by the assembly reference.</span></span>|  
|<span data-ttu-id="9ebb1-113">**描述**</span><span class="sxs-lookup"><span data-stu-id="9ebb1-113">**Description**</span></span>|<span data-ttu-id="9ebb1-114">键入内容即可更改程序集引用的名称。</span><span class="sxs-lookup"><span data-stu-id="9ebb1-114">Type to change the description of the assembly reference.</span></span>|  
|<span data-ttu-id="9ebb1-115">**创建时间戳**</span><span class="sxs-lookup"><span data-stu-id="9ebb1-115">**Create Timestamp**</span></span>|<span data-ttu-id="9ebb1-116">显示程序集引用的创建日期和时间。</span><span class="sxs-lookup"><span data-stu-id="9ebb1-116">Displays the date and time the assembly reference was created.</span></span>|  
|<span data-ttu-id="9ebb1-117">**上次架构更新时间**</span><span class="sxs-lookup"><span data-stu-id="9ebb1-117">**Last Schema Update**</span></span>|<span data-ttu-id="9ebb1-118">显示上次更新程序集引用的元数据的日期和时间。</span><span class="sxs-lookup"><span data-stu-id="9ebb1-118">Displays the date and time the metadata for the assembly reference was last updated.</span></span>|  
|<span data-ttu-id="9ebb1-119">类型</span><span class="sxs-lookup"><span data-stu-id="9ebb1-119">**Type**</span></span>|<span data-ttu-id="9ebb1-120">显示程序集引用的类型。</span><span class="sxs-lookup"><span data-stu-id="9ebb1-120">Displays the type of the assembly reference.</span></span> <span data-ttu-id="9ebb1-121">将显示以下值：</span><span class="sxs-lookup"><span data-stu-id="9ebb1-121">The following values are displayed:</span></span><br /><br /> <span data-ttu-id="9ebb1-122">**.Net 程序集**：程序集引用引用 [!INCLUDE[msCoName](../includes/msconame-md.md)] .NET Framework 程序集。</span><span class="sxs-lookup"><span data-stu-id="9ebb1-122">**.NET Assembly**: The assembly reference refers to a [!INCLUDE[msCoName](../includes/msconame-md.md)] .NET Framework assembly.</span></span><br /><br /> <span data-ttu-id="9ebb1-123">**COM DLL**：程序集引用引用 COM 库。</span><span class="sxs-lookup"><span data-stu-id="9ebb1-123">**COM DLL**: The assembly reference refers to a COM library.</span></span>|  
|<span data-ttu-id="9ebb1-124">**数据源**</span><span class="sxs-lookup"><span data-stu-id="9ebb1-124">**Source**</span></span>|<span data-ttu-id="9ebb1-125">显示程序集引用的源。</span><span class="sxs-lookup"><span data-stu-id="9ebb1-125">Displays the source of the assembly reference.</span></span> <span data-ttu-id="9ebb1-126">此属性通常包含程序集引用所引用的程序集的完整路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="9ebb1-126">This property typically contains the full path and file name of the assembly referred to by the assembly reference.</span></span>|  
|<span data-ttu-id="9ebb1-127">**权限集**</span><span class="sxs-lookup"><span data-stu-id="9ebb1-127">**Permission Set**</span></span>|<span data-ttu-id="9ebb1-128">选择用来确定对程序集引用的访问权限的权限集。</span><span class="sxs-lookup"><span data-stu-id="9ebb1-128">Select the permission set used to determine access to the assembly reference.</span></span> <span data-ttu-id="9ebb1-129">有关此属性的可用值的详细信息，请参阅 <xref:Microsoft.AnalysisServices.ClrAssembly.PermissionSet%2A> 。</span><span class="sxs-lookup"><span data-stu-id="9ebb1-129">For more information about the available values for this property, see <xref:Microsoft.AnalysisServices.ClrAssembly.PermissionSet%2A>.</span></span>|  
|<span data-ttu-id="9ebb1-130">**模拟信息**</span><span class="sxs-lookup"><span data-stu-id="9ebb1-130">**Impersonation Info**</span></span>|<span data-ttu-id="9ebb1-131">选择在访问程序集引用时要使用的模拟信息。</span><span class="sxs-lookup"><span data-stu-id="9ebb1-131">Select the impersonation information to use when accessing the assembly reference.</span></span> <span data-ttu-id="9ebb1-132">有关此属性的可用值的详细信息，请参阅 [ImpersonationInfo 元素 (ASSL)](https://docs.microsoft.com/bi-reference/assl/properties/impersonationinfo-element-assl)</span><span class="sxs-lookup"><span data-stu-id="9ebb1-132">For more information about the available values for this property, see [ImpersonationInfo Element &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/impersonationinfo-element-assl)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9ebb1-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9ebb1-133">See Also</span></span>  
 <span data-ttu-id="9ebb1-134">[&#40;多维数据的 Analysis Services 设计器和对话框&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="9ebb1-134">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="9ebb1-135">多维模型程序集管理</span><span class="sxs-lookup"><span data-stu-id="9ebb1-135">Multidimensional Model Assemblies Management</span></span>](multidimensional-models/multidimensional-model-assemblies-management.md)  
  
  
