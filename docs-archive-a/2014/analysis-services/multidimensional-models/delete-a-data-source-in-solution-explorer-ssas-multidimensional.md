---
title: 删除解决方案资源管理器 (SSAS 多维) 中的数据源 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.deleteobjects.f1
helpviewer_keywords:
- data sources [Analysis Services], deleting
- deleting data sources
- removing data sources
ms.assetid: b45441ef-f909-4736-98b9-cc80d0acac99
author: minewiskan
ms.author: owend
ms.openlocfilehash: d6101c8704579894590994d88e0286197148b694
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590952"
---
# <a name="delete-a-data-source-in-solution-explorer-ssas-multidimensional"></a><span data-ttu-id="b3885-102">在解决方案资源管理器中删除数据源（SSAS 多维）</span><span class="sxs-lookup"><span data-stu-id="b3885-102">Delete a Data Source in Solution Explorer (SSAS Multidimensional)</span></span>
  <span data-ttu-id="b3885-103">您可以删除某一数据源对象以便从 Analysis Services 多维模型项目中永久删除该对象。</span><span class="sxs-lookup"><span data-stu-id="b3885-103">You can delete a data source object to permanently remove it from an Analysis Services multidimensional model project.</span></span>  
  
 <span data-ttu-id="b3885-104">在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]中，数据源提供了构造数据源视图的基础，而后，数据源视图用于定义 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目或数据库中的维度、多维数据集和挖掘结构。</span><span class="sxs-lookup"><span data-stu-id="b3885-104">In [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], data sources provide the basis on which data source views are constructed, and data source views are in turn used to define dimensions, cubes, and mining structures in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project or database.</span></span> <span data-ttu-id="b3885-105">因此，删除数据源可能会导致 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目中的其他 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 对象无效。</span><span class="sxs-lookup"><span data-stu-id="b3885-105">Therefore, deleting a data source may invalidate other [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> <span data-ttu-id="b3885-106">您应该始终在删除对象前查看提供的依赖对象的列表。</span><span class="sxs-lookup"><span data-stu-id="b3885-106">You should always review the list of dependent objects that is provided before deleting the object.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b3885-107">无法从处于联机模式的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 打开的 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 数据库中删除其他对象所依赖的数据源。</span><span class="sxs-lookup"><span data-stu-id="b3885-107">Data sources on which other objects depend cannot be deleted from an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database opened by [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] in online mode.</span></span> <span data-ttu-id="b3885-108">要删除该数据源，必须先删除 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库中所有依赖该数据源的对象。</span><span class="sxs-lookup"><span data-stu-id="b3885-108">You must delete all objects in the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database that depend on that data source before deleting the data source.</span></span> <span data-ttu-id="b3885-109">有关联机模式的详细信息，请参阅 [Connect in Online Mode to an Analysis Services Database](connect-in-online-mode-to-an-analysis-services-database.md)。</span><span class="sxs-lookup"><span data-stu-id="b3885-109">For more information about online mode, see [Connect in Online Mode to an Analysis Services Database](connect-in-online-mode-to-an-analysis-services-database.md).</span></span>  
  
### <a name="to-delete-a-data-source"></a><span data-ttu-id="b3885-110">删除数据源</span><span class="sxs-lookup"><span data-stu-id="b3885-110">To delete a data source</span></span>  
  
1.  <span data-ttu-id="b3885-111">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，打开要从其中删除数据源的项目或连接到要从其中删除数据源的数据库。</span><span class="sxs-lookup"><span data-stu-id="b3885-111">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the project or connect to the database from which you want to delete a data source.</span></span>  
  
2.  <span data-ttu-id="b3885-112">在 **“解决方案资源管理器”** 中，展开 **“数据源”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="b3885-112">In **Solution Explorer**, expand the **Data Sources** folder.</span></span>  
  
3.  <span data-ttu-id="b3885-113">右键单击数据源，然后单击“删除”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b3885-113">Right-click the data source, and then click **Delete**.</span></span> <span data-ttu-id="b3885-114">**“删除对象”**  对话框将出现，其中显示您删除数据源后将失效的对象。</span><span class="sxs-lookup"><span data-stu-id="b3885-114">The **Delete Objects**  dialog box appears, showing the objects that will be invalidated if you delete the data source.</span></span> <span data-ttu-id="b3885-115">在单击 **“确定”** 以便删除数据源之前请仔细查看此列表。</span><span class="sxs-lookup"><span data-stu-id="b3885-115">Review this list carefully before clicking **OK** to delete the data source.</span></span>  
  
4.  <span data-ttu-id="b3885-116">保存项目。</span><span class="sxs-lookup"><span data-stu-id="b3885-116">Save the project.</span></span>  
  
     <span data-ttu-id="b3885-117">在从 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目中删除数据源后，必须保存已修改的项目，否则下次打开此项目时将会收到错误，因为当项目尝试加载已删除的数据源时，此数据源的基础 XML 文件将会丢失。</span><span class="sxs-lookup"><span data-stu-id="b3885-117">After deleting a data source from an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project, you must save the modified project or you will receive an error the next time you open the project because the underlying XML file for the deleted data source will be missing when the project attempts to load the deleted data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3885-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b3885-118">See Also</span></span>  
 <span data-ttu-id="b3885-119">[多维模型中的数据源](data-sources-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="b3885-119">[Data Sources in Multidimensional Models](data-sources-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="b3885-120">支持 &#40;SSAS 多维&#41;的数据源</span><span class="sxs-lookup"><span data-stu-id="b3885-120">Data Sources Supported &#40;SSAS Multidimensional&#41;</span></span>](supported-data-sources-ssas-multidimensional.md)  
  
  
