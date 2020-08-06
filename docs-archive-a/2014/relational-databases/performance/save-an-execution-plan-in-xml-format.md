---
title: 以 XML 格式保存执行计划 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- XML query plans [SQL Server]
- opening execution plans
- XML Showplans [SQL Server]
- execution plans [SQL Server], saving
- saving execution plans
ms.assetid: c439e53b-56f3-4442-97c6-dabd48a203d8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 84ed341d186993ed77260e8361156b324c597839
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588476"
---
# <a name="save-an-execution-plan-in-xml-format"></a><span data-ttu-id="53b0f-102">以 XML 格式保存执行计划</span><span class="sxs-lookup"><span data-stu-id="53b0f-102">Save an Execution Plan in XML Format</span></span>
  <span data-ttu-id="53b0f-103">使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 可以将执行计划保存为 XML 文件，也可以打开这些执行计划进行查看。</span><span class="sxs-lookup"><span data-stu-id="53b0f-103">Use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to save execution plans as an XML file, and to open them for viewing.</span></span>  
  
 <span data-ttu-id="53b0f-104">若要使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中的执行计划功能或使用 XML 显示计划的 SET 选项，用户必须具有执行（要为其生成执行计划的） [!INCLUDE[tsql](../../includes/tsql-md.md)] 查询的相应权限，还必须获得对该查询所引用的所有数据库的 SHOWPLAN 权限。</span><span class="sxs-lookup"><span data-stu-id="53b0f-104">To use the execution plan feature in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], or to use the XML Showplan SET options, users must have the appropriate permissions to execute the [!INCLUDE[tsql](../../includes/tsql-md.md)] query for which an execution plan is being generated, and they must be granted the SHOWPLAN permission for all databases referenced by the query.</span></span>  
  
### <a name="to-save-a-query-plan-by-using-the-xml-showplan-set-options"></a><span data-ttu-id="53b0f-105">使用 XML 显示计划的 SET 选项保存查询计划</span><span class="sxs-lookup"><span data-stu-id="53b0f-105">To save a query plan by using the XML Showplan SET options</span></span>  
  
