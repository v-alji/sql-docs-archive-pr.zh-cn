---
title: 在 SharePoint 集成模式下将 Office 数据连接 ( .odc) 与报表 (Reporting Services) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Office Data Connection (.odc) files
- SharePoint integration [Reporting Services], shared data sources
- .odc files
ms.assetid: e8d6896d-f886-4390-8b5d-96f0a50c250c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d795c46f46b45511079ac03add2d18214ac54489
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577301"
---
# <a name="use-an-office-data-connection-odc-with-reports-reporting-services-in-sharepoint-integrated-mode"></a><span data-ttu-id="3e6be-102">将 Office 数据连接 (.odc) 用于报表（SharePoint 集成模式下的 Reporting Services）</span><span class="sxs-lookup"><span data-stu-id="3e6be-102">Use an Office Data Connection (.odc) with Reports (Reporting Services in SharePoint Integrated Mode)</span></span>
  <span data-ttu-id="3e6be-103">对于局限性方案而言，可以使用现有 Office 数据连接 (.odc) 文件来为 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 报表提供连接信息。</span><span class="sxs-lookup"><span data-stu-id="3e6be-103">For limited scenarios, you can use an existing Office Data Connection (.odc) file to provide connection information to a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report.</span></span> <span data-ttu-id="3e6be-104">在创建共享数据源时，可用 .odc 文件替代 .rsds 文件。</span><span class="sxs-lookup"><span data-stu-id="3e6be-104">An .odc file can be used in place of an .rsds file when you create a shared data source.</span></span> <span data-ttu-id="3e6be-105">报表服务器使用 .odc 文件的方式与使用 .rsds 文件的方式相同；它读取文件以获得数据源类型、连接字符串以及凭据信息。</span><span class="sxs-lookup"><span data-stu-id="3e6be-105">The report server uses an .odc file in the same way it uses an .rsds file; it reads the file for the data source type, a connection string, and credential information.</span></span>  
  
 <span data-ttu-id="3e6be-106">并非所有的 .odc 文件均可用于 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 报表。</span><span class="sxs-lookup"><span data-stu-id="3e6be-106">Not all .odc files can be used with a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report.</span></span> <span data-ttu-id="3e6be-107">数据处理扩展插件和报表及 .odc 文件的特征决定了是否可以使用某个 .odc 文件：</span><span class="sxs-lookup"><span data-stu-id="3e6be-107">The data processing extension and characteristics of the report and .odc file determine whether an .odc can be used:</span></span>  
  
-   <span data-ttu-id="3e6be-108">报表必须设计为与 OLE DB 或 ODBC 数据访问接口配合使用。</span><span class="sxs-lookup"><span data-stu-id="3e6be-108">The report must be designed to work with an OLE DB or ODBC data provider.</span></span> <span data-ttu-id="3e6be-109">如果使用不同的数据处理扩展插件来创建报表，报表或其查询则可能包含 OLE DB 或 ODBC 数据提供程序所不支持的功能。</span><span class="sxs-lookup"><span data-stu-id="3e6be-109">If you used a different data processing extension to create the report, the report or its queries might include functionality that is not supported by the OLE DB or ODBC data provider.</span></span>  
  
-   <span data-ttu-id="3e6be-110">.odc 文件必须包含所需元素和结构。</span><span class="sxs-lookup"><span data-stu-id="3e6be-110">The .odc file must have the expected elements and structure.</span></span> <span data-ttu-id="3e6be-111">必须在文件中显式设置数据访问接口和凭据设置，以使报表服务器能够读取这些设置。</span><span class="sxs-lookup"><span data-stu-id="3e6be-111">The data provider and credential settings must be set explicitly in the file so that they can be read by the report server.</span></span> <span data-ttu-id="3e6be-112">设置这些值的最佳方式是：在将 .odc 文件上载到 SharePoint 库之前将该文件导出。</span><span class="sxs-lookup"><span data-stu-id="3e6be-112">The best way to set these values is to export the .odc file before uploading it to the SharePoint library.</span></span>  
  
-   <span data-ttu-id="3e6be-113">.odc 文件必须指定一个 OLE DB 或 ODBC 连接类型。</span><span class="sxs-lookup"><span data-stu-id="3e6be-113">The .odc file must specify a connection type of OLE DB or ODBC.</span></span>  
  
-   <span data-ttu-id="3e6be-114">.odc 文件必须指定一个连接字符串。</span><span class="sxs-lookup"><span data-stu-id="3e6be-114">The .odc file must specify a connection string.</span></span>  
  
