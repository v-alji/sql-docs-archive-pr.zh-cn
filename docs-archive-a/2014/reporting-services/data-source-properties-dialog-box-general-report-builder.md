---
title: "\"数据源属性\" 对话框-\"常规\" (报表生成器) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10018"
ms.assetid: b956f43a-8426-4679-acc1-00f405d5ff5b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: dcfba8346a3519817a36c21b24be1a91a613e098
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577396"
---
# <a name="data-source-properties-dialog-box-general-report-builder"></a><span data-ttu-id="4a7c2-102">“数据源属性”对话框 -&gt;“常规”（报表生成器）</span><span class="sxs-lookup"><span data-stu-id="4a7c2-102">Data Source Properties Dialog Box, General (Report Builder)</span></span>
  <span data-ttu-id="4a7c2-103">在 **“数据源属性”** 对话框中选择 **“常规”** 可从报表服务器中选择共享数据源，或者创建或修改报表中嵌入的数据源的连接信息。</span><span class="sxs-lookup"><span data-stu-id="4a7c2-103">Select **General** on the **Data Source Properties** dialog box to select a shared data source from a report server or to create or modify connection information for a data source embedded in the report.</span></span>  
  
 <span data-ttu-id="4a7c2-104">在数据源属性中可以指定连接到数据源时使用的凭据的类型。</span><span class="sxs-lookup"><span data-stu-id="4a7c2-104">The type of credentials used to connect to a data source is specified in the data source properties.</span></span> <span data-ttu-id="4a7c2-105">在报表服务器中打开报表时，在数据源属性中指定的运行时凭据可能不适合创建查询和预览报表之类的设计时任务。</span><span class="sxs-lookup"><span data-stu-id="4a7c2-105">When you open a report from the report server, the run-time credentials, specified in the data source properties, might not work for design time tasks such as creating queries and previewing reports.</span></span> <span data-ttu-id="4a7c2-106">例如，数据源可能使用另一个 Windows 凭据（而不是您的凭据）或您不知道的用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="4a7c2-106">For example, the data source might use Windows credentials other than yours or a user name and password that are unknown to you.</span></span>  
  
 <span data-ttu-id="4a7c2-107">如果使用数据源属性中提供的凭据无法连接到数据源，报表生成器会打开 **“输入数据源凭据”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="4a7c2-107">Report Builder opens the **Enter Data Source Credentials** dialog box when it is unable to connect to the data source using the credentials provided in the data source properties.</span></span> <span data-ttu-id="4a7c2-108">通常在以下情况下会打开该对话框：</span><span class="sxs-lookup"><span data-stu-id="4a7c2-108">Typically this happens when:</span></span>  
  
-   <span data-ttu-id="4a7c2-109">数据源配置为提示输入凭据。</span><span class="sxs-lookup"><span data-stu-id="4a7c2-109">The data source is configured to prompt for credentials.</span></span>  
  
