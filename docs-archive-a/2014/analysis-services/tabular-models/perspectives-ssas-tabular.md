---
title: SSAS 表格)  (透视 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 1f78c3a1-ce2c-4e7f-a277-71a657692bea
author: minewiskan
ms.author: owend
ms.openlocfilehash: e11f8be980b99c4e9bd824f281db31e9c3f7d9bf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87683107"
---
# <a name="perspectives-ssas-tabular"></a><span data-ttu-id="29aa3-102">透视（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="29aa3-102">Perspectives (SSAS Tabular)</span></span>
  <span data-ttu-id="29aa3-103">在表格模型中，透视定义模型的可查看子集，借此您可以将注意力集中在该模型中的特定业务或特定应用上。</span><span class="sxs-lookup"><span data-stu-id="29aa3-103">Perspectives, in tabular models, define viewable subsets of a model that provide focused, business-specific, or application-specific viewpoints of the model.</span></span>  
  
 <span data-ttu-id="29aa3-104">本主题的内容：</span><span class="sxs-lookup"><span data-stu-id="29aa3-104">Sections in this topic:</span></span>  
  
-   [<span data-ttu-id="29aa3-105">优点</span><span class="sxs-lookup"><span data-stu-id="29aa3-105">Benefits</span></span>](#bkmk_understanding)  
  
-   [<span data-ttu-id="29aa3-106">测试透视</span><span class="sxs-lookup"><span data-stu-id="29aa3-106">Testing Perspectives</span></span>](#bkmk_testpersp)  
  
-   [<span data-ttu-id="29aa3-107">相关任务</span><span class="sxs-lookup"><span data-stu-id="29aa3-107">Related Tasks</span></span>](#bkmk_related_tasks)  
  
##  <a name="benefits"></a><a name="bkmk_understanding"></a> <span data-ttu-id="29aa3-108">优势</span><span class="sxs-lookup"><span data-stu-id="29aa3-108">Benefits</span></span>  
 <span data-ttu-id="29aa3-109">表格模型可为非常复杂的对象，以使用户进行浏览。</span><span class="sxs-lookup"><span data-stu-id="29aa3-109">Tabular models can be very complex for users to explore.</span></span> <span data-ttu-id="29aa3-110">单个模型可以表示完整的数据仓库内容，可具有多个表、度量值和维度。</span><span class="sxs-lookup"><span data-stu-id="29aa3-110">A single model can represent the contents of a complete data warehouse with many tables, measures, and dimensions.</span></span> <span data-ttu-id="29aa3-111">用户可能只需要与模型的一小部分进行交互即可满足其商业智能和报表要求，因此，这样的复杂性会令用户感到过于复杂。</span><span class="sxs-lookup"><span data-stu-id="29aa3-111">Such complexity can be daunting to users who may only need to interact with a small part of the model in order to satisfy their business intelligence and reporting requirements.</span></span>  
  
 <span data-ttu-id="29aa3-112">在透视中，表、列和度量值（包括 KPI）定义为字段对象。</span><span class="sxs-lookup"><span data-stu-id="29aa3-112">In a perspective, tables, columns, and measures (including KPIs) are defined as field objects.</span></span> <span data-ttu-id="29aa3-113">可为每个透视选择可查看字段。</span><span class="sxs-lookup"><span data-stu-id="29aa3-113">You can select the viewable fields for each perspective.</span></span> <span data-ttu-id="29aa3-114">例如，单个模型可以包含产品、销售、财务、员工和地理数据。</span><span class="sxs-lookup"><span data-stu-id="29aa3-114">For example, a single model may contain product, sales, financial, employee, and geographic data.</span></span> <span data-ttu-id="29aa3-115">在销售部要求产品、销售、促销和地理数据时，他们可能不需要员工和财务数据。</span><span class="sxs-lookup"><span data-stu-id="29aa3-115">While a sales department requires product, sales, promotions, and geography data, they likely do not require employee and financial data.</span></span> <span data-ttu-id="29aa3-116">同样，人力资源部门不需要与销售促销和地理有关的数据。</span><span class="sxs-lookup"><span data-stu-id="29aa3-116">Similarly, a human resources department does not require data about sales promotions and geography.</span></span>  
  
 <span data-ttu-id="29aa3-117">在用户使用定义的透视连接到模型（作为数据源）时，该用户可以选择要使用的透视。</span><span class="sxs-lookup"><span data-stu-id="29aa3-117">When a user connects to a model (as a data source) with defined perspectives, the user can select the perspective they want to use.</span></span> <span data-ttu-id="29aa3-118">例如，当在 Excel 中连接到某一模型数据时，人力资源部门的用户可以在数据连接向导的“选择表和视图”页上选择人力资源透视。</span><span class="sxs-lookup"><span data-stu-id="29aa3-118">For example, when connecting to a model data source in Excel, users in Human Resources can select the Human Resources perspective on the Select Tables and Views page of the Data Connection Wizard.</span></span> <span data-ttu-id="29aa3-119">只有为人力资源透视定义的字段（表、列和度量值）将在数据透视表字段列表中可见。</span><span class="sxs-lookup"><span data-stu-id="29aa3-119">Only fields (tables, columns, and measures) defined for the Human Resources perspective will be visible in the PivotTable Field List.</span></span>  
  
 <span data-ttu-id="29aa3-120">透视的用途不是为了作为一种安全机制，而是作为一个可为用户提供更好体验的工具。</span><span class="sxs-lookup"><span data-stu-id="29aa3-120">Perspectives are not meant to be used as a security mechanism, but as a tool for providing a better user experience.</span></span> <span data-ttu-id="29aa3-121">特定透视的所有安全性都从基础模型继承。</span><span class="sxs-lookup"><span data-stu-id="29aa3-121">All security for a particular perspective is inherited from the underlying model.</span></span> <span data-ttu-id="29aa3-122">透视无法让用户访问该用户尚未拥有访问权的模型对象。</span><span class="sxs-lookup"><span data-stu-id="29aa3-122">Perspectives cannot provide access to model objects to which a user does not already have access.</span></span> <span data-ttu-id="29aa3-123">必须先解决模型数据库的安全性，然后才能通过透视访问模型中的对象。</span><span class="sxs-lookup"><span data-stu-id="29aa3-123">Security for the model database must be resolved before access to objects in the model can be provided through a perspective.</span></span> <span data-ttu-id="29aa3-124">安全角色可用于保护模型元数据和数据。</span><span class="sxs-lookup"><span data-stu-id="29aa3-124">Security roles can be used to secure model metadata and data.</span></span> <span data-ttu-id="29aa3-125">有关详细信息，请参阅 [角色（SSAS 表格）](roles-ssas-tabular.md)中创建的表格模型项目。</span><span class="sxs-lookup"><span data-stu-id="29aa3-125">For more information, see [Roles &#40;SSAS Tabular&#41;](roles-ssas-tabular.md).</span></span>  
  
##  <a name="testing-perspectives"></a><a name="bkmk_testpersp"></a><span data-ttu-id="29aa3-126">测试透视</span><span class="sxs-lookup"><span data-stu-id="29aa3-126">Testing Perspectives</span></span>  
 <span data-ttu-id="29aa3-127">在创作模型时，可以使用模型设计器中的“在 Excel 中分析”功能来测试已定义的透视的效用。</span><span class="sxs-lookup"><span data-stu-id="29aa3-127">When authoring a model, you can use the Analyze in Excel feature in the model designer to test the efficacy of the perspectives you have defined.</span></span> <span data-ttu-id="29aa3-128">从模型设计器中的 **“模型”** 菜单中，当您单击 **“在 Excel 中分析”** 时，在打开 Excel 之前，将会出现 **“选择凭据和透视”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="29aa3-128">From the **Model** menu in the model designer, when you click **Analyze in Excel**, before Excel opens, the **Choose Credentials and Perspective** dialog box appears.</span></span> <span data-ttu-id="29aa3-129">在此对话框中，您可以指定当前用户名、其他用户、角色和一个用于连接作为数据源的模型工作区数据库的透视以及视图数据。</span><span class="sxs-lookup"><span data-stu-id="29aa3-129">In this dialog, you can specify the current username, a different user, a role, and a perspective with which you will use to connect to the model workspace database as a data source and view data.</span></span>  
  
##  <a name="related-tasks"></a><a name="bkmk_related_tasks"></a> <span data-ttu-id="29aa3-130">相关任务</span><span class="sxs-lookup"><span data-stu-id="29aa3-130">Related Tasks</span></span>  
  
|<span data-ttu-id="29aa3-131">主题</span><span class="sxs-lookup"><span data-stu-id="29aa3-131">Topic</span></span>|<span data-ttu-id="29aa3-132">说明</span><span class="sxs-lookup"><span data-stu-id="29aa3-132">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="29aa3-133">创建和管理透视表（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="29aa3-133">Create and Manage Perspectives &#40;SSAS Tabular&#41;</span></span>](perspectives-ssas-tabular.md)|<span data-ttu-id="29aa3-134">描述如何使用模型设计器中的“透视”对话框创建和管理透视。</span><span class="sxs-lookup"><span data-stu-id="29aa3-134">Describes how to create and manage perspectives using the Perspectives dialog box in the model designer.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="29aa3-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="29aa3-135">See Also</span></span>  
 <span data-ttu-id="29aa3-136">[&#40;SSAS 表格&#41;的角色](roles-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="29aa3-136">[Roles &#40;SSAS Tabular&#41;](roles-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="29aa3-137">层次结构（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="29aa3-137">Hierarchies &#40;SSAS Tabular&#41;</span></span>](hierarchies-ssas-tabular.md)  
  
  
