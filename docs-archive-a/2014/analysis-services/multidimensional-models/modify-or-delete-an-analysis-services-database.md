---
title: 修改或删除 Analysis Services 数据库 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- databases [Analysis Services], modifying
- removing databases
- deleting databases
- dropping databases
- databases [Analysis Services], deleting
- modifying databases
ms.assetid: e48e3988-c091-4379-aabc-4da62f709a7e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6182e91bd95754fe639e8a48548b5cab1835bdc7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693130"
---
# <a name="modify-or-delete-an-analysis-services-database"></a><span data-ttu-id="ae961-102">修改或删除 Analysis Services 数据库</span><span class="sxs-lookup"><span data-stu-id="ae961-102">Modify or Delete an Analysis Services Database</span></span>
  <span data-ttu-id="ae961-103">在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中部署之前以及在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中部署之后，可以更改 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]数据库的名称和说明。</span><span class="sxs-lookup"><span data-stu-id="ae961-103">You can change the name and description of an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database before deployment in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and after deployment in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="ae961-104">您还可以调整 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库上的其他设置，这取决于环境。</span><span class="sxs-lookup"><span data-stu-id="ae961-104">You can also adjust additional settings on an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, depending on the environment.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ae961-105">您不能在联机模式下使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 更改数据库属性。</span><span class="sxs-lookup"><span data-stu-id="ae961-105">You cannot change database properties using [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] in online mode.</span></span>  
  
## <a name="modifying-databases-using-sql-server-management-studio"></a><span data-ttu-id="ae961-106">使用 SQL Server Management Studio 修改数据库</span><span class="sxs-lookup"><span data-stu-id="ae961-106">Modifying Databases Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="ae961-107">一旦 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库的部署完成，您就可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 来更改 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 在连接到该数据库包含的数据源时使用的模拟模式。</span><span class="sxs-lookup"><span data-stu-id="ae961-107">Once an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database is deployed, you can use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to change the impersonation mode used by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] when connecting to data sources contained by the database.</span></span> <span data-ttu-id="ae961-108">模拟模式允许您指定 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 在试图连接到某个数据源进行处理、浏览或钻取时使用的安全上下文。</span><span class="sxs-lookup"><span data-stu-id="ae961-108">The impersonation mode allows you to specify the security context used by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] when attempting to connect to a data source for processing, browsing, or drillthrough purposes.</span></span>  
  
## <a name="modifying-databases-using-sql-server-data-tools"></a><span data-ttu-id="ae961-109">使用 SQL Server Data Tools 修改数据库</span><span class="sxs-lookup"><span data-stu-id="ae961-109">Modifying Databases Using SQL Server Data Tools</span></span>  
 <span data-ttu-id="ae961-110">您可以使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 在项目模式下修改用于定义数据库的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目的标题和说明的翻译。</span><span class="sxs-lookup"><span data-stu-id="ae961-110">You can use [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] in project mode to modify the translations for the caption and description of an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project used to define a database.</span></span> <span data-ttu-id="ae961-111">有关在数据库中使用翻译的详细信息 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，请参阅[Analysis Services Multidimensional 的全球化方案](../globalization-scenarios-for-analysis-services-multiidimensional.md)。</span><span class="sxs-lookup"><span data-stu-id="ae961-111">For more information about using translations in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, see [Globalization scenarios for Analysis Services Multiidimensional](../globalization-scenarios-for-analysis-services-multiidimensional.md).</span></span>  
  
 <span data-ttu-id="ae961-112">您还可以设置与由数据库中包含的维度的帐户属性使用的帐户类型相关联的别名和聚合函数。</span><span class="sxs-lookup"><span data-stu-id="ae961-112">You can also set the aliases and aggregation functions associated with account types used by account attributes in dimensions contained by the database.</span></span> <span data-ttu-id="ae961-113">别名允许您为帐户图表中的帐户类型选择您的组织使用的特定于业务的术语。</span><span class="sxs-lookup"><span data-stu-id="ae961-113">Aliases allow you to select the business-specific terminology used by your organization for the account types in a chart of accounts.</span></span> <span data-ttu-id="ae961-114">帐户属性的成员使用帐户类型来指示如何使用为数据库中包含的各个帐户类型指定的聚合函数来针对各个成员聚合度量值。</span><span class="sxs-lookup"><span data-stu-id="ae961-114">The account types are used by members of an account attribute to indicate how to aggregate measures over each member by using the aggregation functions specified for each account type contained in the database.</span></span> <span data-ttu-id="ae961-115">有关帐户属性的详细信息，请参阅 [属性和属性层次结构](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)。</span><span class="sxs-lookup"><span data-stu-id="ae961-115">For more information about account attributes, see [Attributes and Attribute Hierarchies](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md).</span></span>  
  
## <a name="deleting-databases"></a><span data-ttu-id="ae961-116">删除数据库</span><span class="sxs-lookup"><span data-stu-id="ae961-116">Deleting Databases</span></span>  
 <span data-ttu-id="ae961-117">删除某个现有的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库将删除该数据库和该数据库中所有的多维数据集、维度和挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="ae961-117">Deleting an existing [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database deletes the database and all cubes, dimensions, and mining models in the database.</span></span> <span data-ttu-id="ae961-118">您只能在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中删除现有的 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]数据库。</span><span class="sxs-lookup"><span data-stu-id="ae961-118">You can only delete an existing [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
#### <a name="to-delete-an-analysis-services-database"></a><span data-ttu-id="ae961-119">删除 Analysis Services 数据库</span><span class="sxs-lookup"><span data-stu-id="ae961-119">To delete an Analysis Services database</span></span>  
  
1.  <span data-ttu-id="ae961-120">连接到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="ae961-120">Connect to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span>  
  
2.  <span data-ttu-id="ae961-121">**“对象资源管理器”** 中，展开连接的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例的节点，并确保要删除的对象可见。</span><span class="sxs-lookup"><span data-stu-id="ae961-121">In **Object Explorer**, expand the node for the connected [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance and ensure that the object to be deleted is visible.</span></span>  
  
3.  <span data-ttu-id="ae961-122">右键单击要删除的对象，再选择“删除”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ae961-122">Right-click the object to be deleted and select **Delete**.</span></span>  
  
4.  <span data-ttu-id="ae961-123">在 **“删除对象”** 对话框中，单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="ae961-123">In the **Delete Object** dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae961-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ae961-124">See Also</span></span>  
 [<span data-ttu-id="ae961-125">记录和编写 Analysis Services 数据库脚本</span><span class="sxs-lookup"><span data-stu-id="ae961-125">Document and Script an Analysis Services Database</span></span>](document-and-script-an-analysis-services-database.md)  
  
  
