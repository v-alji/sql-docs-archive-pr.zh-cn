---
title: 从 PowerPivot (SSAS 表格) 导入 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.importfromppt.f1
ms.assetid: ac1a6a79-bda3-4122-a717-8b1e2f77da02
author: minewiskan
ms.author: owend
ms.openlocfilehash: 581259d79e5d84bd558ca3f13519fbf4dc0ba52f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687219"
---
# <a name="import-from-powerpivot-ssas-tabular"></a><span data-ttu-id="b3f9a-102">从 PowerPivot 导入（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="b3f9a-102">Import from PowerPivot (SSAS Tabular)</span></span>
  <span data-ttu-id="b3f9a-103">本主题介绍如何通过使用中的 "从 PowerPivot 导入" 项目模板从 PowerPivot 工作簿导入元数据和数据，从而创建新的表格模型项目 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="b3f9a-103">This topic describes how to create a new tabular model project by importing the metadata and data from a PowerPivot workbook by using the Import from PowerPivot project template in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="create-a-new-tabular-model-from-a-powerpivot-for-excel-file"></a><span data-ttu-id="b3f9a-104">从 PowerPivot for Excel 文件创建新的表格模型</span><span class="sxs-lookup"><span data-stu-id="b3f9a-104">Create a new Tabular Model from a PowerPivot for Excel file</span></span>  
 <span data-ttu-id="b3f9a-105">在通过从 PowerPivot 工作簿中导入来创建新的表格模型项目时，将使用定义工作簿结构的元数据来创建和定义 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 中的表格模型项目的结构。</span><span class="sxs-lookup"><span data-stu-id="b3f9a-105">When creating a new tabular model project by importing from a PowerPivot workbook, the metadata that defines the structure of the workbook is used to create and define the structure of the tabular model project in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="b3f9a-106">表、列、度量值和关系之类的对象将与它们处于 PowerPivot 工作簿中一样保留并出现在表格模型项目中。</span><span class="sxs-lookup"><span data-stu-id="b3f9a-106">Objects such as tables, columns, measures, and relationships are retained and will appear in the tabular model project as they are in the PowerPivot workbook.</span></span> <span data-ttu-id="b3f9a-107">不对 .xlsx 工作簿文件进行任何更改。</span><span class="sxs-lookup"><span data-stu-id="b3f9a-107">No changes are made to the .xlsx workbook file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b3f9a-108">表格模型不支持链接表。</span><span class="sxs-lookup"><span data-stu-id="b3f9a-108">Tabular models do not support linked tables.</span></span> <span data-ttu-id="b3f9a-109">在从包含链接表的 PowerPivot 工作簿中导入时，链接表数据将作为复制\粘贴的数据处理并且存储于 Model.bim 文件中。</span><span class="sxs-lookup"><span data-stu-id="b3f9a-109">When importing from a PowerPivot workbook that contains a linked table, linked table data is treated as copy\pasted data and stored in the Model.bim file.</span></span> <span data-ttu-id="b3f9a-110">在查看复制\粘贴的表的属性时，“源数据”\*\*\*\* 属性将被禁用，并且“表”\*\*\*\* 菜单上的“表属性”\*\*\*\* 对话框将被禁用。</span><span class="sxs-lookup"><span data-stu-id="b3f9a-110">When viewing properties for a copy\pasted table, the **Source Data** property is disabled and the **Table Properties** dialog on the **Table** menu is disabled.</span></span>  
