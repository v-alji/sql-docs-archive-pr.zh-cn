---
title: 删除数据源视图 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- deleting data source views
- data source views [Analysis Services], deleting
- removing data source views
ms.assetid: ae3f5ca0-ecbf-4b52-8386-eb457719d854
author: minewiskan
ms.author: owend
ms.openlocfilehash: 24b587e8d8961161ea803915c31d117c11f7cf2f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590949"
---
# <a name="delete-a-data-source-view-analysis-services"></a><span data-ttu-id="a7978-102">删除数据源视图 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="a7978-102">Delete a Data Source View (Analysis Services)</span></span>
  <span data-ttu-id="a7978-103">如果不再在 OLAP 项目中使用数据源视图 (DSV)，则可以从 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]的项目中删除它。</span><span class="sxs-lookup"><span data-stu-id="a7978-103">If you are no longer using a data source view (DSV) in an OLAP project, you can delete it from the project in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="a7978-104">删除 DSV 的操作是永久性的。</span><span class="sxs-lookup"><span data-stu-id="a7978-104">Deleting a DSV is permanent.</span></span> <span data-ttu-id="a7978-105">无法将删除的 DSV 还原到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目或数据库中。</span><span class="sxs-lookup"><span data-stu-id="a7978-105">You cannot restore a deleted DSV to a [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project or database.</span></span>  
  
 <span data-ttu-id="a7978-106">无法从处于联机模式的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 打开的 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 数据库中删除其他对象依赖的 DSV。</span><span class="sxs-lookup"><span data-stu-id="a7978-106">DSVs that other objects depend on cannot be deleted from an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database opened by [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] in online mode.</span></span> <span data-ttu-id="a7978-107">若要从项目中删除连接到在服务器上运行的数据库的 DSV，您必须在删除 DSV 本身之前，首先删除 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库中依赖于该 DSV 的所有对象。</span><span class="sxs-lookup"><span data-stu-id="a7978-107">To delete a DSV from a project that is connected o a database running on a server, you must first delete all objects in the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database that depend on that DSV before deleting the DSV itself.</span></span>  
  
 <span data-ttu-id="a7978-108">删除某一 DSV 将使依赖它的其他 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 对象失效，因此，在您删除该 DSV 之前，将看到在删除 DSV 后将失效的对象的列表。</span><span class="sxs-lookup"><span data-stu-id="a7978-108">Deleting a DSV will invalidate other [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects that depend on it, so before you delete the DSV, you will see the list of objects that will become invalid once the DSV is removed.</span></span> <span data-ttu-id="a7978-109">请仔细查看此列表，确保它不包含您预期仍要使用的对象。</span><span class="sxs-lookup"><span data-stu-id="a7978-109">Review this list carefully to be sure that it does not include objects you still expect to use.</span></span>  
  
 <span data-ttu-id="a7978-110">![“删除对象”对话框](../media/ssas-olapdsv-deleteobjects.gif "“删除对象”对话框")</span><span class="sxs-lookup"><span data-stu-id="a7978-110">![Delete Objects dialog box](../media/ssas-olapdsv-deleteobjects.gif "Delete Objects dialog box")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7978-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a7978-111">See Also</span></span>  
 <span data-ttu-id="a7978-112">[多维模型中的数据源视图](data-source-views-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="a7978-112">[Data Source Views in Multidimensional Models](data-source-views-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="a7978-113">在数据源视图中更改属性 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="a7978-113">Change Properties in a Data Source View &#40;Analysis Services&#41;</span></span>](change-properties-in-a-data-source-view-analysis-services.md)  
  
  