-   <span data-ttu-id="3e6be-115">凭据可设置为 `None`、`Stored` 或 `Integrated`。</span><span class="sxs-lookup"><span data-stu-id="3e6be-115">Credentials can be set to `None`, `Stored`, or `Integrated`.</span></span> <span data-ttu-id="3e6be-116">如果将凭据方法设置为 `Stored`，则报表服务器将提示用户提供凭据，而不要使用已存储凭据。</span><span class="sxs-lookup"><span data-stu-id="3e6be-116">If the credentials method is set to `Stored`, the report server will prompt the user for credentials instead of using the stored credentials.</span></span> <span data-ttu-id="3e6be-117">报表服务器不能按照 .odc 文件中的定义使用已存储凭据。</span><span class="sxs-lookup"><span data-stu-id="3e6be-117">The report server cannot use stored credentials as defined in the .odc file.</span></span>  
  
-   <span data-ttu-id="3e6be-118">数据源所具有的架构必须与创建报表时使用的架构相同。</span><span class="sxs-lookup"><span data-stu-id="3e6be-118">The data source must have schema that is identical to the one used to create the report.</span></span> <span data-ttu-id="3e6be-119">如果数据结构不同，报表将无法运行。</span><span class="sxs-lookup"><span data-stu-id="3e6be-119">If the data structures are different, the report will not run.</span></span>  
  
