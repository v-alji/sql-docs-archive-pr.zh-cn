---
title: 使用维度向导创建维度 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], creating
ms.assetid: d84f66ae-7551-49bf-99d0-88368ca2dd0e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9ec38dc7170b915dce0cedea60c93385560e11f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691964"
---
# <a name="create-a-dimension-using-the-dimension-wizard"></a><span data-ttu-id="60ad1-102">使用维度向导创建维度</span><span class="sxs-lookup"><span data-stu-id="60ad1-102">Create a Dimension Using the Dimension Wizard</span></span>
  <span data-ttu-id="60ad1-103">可以使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中的维度向导创建新维度。</span><span class="sxs-lookup"><span data-stu-id="60ad1-103">You can create a new dimension by using the Dimension Wizard in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
### <a name="to-create-a-new-dimension"></a><span data-ttu-id="60ad1-104">创建新维度</span><span class="sxs-lookup"><span data-stu-id="60ad1-104">To create a new dimension</span></span>  
  
1.  <span data-ttu-id="60ad1-105">在**解决方案资源管理器**中，右键单击 "**维度**"，然后单击 "**新建维度**"。</span><span class="sxs-lookup"><span data-stu-id="60ad1-105">In **Solution Explorer**, right-click **Dimensions**, and then click **New Dimension**.</span></span>  
  
2.  <span data-ttu-id="60ad1-106">在维度向导的 **“选择创建方法”** 页上，选择 **“使用现有表”**，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="60ad1-106">On the **Select Creation Method** page of the Dimension Wizard, select **Use an existing table**, and then click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="60ad1-107">有时可能必须在不使用现有表的情况下创建维度。</span><span class="sxs-lookup"><span data-stu-id="60ad1-107">You might occasionally have to create a dimension without using an existing table.</span></span> <span data-ttu-id="60ad1-108">有关详细信息，请参阅 [通过在数据源中生成非时间表来创建维度](create-a-dimension-by-generating-a-non-time-table-in-the-data-source.md) 和 [通过生成时间表来创建时间维度](create-a-time-dimension-by-generating-a-time-table.md)。</span><span class="sxs-lookup"><span data-stu-id="60ad1-108">For more information, see [Create a Dimension by Generating a Non-Time Table in the Data Source](create-a-dimension-by-generating-a-non-time-table-in-the-data-source.md) and [Create a Time Dimension by Generating a Time Table](create-a-time-dimension-by-generating-a-time-table.md).</span></span>  
  
3.  <span data-ttu-id="60ad1-109">在 **“指定源信息”** 页上，执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="60ad1-109">On the **Specify Source Information** page, do the following procedures:</span></span>  
  
    1.  <span data-ttu-id="60ad1-110">在 **“数据源视图”** 列表中，选择数据源视图。</span><span class="sxs-lookup"><span data-stu-id="60ad1-110">In the **Data source view** list, select a data source view.</span></span>  
  
    2.  <span data-ttu-id="60ad1-111">在 **“主表”** 列表中，选择主维度表。</span><span class="sxs-lookup"><span data-stu-id="60ad1-111">In the **Main table** list, select the main dimension table.</span></span>  
  
    3.  <span data-ttu-id="60ad1-112">在 **“键列”** 列表中，查看向导基于主维度表中定义的主键而自动选择的键列。</span><span class="sxs-lookup"><span data-stu-id="60ad1-112">In the **Key columns** list, review the key columns that the wizard has automatically selected based on the primary key that is defined in the main dimension table.</span></span> <span data-ttu-id="60ad1-113">若要更改此默认设置，请指定将维度表链接到事实数据表的键列。</span><span class="sxs-lookup"><span data-stu-id="60ad1-113">To change this default setting, specify the key columns that link the dimension table to the fact table.</span></span>  
  
    4.  <span data-ttu-id="60ad1-114">在“名称列”下拉列表中，查看向导已自动选择的名称列。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="60ad1-114">In the **Name column** drop-down list, review the name column that the wizard has automatically selected.</span></span>  
  
         <span data-ttu-id="60ad1-115">当列包含说明性信息时，可以使用此默认名称。</span><span class="sxs-lookup"><span data-stu-id="60ad1-115">This default name is appropriate when the column contains descriptive information.</span></span> <span data-ttu-id="60ad1-116">但是，您可能希望指定包含对最终用户更有意义的值的名称。</span><span class="sxs-lookup"><span data-stu-id="60ad1-116">However, you might want to specify a name that contains values that are more meaningful for the end user.</span></span> <span data-ttu-id="60ad1-117">例如，如果“产品”维度中的产品类别属性使用 **ProductCategoryKey** 列作为键列，则可以指定 **ProductCategoryName** 列作为名称列。</span><span class="sxs-lookup"><span data-stu-id="60ad1-117">For example, if a product category attribute in a Products dimension uses the **ProductCategoryKey** column as its key column, you can specify the **ProductCategoryName** column as its name column.</span></span>  
  
         <span data-ttu-id="60ad1-118">如果 **“键列”** 列表包含多个键列，则必须指定为键属性提供成员值的名称列。</span><span class="sxs-lookup"><span data-stu-id="60ad1-118">If the **Key columns** list contains multiple key columns, you must specify a name column that provides the member values for the key attribute.</span></span> <span data-ttu-id="60ad1-119">为此，可在数据源视图中创建命名计算，然后使用该命名计算作为名称列。</span><span class="sxs-lookup"><span data-stu-id="60ad1-119">To do this, you can create a named calculation in the data source view and use that as the name column.</span></span>  
  
    5.  <span data-ttu-id="60ad1-120">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="60ad1-120">Click **Next**.</span></span>  
  
