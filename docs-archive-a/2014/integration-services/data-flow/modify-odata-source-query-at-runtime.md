---
title: 在运行时修改 OData 源查询 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: bcbba7f4-6e5d-46e6-a73a-3f17d3ff376a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b3dbc4d27f2d11537a9d66980ef6ca59b80811b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693410"
---
# <a name="modify-odata-source-query-at-runtime"></a><span data-ttu-id="d7cc1-102">在运行时修改 OData 源查询</span><span class="sxs-lookup"><span data-stu-id="d7cc1-102">Modify OData Source Query at Runtime</span></span>
  <span data-ttu-id="d7cc1-103">可以通过将表达式添加到 [OData 源] 来在运行时修改 OData 源查询 **。 [Query]** 属性。</span><span class="sxs-lookup"><span data-stu-id="d7cc1-103">You can modify the OData Source query at runtime by adding an expression to the **[OData Source].[Query]** property of the Data Flow task.</span></span>  
  
 <span data-ttu-id="d7cc1-104">请注意，列必须保持与设计时使用的内容相同；否则执行包时会出现错误。</span><span class="sxs-lookup"><span data-stu-id="d7cc1-104">Note that the columns must remain the same as what was used at design time; otherwise you will get an error when the package is executed.</span></span> <span data-ttu-id="d7cc1-105">请务必在使用 $select 查询选项时指定相同的列（采用相同顺序）。</span><span class="sxs-lookup"><span data-stu-id="d7cc1-105">Be sure to specify the same columns (in the same order) when using the $select query option.</span></span> <span data-ttu-id="d7cc1-106">使用 $select 选项的更安全替代方法是直接从源组件 UI 中取消选择不需要的列。</span><span class="sxs-lookup"><span data-stu-id="d7cc1-106">A safer alternative to using the $select option is to deselect the columns you don't want directly from the Source Component UI.</span></span>  
  
 <span data-ttu-id="d7cc1-107">可通过几种不同的方式在运行时动态设置查询值。</span><span class="sxs-lookup"><span data-stu-id="d7cc1-107">There are a few different ways of dynamically setting the query value at runtime.</span></span> <span data-ttu-id="d7cc1-108">下面是一些较常用的方法。</span><span class="sxs-lookup"><span data-stu-id="d7cc1-108">Below are some of the more common methods.</span></span>  
  
## <a name="exposing-the-query-as-a-parameter"></a><span data-ttu-id="d7cc1-109">将查询公开为参数</span><span class="sxs-lookup"><span data-stu-id="d7cc1-109">Exposing the Query as a Parameter</span></span>  
 <span data-ttu-id="d7cc1-110">以下过程包含的步骤可将 OData 源组件使用的查询公开为包的参数。</span><span class="sxs-lookup"><span data-stu-id="d7cc1-110">The following procedure has steps to expose query used by an OData Source component as a parameter to the package.</span></span>  
  
1.  <span data-ttu-id="d7cc1-111">右键单击“数据流任务”并选择“参数化…”选项   。</span><span class="sxs-lookup"><span data-stu-id="d7cc1-111">Right click on the **Data Flow task** and select the **Parameterize...** option.</span></span>  
  
2.  <span data-ttu-id="d7cc1-112">在“参数化”对话框中，针对“属性”选择 [\<Name of the OData Source Component>].[Query]  。</span><span class="sxs-lookup"><span data-stu-id="d7cc1-112">In the **Parameterize** dialog, select **[\<Name of the OData Source Component>].[Query]** for **Property**.</span></span>  
  
3.  <span data-ttu-id="d7cc1-113">选择是 **“创建新参数”** 还是 **“使用现有参数”** 。</span><span class="sxs-lookup"><span data-stu-id="d7cc1-113">Choose whether to **create new parameter** or **use an existing parameter**.</span></span>  
  
