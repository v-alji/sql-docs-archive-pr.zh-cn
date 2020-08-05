---
title: 将维度智能添加到维度 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Business Intelligence enhancements [Analysis Services], dimension intelligence
- dimensions [Analysis Services], Business Intelligence enhancements
- dimension intelligence [Analysis Services]
- Type property
ms.assetid: b64fa386-eac2-4286-a320-0631a1887aac
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5cad591d3e89dc306571efa9aeef9d81a235c9fa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579856"
---
# <a name="add-dimension-intelligence-to-a-dimension"></a><span data-ttu-id="436ca-102">向维度中添加维度智能</span><span class="sxs-lookup"><span data-stu-id="436ca-102">Add Dimension Intelligence to a Dimension</span></span>
  <span data-ttu-id="436ca-103">可以在多维数据集或维度中添加维度智能增强功能，以便为维度指定标准业务类型。</span><span class="sxs-lookup"><span data-stu-id="436ca-103">Add the dimension intelligence enhancement to a cube or a dimension to specify a standard business type for a dimension.</span></span> <span data-ttu-id="436ca-104">此增强功能还将为维度属性指定相应的类型。</span><span class="sxs-lookup"><span data-stu-id="436ca-104">This enhancement also specifies the corresponding types for dimension attributes.</span></span> <span data-ttu-id="436ca-105">客户端应用程序在分析数据时可以使用这些指定的类型。</span><span class="sxs-lookup"><span data-stu-id="436ca-105">Client applications can use these type specifications when analyzing data.</span></span>  
  
 <span data-ttu-id="436ca-106">若要添加维度智能，请使用商业智能向导，并在 **“选择增强功能”** 页中选择 **“定义维度智能”** 选项。</span><span class="sxs-lookup"><span data-stu-id="436ca-106">To add dimension intelligence, you use the Business Intelligence Wizard, and select the **Define dimension intelligence** option on the **Choose Enhancement** page.</span></span> <span data-ttu-id="436ca-107">然后，此向导将引导您完成相应的步骤，以选择要应用维度智能的维度，并标识所选维度的属性。</span><span class="sxs-lookup"><span data-stu-id="436ca-107">This wizard then guides you through the steps of selecting a dimension to which you want to apply dimension intelligence and identifying the attributes for the selected dimension.</span></span>  
  
## <a name="selecting-a-dimension"></a><span data-ttu-id="436ca-108">选择维度</span><span class="sxs-lookup"><span data-stu-id="436ca-108">Selecting a Dimension</span></span>  
 <span data-ttu-id="436ca-109">在向导的第一个 **“设置维度智能选项”** 页中，指定要应用维度智能的维度。</span><span class="sxs-lookup"><span data-stu-id="436ca-109">On the first **Set Dimension Intelligence Options** page of the wizard, you specify the dimension to which you want to apply dimension intelligence.</span></span> <span data-ttu-id="436ca-110">添加到此所选维度中的维度智能增强功能将使维度发生更改。</span><span class="sxs-lookup"><span data-stu-id="436ca-110">The dimension intelligence enhancement added to this selected dimension will result in changes to the dimension.</span></span> <span data-ttu-id="436ca-111">所有包含选定维度的多维数据集都将继承这些更改。</span><span class="sxs-lookup"><span data-stu-id="436ca-111">These changes will be inherited by all cubes that include the selected dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="436ca-112">如果选择 **“帐户”** 作为维度，则要指定维度的帐户智能。</span><span class="sxs-lookup"><span data-stu-id="436ca-112">If you select **Account** as the dimension, you will be specifying account intelligence for the dimension.</span></span> <span data-ttu-id="436ca-113">有关详细信息，请参阅 [向维度中添加帐户智能](bi-wizard-add-account-intelligence-to-a-dimension.md)。</span><span class="sxs-lookup"><span data-stu-id="436ca-113">For more information, see [Add Account Intelligence to a Dimension](bi-wizard-add-account-intelligence-to-a-dimension.md).</span></span>  
  