4.  <span data-ttu-id="60ad1-121">在 **“选择相关表”** 页上，选择要在维度中包含的相关表，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="60ad1-121">On the **Select Related Tables** page, select the related tables that you want to include in your dimension, and then click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="60ad1-122"> 如果指定的主维度表与其他维度表有关系，则将显示 **“选择相关表”** 页。</span><span class="sxs-lookup"><span data-stu-id="60ad1-122">The **Select Related Tables** page appears if the main dimension table that you specified has relationships to other dimension tables.</span></span>  
  
5.  <span data-ttu-id="60ad1-123">在 **“选择维度属性”** 页上，选择要在维度中包含的属性，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="60ad1-123">On the **Select Dimension Attributes** page, select the attributes that you want to include in the dimension, and then click **Next**.</span></span>  
  
     <span data-ttu-id="60ad1-124">还可以更改属性名称，启用或禁用浏览以及指定属性类型。</span><span class="sxs-lookup"><span data-stu-id="60ad1-124">Optionally, you can change the attribute names, enable or disable browsing, and specify the attribute type.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="60ad1-125"> 若要激活 **“启用浏览”** 和 **“属性类型”** 字段，必须选择要在维度中包含的属性。</span><span class="sxs-lookup"><span data-stu-id="60ad1-125">To make the **Enable Browsing** and **Attribute Type** fields of an attribute active, the attribute must be selected for inclusion in the dimension.</span></span>  
  
6.  <span data-ttu-id="60ad1-126">在“定义帐户智能”页的“内置帐户类型”列中，选择帐户类型，然后单击“下一步”。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="60ad1-126">On the **Define Account Intelligence** page, in the **Built-In Account Types** column, select the account type, and then click **Next**.</span></span>  
  
     <span data-ttu-id="60ad1-127">该帐户类型必须对应于 **“源表帐户类型”** 列中列出的源表帐户类型。</span><span class="sxs-lookup"><span data-stu-id="60ad1-127">The account type must correspond to the account type of the source table that is listed in the **Source Table Account Types** column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="60ad1-128"> 如果在向导的 **“选择维度属性”** 页中定义了 **“帐户类型”** 维度属性，则将显示 **“定义帐户智能”** 页。</span><span class="sxs-lookup"><span data-stu-id="60ad1-128">The **Define Account Intelligence** page appears if you defined an **Account Type** dimension attribute on the **Select Dimension Attributes** page of the wizard.</span></span>  
  
7.  <span data-ttu-id="60ad1-129">在 **“完成向导”** 页中，输入新维度的名称，并查看维度结构。</span><span class="sxs-lookup"><span data-stu-id="60ad1-129">On the **Completing the Wizard** page, enter a name for the new dimension and review the dimension structure.</span></span> <span data-ttu-id="60ad1-130">若要进行更改，请单击 **“上一步”**；否则，单击 **“完成”**。</span><span class="sxs-lookup"><span data-stu-id="60ad1-130">If you want to make changes, click **Back**; otherwise, click **Finish**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="60ad1-131">完成维度向导后，可以使用维度设计器来添加、删除和配置维度中的属性和层次结构。</span><span class="sxs-lookup"><span data-stu-id="60ad1-131">You can use Dimension Designer after you complete the Dimension Wizard to add, remove, and configure attributes and hierarchies in the dimension.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60ad1-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="60ad1-132">See Also</span></span>  
 [<span data-ttu-id="60ad1-133">使用现有表创建维度</span><span class="sxs-lookup"><span data-stu-id="60ad1-133">Create a Dimension by Using an Existing Table</span></span>](create-a-dimension-by-using-an-existing-table.md)  
  
  