4.  <span data-ttu-id="d7cc1-114">如果选择 **“创建新参数”**，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="d7cc1-114">If you select **Create new parameter**, do the following:</span></span>  
  
    1.  <span data-ttu-id="d7cc1-115">为参数输入 **“名称”** 和 **“说明”** 。</span><span class="sxs-lookup"><span data-stu-id="d7cc1-115">Enter **name** and **description** for the parameter.</span></span>  
  
    2.  <span data-ttu-id="d7cc1-116">为参数指定默认 **“值”** 。</span><span class="sxs-lookup"><span data-stu-id="d7cc1-116">Specify default **value** for the parameter.</span></span>  
  
    3.  <span data-ttu-id="d7cc1-117">为参数指定“范围”  （“包”  或“项目”  ）。</span><span class="sxs-lookup"><span data-stu-id="d7cc1-117">Specify the **scope** (**package** or **project**) for the parameter.</span></span>  
  
    4.  <span data-ttu-id="d7cc1-118">指定参数是否为 **“必需”**</span><span class="sxs-lookup"><span data-stu-id="d7cc1-118">Specify whether the parameter is **required** or not</span></span>  
  
5.  <span data-ttu-id="d7cc1-119">单击 **“确定”** 关闭对话框。</span><span class="sxs-lookup"><span data-stu-id="d7cc1-119">Click **OK** to close the dialog box.</span></span>  
  
## <a name="using-an-expression"></a><span data-ttu-id="d7cc1-120">使用表达式</span><span class="sxs-lookup"><span data-stu-id="d7cc1-120">Using an Expression</span></span>  
 <span data-ttu-id="d7cc1-121">当您要在运行时动态构造查询字符串时，可使用此方法。</span><span class="sxs-lookup"><span data-stu-id="d7cc1-121">This method is useful when you want to dynamically construct query string at runtime.</span></span> <span data-ttu-id="d7cc1-122">在此示例中，MaxRows 变量将通过其他方法（脚本、参数等）进行设置。</span><span class="sxs-lookup"><span data-stu-id="d7cc1-122">In this example, MaxRows variable will be set through other means (script, parameter, etc).</span></span>  
  
1.  <span data-ttu-id="d7cc1-123">选择包含 **“OData 源”** 的 **“数据流任务”**。</span><span class="sxs-lookup"><span data-stu-id="d7cc1-123">Select the **Data Flow Task** which contains your **OData Source**.</span></span>  
  
2.  <span data-ttu-id="d7cc1-124">在 **“属性”** 窗口中，突出显示 **“表达式”** 属性。</span><span class="sxs-lookup"><span data-stu-id="d7cc1-124">In the **Properties** window, highlight the **Expressions** property.</span></span>  
  
3.  <span data-ttu-id="d7cc1-125">单击 "..." (省略号) "按钮以显示"**属性表达式编辑器**"。</span><span class="sxs-lookup"><span data-stu-id="d7cc1-125">Click the ... (ellipses) button to bring up the **Property Expressions Editor**.</span></span>  
  
4.  <span data-ttu-id="d7cc1-126">选择“[OData 源].[查询]”  属性。</span><span class="sxs-lookup"><span data-stu-id="d7cc1-126">Select the **[OData Source].[Query]** property.</span></span>  
  
5.  <span data-ttu-id="d7cc1-127">单击**Expression** (省略号) 按钮。</span><span class="sxs-lookup"><span data-stu-id="d7cc1-127">Click the ... (ellipses) button for **Expression**.</span></span>  
  
6.  <span data-ttu-id="d7cc1-128">输入 **“表达式”** 。</span><span class="sxs-lookup"><span data-stu-id="d7cc1-128">Enter the **expression**.</span></span>  
  
7.  <span data-ttu-id="d7cc1-129">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="d7cc1-129">Click **OK**.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="d7cc1-130">请注意，当使用此方法时，需要确保设置的值为正确编码的 URL。</span><span class="sxs-lookup"><span data-stu-id="d7cc1-130">Note that when using this approach you need to ensure that the values set are properly URL encoded.</span></span> <span data-ttu-id="d7cc1-131">从用户输入接收值时（例如，通过参数设置各个查询选项值），必须确保值已验证，以避免潜在的 SQL 注入类型攻击。</span><span class="sxs-lookup"><span data-stu-id="d7cc1-131">When receiving values from user input (for example, setting individual query option values from a parameter), you must ensure that the values are validated to avoid potential SQL injection-type attacks.</span></span>  
  
  