## <a name="specifying-dimension-attributes"></a><span data-ttu-id="436ca-114">指定维度属性</span><span class="sxs-lookup"><span data-stu-id="436ca-114">Specifying Dimension Attributes</span></span>  
 <span data-ttu-id="436ca-115">在 "**定义维度智能**" 页的 "**维度类型**" 列表中，您所做的选择将设置维度的 `Type` 属性。</span><span class="sxs-lookup"><span data-stu-id="436ca-115">On the **Define Dimension Intelligence** page, in **Dimension Type** list, the selection that you make sets the dimension's `Type` property.</span></span> <span data-ttu-id="436ca-116">`Type` 属性设置可以为服务器和客户端应用程序提供有关维度内容的信息。</span><span class="sxs-lookup"><span data-stu-id="436ca-116">The `Type` property setting provides information to servers and client applications about the contents of a dimension.</span></span> <span data-ttu-id="436ca-117">某些设置只为客户端应用程序提供指导；这些设置是可选的。</span><span class="sxs-lookup"><span data-stu-id="436ca-117">Some settings only provide guidance for client applications; these settings are optional.</span></span> <span data-ttu-id="436ca-118">其他设置（如“帐户”或“时间”）则确定特定的行为，它们在实现特定商业智能增强功能时可能是必需的。</span><span class="sxs-lookup"><span data-stu-id="436ca-118">Other settings, such as Accounts or Time, determine specific behaviors and may be required to implement particular business intelligence enhancements.</span></span> <span data-ttu-id="436ca-119">例如，SQL Server Management Studio 使用维度类型标识“货币”维度，并设置合适的货币换算规则。</span><span class="sxs-lookup"><span data-stu-id="436ca-119">For example, the SQL Server Management Studio uses the dimension type to identify a Currency dimension and set the appropriate currency conversion rules.</span></span> <span data-ttu-id="436ca-120">**“维度类型”** 的默认设置是 **“常规”**，该设置不对维度内容进行任何假设。</span><span class="sxs-lookup"><span data-stu-id="436ca-120">The default setting for the **Dimension Type** is **Regular**, which makes no assumptions about the contents of the dimension.</span></span>  
  
 <span data-ttu-id="436ca-121">选择维度类型后，请在 **“维度属性”** 的 **“包含”** 列中，选中在维度中有其相应属性的每个标准属性类型旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="436ca-121">After selecting the dimension type, in **Dimension attributes**, in the **Include** column, select the check box next to each standard attribute type for which there is a corresponding attribute in the dimension.</span></span> <span data-ttu-id="436ca-122">最后，在“维度属性”\*\*\*\* 列中展开下拉列表，并在维度中选择对应于所选属性类型的属性。</span><span class="sxs-lookup"><span data-stu-id="436ca-122">Finally, in the **Dimension Attribute** column, expand the drop-down list, and select the attribute in the dimension that corresponds to the selected attribute type.</span></span> <span data-ttu-id="436ca-123">如果从该列表选择特性，将会设置特性的 `Type` 属性。</span><span class="sxs-lookup"><span data-stu-id="436ca-123">Selecting the attribute from the list sets the attribute `Type` property for the attributes.</span></span>  
  
 <span data-ttu-id="436ca-124">例如，您希望向“帐户”维度添加维度智能。</span><span class="sxs-lookup"><span data-stu-id="436ca-124">For example, you want to add dimension intelligence to an Accounts dimension.</span></span> <span data-ttu-id="436ca-125">在 **“维度类型”** 中，选择 **“帐户”**。</span><span class="sxs-lookup"><span data-stu-id="436ca-125">In **Dimension Type**, you select **Accounts**.</span></span> <span data-ttu-id="436ca-126">然后，如果维度有 **“帐户类型”** 和 **“帐户说明”** 属性，则在 **“包含”** 列中选中 **“帐户名”** 和 **“帐户类型”** 帐户类型的复选框。</span><span class="sxs-lookup"><span data-stu-id="436ca-126">Then, if the dimension has **Account Type** and **Account Description** attributes, in the **Include** column, you select the check boxes for the **Account Name** and **Account Type** account types.</span></span> <span data-ttu-id="436ca-127">接着，在 **“维度属性”** 列中，将这些帐户类型分别与 **“帐户说明”** 和 **“帐户类型”** 属性关联。</span><span class="sxs-lookup"><span data-stu-id="436ca-127">In the **Dimension Attribute** column, you then associate these account types with the **Account Description** and **Account Type** attributes, respectively, in the dimension.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="436ca-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="436ca-128">See Also</span></span>  
 [<span data-ttu-id="436ca-129">使用商业智能向导定义时间智能计算</span><span class="sxs-lookup"><span data-stu-id="436ca-129">Define Time Intelligence Calculations using the Business Intelligence Wizard</span></span>](define-time-intelligence-calculations-using-the-business-intelligence-wizard.md)  
  
  
