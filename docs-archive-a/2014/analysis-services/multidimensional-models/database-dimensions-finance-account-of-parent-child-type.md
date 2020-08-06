---
title: 创建父子类型维度的财务帐户 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], account
- account dimensions [Analysis Services]
- adding account intelligence
- account intelligence [Analysis Services]
ms.assetid: 2ba74e81-5b4b-407e-acdf-deb2f6accf0a
author: minewiskan
ms.author: owend
ms.openlocfilehash: ba10e642425628426d9183be2b8d2c4ff751c3ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689074"
---
# <a name="create-a-finance-account-of-parent-child-type-dimension"></a><span data-ttu-id="b9f93-102">创建父子类型的财务帐户维度</span><span class="sxs-lookup"><span data-stu-id="b9f93-102">Create a Finance Account of parent-child type Dimension</span></span>
  <span data-ttu-id="b9f93-103">在中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，"帐户类型" 维度是指其属性表示用于财务报表用途的会计科目表的维度。</span><span class="sxs-lookup"><span data-stu-id="b9f93-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], an account type dimension is a dimension whose attributes represent a chart of accounts for financial reporting purposes.</span></span>  
  
 <span data-ttu-id="b9f93-104">使用帐户维度，您可以有选择地管理一段时间内帐户间的聚合行为。</span><span class="sxs-lookup"><span data-stu-id="b9f93-104">An account dimension lets you selectively manage aggregation behavior across accounts over time.</span></span> <span data-ttu-id="b9f93-105">帐户维度还允许您使用标准机制来解决通常在处理财务数据的商业智能解决方案中遇到的大多非标准聚合问题。</span><span class="sxs-lookup"><span data-stu-id="b9f93-105">An account dimension also lets use a standard mechanism to resolve most of the nonstandard aggregation issues typically encountered in business intelligence solutions that handle financial data.</span></span> <span data-ttu-id="b9f93-106">如果不具有此标准机制，那么，解决这些非标准聚合问题就需要自定义汇总公式、计算成员或多维表达式 (MDX) 脚本。</span><span class="sxs-lookup"><span data-stu-id="b9f93-106">If you did not have such a standard mechanism, resolving these nonstandard aggregation issues would require custom rollup formulas, calculated members, or Multidimensional Expressions (MDX) scripts.</span></span>  
  
 <span data-ttu-id="b9f93-107">若要将维度标识为帐户维度，请将维度的 `Type` 属性设置为 `Accounts`。</span><span class="sxs-lookup"><span data-stu-id="b9f93-107">To identify a dimension as an account dimension, set the `Type` property of the dimension to `Accounts`.</span></span>  
  
## <a name="dimension-structure"></a><span data-ttu-id="b9f93-108">维度结构</span><span class="sxs-lookup"><span data-stu-id="b9f93-108">Dimension Structure</span></span>  
 <span data-ttu-id="b9f93-109">帐户维度至少包含两种属性：</span><span class="sxs-lookup"><span data-stu-id="b9f93-109">An account dimension contains, at least, two attributes:</span></span>  
  
-   <span data-ttu-id="b9f93-110">键属性-标识帐户维度的维度表中各个帐户的属性。</span><span class="sxs-lookup"><span data-stu-id="b9f93-110">A key attribute-an attribute that identifies individual accounts in the dimension table for the account dimension.</span></span>  
  
-   <span data-ttu-id="b9f93-111">帐户属性-说明如何在帐户维度中按层次结构排列帐户的父属性。</span><span class="sxs-lookup"><span data-stu-id="b9f93-111">An account attribute-a parent attribute that describes how accounts are hierarchically arranged in the account dimension.</span></span>  
  
     <span data-ttu-id="b9f93-112">若要将特性标识为帐户特性，请将该特性的 `Type` 属性设置为 `Account`，将 `Usage` 属性设置为 `Parent`。</span><span class="sxs-lookup"><span data-stu-id="b9f93-112">To identify an attribute as an account attribute, set the `Type` property of the attribute to `Account` and the `Usage` property to `Parent`.</span></span>  
  
 <span data-ttu-id="b9f93-113">帐户维度也可以包含以下属性：</span><span class="sxs-lookup"><span data-stu-id="b9f93-113">Account dimensions can optionally contain the following attributes:</span></span>  
  