-   <span data-ttu-id="4a7c2-110">数据源配置为使用存储的凭据。</span><span class="sxs-lookup"><span data-stu-id="4a7c2-110">The data source is configured to use stored credentials.</span></span>  <span data-ttu-id="4a7c2-111">为了将安全风险降到最低，报表生成器设计为不检索服务器上存储的凭据。</span><span class="sxs-lookup"><span data-stu-id="4a7c2-111">To minimize potential security threats, Report Builder is designed to not retrieve credentials stored on the server.</span></span>  
  
 <span data-ttu-id="4a7c2-112">您可以使用 **“输入数据源凭据”** 对话框更改报表生成器在设计时使用的凭据，从而作为当前 Windows 用户连接到数据源，或者使用该对话框提供用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="4a7c2-112">You can use the **Enter Data Source Credentials** dialog box to change the credentials used by Report Builder at design time to connect to the data source as the current Windows user or provide a user name and password.</span></span> <span data-ttu-id="4a7c2-113">如果您提供用户名和密码，则可以指明它们是否用作 Windows 凭据。</span><span class="sxs-lookup"><span data-stu-id="4a7c2-113">If you provide a user name and password you can indicate whether they are used as Windows credentials.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4a7c2-114">虽然使用查询设计器可以为设计时凭据指定其他凭据类型，但报表预览只允许输入在数据源中指定的现有凭据选项的用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="4a7c2-114">Although the query designers allow you to specify other another credentials type for design-time credentials, report preview only allows you to enter the user name and password for the existing credentials options specified in the data source.</span></span>  
  
 <span data-ttu-id="4a7c2-115">单击 **“测试连接”** 时，将使用在数据源属性凭据页中指定的凭据测试与数据源的连接。</span><span class="sxs-lookup"><span data-stu-id="4a7c2-115">When you click **Test Connection**, the connection to the data source is tested using the credentials specified in the data source properties credentials page.</span></span> <span data-ttu-id="4a7c2-116">可以测试与嵌入数据源和共享数据源的连接。</span><span class="sxs-lookup"><span data-stu-id="4a7c2-116">You can test connections to embedded and shared data sources.</span></span>  
  
 <span data-ttu-id="4a7c2-117">如果指定的凭据不完整（例如需要密码），则报表生成器会在需要连接到数据源时再次提示您输入运行时凭据。</span><span class="sxs-lookup"><span data-stu-id="4a7c2-117">If the credentials specified are incomplete (for example, a password is required), Report Builder prompts you again for run-time credentials when it needs to connect the data source.</span></span> <span data-ttu-id="4a7c2-118">设计时凭据将存储起来，不再提示您进行输入。</span><span class="sxs-lookup"><span data-stu-id="4a7c2-118">The design-time credentials are stored and you are not prompted again.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4a7c2-119">选项</span><span class="sxs-lookup"><span data-stu-id="4a7c2-119">Options</span></span>  
 <span data-ttu-id="4a7c2-120">**名称**</span><span class="sxs-lookup"><span data-stu-id="4a7c2-120">**Name**</span></span>  
 <span data-ttu-id="4a7c2-121">键入数据源的名称。</span><span class="sxs-lookup"><span data-stu-id="4a7c2-121">Type the name of the data source.</span></span> <span data-ttu-id="4a7c2-122">数据源名称在报表中必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="4a7c2-122">The data source name must be unique within the report.</span></span> <span data-ttu-id="4a7c2-123">默认情况下，会为数据源分配一个常规名称，如 DataSource1 或 DataSource2。</span><span class="sxs-lookup"><span data-stu-id="4a7c2-123">By default, a general name, such as DataSource1 or DataSource2, is assigned to the data source.</span></span>  
  
 <span data-ttu-id="4a7c2-124">**使用共享连接**</span><span class="sxs-lookup"><span data-stu-id="4a7c2-124">**Use a shared connection**</span></span>  
 <span data-ttu-id="4a7c2-125">选择此选项可浏览已发布到报表服务器的共享数据源。</span><span class="sxs-lookup"><span data-stu-id="4a7c2-125">Select this option to browse to a shared data source that has been published to a report server.</span></span>  
  
 <span data-ttu-id="4a7c2-126">从报表服务器选择数据源后，报表生成器会保持到此报表服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="4a7c2-126">After you select a data source from a report server, Report Builder maintains a connection to this report server.</span></span>  
  
 <span data-ttu-id="4a7c2-127">**使用我的报表中嵌入的连接**</span><span class="sxs-lookup"><span data-stu-id="4a7c2-127">**Use a connection embedded in my report**</span></span>  
 <span data-ttu-id="4a7c2-128">选择此选项可创建仅供此报表使用的数据源。</span><span class="sxs-lookup"><span data-stu-id="4a7c2-128">Select this option to create a data source that is used only by this report.</span></span>  
  
 <span data-ttu-id="4a7c2-129">**Type**</span><span class="sxs-lookup"><span data-stu-id="4a7c2-129">**Type**</span></span>  
 <span data-ttu-id="4a7c2-130">选择数据处理扩展插件。</span><span class="sxs-lookup"><span data-stu-id="4a7c2-130">Select a data processing extension.</span></span> <span data-ttu-id="4a7c2-131">该列表显示所有已注册的扩展插件。</span><span class="sxs-lookup"><span data-stu-id="4a7c2-131">The list displays all registered extensions.</span></span>  
  
 <span data-ttu-id="4a7c2-132">**连接字符串**</span><span class="sxs-lookup"><span data-stu-id="4a7c2-132">**Connection string**</span></span>  
 <span data-ttu-id="4a7c2-133">输入数据源的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="4a7c2-133">Enter a connection string for the data source.</span></span> <span data-ttu-id="4a7c2-134">单击 **“生成”** 可使用 **“连接属性”** 对话框生成连接字符串。</span><span class="sxs-lookup"><span data-stu-id="4a7c2-134">Click **Build** to build the connection string using the **Connection Properties** dialog box.</span></span> <span data-ttu-id="4a7c2-135">单击“表达式”\*\*\*\* (*fx*) 按钮可编辑表达式。</span><span class="sxs-lookup"><span data-stu-id="4a7c2-135">Click the **Expressions** (*fx*) button to edit the expression.</span></span>  
  
 <span data-ttu-id="4a7c2-136">**处理查询时使用单个事务**</span><span class="sxs-lookup"><span data-stu-id="4a7c2-136">**Use a single transaction when processing the queries**</span></span>  
 <span data-ttu-id="4a7c2-137">选择此选项可指示使用此数据源的数据集在针对数据库的单个事务中运行。</span><span class="sxs-lookup"><span data-stu-id="4a7c2-137">Select this option to indicate that datasets that use this data source are run in a single transaction against the database.</span></span> <span data-ttu-id="4a7c2-138">若要将使用同一数据源的子报表的事务包括在内，请选择该子报表，然后在“属性”窗格中，将 **MergeTransactions** 设置为 **True**。</span><span class="sxs-lookup"><span data-stu-id="4a7c2-138">To include transactions for subreports that use the same data source, select the subreport, and in the Properties pane, set **MergeTransactions** to **True**.</span></span>  
  
 <span data-ttu-id="4a7c2-139">**测试连接**</span><span class="sxs-lookup"><span data-stu-id="4a7c2-139">**Test Connection**</span></span>  
 <span data-ttu-id="4a7c2-140">单击以使用指定的凭据验证数据源连接是否正常工作。</span><span class="sxs-lookup"><span data-stu-id="4a7c2-140">Click to verify that the data source connection works by using the specified credentials.</span></span> <span data-ttu-id="4a7c2-141">如果不能建立连接，则需要验证您的凭据和服务器可用性。</span><span class="sxs-lookup"><span data-stu-id="4a7c2-141">If the connection cannot be made, you need to verify your credentials and the server availability.</span></span> <span data-ttu-id="4a7c2-142">可以为嵌入数据源和共享数据源测试数据源连接。</span><span class="sxs-lookup"><span data-stu-id="4a7c2-142">You can test data source connections for embedded and shared data sources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a7c2-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4a7c2-143">See Also</span></span>  
 <span data-ttu-id="4a7c2-144">[将数据添加到报表 &#40;报表生成器和 SSRS&#41;](report-data/report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4a7c2-144">[Add Data to a Report &#40;Report Builder and SSRS&#41;](report-data/report-datasets-ssrs.md) </span></span>  
 <span data-ttu-id="4a7c2-145">[添加和验证数据连接或数据源 &#40;报表生成器和 SSRS&#41;](report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4a7c2-145">[Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4a7c2-146">[报表生成器中的数据连接、数据源和连接字符串](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="4a7c2-146">[Data Connections, Data Sources, and Connection Strings in Report Builder](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-report-builder.md) </span></span>  
 <span data-ttu-id="4a7c2-147">["数据源属性" 对话框-"凭据 &#40;报表生成器&#41;](../../2014/reporting-services/data-source-properties-dialog-box-credentials-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="4a7c2-147">[Data Source Properties Dialog Box, Credentials &#40;Report Builder&#41;](../../2014/reporting-services/data-source-properties-dialog-box-credentials-report-builder.md) </span></span>  
 [<span data-ttu-id="4a7c2-148">用于对话框、窗格和向导的报表生成器帮助</span><span class="sxs-lookup"><span data-stu-id="4a7c2-148">Report Builder Help for Dialog Boxes, Panes, and Wizards</span></span>](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)  
  
  
