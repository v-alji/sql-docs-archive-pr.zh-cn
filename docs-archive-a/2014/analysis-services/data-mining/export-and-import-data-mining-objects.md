---
title: 导出和导入数据挖掘对象 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- backing up databases [Analysis Services]
- exporting mining models
- exporting mining structures
- mining structures [Analysis Services], creating
- mining structures [DMX], exporting
- mining models [Analysis Services], migration
ms.assetid: 10a83b13-2640-4ff5-80c8-a35e1d692908
author: minewiskan
ms.author: owend
ms.openlocfilehash: 01e8651dd7e9d59012b0ba065bccb9ea62a1ee54
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588753"
---
# <a name="export-and-import-data-mining-objects"></a><span data-ttu-id="aba50-102">导出和导入数据挖掘对象</span><span class="sxs-lookup"><span data-stu-id="aba50-102">Export and Import Data Mining Objects</span></span>
  <span data-ttu-id="aba50-103">除了 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中提供的用于备份、还原和迁移解决方案的功能外，SQL Server 数据挖掘还提供了可通过使用数据挖掘扩展插件 (DMX)，在不同的服务器之间快速传输数据挖掘结构和模型的功能。</span><span class="sxs-lookup"><span data-stu-id="aba50-103">In addition to the functionality provided in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] for backing up, restoring, and migrating solutions, SQL Server Data Mining provides the ability to quickly transfer data mining structures and models between different servers by using Data Mining Extensions (DMX).</span></span>  
  
 <span data-ttu-id="aba50-104">如果您的数据挖掘解决方案使用的是关系数据而不是多维数据库时，与使用数据还原或部署整个解决方案相比，使用 `EXPORT` 和 `IMPORT` 来传输模型更加快捷。</span><span class="sxs-lookup"><span data-stu-id="aba50-104">If your data mining solution uses relational data instead of a multidimensional database, transferring models by using `EXPORT` and `IMPORT` is much faster and easier than either using database restore or deploying an entire solution.</span></span>  
  
 <span data-ttu-id="aba50-105">本节简要说明如何使用 DMX 语句来传输数据挖掘结构和模型。</span><span class="sxs-lookup"><span data-stu-id="aba50-105">This section provides an overview of how to transfer data mining structures and models by using DMX statements.</span></span> <span data-ttu-id="aba50-106">有关语法的详细信息以及相应的示例，请参阅 [EXPORT (DMX)](/sql/dmx/export-dmx) 和 [IMPORT (DMX)](/sql/dmx/import-dmx)。</span><span class="sxs-lookup"><span data-stu-id="aba50-106">For details of the syntax, together with examples, see [EXPORT &#40;DMX&#41;](/sql/dmx/export-dmx) and [IMPORT &#40;DMX&#41;](/sql/dmx/import-dmx).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aba50-107">只有数据库或服务器管理员才能从 Microsoft SQL Server Analysis Services 数据库导出对象或向其中导入对象。</span><span class="sxs-lookup"><span data-stu-id="aba50-107">You must be a database or server administrator to export or import objects from a Microsoft SQL Server Analysis Services database.</span></span>  
  
## <a name="exporting-data-mining-structures"></a><span data-ttu-id="aba50-108">导出数据挖掘结构</span><span class="sxs-lookup"><span data-stu-id="aba50-108">Exporting Data Mining Structures</span></span>  
 <span data-ttu-id="aba50-109">导出挖掘结构时，EXPORT 语句将自动导出所有关联的模型。</span><span class="sxs-lookup"><span data-stu-id="aba50-109">When you export a mining structure, the EXPORT statement automatically exports all associated models.</span></span> <span data-ttu-id="aba50-110">若要控制导出的对象，则必须按名称逐个指定每个对象。</span><span class="sxs-lookup"><span data-stu-id="aba50-110">If you want to control the objects that are exported, you must specify each object by name.</span></span>  
  
 <span data-ttu-id="aba50-111">如果挖掘结构已经过处理且已缓存结果（这是默认行为），则在您导出挖掘结构时，定义中将包含该结构所基于的数据的摘要。</span><span class="sxs-lookup"><span data-stu-id="aba50-111">If the mining structure has been processed and the results have been cached, which is the default behavior, when you export the mining structure, the definition contains a summary of the data on which the structure is based.</span></span> <span data-ttu-id="aba50-112">若要删除此摘要，则必须通过执行 `Process Clear Structure` 操作来清除与挖掘结构相关联的缓存。</span><span class="sxs-lookup"><span data-stu-id="aba50-112">To remove this summary, you must clear the cache associated with the mining structure by performing a `Process Clear Structure` operation.</span></span> <span data-ttu-id="aba50-113">有关详细信息，请参阅 [Process a Mining Structure](process-a-mining-structure.md)。</span><span class="sxs-lookup"><span data-stu-id="aba50-113">For more information, see [Process a Mining Structure](process-a-mining-structure.md).</span></span>  
  
### <a name="exporting-data-mining-models"></a><span data-ttu-id="aba50-114">导出数据挖掘模型</span><span class="sxs-lookup"><span data-stu-id="aba50-114">Exporting Data Mining Models</span></span>  
 <span data-ttu-id="aba50-115">您可以使用 `WITH DEPENDENCIES` 关键字导出数据源、数据源视图定义以及挖掘模型及其结构。</span><span class="sxs-lookup"><span data-stu-id="aba50-115">You can use the `WITH DEPENDENCIES` keyword to export the data source and data source view definition together with the mining model and its structure.</span></span>  
  
 <span data-ttu-id="aba50-116">如果导出挖掘模型，但却不导出其依赖项，则 EXPORT 语句将导出挖掘模型的定义及其挖掘结构，而不导出数据源的定义。</span><span class="sxs-lookup"><span data-stu-id="aba50-116">When you export a mining model without exporting its dependencies, the EXPORT statement will export the definition of the mining model and its mining structure, but does not export the definition of the data sources.</span></span> <span data-ttu-id="aba50-117">因此，导入了模型后您将能够立即浏览该模型，但是，如果您想要在目标服务器上重新处理挖掘模型，或对基础数据运行查询，则必须在目标服务器上创建相应的数据源。</span><span class="sxs-lookup"><span data-stu-id="aba50-117">As a consequence, after you import the model you will be able to browse the model immediately, but if you want to reprocess the mining model on the target server, or run queries against the underlying data, you must create a corresponding data source on the destination server.</span></span>  
  
## <a name="importing-data-mining-structures-and-models"></a><span data-ttu-id="aba50-118">导入数据挖掘结构和模型</span><span class="sxs-lookup"><span data-stu-id="aba50-118">Importing Data Mining Structures and Models</span></span>  
 <span data-ttu-id="aba50-119">导入数据挖掘对象时，对象将被导入到您在执行 IMPORT 语句时所连接到的服务器和数据库。</span><span class="sxs-lookup"><span data-stu-id="aba50-119">When you import a data mining object, the object is imported to the server and database to which you are connected when you execute the IMPORT statement.</span></span> <span data-ttu-id="aba50-120">如果导入文件包含服务器中不存在的数据库，则系统将创建该数据库。</span><span class="sxs-lookup"><span data-stu-id="aba50-120">If the import file includes a database that does not exist on the server, the database will be created.</span></span>  
  
 <span data-ttu-id="aba50-121">您还可以使用 `Restore` 命令来导入挖掘结构或挖掘模型。</span><span class="sxs-lookup"><span data-stu-id="aba50-121">You can also import a mining structure or mining model by using the `Restore` command.</span></span> <span data-ttu-id="aba50-122">您的模型或结构将被还原到与其所导出的数据库同名的数据库中。</span><span class="sxs-lookup"><span data-stu-id="aba50-122">Your models or structures will be restored into the database that has the same name as the database from which they were exported.</span></span> <span data-ttu-id="aba50-123">有关详细信息，请参阅 [Restore Options](../multidimensional-models/restore-options.md)。</span><span class="sxs-lookup"><span data-stu-id="aba50-123">For more information, see [Restore Options](../multidimensional-models/restore-options.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aba50-124">备注</span><span class="sxs-lookup"><span data-stu-id="aba50-124">Remarks</span></span>  
 <span data-ttu-id="aba50-125">如果服务器中已存在同名模型或结构，则不能将模型或结构导入该服务器。</span><span class="sxs-lookup"><span data-stu-id="aba50-125">You cannot import a model or structure to a server if a model or structure of the same name already exists on that server.</span></span> <span data-ttu-id="aba50-126">同样，也不能先导出数据挖掘对象，然后在导出文件中修改对象的名称。</span><span class="sxs-lookup"><span data-stu-id="aba50-126">Also, you cannot export a data mining object and then modify the name of that object in the export file.</span></span> <span data-ttu-id="aba50-127">因此，如果预计会出现命名冲突，请删除目标服务器上的数据挖掘对象，或在导出定义前重新命名该数据挖掘对象。</span><span class="sxs-lookup"><span data-stu-id="aba50-127">Therefore, if you anticipate naming conflicts, you should either delete the data mining object on the target server, or rename the data mining object before you export the definition.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aba50-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aba50-128">See Also</span></span>  
 [<span data-ttu-id="aba50-129">管理数据挖掘解决方案和对象</span><span class="sxs-lookup"><span data-stu-id="aba50-129">Management of Data Mining Solutions and Objects</span></span>](management-of-data-mining-solutions-and-objects.md)  
  
  