-   <span data-ttu-id="b9f93-114">帐户类型属性-为维度中的每个帐户定义帐户类型的属性。</span><span class="sxs-lookup"><span data-stu-id="b9f93-114">An account type attribute-an attribute that defines the account type for each account in the dimension.</span></span> <span data-ttu-id="b9f93-115">帐户类型属性的成员名称映射到为 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库或项目定义的帐户类型，并指示 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 针对那些帐户使用的聚合函数。</span><span class="sxs-lookup"><span data-stu-id="b9f93-115">The member names of the account type attribute map to the account types defined for the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database or project, and indicate the aggregation function used by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] for those accounts.</span></span> <span data-ttu-id="b9f93-116">您也可以使用一元运算符或自定义汇总公式来决定帐户属性的聚合行为，但通过帐户类型可以轻松地将一致的行为应用于帐户图表，而无需对基础关系数据库进行更改。</span><span class="sxs-lookup"><span data-stu-id="b9f93-116">You can also use unary operators or custom rollup formulas to determine aggregation behavior for account attributes, but account types let you to easily apply consistent behavior to a chart of accounts without requiring changes to the underlying relational database.</span></span>  
  
     <span data-ttu-id="b9f93-117">若要标识帐户类型特性，请将该特性的 `Type` 属性设置为 `AccountType`。</span><span class="sxs-lookup"><span data-stu-id="b9f93-117">To identify an account type attribute, set the `Type` property of the attribute to `AccountType`.</span></span>  
  
-   <span data-ttu-id="b9f93-118">帐户名称属性-用于报表用途的属性。</span><span class="sxs-lookup"><span data-stu-id="b9f93-118">An account name attribute-an attribute that is used for reporting purposes.</span></span> <span data-ttu-id="b9f93-119">您可以通过将特性的 `Type` 属性设置为 `AccountName` 以标识帐户名称特性。</span><span class="sxs-lookup"><span data-stu-id="b9f93-119">You identify an account name attribute by setting the `Type` property of the attribute to `AccountName`.</span></span>  
  
-   <span data-ttu-id="b9f93-120">帐号属性-用于报表用途的属性。</span><span class="sxs-lookup"><span data-stu-id="b9f93-120">An account number attribute-an attribute that is used for reporting purposes.</span></span> <span data-ttu-id="b9f93-121">您可以通过将特性的 `Type` 属性设置为 `AccountNumber` 来标识帐号特性。</span><span class="sxs-lookup"><span data-stu-id="b9f93-121">You identify an account number attribute by setting the `Type` property of the attribute to `AccountNumber`.</span></span>  
  
 <span data-ttu-id="b9f93-122">有关属性类型的详细信息，请参阅 [配置属性类型](attribute-properties-configure-attribute-types.md)。</span><span class="sxs-lookup"><span data-stu-id="b9f93-122">For more information about attribute types, see [Configure Attribute Types](attribute-properties-configure-attribute-types.md).</span></span>  
  
## <a name="adding-account-intelligence-with-the-business-intelligence-wizard"></a><span data-ttu-id="b9f93-123">通过商业智能向导添加帐户智能</span><span class="sxs-lookup"><span data-stu-id="b9f93-123">Adding Account Intelligence with the Business Intelligence Wizard</span></span>  
 <span data-ttu-id="b9f93-124">定义帐户维度并将该维度添加到多维数据集后，可以使用商业智能向导添加帐户智能功能，例如，标识帐户类型，将帐户类型映射到维度。</span><span class="sxs-lookup"><span data-stu-id="b9f93-124">After you have defined an account dimension and added that dimension to a cube, you can use the Business Intelligence Wizard to adding account intelligence functionality, such as identifying and mapping account types, to the dimension.</span></span> <span data-ttu-id="b9f93-125">有关详细信息，请参阅 [向维度中添加帐户智能](bi-wizard-add-account-intelligence-to-a-dimension.md)。</span><span class="sxs-lookup"><span data-stu-id="b9f93-125">For more information, see [Add Account Intelligence to a Dimension](bi-wizard-add-account-intelligence-to-a-dimension.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9f93-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b9f93-126">See Also</span></span>  
 <span data-ttu-id="b9f93-127">[属性和属性层次结构](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md) </span><span class="sxs-lookup"><span data-stu-id="b9f93-127">[Attributes and Attribute Hierarchies](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md) </span></span>  
 <span data-ttu-id="b9f93-128">[商业智能向导的 F1 帮助](../business-intelligence-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="b9f93-128">[Business Intelligence Wizard F1 Help](../business-intelligence-wizard-f1-help.md) </span></span>  
 [<span data-ttu-id="b9f93-129">维度类型</span><span class="sxs-lookup"><span data-stu-id="b9f93-129">Dimension Types</span></span>](../multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md)  
  
  
