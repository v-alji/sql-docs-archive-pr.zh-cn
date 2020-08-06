---
title: 从 Analysis Services (SSAS 表格) 导入 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b9a21b23-3a06-4ef8-bc06-9c79cdc54870
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7d6c3d226e46cdb4101bc8db52830046d27b0706
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687228"
---
# <a name="import-from-analysis-services-ssas-tabular"></a><span data-ttu-id="70a8c-102">从 Analysis Services 导入（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="70a8c-102">Import from Analysis Services (SSAS Tabular)</span></span>
  <span data-ttu-id="70a8c-103">本主题介绍如何通过使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中的“从服务器导入”项目模板从现有的表格模型导入元数据，创建新的表格模型项目。</span><span class="sxs-lookup"><span data-stu-id="70a8c-103">This topic describes how to create a new tabular model project by importing the metadata from an existing tabular model by using the Import from Server project template in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="create-a-new-model-by-importing-metadata-from-an-existing-model-in-analysis-services"></a><span data-ttu-id="70a8c-104">通过从 Analysis Services 的现有模型中导入元数据来创建新的模型</span><span class="sxs-lookup"><span data-stu-id="70a8c-104">Create a new model by importing metadata from an existing model in Analysis Services</span></span>  
 <span data-ttu-id="70a8c-105">您可以使用“从服务器导入”项目模板从 Analysis Services 服务器上的现有表格模型复制元数据，来创建新的表格模型项目。</span><span class="sxs-lookup"><span data-stu-id="70a8c-105">You can use the Import from Server project template to create a new tabular model project by copying the metadata from an existing tabular model on an Analysis Services server.</span></span> <span data-ttu-id="70a8c-106">创建的新项目将具有与从中导入该项目的模型相同的数据源连接、表、关系、度量值、KPI、角色、层次结构、透视和分区。</span><span class="sxs-lookup"><span data-stu-id="70a8c-106">The new project will be created with the same data source connections, tables, relationships, measures, KPIs, roles, hierarchies, perspectives, and partitions as the model it was imported from.</span></span> <span data-ttu-id="70a8c-107">但是，数据不会从现有模型复制到新的模型工作区。</span><span class="sxs-lookup"><span data-stu-id="70a8c-107">The data, however, is not copied from the existing model to the new model workspace.</span></span> <span data-ttu-id="70a8c-108">完成导入过程且创建新模型项目后，您必须运行“全部处理”将数据从数据源加载到新的模型项目工作区数据库中。</span><span class="sxs-lookup"><span data-stu-id="70a8c-108">Once the import process has completed, and the new model project created, you must run a Process All to load the data from the data sources into the new model project workspace database.</span></span>  
  
#### <a name="to-create-a-new-model-by-importing-metadata-from-an-existing-model"></a><span data-ttu-id="70a8c-109">通过从现有模型中导入元数据来创建新的模型</span><span class="sxs-lookup"><span data-stu-id="70a8c-109">To create a new model by importing metadata from an existing model</span></span>  
  
1.  <span data-ttu-id="70a8c-110">在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中，在 **“文件”** 菜单上，单击 **“新建”**，然后单击 **“项目”**。</span><span class="sxs-lookup"><span data-stu-id="70a8c-110">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], on the **File** menu, click **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="70a8c-111">在 **“新建项目”** 对话框中，在 **“已安装的模板”** 下，单击 **“商业智能”**，然后单击 **“从服务器导入”**。</span><span class="sxs-lookup"><span data-stu-id="70a8c-111">In the **New Project** dialog box, under **Installed Templates**, click **Business Intelligence**, and then click **Import from Server**.</span></span>  
  
3.  <span data-ttu-id="70a8c-112">在 **“名称”** 中，键入项目的名称，然后指定位置和解决方案名称，再单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="70a8c-112">In **Name**, type a name for the project, then specify a location and solution name, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="70a8c-113">在 **“从 Analysis Services 导入”** 对话框的 **“服务器名称”** 中，指定包含您要导入的模型元数据的 Analysis Services 服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="70a8c-113">In the **Import from Analysis Services** dialog box, in **Server Name**, specify the name of the Analysis Services server that contains the model metadata you want to import.</span></span>  
  
5.  <span data-ttu-id="70a8c-114">在 **“数据库名称”** 中，选择包含您要导入的模型元数据的表格模型数据库，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="70a8c-114">In **Database Name**, select the tabular model database that contains the model metadata you want to import, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70a8c-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="70a8c-115">See Also</span></span>  
 [<span data-ttu-id="70a8c-116">项目属性（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="70a8c-116">Project Properties &#40;SSAS Tabular&#41;</span></span>](properties-ssas-tabular.md)  
  
  
