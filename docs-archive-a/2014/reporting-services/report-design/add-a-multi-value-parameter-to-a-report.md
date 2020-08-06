---
title: 将多值参数添加到报表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 12ad0e77-4c28-4bbb-ab11-473ae89ec9f1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5269293b6a21f3b1d82eb6835efbd275e3be9620
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687480"
---
# <a name="add-a-multi-value-parameter-to-a-report"></a><span data-ttu-id="a93cf-102">将多值参数添加到报表</span><span class="sxs-lookup"><span data-stu-id="a93cf-102">Add a multi-value parameter to a Report</span></span>
  <span data-ttu-id="a93cf-103">可以将参数添加到报表，以允许用户为参数选择多个值。</span><span class="sxs-lookup"><span data-stu-id="a93cf-103">You can add a parameter to a report that allows the user to select more than one value for the parameter.</span></span>  
  
 <span data-ttu-id="a93cf-104">您可以在报表 URL 中将多个参数值传递给报表。</span><span class="sxs-lookup"><span data-stu-id="a93cf-104">You can pass multiple parameter values to the report within the report URL.</span></span> <span data-ttu-id="a93cf-105">有关包含多值参数的 URL 示例，请参阅 [在 URL 内传递报表参数](../pass-a-report-parameter-within-a-url.md)。</span><span class="sxs-lookup"><span data-stu-id="a93cf-105">For a URL example includes a multi-value parameter, see [Pass a Report Parameter Within a URL](../pass-a-report-parameter-within-a-url.md).</span></span>  
  
 <span data-ttu-id="a93cf-106">有关如何将多个参数值传递给存储过程的信息，请参阅 mssqltips.com 上的 [使用 SSRS 报表的多选参数](https://go.microsoft.com/fwlink/?LinkId=321529) 。</span><span class="sxs-lookup"><span data-stu-id="a93cf-106">For information on how to pass multiple parameter values to a stored procedure, see [Working With Multi-Select Parameters for SSRS Reports](https://go.microsoft.com/fwlink/?LinkId=321529) on mssqltips.com.</span></span>  
  
### <a name="to-add-a-multi-value-parameter"></a><span data-ttu-id="a93cf-107">添加多值参数</span><span class="sxs-lookup"><span data-stu-id="a93cf-107">To add a multi-value parameter</span></span>  
  
1.  <span data-ttu-id="a93cf-108">在报表生成器中，打开您希望将多值参数添加到其中的报表。</span><span class="sxs-lookup"><span data-stu-id="a93cf-108">In Report Builder, open the report that you want to add the multi-value parameter to.</span></span>  
  
2.  <span data-ttu-id="a93cf-109">右键单击报表数据集，然后单击“数据集属性” </span><span class="sxs-lookup"><span data-stu-id="a93cf-109">Right-click the report dataset, and then click **Dataset Properties**</span></span>  
  
3.  <span data-ttu-id="a93cf-110">通过在 **“查询”** 框中编辑查询文本或通过使用查询设计器添加筛选器，将变量添加到数据集查询中。</span><span class="sxs-lookup"><span data-stu-id="a93cf-110">Add a variable to the dataset query by either editing the query text in the **Query** box, or by adding a filter by using the query designer.</span></span> <span data-ttu-id="a93cf-111">有关详细信息，请参阅[在关系查询设计器中生成查询（报表生成器和 SSRS）](../report-data/build-a-query-in-the-relational-query-designer-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="a93cf-111">For more information, see [Build a Query in the Relational Query Designer &#40;Report Builder and SSRS&#41;](../report-data/build-a-query-in-the-relational-query-designer-report-builder-and-ssrs.md).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="a93cf-112">查询文本不得包含针对查询变量的 DECLARE 语句。</span><span class="sxs-lookup"><span data-stu-id="a93cf-112">The query text must not include the DECLARE statement for the query variable.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="a93cf-113">查询变量的文本必须包含 `IN` 运算符，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="a93cf-113">The text for the query variable must include the `IN` operator, as shown in the following example.</span></span>  
  
    ```  
    WHERE  
      Production.ProductInventory.ProductID IN (@ProductID)  
    ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="a93cf-114">如果在上面所示的变量周围不包含括号，则报表将无法呈现并显示 "必须声明标量变量" 错误。</span><span class="sxs-lookup"><span data-stu-id="a93cf-114">If you don't include the parentheses around the variable as shown above, the report fails to render and the "must declare the scalar variable" error is displayed.</span></span>  
  
     <span data-ttu-id="a93cf-115">自动为查询变量创建嵌入数据集或共享数据集的数据集参数。</span><span class="sxs-lookup"><span data-stu-id="a93cf-115">A dataset parameter for an embedded dataset or a shared dataset is created automatically for the query variable.</span></span> <span data-ttu-id="a93cf-116">自动为数据集参数创建报表参数。</span><span class="sxs-lookup"><span data-stu-id="a93cf-116">A report parameter is created automatically for the dataset parameter.</span></span>  
  
4.  <span data-ttu-id="a93cf-117">在“报表数据”窗格中展开“参数”节点，右键单击为数据集参数自动创建的报表参数，然后单击“参数属性”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a93cf-117">In the **Report Data** pane, expand the **Parameters** node, right-click the report parameter that was automatically created for the dataset parameter, and then click **Parameter Properties**.</span></span>  
  
5.  <span data-ttu-id="a93cf-118">在 **“常规”** 选项卡中，选择 **“允许多个值”** 以允许用户为参数选择多个值。</span><span class="sxs-lookup"><span data-stu-id="a93cf-118">In the **General** tab, select **Allow multiple values** to allow a user to select more than one value for the parameter.</span></span>  
  
6.  <span data-ttu-id="a93cf-119">（可选）在“可用”值选项卡中，指定要显示给用户的可用值列表\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a93cf-119">(Optionally) In the **Available** values tab, specify a list of available values to display to the user.</span></span>  
  
     <span data-ttu-id="a93cf-120">可用值列表将限制用户只能选择参数的有效值。</span><span class="sxs-lookup"><span data-stu-id="a93cf-120">An available values list limits the choices a user can make to only valid values for the parameter.</span></span> <span data-ttu-id="a93cf-121">对于多值参数，列表的顶部具有一个 **“全选”** 功能，因此用户只需一次单击即可选中或取消选中所有值。</span><span class="sxs-lookup"><span data-stu-id="a93cf-121">For multiple values, the top of list begins with a **Select All** feature so the user can select or clear all values with a single click.</span></span> <span data-ttu-id="a93cf-122">如果您选择从数据集查询中获取报表参数的可用值，请确保选择不包含与同一报表参数关联的查询变量的数据集。</span><span class="sxs-lookup"><span data-stu-id="a93cf-122">If you choose to get the available values for the report parameter from a dataset query, be sure to select a dataset that does not contain the query variable that is associated with the same report parameter.</span></span>  
  
     <span data-ttu-id="a93cf-123">有关详细信息，请参阅[为报表参数添加、更改或删除可用值（报表生成器和 SSRS）](add-change-or-delete-available-values-for-a-report-parameter.md)。</span><span class="sxs-lookup"><span data-stu-id="a93cf-123">For more information, see [Add, Change, or Delete Available Values for a Report Parameter &#40;Report Builder and SSRS&#41;](add-change-or-delete-available-values-for-a-report-parameter.md).</span></span>  
  
### <a name="to-add-a-multi-value-parameter"></a><span data-ttu-id="a93cf-124">添加多值参数</span><span class="sxs-lookup"><span data-stu-id="a93cf-124">To add a multi-value parameter</span></span>  
  
1.  <span data-ttu-id="a93cf-125">在报表生成器中，打开您希望将多值参数添加到其中的报表。</span><span class="sxs-lookup"><span data-stu-id="a93cf-125">In Report Builder, open the report that you want to add the multi-value parameter to.</span></span>  
  
2.  <span data-ttu-id="a93cf-126">右键单击报表数据集，然后单击“数据集属性”\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="a93cf-126">Right-click the report dataset, and then click **Dataset Properties**</span></span>  
  
3.  <span data-ttu-id="a93cf-127">通过在 **“查询”** 框中编辑查询文本或通过使用查询设计器添加筛选器，将变量添加到数据集查询中。</span><span class="sxs-lookup"><span data-stu-id="a93cf-127">Add a variable to the dataset query by either editing the query text in the **Query** box, or by adding a filter by using the query designer.</span></span> <span data-ttu-id="a93cf-128">有关详细信息，请参阅[在关系查询设计器中生成查询（报表生成器和 SSRS）](../report-data/build-a-query-in-the-relational-query-designer-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="a93cf-128">For more information, see [Build a Query in the Relational Query Designer &#40;Report Builder and SSRS&#41;](../report-data/build-a-query-in-the-relational-query-designer-report-builder-and-ssrs.md).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="a93cf-129">查询文本不得包含针对查询变量的 DECLARE 语句。</span><span class="sxs-lookup"><span data-stu-id="a93cf-129">The query text must not include the DECLARE statement for the query variable.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="a93cf-130">查询变量的文本必须包含 `IN` 运算符，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="a93cf-130">The text for the query variable must include the `IN` operator, as shown in the following example.</span></span>  
  
    ```  
    WHERE  
      Production.ProductInventory.ProductID IN (@ProductID)  
    ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="a93cf-131">如果在上面所示的变量周围不包含括号，则报表将无法呈现并显示 "必须声明标量变量" 错误。</span><span class="sxs-lookup"><span data-stu-id="a93cf-131">If you don't include the parentheses around the variable as shown above, the report fails to render and the "must declare the scalar variable" error is displayed.</span></span>  
  
     <span data-ttu-id="a93cf-132">自动为查询变量创建嵌入数据集或共享数据集的数据集参数。</span><span class="sxs-lookup"><span data-stu-id="a93cf-132">A dataset parameter for an embedded dataset or a shared dataset is created automatically for the query variable.</span></span> <span data-ttu-id="a93cf-133">自动为数据集参数创建报表参数。</span><span class="sxs-lookup"><span data-stu-id="a93cf-133">A report parameter is created automatically for the dataset parameter.</span></span>  
  
4.  <span data-ttu-id="a93cf-134">在“报表数据”窗格中展开“参数”节点，右键单击为数据集参数自动创建的报表参数，然后单击“参数属性”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a93cf-134">In the **Report Data** pane, expand the **Parameters** node, right-click the report parameter that was automatically created for the dataset parameter, and then click **Parameter Properties**.</span></span>  
  
5.  <span data-ttu-id="a93cf-135">在 **“常规”** 选项卡中，选择 **“允许多个值”** 以允许用户为参数选择多个值。</span><span class="sxs-lookup"><span data-stu-id="a93cf-135">In the **General** tab, select **Allow multiple values** to allow a user to select more than one value for the parameter.</span></span>  
  
6.  <span data-ttu-id="a93cf-136">（可选）在“可用”值选项卡中，指定要显示给用户的可用值列表\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a93cf-136">(Optionally) In the **Available** values tab, specify a list of available values to display to the user.</span></span>  
  
     <span data-ttu-id="a93cf-137">可用值列表将限制用户只能选择参数的有效值。</span><span class="sxs-lookup"><span data-stu-id="a93cf-137">An available values list limits the choices a user can make to only valid values for the parameter.</span></span> <span data-ttu-id="a93cf-138">对于多值参数，列表的顶部具有一个 **“全选”** 功能，因此用户只需一次单击即可选中或取消选中所有值。</span><span class="sxs-lookup"><span data-stu-id="a93cf-138">For multiple values, the top of list begins with a **Select All** feature so the user can select or clear all values with a single click.</span></span> <span data-ttu-id="a93cf-139">如果您选择从数据集查询中获取报表参数的可用值，请确保选择不包含与同一报表参数关联的查询变量的数据集。</span><span class="sxs-lookup"><span data-stu-id="a93cf-139">If you choose to get the available values for the report parameter from a dataset query, be sure to select a dataset that does not contain the query variable that is associated with the same report parameter.</span></span>  
  
     <span data-ttu-id="a93cf-140">有关详细信息，请参阅[为报表参数添加、更改或删除可用值（报表生成器和 SSRS）](add-change-or-delete-available-values-for-a-report-parameter.md)。</span><span class="sxs-lookup"><span data-stu-id="a93cf-140">For more information, see [Add, Change, or Delete Available Values for a Report Parameter &#40;Report Builder and SSRS&#41;](add-change-or-delete-available-values-for-a-report-parameter.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a93cf-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a93cf-141">See Also</span></span>  
 <span data-ttu-id="a93cf-142">[向报表添加级联参数 &#40;报表生成器和 SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a93cf-142">[Add Cascading Parameters to a Report &#40;Report Builder and SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="a93cf-143">添加、更改或删除报表参数（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="a93cf-143">Add, Change, or Delete a Report Parameter &#40;Report Builder and SSRS&#41;</span></span>](add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md)  
  
  
