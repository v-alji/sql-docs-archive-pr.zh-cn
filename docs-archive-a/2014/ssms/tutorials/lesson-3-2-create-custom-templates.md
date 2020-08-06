---
title: 创建自定义模板 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- tql
- templates [Transact-SQL], creating
- templates [Transact-SQL]
ms.assetid: 41098e78-b482-410e-bfe8-2ac10769ac4a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 771547b9c47672d2c075b5e7215d78744fe5f18e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690275"
---
# <a name="create-custom-templates"></a><span data-ttu-id="d7da5-102">创建自定义模板</span><span class="sxs-lookup"><span data-stu-id="d7da5-102">Create Custom Templates</span></span>
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="d7da5-103">附带用于许多常见任务的模板，但模板的真正作用在于它能为必须频繁创建的复杂脚本创建自定义模板。</span><span class="sxs-lookup"><span data-stu-id="d7da5-103">comes with templates for many common tasks, but the real power of templates lies in the ability to create a custom template for a complex script that you must create frequently.</span></span> <span data-ttu-id="d7da5-104">在本练习中，您将创建带有较少参数的简单脚本，但是模板也适用于较长的重复脚本。</span><span class="sxs-lookup"><span data-stu-id="d7da5-104">In this practice you will create a simple script with few parameters, but templates are useful for long, repetitive scripts, too.</span></span>  
  
## <a name="using-custom-templates"></a><span data-ttu-id="d7da5-105">使用自定义模板</span><span class="sxs-lookup"><span data-stu-id="d7da5-105">Using Custom Templates</span></span>  
  
#### <a name="to-create-a-custom-template"></a><span data-ttu-id="d7da5-106">创建自定义模板</span><span class="sxs-lookup"><span data-stu-id="d7da5-106">To create a custom template</span></span>  
  
1.  <span data-ttu-id="d7da5-107">在模板资源管理器中，展开“SQL Server 模板”\*\*\*\*，右键单击“存储过程”\*\*\*\*，指向“新建”\*\*\*\*，然后单击“文件夹”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d7da5-107">In Template Explorer, expand **SQL Server Templates**, right-click **Stored Procedure**, point to **New**, and then click **Folder**.</span></span>  
  
2.  <span data-ttu-id="d7da5-108">键入 **Custom** 作为新模板文件夹的名称，然后按 Enter。</span><span class="sxs-lookup"><span data-stu-id="d7da5-108">Type **Custom** as the name of your new template folder, and then press ENTER.</span></span>  
  
3.  <span data-ttu-id="d7da5-109">右键单击“Custom”\*\*\*\*，指向“新建”\*\*\*\*，然后单击“模板”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d7da5-109">Right-click **Custom**, point to **New**, and then click **Template**.</span></span>  
  
4.  <span data-ttu-id="d7da5-110">键入 **WorkOrdersProc** 作为新模板的名称，然后按 **Enter**。</span><span class="sxs-lookup"><span data-stu-id="d7da5-110">Type **WorkOrdersProc** as the name of your new template, and then press **Enter**.</span></span>  
  
5.  <span data-ttu-id="d7da5-111">右键单击“WorkOrdersProc”\*\*\*\*，然后单击“编辑”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d7da5-111">Right-click **WorkOrdersProc**, and then click **Edit**.</span></span>  
  
6.  <span data-ttu-id="d7da5-112">在“连接到数据库引擎”\*\*\*\* 对话框中，验证连接信息，然后单击“连接”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d7da5-112">In the **Connect to Database Engine** dialog box, verify the connection information and then click **Connect**.</span></span>  
  
7.  <span data-ttu-id="d7da5-113">在查询编辑器中，键入以下脚本以创建用于查找特定部分（在此事例中是 Blade）顺序的存储过程。</span><span class="sxs-lookup"><span data-stu-id="d7da5-113">In Query Editor, type the following script to create a stored procedure that looks up orders for a particular part, in this case the Blade.</span></span> <span data-ttu-id="d7da5-114">（您可以从“教程”窗口中复制和粘贴代码。）</span><span class="sxs-lookup"><span data-stu-id="d7da5-114">(You can copy and paste the code from the Tutorial window.)</span></span>  
  
    ```  
    USE AdventureWorks20012;  
    GO  
    IF EXISTS (  
    SELECT *   
       FROM INFORMATION_SCHEMA.ROUTINES   
       WHERE SPECIFIC_NAME = 'WorkOrdersForBlade')  
       DROP PROCEDURE dbo.WorkOrdersForBlade;  
    GO  
    CREATE PROCEDURE dbo.WorkOrdersForBlade  
    AS  
    SELECT Name, WorkOrderID   
    FROM Production.WorkOrder AS WO  
    JOIN Production.Product AS Prod  
    ON WO.ProductID = Prod.ProductID  
    WHERE Name = 'Blade';  
    GO  
    ```  
  
8.  <span data-ttu-id="d7da5-115">按 F5 执行此脚本，创建 **WorkOrdersForBlade** 过程。</span><span class="sxs-lookup"><span data-stu-id="d7da5-115">Press F5 to execute this script, creating the **WorkOrdersForBlade** procedure.</span></span>  
  
9. <span data-ttu-id="d7da5-116">在对象资源管理器中，右键单击服务器，然后单击“新建查询”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d7da5-116">In Object Explorer, right-click your server, and then click **New Query**.</span></span> <span data-ttu-id="d7da5-117">系统将打开新的“查询编辑器”窗口。</span><span class="sxs-lookup"><span data-stu-id="d7da5-117">A new Query Editor window opens.</span></span>  
  
