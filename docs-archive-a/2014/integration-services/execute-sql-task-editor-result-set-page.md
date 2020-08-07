---
title: " (\"结果集\" 页上执行 SQL 任务编辑器) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executesqltask.resultset.f1
helpviewer_keywords:
- Execute SQL Task Editor
ms.assetid: d27000c8-8d91-4e1c-b45e-bca9a3c12f6d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 027f3c77e84b47958e9fb6567acdb308c14eb1e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580316"
---
# <a name="execute-sql-task-editor-result-set-page"></a><span data-ttu-id="d501e-102">执行 SQL 任务编辑器（“结果集”页）</span><span class="sxs-lookup"><span data-stu-id="d501e-102">Execute SQL Task Editor (Result Set Page)</span></span>
  <span data-ttu-id="d501e-103">可以使用 **“执行 SQL 任务编辑器”** 对话框的 **“结果集”** 页，将 SQL 语句的结果映射到新变量或现有变量。</span><span class="sxs-lookup"><span data-stu-id="d501e-103">Use the **Result Set** page of the **Execute SQL Task Editor** dialog to map the result of the SQL statement to new or existing variables.</span></span> <span data-ttu-id="d501e-104">如果将“常规”页上的 **ResultSet** 设置为 **“无”** ，将禁用此对话框中的选项。</span><span class="sxs-lookup"><span data-stu-id="d501e-104">The options in this dialog box are disabled if **ResultSet** on the General page is set to **None**.</span></span>  
  
 <span data-ttu-id="d501e-105">有关此任务的详细信息，请参阅 [执行 SQL 任务](control-flow/execute-sql-task.md) 和 [执行 SQL 任务中的结果集](../../2014/integration-services/result-sets-in-the-execute-sql-task.md)。</span><span class="sxs-lookup"><span data-stu-id="d501e-105">For more information about this task, see [Execute SQL Task](control-flow/execute-sql-task.md) and [Result Sets in the Execute SQL Task](../../2014/integration-services/result-sets-in-the-execute-sql-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="d501e-106">选项</span><span class="sxs-lookup"><span data-stu-id="d501e-106">Options</span></span>  
 <span data-ttu-id="d501e-107">**结果名称**</span><span class="sxs-lookup"><span data-stu-id="d501e-107">**Result Name**</span></span>  
 <span data-ttu-id="d501e-108">通过单击“添加”  添加了结果集映射集之后，为结果提供名称。</span><span class="sxs-lookup"><span data-stu-id="d501e-108">After you have added a result set mapping set by clicking **Add**, provide a name for the result.</span></span> <span data-ttu-id="d501e-109">必须根据结果集类型使用特定的结果名称。</span><span class="sxs-lookup"><span data-stu-id="d501e-109">Depending on the result set type, you must use specific result names.</span></span>  
  
 <span data-ttu-id="d501e-110">如果结果集的类型为“单行”  ，则可以使用由查询返回的列的名称，也可以使用代表列在查询所返回列的列表中位置的数字。</span><span class="sxs-lookup"><span data-stu-id="d501e-110">If the result set type is **Single row**, you can use either the name of a column returned by the query or the number that represents the position of a column in the column list of a column returned by the query.</span></span>  
  
 <span data-ttu-id="d501e-111">如果结果集类型为“完整结果集”  或 **XML**，则必须使用 0 作为结果集名称。</span><span class="sxs-lookup"><span data-stu-id="d501e-111">If the result set type is **Full result set** or **XML**, you must use 0 as the result set name.</span></span>  
  
 <span data-ttu-id="d501e-112">**相关主题**：[执行 SQL 任务中的结果集](../../2014/integration-services/result-sets-in-the-execute-sql-task.md)</span><span class="sxs-lookup"><span data-stu-id="d501e-112">**Related Topics**: [Result Sets in the Execute SQL Task](../../2014/integration-services/result-sets-in-the-execute-sql-task.md)</span></span>  
  
 <span data-ttu-id="d501e-113">**“变量名称”**</span><span class="sxs-lookup"><span data-stu-id="d501e-113">**Variable Name**</span></span>  
 <span data-ttu-id="d501e-114">选择变量或单击“\<**New variable...**>”使用“添加变量”对话框添加新的变量，将结果集映射到变量。</span><span class="sxs-lookup"><span data-stu-id="d501e-114">Map the result set to a variable by selecting a variable or click \<**New variable...**> to add a new variable by using the **Add Variable** dialog box.</span></span>  
  
 <span data-ttu-id="d501e-115">**添加**</span><span class="sxs-lookup"><span data-stu-id="d501e-115">**Add**</span></span>  
 <span data-ttu-id="d501e-116">单击此项可以添加结果集映射。</span><span class="sxs-lookup"><span data-stu-id="d501e-116">Click to add a result set mapping.</span></span>  
  
 <span data-ttu-id="d501e-117">**删除**</span><span class="sxs-lookup"><span data-stu-id="d501e-117">**Remove**</span></span>  
 <span data-ttu-id="d501e-118">在列表中选择结果集映射，再单击“删除”  。</span><span class="sxs-lookup"><span data-stu-id="d501e-118">Select a result set mapping in the list and then click **Remove**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d501e-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d501e-119">See Also</span></span>  
 <span data-ttu-id="d501e-120">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="d501e-120">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="d501e-121">[&#40;"常规" 页上执行 SQL 任务编辑器&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="d501e-121">[Execute SQL Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="d501e-122">[执行 SQL 任务编辑器 &#40;参数映射页&#41;](../../2014/integration-services/execute-sql-task-editor-parameter-mapping-page.md) </span><span class="sxs-lookup"><span data-stu-id="d501e-122">[Execute SQL Task Editor &#40;Parameter Mapping Page&#41;](../../2014/integration-services/execute-sql-task-editor-parameter-mapping-page.md) </span></span>  
 [<span data-ttu-id="d501e-123">Transact-SQL 参考（数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="d501e-123">Transact-SQL Reference &#40;Database Engine&#41;</span></span>](/sql/t-sql/language-reference)  
  
  
