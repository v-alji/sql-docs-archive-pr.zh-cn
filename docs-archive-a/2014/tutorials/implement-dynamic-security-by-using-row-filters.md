---
title: 使用行筛选器实现动态安全性 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 8bf03c45-caf5-4eda-9314-e4f8f24a159f
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 09a15f818f57d7a9d808c89ced41b285536a7883
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577966"
---
# <a name="implement-dynamic-security-by-using-row-filters"></a><span data-ttu-id="a8f85-102">通过使用行筛选器实现动态安全性</span><span class="sxs-lookup"><span data-stu-id="a8f85-102">Implement Dynamic Security by Using Row Filters</span></span>
  <span data-ttu-id="a8f85-103">在本补充课程中，您将另外创建一个实现动态安全性的角色。</span><span class="sxs-lookup"><span data-stu-id="a8f85-103">In this supplemental lesson, you will create an additional role that implements dynamic security.</span></span> <span data-ttu-id="a8f85-104">动态安全性基于当前已登录用户的用户名或登录 ID 提供行级别安全性。</span><span class="sxs-lookup"><span data-stu-id="a8f85-104">Dynamic security provides row-level security based on the user name or login id of the user currently logged on.</span></span> <span data-ttu-id="a8f85-105">若要了解详细信息，请参阅[角色（SSAS 表格）](https://docs.microsoft.com/analysis-services/tabular-models/roles-ssas-tabular)。</span><span class="sxs-lookup"><span data-stu-id="a8f85-105">To learn more, see [Roles &#40;SSAS Tabular&#41;](https://docs.microsoft.com/analysis-services/tabular-models/roles-ssas-tabular).</span></span>  
  
 <span data-ttu-id="a8f85-106">若要实现动态安全性，您必须向模型中添加一个表，该表中包含那些可以创建与模型的连接作为数据源并可浏览模型对象和数据的用户的 Windows 用户名。</span><span class="sxs-lookup"><span data-stu-id="a8f85-106">To implement dynamic security, you must add a table to your model containing the Windows user names of those users that can create a connection to the model as a data source and browse model objects and data.</span></span> <span data-ttu-id="a8f85-107">您使用本教程创建的模型位于 Adventure Works Corp. 上下文中；但是，若要完成本课程，您必须添加一个表，其中包含来自您自己域的用户。</span><span class="sxs-lookup"><span data-stu-id="a8f85-107">The model you create using this tutorial is in the context of Adventure Works Corp.; however, in order to complete this lesson, you must add a table containing users from your own domain.</span></span> <span data-ttu-id="a8f85-108">您不需要将添加的用户名的密码。</span><span class="sxs-lookup"><span data-stu-id="a8f85-108">You will not need the passwords for the user names that will be added.</span></span> <span data-ttu-id="a8f85-109">若要使用您自己域中的少量示例用户创建一个 Employee Security 表，您需要使用粘贴功能，从 Excel 电子表格中粘贴员工数据。</span><span class="sxs-lookup"><span data-stu-id="a8f85-109">To create an Employee Security table, with a small sample of users from your own domain, you will use the Paste feature, pasting employee data from an Excel spreadsheet.</span></span> <span data-ttu-id="a8f85-110">在实际应用场景中，包含添加到模型中的用户名的表通常将使用实际数据库中的表作为数据源；例如，实际的 dimEmployee 表。</span><span class="sxs-lookup"><span data-stu-id="a8f85-110">In a real-world scenario, the table containing user names you add to a model would typically use a table from an actual database as a data source; for example, a real dimEmployee table.</span></span>  
  
 <span data-ttu-id="a8f85-111">为了实现动态安全性，你将使用两个新的 DAX 函数： [USERNAME 函数 &#40;dax&#41;](/dax/username-function-dax)和[LOOKUPVALUE function &#40;dax&#41;](/dax/lookupvalue-function-dax)。</span><span class="sxs-lookup"><span data-stu-id="a8f85-111">In order to implement dynamic security, you will use two new DAX functions: [USERNAME Function &#40;DAX&#41;](/dax/username-function-dax) and [LOOKUPVALUE Function &#40;DAX&#41;](/dax/lookupvalue-function-dax).</span></span> <span data-ttu-id="a8f85-112">在行筛选器公式中应用的这些函数在新角色中定义。</span><span class="sxs-lookup"><span data-stu-id="a8f85-112">These functions, applied in a row filter formula, are defined in a new role.</span></span> <span data-ttu-id="a8f85-113">该公式使用 LOOKUPVALUE 函数从 Employee Security 表指定一个值，然后将该值传递给 USERNAME 函数，后者指定登录用户的用户名属于此角色。</span><span class="sxs-lookup"><span data-stu-id="a8f85-113">Using the LOOKUPVALUE function, the formula specifies a value from the Employee Security table and then passes that value to the USERNAME function, which specifies the user name of the user logged on belongs to this role.</span></span> <span data-ttu-id="a8f85-114">然后，用户可以只浏览角色的行筛选器指定的数据。</span><span class="sxs-lookup"><span data-stu-id="a8f85-114">The user can then browse only data specified by the role's row filters.</span></span> <span data-ttu-id="a8f85-115">在这种情况下，您将指定销售员工只能浏览自己为其中成员的销售区域的 Internet 销售数据。</span><span class="sxs-lookup"><span data-stu-id="a8f85-115">In this scenario, you will specify that sales employees can only browse internet sales data for the sales territories in which they are a member.</span></span>  
  
 <span data-ttu-id="a8f85-116">若要完成本补充课程，您将需要完成一系列任务。</span><span class="sxs-lookup"><span data-stu-id="a8f85-116">In order to complete this supplemental lesson, you will complete a series of tasks.</span></span> <span data-ttu-id="a8f85-117">本 Adventure Works 表格模型方案特有的、但不一定适用于真实方案的任务就是以这种形式确定的。</span><span class="sxs-lookup"><span data-stu-id="a8f85-117">Those tasks that are unique to this Adventure Works tabular model scenario, but would not necessarily apply to a real-world scenario are identified as such.</span></span> <span data-ttu-id="a8f85-118">每个任务包括附加的信息用于描述任务的目的。</span><span class="sxs-lookup"><span data-stu-id="a8f85-118">Each task includes additional information describing the purpose of the task.</span></span>  
  
 <span data-ttu-id="a8f85-119">学完本课的估计时间： **30 分钟**</span><span class="sxs-lookup"><span data-stu-id="a8f85-119">Estimated time to complete this lesson: **30 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a8f85-120">先决条件</span><span class="sxs-lookup"><span data-stu-id="a8f85-120">Prerequisites</span></span>  
 <span data-ttu-id="a8f85-121">本补充课程主题是表格建模教程的一部分，应当按顺序完成。</span><span class="sxs-lookup"><span data-stu-id="a8f85-121">This supplemental lesson topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="a8f85-122">在执行本补充课程中的任务之前，应已完成前面的课程。</span><span class="sxs-lookup"><span data-stu-id="a8f85-122">Before performing the tasks in this supplemental lesson, you should have completed all previous lessons.</span></span>  
  
## <a name="add-the-dimsalesterritory-table-to-the-aw-internet-sales-tabular-model-project"></a><span data-ttu-id="a8f85-123">将 dimSalesTerritory 表添加到 AW Internet Sales 表格模型项目中</span><span class="sxs-lookup"><span data-stu-id="a8f85-123">Add the dimSalesTerritory table to the AW Internet Sales Tabular Model Project</span></span>  
 <span data-ttu-id="a8f85-124">若要为此 Adventure Works 方案实现动态安全性，您必须向模型中另外添加两个表。</span><span class="sxs-lookup"><span data-stu-id="a8f85-124">In order to implement dynamic security for this Adventure Works scenario, you must add two additional tables to your model.</span></span> <span data-ttu-id="a8f85-125">第一个要添加的表是来自同一 AdventureWorksDW 数据库的 dimSalesTerritory（作为 Sales Territory）。</span><span class="sxs-lookup"><span data-stu-id="a8f85-125">The first table you will add is dimSalesTerritory (as Sales Territory) from the same AdventureWorksDW database.</span></span> <span data-ttu-id="a8f85-126">稍后，您将会对 Sales Territory 表应用行筛选器，以定义登录用户可以浏览的特定数据。</span><span class="sxs-lookup"><span data-stu-id="a8f85-126">You will later apply a row filter to the Sales Territory table that defines the particular data the logged on user can browse.</span></span>  
  
#### <a name="to-add-the-dimsalesterritory-table"></a><span data-ttu-id="a8f85-127">添加 dimSalesTerritory 表</span><span class="sxs-lookup"><span data-stu-id="a8f85-127">To add the dimSalesTerritory table</span></span>  
  
1.  <span data-ttu-id="a8f85-128">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中，单击 **“模型”** 菜单，然后单击 **“现有连接”**。</span><span class="sxs-lookup"><span data-stu-id="a8f85-128">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click on the **Model** menu, and then click **Existing Connections**.</span></span>  
  
2.  <span data-ttu-id="a8f85-129">在“现有连接”\*\*\*\* 对话框中，确认已选中“Adventure Works DB from SQL”\*\*\*\* 数据源连接，然后单击“打开”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a8f85-129">In the **Existing Connections** dialog box, verify the **Adventure Works DB from SQL** data source connection is selected, and then click **Open**.</span></span>  
  
     <span data-ttu-id="a8f85-130">如果出现“模拟凭据”对话框，请键入在“第 2 课：添加数据”中使用的模拟凭据。</span><span class="sxs-lookup"><span data-stu-id="a8f85-130">If the Impersonation Credentials dialog box appears, type the impersonation credentials you used in Lesson 2: Add Data.</span></span>  
  
3.  <span data-ttu-id="a8f85-131">在“选择如何导入数据”\*\*\*\* 页上，保持选中“从表和视图的列表中进行选择，以便选择要导入的数据”\*\*\*\*，然后单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a8f85-131">On the **Choose How to Import the Data** page, leave **Select from a list of tables and views to choose the data to import** selected, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="a8f85-132">在“选择表和视图”\*\*\*\* 页上，选择“DimSalesTerritory”\*\*\*\* 表。</span><span class="sxs-lookup"><span data-stu-id="a8f85-132">On the **Select Tables and Views** page, select the **DimSalesTerritory** table.</span></span>  
  
5.  <span data-ttu-id="a8f85-133">在“友好名称”列中，键入 **Sales Territory**。</span><span class="sxs-lookup"><span data-stu-id="a8f85-133">In the Friendly Name column, type **Sales Territory**.</span></span>  
  
6.  <span data-ttu-id="a8f85-134">单击“预览并筛选”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a8f85-134">Click **Preview and Filter**.</span></span>  
  
7.  <span data-ttu-id="a8f85-135">取消选择“SalesTerritoryAlternateKey”\*\*\*\* 列，然后单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a8f85-135">Deselect the **SalesTerritoryAlternateKey** column, and then click **Ok**.</span></span>  
  
8.  <span data-ttu-id="a8f85-136">在“选择表和视图”\*\*\*\* 页上，单击“完成”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a8f85-136">On the **Select Tables and Views** page, click **Finish**.</span></span>  
  
     <span data-ttu-id="a8f85-137">新表将添加到模型工作区中。</span><span class="sxs-lookup"><span data-stu-id="a8f85-137">The new table will be added to the model workspace.</span></span> <span data-ttu-id="a8f85-138">源 dimSalesTerritory 表中的对象和数据随后将导入到 AW Internet Sales 表格模型中的新 Sales Territory 表中。</span><span class="sxs-lookup"><span data-stu-id="a8f85-138">Objects and data from the source dimSalesTerritory table are then imported into the new Sales Territory table in your AW Internet Sales Tabular Model.</span></span>  
  
9. <span data-ttu-id="a8f85-139">导入该表后，单击“关闭”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a8f85-139">After the table has been imported, click **Close**.</span></span>  
  
## <a name="give-the-columns-friendly-names"></a><span data-ttu-id="a8f85-140">为列指定友好名称</span><span class="sxs-lookup"><span data-stu-id="a8f85-140">Give the Columns Friendly Names</span></span>  
 <span data-ttu-id="a8f85-141">在此任务中，您将重命名 Sales Territory 表中的列，为它们指定友好名称。</span><span class="sxs-lookup"><span data-stu-id="a8f85-141">In this task, you will rename the columns in the Sales Territory table, giving them friendly names.</span></span> <span data-ttu-id="a8f85-142">并不总是要为表和/或列指定友好名称；不过这样做以后，更易于在模型设计器中导航您的模型项目，用户也更易于浏览客户端应用程序字段列表中的模型对象和数据。</span><span class="sxs-lookup"><span data-stu-id="a8f85-142">It is not always necessary to give tables and/or columns friendly names; however, it does make your model project easier to navigate in the model designer as well as for users browsing model objects and data in a client application field list.</span></span>  
  
#### <a name="to-rename-columns-in-the-sales-territory-table"></a><span data-ttu-id="a8f85-143">重命名 Sales Territory 表中的列</span><span class="sxs-lookup"><span data-stu-id="a8f85-143">To rename Columns in the Sales Territory Table</span></span>  
  
-   <span data-ttu-id="a8f85-144">在模型设计器中，重命名“Sales Territory”\*\*\*\* 表中的列：</span><span class="sxs-lookup"><span data-stu-id="a8f85-144">In the model designer, rename the columns in the **Sales Territory** table:</span></span>  
  
     <span data-ttu-id="a8f85-145">**Sales Territory**</span><span class="sxs-lookup"><span data-stu-id="a8f85-145">**Sales Territory**</span></span>  
  
    |<span data-ttu-id="a8f85-146">源名称</span><span class="sxs-lookup"><span data-stu-id="a8f85-146">Source Name</span></span>|<span data-ttu-id="a8f85-147">友好名称</span><span class="sxs-lookup"><span data-stu-id="a8f85-147">Friendly Name</span></span>|  
    |-----------------|-------------------|  
    |<span data-ttu-id="a8f85-148">SalesTerritoryKey</span><span class="sxs-lookup"><span data-stu-id="a8f85-148">SalesTerritoryKey</span></span>|<span data-ttu-id="a8f85-149">Sales Territory Id</span><span class="sxs-lookup"><span data-stu-id="a8f85-149">Sales Territory Id</span></span>|  
    |<span data-ttu-id="a8f85-150">SalesTerritoryRegion</span><span class="sxs-lookup"><span data-stu-id="a8f85-150">SalesTerritoryRegion</span></span>|<span data-ttu-id="a8f85-151">销售区域所属地区</span><span class="sxs-lookup"><span data-stu-id="a8f85-151">Sales Territory Region</span></span>|  
    |<span data-ttu-id="a8f85-152">SalesTerritoryCountry</span><span class="sxs-lookup"><span data-stu-id="a8f85-152">SalesTerritoryCountry</span></span>|<span data-ttu-id="a8f85-153">销售区域所属国家/地区</span><span class="sxs-lookup"><span data-stu-id="a8f85-153">Sales Territory Country</span></span>|  
    |<span data-ttu-id="a8f85-154">SalesTerritoryGroup</span><span class="sxs-lookup"><span data-stu-id="a8f85-154">SalesTerritoryGroup</span></span>|<span data-ttu-id="a8f85-155">销售区域组</span><span class="sxs-lookup"><span data-stu-id="a8f85-155">Sales Territory Group</span></span>|  
  
## <a name="add-a-table-with-user-name-data"></a><span data-ttu-id="a8f85-156">添加包含用户名数据的表</span><span class="sxs-lookup"><span data-stu-id="a8f85-156">Add a table with user name data</span></span>  
 <span data-ttu-id="a8f85-157">由于 AdventureWorksDW 示例数据库中的 dimEmployee 表包含来自 AdventureWorks 域的用户，而您自己的环境中不存在这些用户名，因此必须在您的模型中创建一个表，包含您组织中的少量实际示例用户（三个用户）。</span><span class="sxs-lookup"><span data-stu-id="a8f85-157">Because the dimEmployee table in the AdventureWorksDW sample database contains users from the AdventureWorks domain, and those user names do not exist in your own environment, you must create a table in your model that contains a small sample (three) of actual users from your organization.</span></span> <span data-ttu-id="a8f85-158">然后，将这些用户作为成员添加到新角色中。</span><span class="sxs-lookup"><span data-stu-id="a8f85-158">You will then add these users as members to the new role.</span></span> <span data-ttu-id="a8f85-159">您不需要示例用户名的密码，但需要来自您自己域的实际 Windows 用户名。</span><span class="sxs-lookup"><span data-stu-id="a8f85-159">You do not need the passwords for the sample user names, but you will need actual Windows user names from your own domain.</span></span>  
  
#### <a name="to-add-an-employee-security-table"></a><span data-ttu-id="a8f85-160">添加 Employee Security 表</span><span class="sxs-lookup"><span data-stu-id="a8f85-160">To add an Employee Security table</span></span>  
  
1.  <span data-ttu-id="a8f85-161">打开 Microsoft Excel 并创建新的工作表。</span><span class="sxs-lookup"><span data-stu-id="a8f85-161">Open Microsoft Excel, creating a new worksheet.</span></span>  
  
2.  <span data-ttu-id="a8f85-162">复制以下表（包括标题行），然后将其粘贴到该工作表。</span><span class="sxs-lookup"><span data-stu-id="a8f85-162">Copy the following table, including the header row, and then paste it into the worksheet.</span></span>  
  
    |<span data-ttu-id="a8f85-163">Employee Id</span><span class="sxs-lookup"><span data-stu-id="a8f85-163">Employee Id</span></span>|<span data-ttu-id="a8f85-164">Sales Territory Id</span><span class="sxs-lookup"><span data-stu-id="a8f85-164">Sales Territory Id</span></span>|<span data-ttu-id="a8f85-165">名字</span><span class="sxs-lookup"><span data-stu-id="a8f85-165">First Name</span></span>|<span data-ttu-id="a8f85-166">姓氏</span><span class="sxs-lookup"><span data-stu-id="a8f85-166">Last Name</span></span>|<span data-ttu-id="a8f85-167">Login Id</span><span class="sxs-lookup"><span data-stu-id="a8f85-167">Login Id</span></span>|  
    |-----------------|------------------------|----------------|---------------|--------------|  
    |<span data-ttu-id="a8f85-168">1</span><span class="sxs-lookup"><span data-stu-id="a8f85-168">1</span></span>|<span data-ttu-id="a8f85-169">2</span><span class="sxs-lookup"><span data-stu-id="a8f85-169">2</span></span>|\<user first name>|\<user last name>|\<domain\username>|  
    |<span data-ttu-id="a8f85-170">1</span><span class="sxs-lookup"><span data-stu-id="a8f85-170">1</span></span>|<span data-ttu-id="a8f85-171">3</span><span class="sxs-lookup"><span data-stu-id="a8f85-171">3</span></span>|\<user first name>|\<user last name>|\<domain\username>|  
    |<span data-ttu-id="a8f85-172">2</span><span class="sxs-lookup"><span data-stu-id="a8f85-172">2</span></span>|<span data-ttu-id="a8f85-173">4</span><span class="sxs-lookup"><span data-stu-id="a8f85-173">4</span></span>|\<user first name>|\<user last name>|\<domain\username>|  
    |<span data-ttu-id="a8f85-174">3</span><span class="sxs-lookup"><span data-stu-id="a8f85-174">3</span></span>|<span data-ttu-id="a8f85-175">5</span><span class="sxs-lookup"><span data-stu-id="a8f85-175">5</span></span>|\<user first name>|\<user last name>|\<domain\username>|  
  
3.  <span data-ttu-id="a8f85-176">在新工作表中，将 first name、last name 和 domain\username 替换为您组织中的三个用户的姓名和登录 ID。</span><span class="sxs-lookup"><span data-stu-id="a8f85-176">In the new worksheet, replace the first name, last name, and domain\username with the names and login ids of three users in your organization.</span></span> <span data-ttu-id="a8f85-177">将同一个用户置于前两行，Employee Id 为 1。</span><span class="sxs-lookup"><span data-stu-id="a8f85-177">Put the same user on the first two rows, for Employee Id 1.</span></span> <span data-ttu-id="a8f85-178">这表示此用户属于多个销售区域。</span><span class="sxs-lookup"><span data-stu-id="a8f85-178">This will show this user belongs to more than one sales territory.</span></span> <span data-ttu-id="a8f85-179">保持 Employee Id 和 Sales Territory Id 字段不变。</span><span class="sxs-lookup"><span data-stu-id="a8f85-179">Leave the Employee Id and Sales Territory Id fields as they are.</span></span>  
  
4.  <span data-ttu-id="a8f85-180">将工作表另存为 `Sample Employee` 。</span><span class="sxs-lookup"><span data-stu-id="a8f85-180">Save the worksheet as `Sample Employee`.</span></span>  
  
5.  <span data-ttu-id="a8f85-181">在该工作表中，选择包含员工数据的所有单元（包括标题），在所选数据上右键单击，然后单击“复制”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a8f85-181">In the worksheet, select all of the cells with employee data, including the headers, then right click the selected data, and then click **Copy**.</span></span>  
  
6.  <span data-ttu-id="a8f85-182">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 中，单击“编辑”\*\*\*\* 菜单，然后单击“粘贴”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a8f85-182">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click the **Edit** menu, and then click **Paste**.</span></span>  
  
     <span data-ttu-id="a8f85-183">如果“粘贴”灰显，请单击模型设计器窗口中的任意表中的任意列，然后依次单击“编辑”\*\*\*\* 菜单和“粘贴”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a8f85-183">If Paste is greyed out, click any column in any table in the model designer window, and then click the **Edit** menu, and then click **Paste**.</span></span>  
  
7.  <span data-ttu-id="a8f85-184">在 "**粘贴预览**" 对话框中的 "**表名**" 中，键入 `Employee Security` 。</span><span class="sxs-lookup"><span data-stu-id="a8f85-184">In the **Paste Preview** dialog box, in **Table Name**, type `Employee Security`.</span></span>  
  
8.  <span data-ttu-id="a8f85-185">在“要粘贴的数据”\*\*\*\* 中，确认数据包含“Sample Employee”工作表中的所有用户数据和标题。</span><span class="sxs-lookup"><span data-stu-id="a8f85-185">In **Data to be pasted**, verify the data includes all of the user data and headers from the Sample Employee worksheet.</span></span>  
  
9. <span data-ttu-id="a8f85-186">检查是否已选中“使用第一行作为列标题”，并单击“确定”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="a8f85-186">Verify **Use first row as column headers** is checked, and then click **Ok**.</span></span>  
  
     <span data-ttu-id="a8f85-187">包含从 Sample Employee 工作表复制的员工数据的名为“Employee Security”的新表即已创建。</span><span class="sxs-lookup"><span data-stu-id="a8f85-187">A new table named Employee Security with employee data copied from the Sample Employee worksheet is created.</span></span>  
  
## <a name="create-relationships-between-internet-sales-geography-and-sales-territory-table"></a><span data-ttu-id="a8f85-188">在“Internet Sales”、“Geography”和“Sales Territory”表之间创建关系</span><span class="sxs-lookup"><span data-stu-id="a8f85-188">Create Relationships Between Internet Sales, Geography, and Sales Territory table</span></span>  
 <span data-ttu-id="a8f85-189">"Internet 销售"、"地域" 和 "销售区域" 表都包含一个公共列、销售区域 Id。"销售区域" 表中的 "销售区域 Id" 列包含每个销售区域的不同 Id 值。</span><span class="sxs-lookup"><span data-stu-id="a8f85-189">The Internet Sales, Geography, and Sales Territory table all contain a common column, Sales Territory Id. The Sales Territory Id column in the Sales Territory table contains values with a different Id for each sales territory.</span></span>  
  
#### <a name="to-create-relationships-between-the-internet-sales-geography-and-the-sales-territory-table"></a><span data-ttu-id="a8f85-190">在 Internet Sales、Geography 和 Sales Territory 表之间创建关系</span><span class="sxs-lookup"><span data-stu-id="a8f85-190">To create relationships between the Internet Sales, Geography, and the Sales Territory table</span></span>  
  
1.  <span data-ttu-id="a8f85-191">在模型设计器的“关系图视图”中，在“Geography”\*\*\*\* 表中单击并按住“Sales Territory Id”\*\*\*\* 列，将光标拖到“Sales Territory”\*\*\*\* 表中的“Sales Territory Id”\*\*\*\* 列，然后释放。</span><span class="sxs-lookup"><span data-stu-id="a8f85-191">In the model designer, in Diagram View, in the **Geography** table, click and hold on the **Sales Territory Id** column, then drag the cursor to the **Sales Territory Id** column in the **Sales Territory** table, and then release.</span></span>  
  
2.  <span data-ttu-id="a8f85-192">在“Internet Sales”\*\*\*\* 表中单击并按住“Sales Territory Id”\*\*\*\* 列，将光标拖到“Sales Territory”\*\*\*\* 表中的“Sales Territory Id”\*\*\*\* 列，然后释放。</span><span class="sxs-lookup"><span data-stu-id="a8f85-192">In the **Internet Sales** table, click and hold on the **Sales Territory Id** column, then drag the cursor to the **Sales Territory Id** column in the **Sales Territory** table, and then release.</span></span>  
  
     <span data-ttu-id="a8f85-193">注意，此关系的 Active 属性为 False，表示它不活动。</span><span class="sxs-lookup"><span data-stu-id="a8f85-193">Notice the Active property for this relationship is False, meaning it is inactive.</span></span> <span data-ttu-id="a8f85-194">这是因为 Internet Sales 表已有另一个在度量值中使用的活动关系。</span><span class="sxs-lookup"><span data-stu-id="a8f85-194">This is because the Internet Sales table already has another active relationship that is used in measures.</span></span>  
  
## <a name="hide-the-employee-security-table-from-client-applications"></a><span data-ttu-id="a8f85-195">在客户端应用程序中隐藏 Employee Security 表</span><span class="sxs-lookup"><span data-stu-id="a8f85-195">Hide the Employee Security Table from Client Applications</span></span>  
 <span data-ttu-id="a8f85-196">在此任务中，您将隐藏 Employee Security 表，使其不显示在客户端应用程序的字段列表中。</span><span class="sxs-lookup"><span data-stu-id="a8f85-196">In this task, you will hide the Employee Security table, keeping it from appearing in a client application's field list.</span></span> <span data-ttu-id="a8f85-197">请注意，隐藏某个表并不会对它提供保护。</span><span class="sxs-lookup"><span data-stu-id="a8f85-197">Keep in-mind that hiding a table does not secure it.</span></span> <span data-ttu-id="a8f85-198">用户仍可以查询 Employee Security 表数据，如果他们知道怎么查询的话。</span><span class="sxs-lookup"><span data-stu-id="a8f85-198">Users can still query Employee Security table data if they know how.</span></span> <span data-ttu-id="a8f85-199">若要保护 Employee Security 表数据的安全，以阻止用户能够查询其任何数据，您将需要在后面的任务中应用筛选器。</span><span class="sxs-lookup"><span data-stu-id="a8f85-199">In order to secure the Employee Security table data, preventing users from being able to query any of its data, you will apply a filter in a later task.</span></span>  
  
#### <a name="to-hide-the-employee-table-from-client-applications"></a><span data-ttu-id="a8f85-200">在客户端应用程序中隐藏 Employee 表</span><span class="sxs-lookup"><span data-stu-id="a8f85-200">To hide the Employee Table from client applications</span></span>  
  
-   <span data-ttu-id="a8f85-201">在模型设计器的“关系图视图”中，右键单击“员工”表标题，并单击“从客户端工具中隐藏”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="a8f85-201">In the model designer, in Diagram View, right-click the **Employee** table heading, and then click **Hide from Client Tools**.</span></span>  
  
## <a name="create-a-sales-employees-by-territory-user-role"></a><span data-ttu-id="a8f85-202">创建“区域销售员工”用户角色</span><span class="sxs-lookup"><span data-stu-id="a8f85-202">Create a Sales Employees by Territory user role</span></span>  
 <span data-ttu-id="a8f85-203">在此任务中，您将创建一个新的用户角色。</span><span class="sxs-lookup"><span data-stu-id="a8f85-203">In this task, you will create a new user role.</span></span> <span data-ttu-id="a8f85-204">此角色将包含一个行筛选器，用于定义 Sales Territory 表的哪些行对用户可见。</span><span class="sxs-lookup"><span data-stu-id="a8f85-204">This role will include a row filter defining which rows of the Sales Territory table are visible to users.</span></span> <span data-ttu-id="a8f85-205">然后，此筛选器将在一对多关系方向中应用于与 Sales Territory 相关的所有其他表。</span><span class="sxs-lookup"><span data-stu-id="a8f85-205">The filter is then applied in the one-to many relationship direction to all other tables related to Sales Territory.</span></span> <span data-ttu-id="a8f85-206">您还将应用一个简单的筛选器，使属于此角色成员的所有用户都无法查询整个 Employee Security 表。</span><span class="sxs-lookup"><span data-stu-id="a8f85-206">You will also apply a simple filter that secures the entire Employee Security table from being queryable by any user that is a member of the role.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a8f85-207">在本课程中创建的“区域销售员工”角色将成员限制为只能浏览（或查询）他们所属销售区域的销售数据。</span><span class="sxs-lookup"><span data-stu-id="a8f85-207">The Sales Employees by Territory role you create in this lesson restricts members to browse (or query) only sales data for the sales territory to which they belong.</span></span> <span data-ttu-id="a8f85-208">如果将某一用户添加为 Sales Employees by Territory 角色的成员，而该用户也同时作为在 [第 12 课：创建角色](../analysis-services/lesson-11-create-roles.md)中创建的角色的成员，则将获得权限组合。</span><span class="sxs-lookup"><span data-stu-id="a8f85-208">If you add a user as a member to the Sales Employees by Territory role that also exists as a member in a role created in [Lesson 12: Create Roles](../analysis-services/lesson-11-create-roles.md), you will get a combination of permissions.</span></span> <span data-ttu-id="a8f85-209">如果用户是多个角色的成员，则针对每个角色定义的权限和行筛选器可以累计。</span><span class="sxs-lookup"><span data-stu-id="a8f85-209">When a user is a member of multiple roles, the permissions, and row filters defined for each role are cumulative.</span></span> <span data-ttu-id="a8f85-210">也就是说，该用户将具有角色组合所确定的更大权限。</span><span class="sxs-lookup"><span data-stu-id="a8f85-210">That is, the user will have the greater permissions determined by the combination of roles.</span></span>  
  
#### <a name="to-create-a-sales-employees-by-territory-user-role"></a><span data-ttu-id="a8f85-211">创建“区域销售员工”用户角色</span><span class="sxs-lookup"><span data-stu-id="a8f85-211">To create a Sales Employees by Territory user role</span></span>  
  
1.  <span data-ttu-id="a8f85-212">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 中，单击“模型”\*\*\*\* 菜单，然后单击“角色”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a8f85-212">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click the **Model** menu, and then click **Roles**.</span></span>  
  
2.  <span data-ttu-id="a8f85-213">在 **“角色管理器”** 对话框中，单击 **“新建”**。</span><span class="sxs-lookup"><span data-stu-id="a8f85-213">In the **Role Manager** dialog box, click **New**.</span></span>  
  
     <span data-ttu-id="a8f85-214">随后会将一个“无”权限的新角色添加到列表中。</span><span class="sxs-lookup"><span data-stu-id="a8f85-214">A new role with the None permission is added to the list.</span></span>  
  
3.  <span data-ttu-id="a8f85-215">单击新角色，然后在 "**名称**" 列中，将角色重命名为 `Sales Employees by Territory` 。</span><span class="sxs-lookup"><span data-stu-id="a8f85-215">Click on the new role, and then in the **Name** column, rename the role to `Sales Employees by Territory`.</span></span>  
  
4.  <span data-ttu-id="a8f85-216">在“权限”列中，单击下拉列表，并选择“读取”权限。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="a8f85-216">In the **Permissions** column, click the dropdown list, and then select the **Read** permission.</span></span>  
  
5.  <span data-ttu-id="a8f85-217">单击“成员”\*\*\*\* 选项卡，然后单击“添加”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a8f85-217">Click on the **Members** tab, and then click **Add**.</span></span>  
  
6.  <span data-ttu-id="a8f85-218">在“选择用户或组”\*\*\*\* 对话框的“输入要选择的对象名称”\*\*\*\* 中，键入在创建“Employee Security”表时使用的第一个示例用户名。</span><span class="sxs-lookup"><span data-stu-id="a8f85-218">In the **Select User or Group** dialog box, in **Enter the object named to select**, type the first sample user name you used when creating the Employee Security table.</span></span> <span data-ttu-id="a8f85-219">单击“检查名称”验证该用户名是否有效，并单击“确定”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="a8f85-219">Click **Check Names** to verify the user name is valid, and then click **Ok**.</span></span>  
  
     <span data-ttu-id="a8f85-220">重复此步骤，添加您在创建 Employee Security 表时使用的其他示例用户名。</span><span class="sxs-lookup"><span data-stu-id="a8f85-220">Repeat this step, adding the other sample user names you used when creating the Employee Security table.</span></span>  
  
7.  <span data-ttu-id="a8f85-221">单击“行筛选器”\*\*\*\* 选项卡。</span><span class="sxs-lookup"><span data-stu-id="a8f85-221">Click on the **Row Filters** tab.</span></span>  
  
8.  <span data-ttu-id="a8f85-222">对于 `Employee Security` 表，在 " **DAX 筛选器**" 列中键入以下公式。</span><span class="sxs-lookup"><span data-stu-id="a8f85-222">For the `Employee Security` table, in the **DAX Filter** column, type the following formula.</span></span>  
  
     `=FALSE()`  
  
     <span data-ttu-id="a8f85-223">在您完成公式的建立后，按 Enter。</span><span class="sxs-lookup"><span data-stu-id="a8f85-223">When you have finished building the formula, press ENTER.</span></span>  
  
     <span data-ttu-id="a8f85-224">此公式指定所有列均解析为 False 布尔条件；因此，Sales Employees by Territory 用户角色的成员不能查询 Employee Security 表的任何列。</span><span class="sxs-lookup"><span data-stu-id="a8f85-224">This formula specifies that all columns resolve to the false Boolean condition; therefore, no columns for the Employee Security table can be queried by a member of the Sales Employees by Territory user role.</span></span>  
  
9. <span data-ttu-id="a8f85-225">对于“Sales Territory”\*\*\*\* 表，键入以下公式。</span><span class="sxs-lookup"><span data-stu-id="a8f85-225">For the **Sales Territory** table, type the following formula.</span></span>  
  
     `='Sales Territory'[Sales Territory Id]=LOOKUPVALUE('Employee Security'[Sales Territory Id], 'Employee Security'[Login Id], USERNAME(), 'Employee Security'[Sales Territory Id], 'Sales Territory'[Sales Territory Id])`  
  
     <span data-ttu-id="a8f85-226">在您完成公式的建立后，按 Enter。</span><span class="sxs-lookup"><span data-stu-id="a8f85-226">When you have finished building the formula, press ENTER.</span></span>  
  
     <span data-ttu-id="a8f85-227">在此公式中，LOOKUPVALUE 函数返回 Employee Security[Sales Territory Id] 列的所有值，其中 Employee Security[Login Id] 与当前登录的 Windows 用户名相同，Employee Security[Sales Territory Id] 与 Sales Territory[Sales Territory Id] 相同。</span><span class="sxs-lookup"><span data-stu-id="a8f85-227">In this formula, the LOOKUPVALUE function returns all values for the Employee Security[Sales Territory Id] column, where the Employee Security[Login Id] is the same as the current logged on Windows user name, and Employee Security[Sales Territory Id] is the same as the Sales Territory[Sales Territory Id].</span></span>  
  
     <span data-ttu-id="a8f85-228">然后，使用 LOOKUPVALUE 返回的 Sales Territory ID 集来限制在 Sales Territory 表中显示的行。</span><span class="sxs-lookup"><span data-stu-id="a8f85-228">The set of Sales Territory IDs returned by LOOKUPVALUE is then used to restrict the rows shown in the Sales Territory table.</span></span> <span data-ttu-id="a8f85-229">仅显示行的 Sales Territory ID 位于 LOOKUPVALUE 函数返回的 ID 集中的行。</span><span class="sxs-lookup"><span data-stu-id="a8f85-229">Only rows where the Sales Territory ID for the row is in the set of IDs returned by the LOOKUPVALUE function are displayed.</span></span>  
  
10. <span data-ttu-id="a8f85-230">在“角色管理器”对话框中，单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a8f85-230">In the Role Manager dialog box, click **Ok**.</span></span>  
  
## <a name="test-the-sales-employees-by-territory-user-role"></a><span data-ttu-id="a8f85-231">测试“区域销售员工”用户角色</span><span class="sxs-lookup"><span data-stu-id="a8f85-231">Test the Sales Employees by Territory User Role</span></span>  
 <span data-ttu-id="a8f85-232">在此任务中，您将使用 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 中的“在 Excel 中分析”功能来测试 Sales Employees by Territory 用户角色的效用。</span><span class="sxs-lookup"><span data-stu-id="a8f85-232">In this task, you will use the Analyze in Excel feature in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] to test the efficacy of the Sales Employees by Territory user role.</span></span> <span data-ttu-id="a8f85-233">您将指定已添加到 Employee Security 表且作为此角色的成员的用户名之一。</span><span class="sxs-lookup"><span data-stu-id="a8f85-233">You will specify one of the user names you added to the Employee Security table and as a member of the role.</span></span> <span data-ttu-id="a8f85-234">然后，此用户名将用作在 Excel 和模型之间创建的连接中的有效用户名。</span><span class="sxs-lookup"><span data-stu-id="a8f85-234">This user name will then be used as the effective user name in the connection created between Excel and the model.</span></span>  
  
#### <a name="to-test-the-sales-employees-by-territory-user-role"></a><span data-ttu-id="a8f85-235">测试“区域销售员工”用户角色</span><span class="sxs-lookup"><span data-stu-id="a8f85-235">To test the Sales Employees by Territory user role</span></span>  
  
1.  <span data-ttu-id="a8f85-236">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中，单击 **“模型”** 菜单，然后单击 **“在 Excel 中分析”**。</span><span class="sxs-lookup"><span data-stu-id="a8f85-236">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click the **Model** menu, and then click **Analyze in Excel**.</span></span>  
  
2.  <span data-ttu-id="a8f85-237">在“在 Excel 中分析”对话框中的“指定用于连接到模型的用户名或角色”内，选择“其他 Windows 用户”，然后单击“浏览”。\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="a8f85-237">In the **Analyze in Excel** dialog box, in **Specify the user name or role to use to connect to the model**, select **Other Windows User**, and then click **Browse**.</span></span>  
  
3.  <span data-ttu-id="a8f85-238">在“选择用户或组”\*\*\*\* 对话框的“输入要选择的对象名称”\*\*\*\* 中，键入包括在“Employee”表中的其中一个用户名，然后单击“检查名称”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a8f85-238">In the **Select User or Group** dialog box, in **Enter the object name to select**, type one of the user names you included in the Employee table, and then click **Check Names**.</span></span>  
  
4.  <span data-ttu-id="a8f85-239">单击“确定”关闭“选择用户或组”对话框，并单击“确定”关闭“在 Excel 中分析”对话框。\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="a8f85-239">Click **Ok** to close the **Select User or Group** dialog box, and then click **Ok** to close the **Analyze in Excel** dialog box.</span></span>  
  
     <span data-ttu-id="a8f85-240">Excel 将打开一个新的工作簿。</span><span class="sxs-lookup"><span data-stu-id="a8f85-240">Excel will open with a new workbook.</span></span> <span data-ttu-id="a8f85-241">将自动创建一个数据透视表。</span><span class="sxs-lookup"><span data-stu-id="a8f85-241">A Pivot table is automatically created.</span></span> <span data-ttu-id="a8f85-242">数据透视表字段列表包含您的新模型中提供的大多数数据字段。</span><span class="sxs-lookup"><span data-stu-id="a8f85-242">The Pivot Table Field List includes most of the data fields available in your new model.</span></span>  
  
     <span data-ttu-id="a8f85-243">请注意，Employee Security 表在数据透视表字段列表中不可见。</span><span class="sxs-lookup"><span data-stu-id="a8f85-243">Notice the Employee Security table is not visible in the Pivot Table Field List.</span></span> <span data-ttu-id="a8f85-244">这是因为您在前一任务中选择了从客户端工具隐藏此表。</span><span class="sxs-lookup"><span data-stu-id="a8f85-244">This is because you chose to hide this table from client tools in a previous task.</span></span>  
  
5.  <span data-ttu-id="a8f85-245">在“数据透视表字段”\*\*\*\* 列表中，在“∑ Internet Sales”\*\*\*\*（度量值）中选择“Internet Total Sales”\*\*\*\* 度量值。</span><span class="sxs-lookup"><span data-stu-id="a8f85-245">In the **Pivot Table Field** list, in **∑ Internet Sales** (measures), select the **Internet Total Sales** measure.</span></span> <span data-ttu-id="a8f85-246">该度量值将会输入到“值”\*\*\*\* 字段中。</span><span class="sxs-lookup"><span data-stu-id="a8f85-246">The measure will be entered into the **Values** fields.</span></span>  
  
6.  <span data-ttu-id="a8f85-247">在“数据透视表字段”\*\*\*\* 列表中，从“Sales Territory”\*\*\*\* 表中选择“Sales Territory Id”\*\*\*\* 列。</span><span class="sxs-lookup"><span data-stu-id="a8f85-247">In the **Pivot Table Field** list, select the **Sales Territory Id** column from the **Sales Territory** table.</span></span> <span data-ttu-id="a8f85-248">该列将会输入到“行标签”\*\*\*\* 字段中。</span><span class="sxs-lookup"><span data-stu-id="a8f85-248">The column will be entered into the **Row Labels** fields.</span></span>  
  
     <span data-ttu-id="a8f85-249">请注意，只显示所用有效用户名所属的一个区域的 Internet 销售数字。</span><span class="sxs-lookup"><span data-stu-id="a8f85-249">Notice Internet sales figures appear only for the one region to which the effective user name you used belongs.</span></span> <span data-ttu-id="a8f85-250">如果您选择了另一列，例如，从 Geography 表选择 City 列作为“行标签”字段，则仅显示有效用户所属的销售区域中的城市。</span><span class="sxs-lookup"><span data-stu-id="a8f85-250">If you select another column; for example, City, from the Geography table as Row Label field, only cities in the sales territory to which the effective user belongs are displayed.</span></span>  
  
     <span data-ttu-id="a8f85-251">此用户不能浏览或查询其所属的区域之外的区域的任何 Internet 销售数据，因为在 Sales Employees by Territory 用户角色中为 Sales Territory 表定义的行筛选器有效地保护了与其他销售区域相关的所有数据。</span><span class="sxs-lookup"><span data-stu-id="a8f85-251">This user cannot browse or query any Internet sales data for territories other than the one they belong because the row filter defined for the Sales Territory table in the Sales Employees by Territory user role effectively secures data for all data related to other sales territories.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8f85-252">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a8f85-252">See Also</span></span>  
 <span data-ttu-id="a8f85-253">[USERNAME 函数 &#40;DAX&#41;](/dax/username-function-dax) </span><span class="sxs-lookup"><span data-stu-id="a8f85-253">[USERNAME Function &#40;DAX&#41;](/dax/username-function-dax) </span></span>  
 <span data-ttu-id="a8f85-254">[&#40;DAX&#41;的 LOOKUPVALUE 函数](/dax/lookupvalue-function-dax) </span><span class="sxs-lookup"><span data-stu-id="a8f85-254">[LOOKUPVALUE Function &#40;DAX&#41;](/dax/lookupvalue-function-dax) </span></span>  
 [<span data-ttu-id="a8f85-255">&#40;DAX&#41;的 CUSTOMDATA 函数</span><span class="sxs-lookup"><span data-stu-id="a8f85-255">CUSTOMDATA Function &#40;DAX&#41;</span></span>](/dax/customdata-function-dax)  
  
  