1.  <span data-ttu-id="53b0f-106">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，打开查询编辑器并连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="53b0f-106">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] open a query editor and connect to [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="53b0f-107">使用以下语句打开 SHOWPLAN_XML：</span><span class="sxs-lookup"><span data-stu-id="53b0f-107">Turn SHOWPLAN_XML on with the following statement:</span></span>  
  
    ```  
    SET SHOWPLAN_XML ON;  
    GO  
    ```  
  
     <span data-ttu-id="53b0f-108">若要打开 STATISTICS XML，请使用以下语句：</span><span class="sxs-lookup"><span data-stu-id="53b0f-108">To turn STATISTICS XML on, use the following statement:</span></span>  
  
    ```  
    SET STATISTICS XML ON;  
    GO  
    ```  
  
     <span data-ttu-id="53b0f-109">SHOWPLAN_XML 将会为查询生成编译时查询执行计划信息，但是不会执行查询。</span><span class="sxs-lookup"><span data-stu-id="53b0f-109">SHOWPLAN_XML generates compile-time query execution plan information for a query, but does not execute the query.</span></span> <span data-ttu-id="53b0f-110">STATISTICS XML 将会为查询生成运行时查询执行计划信息，而且会执行查询。</span><span class="sxs-lookup"><span data-stu-id="53b0f-110">STATISTICS XML generates run-time query execution plan information for a query, and executes the query.</span></span>  
  
3.  <span data-ttu-id="53b0f-111">执行查询。</span><span class="sxs-lookup"><span data-stu-id="53b0f-111">Execute a query.</span></span> <span data-ttu-id="53b0f-112">示例：</span><span class="sxs-lookup"><span data-stu-id="53b0f-112">Example:</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SET SHOWPLAN_XML ON;  
    GO  
    -- Execute a query.  
    SELECT BusinessEntityID   
    FROM HumanResources.Employee  
    WHERE NationalIDNumber = '509647174';  
    GO  
    SET SHOWPLAN_XML OFF;  
    ```  
  
4.  <span data-ttu-id="53b0f-113">在“结果”窗格中，右键单击包含查询计划的“Microsoft SQL Server XML 显示计划”，然后单击“将结果另存为”。</span><span class="sxs-lookup"><span data-stu-id="53b0f-113">In the **Results** pane, right-click the **Microsoft SQL Server XML Showplan** that contains the query plan, and then click **Save Results As**.</span></span>  
  
5.  <span data-ttu-id="53b0f-114">在“保存 \<Grid or Text> 结果”对话框中的“保存类型”框中，单击“所有文件(\*.\*)”   。</span><span class="sxs-lookup"><span data-stu-id="53b0f-114">In the **Save** \<Grid or Text> **Results** dialog box, in the **Save as type** box, click **All files (\*.\*)**.</span></span>  
  
6.  <span data-ttu-id="53b0f-115">在“文件名”框中，提供“\<name**>.sqlplan\*\*”格式的名称，然后单击“保存” 。</span><span class="sxs-lookup"><span data-stu-id="53b0f-115">In the **File name** box provide a name, in the format \<name**>.sqlplan\*\*, and then click **Save**.</span></span>  
  
### <a name="to-save-an-execution-plan-by-using-sql-server-management-studio-options"></a><span data-ttu-id="53b0f-116">使用 SQL Server Management Studio 选项保存执行计划</span><span class="sxs-lookup"><span data-stu-id="53b0f-116">To save an execution plan by using SQL Server Management Studio options</span></span>  
  
1.  <span data-ttu-id="53b0f-117">使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]生成估计的执行计划或实际的执行计划。</span><span class="sxs-lookup"><span data-stu-id="53b0f-117">Generate either an estimated execution plan or an actual execution plan by using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="53b0f-118">有关详细信息，请参阅 [显示估计的执行计划](display-the-estimated-execution-plan.md) 或 [显示实际执行计划](display-an-actual-execution-plan.md)。</span><span class="sxs-lookup"><span data-stu-id="53b0f-118">For more information, see [Display the Estimated Execution Plan](display-the-estimated-execution-plan.md) or [Display an Actual Execution Plan](display-an-actual-execution-plan.md).</span></span>  
  
2.  <span data-ttu-id="53b0f-119">在“结果”窗格的“执行计划”选项卡上，右键单击图形执行计划，然后选择“将执行计划另存为”。</span><span class="sxs-lookup"><span data-stu-id="53b0f-119">In the **Execution plan** tab of the results pane, right-click the graphical execution plan, and choose **Save Execution Plan As**.</span></span>  
  
     <span data-ttu-id="53b0f-120">此外，还可以在 **“文件”** 菜单上选择 **“将执行计划另存为”** 。</span><span class="sxs-lookup"><span data-stu-id="53b0f-120">As an alternative, you can also choose **Save Execution Plan As** on the **File** menu.</span></span>  
  
3.  <span data-ttu-id="53b0f-121">在“另存为”对话框中，确保将“保存类型”设置为“执行计划文件(\*.sqlplan)”。</span><span class="sxs-lookup"><span data-stu-id="53b0f-121">In the **Save As** dialog box, make sure that the **Save as type** is set to **Execution Plan Files (\*.sqlplan)**.</span></span>  
  
4.  <span data-ttu-id="53b0f-122">在“文件名”框中，提供“\<name**>.sqlplan\*\*”格式的名称，然后单击“保存” 。</span><span class="sxs-lookup"><span data-stu-id="53b0f-122">In the **File name** box provide a name, in the format \<name**>.sqlplan\*\*, and then click **Save**.</span></span>  
  
### <a name="to-open-a-saved-xml-query-plan-in-sql-server-management-studio"></a><span data-ttu-id="53b0f-123">在 SQL Server Management Studio 中打开保存的 XML 查询计划</span><span class="sxs-lookup"><span data-stu-id="53b0f-123">To open a saved XML query plan in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="53b0f-124">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的 **“文件”** 菜单上，选择 **“打开”** ，然后单击 **“文件”** 。</span><span class="sxs-lookup"><span data-stu-id="53b0f-124">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **File** menu, choose **Open**, and then click **File**.</span></span>  
  
2.  <span data-ttu-id="53b0f-125">在“打开文件”对话框中，将“文件类型”设置为“执行计划文件(\*.sqlplan)”，以筛选出保存的 XML 查询计划文件的列表。</span><span class="sxs-lookup"><span data-stu-id="53b0f-125">In the **Open File** dialog box, set **Files of type** to **Execution Plan Files (\*.sqlplan)** to produce a filtered list of saved XML query plan files.</span></span>  
  
3.  <span data-ttu-id="53b0f-126">选择要查看的 XML 查询计划文件，然后单击 **“打开”** 。</span><span class="sxs-lookup"><span data-stu-id="53b0f-126">Select the XML query plan file that you want to view, and click **Open**.</span></span>  
  
     <span data-ttu-id="53b0f-127">此外，还可以在 Windows 资源管理器中双击扩展名为 **.sqlplan**的文件。</span><span class="sxs-lookup"><span data-stu-id="53b0f-127">As an alternative, in Windows Explorer, double-click a file with extension **.sqlplan**.</span></span> <span data-ttu-id="53b0f-128">该计划便会在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中打开。</span><span class="sxs-lookup"><span data-stu-id="53b0f-128">The plan opens in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53b0f-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="53b0f-129">See Also</span></span>  
 <span data-ttu-id="53b0f-130">[SET SHOWPLAN_XML (Transact-SQL)](/sql/t-sql/statements/set-showplan-xml-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="53b0f-130">[SET SHOWPLAN_XML &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-showplan-xml-transact-sql) </span></span>  
 [<span data-ttu-id="53b0f-131">SET STATISTICS XML (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="53b0f-131">SET STATISTICS XML &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/set-statistics-xml-transact-sql)  
  
  
