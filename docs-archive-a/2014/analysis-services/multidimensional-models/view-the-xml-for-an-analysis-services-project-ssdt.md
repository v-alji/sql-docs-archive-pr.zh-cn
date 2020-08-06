---
title: 查看 Analysis Services 项目的 XML (SSDT) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- projects [Analysis Services], viewing XML
ms.assetid: dd1a4bc6-57b5-47df-8619-09f921aa6351
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1c320145be2073c741498bed0f10732ac8d528e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693116"
---
# <a name="view-the-xml-for-an-analysis-services-project-ssdt"></a><span data-ttu-id="c2c7e-102">查看 Analysis Services 项目的 XML (SSDT)</span><span class="sxs-lookup"><span data-stu-id="c2c7e-102">View the XML for an Analysis Services Project (SSDT)</span></span>
  <span data-ttu-id="c2c7e-103">在项目模式下使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库时， [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 为项目文件夹中的每个对象创建 XML 定义。</span><span class="sxs-lookup"><span data-stu-id="c2c7e-103">When you are working with an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database in project mode, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] creates an XML definition for each object within the project folder.</span></span> <span data-ttu-id="c2c7e-104">您可以查看 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中每个对象的 XML 文件的内容，</span><span class="sxs-lookup"><span data-stu-id="c2c7e-104">You can view the contents of the XML file for each object within [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="c2c7e-105">还可以直接编辑 XML 文件；但是，大多数情况下不建议这样做，因为您所做的更改可能会使 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]无法读取 XML。</span><span class="sxs-lookup"><span data-stu-id="c2c7e-105">You can also edit the XML file directly; however, this is not recommended in most circumstances as you may make changes that make the XML unreadable by [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c2c7e-106">您无法查看整个项目的 XML 代码，但是可以查看每个对象的代码，因为每个对象都有单独的文件。</span><span class="sxs-lookup"><span data-stu-id="c2c7e-106">You cannot view the xml code for an entire project, but rather you view the code for each object because a separate file exists for each object.</span></span> <span data-ttu-id="c2c7e-107">查看整个项目的代码的唯一方法是生成项目并查看 .asdatabase 文件中的 ASSL 代码 \<project name> 。</span><span class="sxs-lookup"><span data-stu-id="c2c7e-107">The only way to view the code for an entire project is to build the project and view the ASSL code in the \<project name>.asdatabase file.</span></span>  
  
### <a name="to-view-the-xml-code-for-an-object"></a><span data-ttu-id="c2c7e-108">查看对象的 XML 代码</span><span class="sxs-lookup"><span data-stu-id="c2c7e-108">To view the XML code for an object</span></span>  
  
1.  <span data-ttu-id="c2c7e-109">在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中打开 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]项目。</span><span class="sxs-lookup"><span data-stu-id="c2c7e-109">Open the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="c2c7e-110">在解决方案资源管理器中右键单击对象，再单击“查看代码”。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="c2c7e-110">Right-click the object in Solution Explorer and then click **View Code**.</span></span>  
  
     <span data-ttu-id="c2c7e-111">将在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中显示此对象的 XML 代码。</span><span class="sxs-lookup"><span data-stu-id="c2c7e-111">The XML code for the object appears in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2c7e-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c2c7e-112">See Also</span></span>  
 [<span data-ttu-id="c2c7e-113">生成 Analysis Services 项目 (SSDT)</span><span class="sxs-lookup"><span data-stu-id="c2c7e-113">Build Analysis Services Projects &#40;SSDT&#41;</span></span>](build-analysis-services-projects-ssdt.md)  
  
  