>   
>  <span data-ttu-id="b3f9a-111">对于可添加到在模型中嵌入的数据中的行数，有最多 10,000 行的限制。</span><span class="sxs-lookup"><span data-stu-id="b3f9a-111">There is a limit of 10,000 rows that can be added to the data embedded in the model.</span></span> <span data-ttu-id="b3f9a-112">如果从 PowerPivot 导入模型并看到错误 "数据已被截断。</span><span class="sxs-lookup"><span data-stu-id="b3f9a-112">If you import a model from PowerPivot and see the error, "Data was truncated.</span></span> <span data-ttu-id="b3f9a-113">粘贴的表不能包含超过10000行 "您应该通过将嵌入的数据移到另一个数据源（如 SQL Server 中的表），然后重新导入来修改 PowerPivot 模型。</span><span class="sxs-lookup"><span data-stu-id="b3f9a-113">Pasted tables cannot contain more than 10000 rows" you should revise the PowerPivot model by moving the embedded data into another data source, such as a table in SQL Server, and then re-import.</span></span>  
  
 <span data-ttu-id="b3f9a-114">有一些特别注意事项，这取决于工作区数据库是在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 所处的计算机（本地）上的 Analysis Services 实例中还是在远程 Analysis Services 实例中。</span><span class="sxs-lookup"><span data-stu-id="b3f9a-114">There are special considerations depending on whether or not the workspace database is on an Analysis Services instance on the same computer (local) as [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] or is on a remote Analysis Services instance..</span></span>  
  
 <span data-ttu-id="b3f9a-115">如果工作区数据库在本地 Analysis Services 实例中，则可以从 PowerPivot 工作簿导入元数据和数据。</span><span class="sxs-lookup"><span data-stu-id="b3f9a-115">If the workspace database is on a local instance of Analysis Services, you can import both the metadata and data from the PowerPivot workbook.</span></span> <span data-ttu-id="b3f9a-116">从工作簿复制元数据并使用该元数据创建表格模型项目。</span><span class="sxs-lookup"><span data-stu-id="b3f9a-116">The metadata is copied from the workbook and used to create the tabular model project.</span></span> <span data-ttu-id="b3f9a-117">然后，从工作簿复制数据并将其存储到项目的工作区数据库中 (除了复制/粘贴数据，) 存储在 model.bim 文件中。</span><span class="sxs-lookup"><span data-stu-id="b3f9a-117">The data is then copied from the workbook and stored in the project's workspace database (except for copy/pasted data, which is stored in the Model.bim file).</span></span>  
  
 <span data-ttu-id="b3f9a-118">如果工作区数据库在远程 Analysis Services 实例中，则无法从 PowerPivot for Excel 工作簿导入数据。</span><span class="sxs-lookup"><span data-stu-id="b3f9a-118">If the workspace database is on a remote Analysis Services instance, you cannot import data from a PowerPivot for Excel workbook.</span></span> <span data-ttu-id="b3f9a-119">您仍可以导入工作薄元数据；不过，这将导致脚本在远程 Analysis Services 实例中运行。</span><span class="sxs-lookup"><span data-stu-id="b3f9a-119">You can still import the workbook metadata; however, this will cause a script to be run on the remote Analysis Services instance.</span></span> <span data-ttu-id="b3f9a-120">您应只从受信任的 PowerPivot 工作薄导入元数据。</span><span class="sxs-lookup"><span data-stu-id="b3f9a-120">You should only import metadata from a trusted PowerPivot workbook.</span></span> <span data-ttu-id="b3f9a-121">必须从数据源连接所定义的源中导入数据。</span><span class="sxs-lookup"><span data-stu-id="b3f9a-121">Data must be imported from sources defined in the data source connections.</span></span> <span data-ttu-id="b3f9a-122">必须将 PowerPivot 工作簿中的复制/粘贴的数据和链接表数据复制并粘贴到表格模型项目中。</span><span class="sxs-lookup"><span data-stu-id="b3f9a-122">Copy/pasted and linked table data in the PowerPivot workbook must be copied and pasted into the tabular model project.</span></span>  
  
#### <a name="to-create-a-new-tabular-model-project-from-a-powerpivot-for-excel-file"></a><span data-ttu-id="b3f9a-123">从 PowerPivot for Excel 文件创建新的表格模型项目</span><span class="sxs-lookup"><span data-stu-id="b3f9a-123">To create a new tabular model project from a PowerPivot for Excel file</span></span>  
  
1.  <span data-ttu-id="b3f9a-124">在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中，在 **“文件”** 菜单上，单击 **“新建”**，然后单击 **“项目”**。</span><span class="sxs-lookup"><span data-stu-id="b3f9a-124">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], on the **File** menu, click **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="b3f9a-125">在 "**新建项目**" 对话框中的 "**已安装的模板**" 下，单击 "**商业智能**"，然后单击 "**从 PowerPivot 导入**"。</span><span class="sxs-lookup"><span data-stu-id="b3f9a-125">In the **New Project** dialog box, under **Installed Templates**, click **Business Intelligence**, and then click **Import from PowerPivot**.</span></span>  
  
3.  <span data-ttu-id="b3f9a-126">在 "**名称**" 中，键入项目的名称，然后指定位置和解决方案名称，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="b3f9a-126">In  **Name**, type a name for the project, then specify a location and solution name, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="b3f9a-127">在 **“打开”** 对话框中，选择包含您要导入的模型元数据和数据的 [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] 文件，然后单击 **“打开”**。</span><span class="sxs-lookup"><span data-stu-id="b3f9a-127">In the **Open** dialog box, select the [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] file that contains the model metadata and data you want to import, and then click **Open**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3f9a-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b3f9a-128">See Also</span></span>  
 <span data-ttu-id="b3f9a-129">[工作区数据库 &#40;SSAS 表格&#41;](workspace-database-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="b3f9a-129">[Workspace Database &#40;SSAS Tabular&#41;](workspace-database-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="b3f9a-130">复制并粘贴数据（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="b3f9a-130">Copy and Paste Data &#40;SSAS Tabular&#41;</span></span>](../copy-and-paste-data-ssas-tabular.md)  
  
  
