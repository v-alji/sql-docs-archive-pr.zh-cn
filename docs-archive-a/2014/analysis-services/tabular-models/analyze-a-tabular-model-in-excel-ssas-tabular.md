---
title: 在 Excel 中分析表格模型 (SSAS 表格) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.chooseperspect.f1
ms.assetid: 47fa45fc-60ab-41a1-bde3-5781c8462889
author: minewiskan
ms.author: owend
ms.openlocfilehash: fae542ffb5b470d23d9cf27fcc11367f571e7cec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589226"
---
# <a name="analyze-a-tabular-model-in-excel-ssas-tabular"></a><span data-ttu-id="70a5b-102">在 Excel 中分析表格模型（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="70a5b-102">Analyze a Tabular Model in Excel (SSAS Tabular)</span></span>
  <span data-ttu-id="70a5b-103">使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中的“在 Excel 中分析”功能可以打开 Microsoft Excel、创建到模型工作区数据库的数据源连接以及将数据透视表添加到工作表。</span><span class="sxs-lookup"><span data-stu-id="70a5b-103">The Analyze in Excel feature in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] opens Microsoft Excel, creates a data source connection to the model workspace database, and adds a PivotTable to the worksheet.</span></span> <span data-ttu-id="70a5b-104">模型对象（表、列、度量值、层次结构和 KPI）作为数据透视表字段列表中的字段包含。</span><span class="sxs-lookup"><span data-stu-id="70a5b-104">Model objects (tables, columns, measures, hierarchies, and KPIs) are included as fields in the PivotTable field list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="70a5b-105">为了使用“在 Excel 中分析”功能，您必须在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]所在的计算机上安装 Microsoft Office 2003 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="70a5b-105">To use the Analyze in Excel feature, you must have Microsoft Office 2003 or later installed on the same computer as [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="70a5b-106">如果 Office 安装在不同的计算机上，您可以在另一计算机上使用 Excel 并连接到作为数据源的模型工作区数据库。</span><span class="sxs-lookup"><span data-stu-id="70a5b-106">If Office is not installed on the same computer, you can use Excel on another computer and connect to the model workspace database as a data source.</span></span> <span data-ttu-id="70a5b-107">然后可以将数据透视表手动添加到工作表。</span><span class="sxs-lookup"><span data-stu-id="70a5b-107">You can then manually add a PivotTable to the worksheet.</span></span> <span data-ttu-id="70a5b-108">模型对象（表、列、度量值和 KPI）作为数据透视表字段列表中的字段包含。</span><span class="sxs-lookup"><span data-stu-id="70a5b-108">Model objects (tables, columns, measures, and KPIs) are included as fields in the PivotTable field list.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="70a5b-109">任务</span><span class="sxs-lookup"><span data-stu-id="70a5b-109">Tasks</span></span>  
  
#### <a name="to-analyze-a-tabular-model-project-by-using-the-analyze-in-excel-feature"></a><span data-ttu-id="70a5b-110">使用“在 Excel 中分析”功能分析表格模型项目</span><span class="sxs-lookup"><span data-stu-id="70a5b-110">To analyze a tabular model project by using the Analyze in Excel feature</span></span>  
  
1.  <span data-ttu-id="70a5b-111">在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中，单击 **“模型”** 菜单，然后单击 **“在 Excel 中分析”**。</span><span class="sxs-lookup"><span data-stu-id="70a5b-111">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], click the **Model** menu, and then click **Analyze in Excel**.</span></span>  
  
2.  <span data-ttu-id="70a5b-112">在 **“选择凭据和透视”** 对话框中，选择以下凭据选项之一以连接到模型工作区数据源：</span><span class="sxs-lookup"><span data-stu-id="70a5b-112">In the **Choose Credential and Perspective** dialog box, select one of the following credential options to connect to the model workspace data source:</span></span>  
  
    -   <span data-ttu-id="70a5b-113">若要使用当前用户帐户，请选择 **“当前 Windows 用户”**。</span><span class="sxs-lookup"><span data-stu-id="70a5b-113">To use the current user account, select **Current Windows User**.</span></span>  
  
    -   <span data-ttu-id="70a5b-114">若要使用其他用户帐户，请选择 **“其他 Windows 用户”**。</span><span class="sxs-lookup"><span data-stu-id="70a5b-114">To use a different user account, select **Other Windows User**.</span></span>  
  
         <span data-ttu-id="70a5b-115">通常，此用户帐户将是某个角色的成员。</span><span class="sxs-lookup"><span data-stu-id="70a5b-115">Typically, this user account will be a member of a role.</span></span> <span data-ttu-id="70a5b-116">不需要密码。</span><span class="sxs-lookup"><span data-stu-id="70a5b-116">No password is required.</span></span> <span data-ttu-id="70a5b-117">只能在工作区数据库的 Excel 连接的上下文中使用此帐户。</span><span class="sxs-lookup"><span data-stu-id="70a5b-117">The account can only be used in the context of an Excel connection to the workspace database.</span></span>  
  
    -   <span data-ttu-id="70a5b-118">若要使用安全角色，请选择 **“角色”**，然后在列表框中选择一个或多个角色。</span><span class="sxs-lookup"><span data-stu-id="70a5b-118">To use a security role, select **Role**, and then in the listbox, select one or more roles.</span></span>  
  
         <span data-ttu-id="70a5b-119">必须使用角色管理器定义安全角色。</span><span class="sxs-lookup"><span data-stu-id="70a5b-119">Security roles must be defined using the Role Manager.</span></span> <span data-ttu-id="70a5b-120">有关详细信息，请参阅[创建和管理角色（SSAS 表格）](roles-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="70a5b-120">For more information, see [Create and Manage Roles &#40;SSAS Tabular&#41;](roles-ssas-tabular.md).</span></span>  
  
3.  <span data-ttu-id="70a5b-121">若要使用透视，请在 **“透视”** 列表框中选择一个透视。</span><span class="sxs-lookup"><span data-stu-id="70a5b-121">To use a perspective, in the **Perspective** listbox, select a perspective.</span></span>  
  
     <span data-ttu-id="70a5b-122">必须使用“透视”对话框定义透视（非默认值）。</span><span class="sxs-lookup"><span data-stu-id="70a5b-122">Perspectives (other than default) must be defined using the Perspectives dialog box.</span></span> <span data-ttu-id="70a5b-123">有关详细信息，请参阅[创建和管理 &#40;SSAS 表格&#41;的透视](perspectives-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="70a5b-123">For more information, see [Create and Manage Perspectives &#40;SSAS Tabular&#41;](perspectives-ssas-tabular.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="70a5b-124">当您在模型设计器中更改模型项目时，Excel 中的数据透视表字段列表不会自动刷新。</span><span class="sxs-lookup"><span data-stu-id="70a5b-124">The PivotTable Field List in Excel does not refresh automatically as you make changes to the model project in the model designer.</span></span> <span data-ttu-id="70a5b-125">若要刷新 Excel 中的数据透视表字段列表，请在 **“选项”** 功能区上单击 **“刷新”**。</span><span class="sxs-lookup"><span data-stu-id="70a5b-125">To refresh the PivotTable Field List, in Excel, on the **Options** ribbon, click **Refresh**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70a5b-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="70a5b-126">See Also</span></span>  
 [<span data-ttu-id="70a5b-127">在 Excel 中分析（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="70a5b-127">Analyze in Excel &#40;SSAS Tabular&#41;</span></span>](analyze-in-excel-ssas-tabular.md)  
  
  