10. <span data-ttu-id="d7da5-118">在查询编辑器中，键入 **EXECUTE dbo.WorkOrdersForBlade**，然后按 F5 执行查询。</span><span class="sxs-lookup"><span data-stu-id="d7da5-118">In Query Editor, type **EXECUTE dbo.WorkOrdersForBlade**, and then press F5 to execute the query.</span></span> <span data-ttu-id="d7da5-119">确认“结果”\*\*\*\* 窗格返回 Blade 的工作订单列表。</span><span class="sxs-lookup"><span data-stu-id="d7da5-119">Confirm that the **Results** pane returns a list of work orders for blades.</span></span>  
  
11. <span data-ttu-id="d7da5-120"> (步骤 7) 中的脚本编辑模板脚本，将 "产品名称" 边栏选项卡替换为参数<strong> *<* product_name</strong>， `nvarchar(50)` ， <strong> *>* 名称</strong>，在四个位置。</span><span class="sxs-lookup"><span data-stu-id="d7da5-120">Edit the template script (the script in step 7), replacing the product name Blade with the parameter <strong>*<* product_name</strong>, `nvarchar(50)`, <strong>name*>*</strong>, in four places.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d7da5-121">参数需要三个元素：要替换的参数的名称、该参数的数据类型以及该参数的默认值。</span><span class="sxs-lookup"><span data-stu-id="d7da5-121">Parameters require three elements: the name of the parameter that you want to replace, the data type of the parameter, and a default value for the parameter.</span></span>  
  
12. <span data-ttu-id="d7da5-122">现在脚本应该如下所示：</span><span class="sxs-lookup"><span data-stu-id="d7da5-122">Now the script should look like:</span></span>  
  
    ```  
    USE AdventureWorks20012;  
    GO  
    IF EXISTS (  
    SELECT *   
       FROM INFORMATION_SCHEMA.ROUTINES   
       WHERE SPECIFIC_NAME = 'WorkOrdersFor<product_name, nvarchar(50), name>')  
       DROP PROCEDURE dbo.WorkOrdersFor<product_name, nvarchar(50), name>;  
    GO  
    CREATE PROCEDURE dbo.WorkOrdersFor<product_name, nvarchar(50), name>  
    AS  
    SELECT Name, WorkOrderID   
    FROM Production.WorkOrder AS WO  
    JOIN Production.Product AS Prod  
    ON WO.ProductID = Prod.ProductID  
    WHERE Name = '<product_name, nvarchar(50), name>';  
    GO  
    ```  
  
13. <span data-ttu-id="d7da5-123">在“文件”\*\*\*\* 菜单中，单击“保存 WorkOrdersProc.sql”\*\*\*\* 以保存模板。</span><span class="sxs-lookup"><span data-stu-id="d7da5-123">On the **File** menu, click **Save WorkOrdersProc.sql** to save your template.</span></span>  
  
#### <a name="to-test-the-custom-template"></a><span data-ttu-id="d7da5-124">测试自定义模板</span><span class="sxs-lookup"><span data-stu-id="d7da5-124">To test the custom template</span></span>  
  
1.  <span data-ttu-id="d7da5-125">在模板资源管理器中，依次展开“存储过程”\*\*\*\* 和“Custom”\*\*\*\*，然后双击“WorkOrderProc”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d7da5-125">In Template Explorer, expand **Stored Procedure**, expand **Custom**, and then double-click **WorkOrderProc**.</span></span>  
  
2.  <span data-ttu-id="d7da5-126">在“连接到数据库引擎”\*\*\*\* 对话框中，填写连接信息，然后单击“连接”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d7da5-126">In the **Connect to Database Engine** dialog box, complete the connection information and then click **Connect**.</span></span> <span data-ttu-id="d7da5-127">系统将打开新的“查询编辑器”窗口，其中包含“WorkOrderProc”\*\*\*\* 模板的内容。</span><span class="sxs-lookup"><span data-stu-id="d7da5-127">A new Query Editor window opens, containing the contents of the **WorkOrderProc** template.</span></span>  
  
3.  <span data-ttu-id="d7da5-128">在 **“查询”** 菜单上，单击 **“指定模板参数的值”** 。</span><span class="sxs-lookup"><span data-stu-id="d7da5-128">On the **Query** menu, click **Specify Values for Template Parameters**.</span></span>  
  
4.  <span data-ttu-id="d7da5-129">在 "**替换模板参数**" 对话框中， `product_name` 键入 " **FreeWheel** (覆盖默认内容") ，然后单击 **"确定"** 以关闭 "**替换模板参数**" 对话框，并在查询编辑器中修改脚本。</span><span class="sxs-lookup"><span data-stu-id="d7da5-129">In the **Replace Template Parameters** dialog box, for the `product_name` value, type **FreeWheel** (overwriting the default contents), and then click **OK** to close the **Replace Template Parameters** dialog box and modify the script in the Query Editor.</span></span>  
  
5.  <span data-ttu-id="d7da5-130">按 F5 键执行查询，并创建过程。</span><span class="sxs-lookup"><span data-stu-id="d7da5-130">Press F5 to execute the query, creating the procedure.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="d7da5-131">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="d7da5-131">Next Task in Lesson</span></span>  
 [<span data-ttu-id="d7da5-132">将脚本另存为项目或解决方案</span><span class="sxs-lookup"><span data-stu-id="d7da5-132">Save Scripts as Projects or Solutions</span></span>](lesson-3-3-save-scripts-as-projects-or-solutions.md)  
  
  