-   <span data-ttu-id="3e6be-120">必须在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office 2007 中创建 .odc 文件（早期版本的 .odc 文件与报表定义文件不兼容）。</span><span class="sxs-lookup"><span data-stu-id="3e6be-120">The .odc file must be created in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office 2007 (older versions of .odc are not compatible with report definition files).</span></span>  
  
 <span data-ttu-id="3e6be-121">如果 .odc 文件指定的连接指向不能在报表服务器上进行处理的数据源，那么即便 .odc 数据源类型与支持的数据源类型相似，也不能使用该 .odc 文件。</span><span class="sxs-lookup"><span data-stu-id="3e6be-121">You cannot use .odc files that specify connections to data sources that cannot be processed on a report server, even if the .odc data source types look similar to supported data source types.</span></span> <span data-ttu-id="3e6be-122">具体而言，如果在 Microsoft Excel 2007 中创建了 .odc 文件，而该文件从 Microsoft Access、Web 或文本文件检索数据，则不能使用该 .odc 文件来为报表提供数据。</span><span class="sxs-lookup"><span data-stu-id="3e6be-122">Specifically, if you created an .odc file in Microsoft Excel 2007 that retrieves data from Microsoft Access, the Web, or a text file, you cannot use that .odc file to provide data to a report.</span></span>  
  
 <span data-ttu-id="3e6be-123">报表生成器报表和模型不能与 .odc 文件配合使用。</span><span class="sxs-lookup"><span data-stu-id="3e6be-123">Report Builder reports and models do not work with .odc file.</span></span> <span data-ttu-id="3e6be-124">不能使用 .odc 文件生成模型，且不能将模型配置为使用链接到 .odc 文件的共享数据源。</span><span class="sxs-lookup"><span data-stu-id="3e6be-124">You cannot use an .odc file to generate a model, and you cannot configure the model to use a shared data source that links to an .odc file.</span></span>  
  
 <span data-ttu-id="3e6be-125">如果不熟悉 .odc 文件，可以使用以下说明来创建并导出文件。</span><span class="sxs-lookup"><span data-stu-id="3e6be-125">If you are not familiar with .odc files, you can use the following instructions to create and export one.</span></span> <span data-ttu-id="3e6be-126">为 OLE DB 数据源创建 .odc 文件的一种简便方法就是使用 Excel 2007 和数据连接向导。</span><span class="sxs-lookup"><span data-stu-id="3e6be-126">One easy way to create an .odc file for an OLE DB data source is to use Excel 2007 and the Data Connection Wizard.</span></span> <span data-ttu-id="3e6be-127">注意：向导不会创建数据源，您必须拥有已定义的外部数据源。</span><span class="sxs-lookup"><span data-stu-id="3e6be-127">Note that the wizard does not create a data source; you must have an external data source that is already defined.</span></span>  
  
 <span data-ttu-id="3e6be-128">只有在现有 .odc 文件与报表和查询完全兼容的情况下，才能使用现有 .odc 文件。</span><span class="sxs-lookup"><span data-stu-id="3e6be-128">An existing .odc file should only be used if it is fully compatible with the report and queries.</span></span> <span data-ttu-id="3e6be-129">如果遇到需要对报表或 .odc 文件进行重大修改的错误，则应为报表创建新的 .rsds 文件。</span><span class="sxs-lookup"><span data-stu-id="3e6be-129">If you run into errors that require significant modifications to either the report or to the .odc file, you should create a new .rsds file for the report.</span></span> <span data-ttu-id="3e6be-130">有关如何创建使用 .rsds 文件的共享数据源的详细信息，请参阅[创建和管理共享数据源（SharePoint 集成模式下的 Reporting Services）](../create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="3e6be-130">For more information about how to create a shared data source that uses an .rsds file, see [Create and Manage Shared Data Sources &#40;Reporting Services in SharePoint Integrated Mode&#41;](../create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md).</span></span>  
  
### <a name="to-create-and-export-an-odc-file"></a><span data-ttu-id="3e6be-131">创建并导出 .odc 文件</span><span class="sxs-lookup"><span data-stu-id="3e6be-131">To create and export an .odc file</span></span>  
  
1.  <span data-ttu-id="3e6be-132">启动 Excel 2007。</span><span class="sxs-lookup"><span data-stu-id="3e6be-132">Start Excel 2007.</span></span>  
  
2.  <span data-ttu-id="3e6be-133">在 **“数据”** 选项卡上的 **“获取外部数据”** 组中，单击 **“从其他来源”** ，然后单击 **“从数据连接向导”** 。</span><span class="sxs-lookup"><span data-stu-id="3e6be-133">On the **Data** tab, in the **Get External Data** group, click **From Other Sources**, and then click **From Data Connection Wizard**.</span></span>  
  
3.  <span data-ttu-id="3e6be-134">选择“其他/高级”，然后单击“下一步”   。</span><span class="sxs-lookup"><span data-stu-id="3e6be-134">Select **Other/Advanced**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="3e6be-135">选择 **“Microsoft OLE DB Provider for SQL Server”** ，然后单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="3e6be-135">Select **Microsoft OLE DB Provider for SQL Server**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="3e6be-136">输入服务器名称（默认情况下，该名称是计算机的网络名称）和具有有效登录名及数据库权限的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="3e6be-136">Enter the name of the server (by default, it is the network name of the computer) and a user account that has a valid login and database permissions.</span></span> <span data-ttu-id="3e6be-137">单击“下一步”。 </span><span class="sxs-lookup"><span data-stu-id="3e6be-137">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="3e6be-138">选择一个数据库，然后单击 **“确定”** 以关闭 **“数据链接”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="3e6be-138">Select a database, and then click **OK** to close the **Data Link** dialog box.</span></span>  
  
7.  <span data-ttu-id="3e6be-139">默认情况下， **“连接到特定表”** 复选框处于选中状态。</span><span class="sxs-lookup"><span data-stu-id="3e6be-139">The **Connect to specific table** check box is selected by default.</span></span> <span data-ttu-id="3e6be-140">它用于从特定表检索数据。</span><span class="sxs-lookup"><span data-stu-id="3e6be-140">It is used to retrieve data from a specific table.</span></span> <span data-ttu-id="3e6be-141">报表服务器将忽略 .odc 文件中的所有查询，因此选中或清除该复选框均无关紧要。</span><span class="sxs-lookup"><span data-stu-id="3e6be-141">The report server ignores all queries in an .odc file, so it does not matter whether you select or clear the check box.</span></span> <span data-ttu-id="3e6be-142">检索报表数据的查询包含在报表定义文件中，而不是包含在外部文件中。</span><span class="sxs-lookup"><span data-stu-id="3e6be-142">Queries that retrieve data for a report are included in a report definition file and not in external files.</span></span>  
  
8.  <span data-ttu-id="3e6be-143">连接打开时，可以编辑属性并将其导出。</span><span class="sxs-lookup"><span data-stu-id="3e6be-143">While the connection is open, you can edit properties and export it.</span></span> <span data-ttu-id="3e6be-144">在 **“数据”** 选项卡的 **“连接”** 组中，单击 **“属性”** ，然后单击连接名称旁边的 **“连接属性”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="3e6be-144">On the **Data** tab, in the **Connections** group, click **Properties**, and then click the **Connection Properties** button next to the connection name.</span></span>  
  
9. <span data-ttu-id="3e6be-145">在 **“定义”** 选项卡上，单击 **“导出连接文件”** 。</span><span class="sxs-lookup"><span data-stu-id="3e6be-145">On the **Definition** tab, click **Export Connection File**.</span></span>  
  
10. <span data-ttu-id="3e6be-146">输入文件名，然后单击 **“保存”** 。</span><span class="sxs-lookup"><span data-stu-id="3e6be-146">Enter a name for the file, and then click **Save**.</span></span> <span data-ttu-id="3e6be-147">关闭应用程序和所有打开的文件。</span><span class="sxs-lookup"><span data-stu-id="3e6be-147">Close the application and all open files.</span></span>  
  
### <a name="to-upload-and-use-an-odc-file"></a><span data-ttu-id="3e6be-148">上载并使用 .odc 文件</span><span class="sxs-lookup"><span data-stu-id="3e6be-148">To upload and use an .odc file</span></span>  
  
1.  <span data-ttu-id="3e6be-149">打开连接文件将要上载到其中的库。</span><span class="sxs-lookup"><span data-stu-id="3e6be-149">Open the library into which you want to upload the connection file.</span></span>  
  
2.  <span data-ttu-id="3e6be-150">在 **“上载”** 菜单中，单击 **“上载文档”** 。</span><span class="sxs-lookup"><span data-stu-id="3e6be-150">On the **Upload** menu, click **Upload document**.</span></span>  
  
3.  <span data-ttu-id="3e6be-151">单击“浏览”  。</span><span class="sxs-lookup"><span data-stu-id="3e6be-151">Click **Browse**.</span></span>  
  
4.  <span data-ttu-id="3e6be-152">选择所创建的 .odc 文件。</span><span class="sxs-lookup"><span data-stu-id="3e6be-152">Select the .odc file you created.</span></span> <span data-ttu-id="3e6be-153">默认情况下，.odc 文件位于“我的文档”文件夹的“我的数据源”中。</span><span class="sxs-lookup"><span data-stu-id="3e6be-153">By default, the .odc file is in the My Documents folder, in My Data Sources.</span></span>  
  
5.  <span data-ttu-id="3e6be-154">单击 **“打开”** 以选择该文件，单击 **“确定”** 保存选择。</span><span class="sxs-lookup"><span data-stu-id="3e6be-154">Click **Open** to select the file, click **OK** to save the selection.</span></span> <span data-ttu-id="3e6be-155">新项的属性页将自动打开。</span><span class="sxs-lookup"><span data-stu-id="3e6be-155">The properties page for the new item opens automatically.</span></span>  
  
6.  <span data-ttu-id="3e6be-156">在“内容类型”中，选择 **“报表数据源”** ，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="3e6be-156">In Content Type, select **Report Data Source**, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="3e6be-157">指向报表。</span><span class="sxs-lookup"><span data-stu-id="3e6be-157">Point to a report.</span></span>  
  
8.  <span data-ttu-id="3e6be-158">单击下箭头，然后选择 **“管理数据源”** 。</span><span class="sxs-lookup"><span data-stu-id="3e6be-158">Click the down arrow, and select **Manage Data Sources**.</span></span>  
  
9. <span data-ttu-id="3e6be-159">单击数据源名称。</span><span class="sxs-lookup"><span data-stu-id="3e6be-159">Click the data source name.</span></span>  
  
10. <span data-ttu-id="3e6be-160">如果报表使用自定义数据源信息，请单击 **“共享”** 。</span><span class="sxs-lookup"><span data-stu-id="3e6be-160">If the report uses custom data source information, click **Shared**.</span></span>  
  
11. <span data-ttu-id="3e6be-161">在“数据源链接”中，单击“浏览(...)”按钮   。</span><span class="sxs-lookup"><span data-stu-id="3e6be-161">In **Data Source Link**, click the browse (**...**) button.</span></span>  
  
12. <span data-ttu-id="3e6be-162">选择刚上载的 .odc 文件。</span><span class="sxs-lookup"><span data-stu-id="3e6be-162">Select the .odc file you just uploaded.</span></span>  
  
13. <span data-ttu-id="3e6be-163">单击 **“确定”** 以选择该文件，然后单击 **“确定”** 保存更改。</span><span class="sxs-lookup"><span data-stu-id="3e6be-163">Click **OK** to select the file, and then click **OK** to save your changes.</span></span>  
  
     <span data-ttu-id="3e6be-164">如果尝试将上述步骤用于 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 示例数据库和示例报表，请注意：只有 Company Sales 报表可不经修改地立即与 .odc 文件一起使用。</span><span class="sxs-lookup"><span data-stu-id="3e6be-164">If you are trying these steps with the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database and sample reports, be aware that only the Company Sales report will work out-of-the-box with an .odc file.</span></span> <span data-ttu-id="3e6be-165">其他示例报表包含有不能与 OLE DB 提供程序配合使用的查询参数和功能。</span><span class="sxs-lookup"><span data-stu-id="3e6be-165">The other sample reports contain query parameters and features that do not work with the OLE DB provider.</span></span> <span data-ttu-id="3e6be-166">但是，如果先在报表设计器中对这些报表进行修改，那么就可以让报表与 OLE DB 访问接口配合使用。</span><span class="sxs-lookup"><span data-stu-id="3e6be-166">However, you can make the reports work with the OLE DB provider if you modify them first in Report Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e6be-167">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3e6be-167">See Also</span></span>  
 [<span data-ttu-id="3e6be-168">创建、修改和删除共享数据源 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="3e6be-168">Create, Modify, and Delete Shared Data Sources &#40;SSRS&#41;</span></span>](create-modify-and-delete-shared-data-sources-ssrs.md)  
  
  
