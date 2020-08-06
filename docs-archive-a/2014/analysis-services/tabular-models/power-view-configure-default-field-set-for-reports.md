---
title: " (SSAS 表格) 配置 Power View 报表的默认字段集 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- ql12.asvs.bidtoolset.deffieldset.f1
ms.assetid: 6836b42f-28b8-4a98-a86d-2c3c109f0189
author: minewiskan
ms.author: owend
ms.openlocfilehash: c66fbbacd0cc2efd7d379bcc8e68149551476869
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87683106"
---
# <a name="configure-default-field-set-for-power-view-reports-ssas-tabular"></a><span data-ttu-id="cb21e-102">配置 Power View 报表的默认字段集（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="cb21e-102">Configure Default Field Set for Power View Reports (SSAS Tabular)</span></span>
  <span data-ttu-id="cb21e-103">默认字段集是一个列和度量值的预定义列表，当您选择报表字段列表中的表时，这些列和度量值会自动添加到 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] 报表画布中。</span><span class="sxs-lookup"><span data-stu-id="cb21e-103">A default field set is a predefined list of columns and measures that are automatically added to a [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] report canvas when the table is selected in the report field list.</span></span> <span data-ttu-id="cb21e-104">表格模型作者可以创建默认字段集，使得将模型用于其报表的报表作者无需执行冗余步骤。</span><span class="sxs-lookup"><span data-stu-id="cb21e-104">Tabular model authors can create a default field set to eliminate redundant steps for report authors who use the model for their reports.</span></span> <span data-ttu-id="cb21e-105">例如，如果您知道大多数使用客户联系信息的报表作者总是希望查看联系人姓名、主要电话号码、电子邮件地址和公司名称，您可以预先选择这些列，以便在作者单击客户联系表时，这些列总是会添加到报表画布中。</span><span class="sxs-lookup"><span data-stu-id="cb21e-105">For example, if you know that most report authors who work with customer contact information always want to see a contact name, a primary phone number, an email address, and a company name, you can pre-select those columns so that they are always added to the report canvas when the author clicks the Customer Contact table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cb21e-106">默认字段集仅应用于 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]中用作数据模型的表格模型。</span><span class="sxs-lookup"><span data-stu-id="cb21e-106">A default field set applies only to a tabular model used as a data model in [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)].</span></span> <span data-ttu-id="cb21e-107">Excel 透视报表不支持默认字段集。</span><span class="sxs-lookup"><span data-stu-id="cb21e-107">Default field sets are not supported in Excel pivot reports.</span></span>  
  
## <a name="creating-a-default-field-set"></a><span data-ttu-id="cb21e-108">创建默认字段集</span><span class="sxs-lookup"><span data-stu-id="cb21e-108">Creating a Default Field Set</span></span>  
 <span data-ttu-id="cb21e-109">您可以确定当在 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]中选择某个特定表时，默认情况下包含的字段（如果有）。</span><span class="sxs-lookup"><span data-stu-id="cb21e-109">You can determine which fields, if any, are included by default whenever a specific table is selected in [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)].</span></span> <span data-ttu-id="cb21e-110">还可以确定这些字段在列表中的显示顺序。</span><span class="sxs-lookup"><span data-stu-id="cb21e-110">You can also determine the order in which fields appear in the list.</span></span> <span data-ttu-id="cb21e-111">若要指定默认字段集，您可以在表格模型项目中设置报表属性。</span><span class="sxs-lookup"><span data-stu-id="cb21e-111">To specify a default field set, you set report properties in the tabular model project.</span></span>  
  
#### <a name="to-add-a-default-field-set"></a><span data-ttu-id="cb21e-112">添加默认字段集</span><span class="sxs-lookup"><span data-stu-id="cb21e-112">To add a default field set</span></span>  
  
1.  <span data-ttu-id="cb21e-113">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，单击要为其配置默认字段列表的表。</span><span class="sxs-lookup"><span data-stu-id="cb21e-113">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click the table (tab) for which you are configuring a default field list.</span></span>  
  
2.  <span data-ttu-id="cb21e-114">在 **“属性”** 窗口的 **“默认字段集”** 属性中，单击 **“单击可编辑”**。</span><span class="sxs-lookup"><span data-stu-id="cb21e-114">In the **Properties** window, in the **Default Field Set** property, click **Click to edit**.</span></span>  
  
3.  <span data-ttu-id="cb21e-115">在“默认字段集”对话框中，选择一个或多个字段。</span><span class="sxs-lookup"><span data-stu-id="cb21e-115">In the Default Field Set dialog, select one or more fields.</span></span> <span data-ttu-id="cb21e-116">可以选择表中的任何字段，包括度量值。</span><span class="sxs-lookup"><span data-stu-id="cb21e-116">You can choose any field in the table, including measures.</span></span> <span data-ttu-id="cb21e-117">按住 Shift 键以选择范围，或按住 Ctrl 键以选择单个字段。</span><span class="sxs-lookup"><span data-stu-id="cb21e-117">Hold down the Shift key to select a range, or the Ctrl key to select individual fields.</span></span>  
  
4.  <span data-ttu-id="cb21e-118">单击 **“添加”** 以将其添加到默认字段集。</span><span class="sxs-lookup"><span data-stu-id="cb21e-118">Click **Add** to add them to the default field set.</span></span>  
  
5.  <span data-ttu-id="cb21e-119">使用“上移”和“下移”按钮指定字段列表的顺序。</span><span class="sxs-lookup"><span data-stu-id="cb21e-119">Use the Up and Down buttons to specify an order to the field list.</span></span> <span data-ttu-id="cb21e-120">按照为字段集定义的顺序将字段添加到报表中。</span><span class="sxs-lookup"><span data-stu-id="cb21e-120">Fields will be added to the report in the order defined for the field set.</span></span>  
  
6.  <span data-ttu-id="cb21e-121">对工作簿中的其他表重复这些步骤。</span><span class="sxs-lookup"><span data-stu-id="cb21e-121">Repeat these steps for other tables in your workbook.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="cb21e-122">下一步</span><span class="sxs-lookup"><span data-stu-id="cb21e-122">Next Step</span></span>  
 <span data-ttu-id="cb21e-123">创建默认字段集后，您可以通过指定默认标签、默认图像、默认组行为或是将包含相同值的各个行组合到一个行中还是分别列出这些行，来进一步影响报表设计体验。</span><span class="sxs-lookup"><span data-stu-id="cb21e-123">After you create a default field set, you can further influence the report design experience by specifying default labels, default images, default group behavior, or whether rows that contain the same value are grouped together in one row or listed individually.</span></span> <span data-ttu-id="cb21e-124">有关详细信息，请参阅[为 Power View 报表配置表行为属性（SSAS 表格）](power-view-configure-table-behavior-properties-for-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="cb21e-124">For more information, see [Configure Table Behavior Properties for Power View Reports &#40;SSAS Tabular&#41;](power-view-configure-table-behavior-properties-for-reports.md).</span></span>  
  
  
