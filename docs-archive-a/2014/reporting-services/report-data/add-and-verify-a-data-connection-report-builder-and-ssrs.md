---
title: 添加和验证数据连接或数据源 (报表生成器和 SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 1d3b2573-e29d-480d-9dde-d26379c86618
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d86b3e6598c12545f0e24ef1d162eeb1131bd15d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577339"
---
# <a name="add-and-verify-a-data-connection-or-data-source-report-builder-and-ssrs"></a><span data-ttu-id="ddc83-102">添加和验证数据连接或数据源（报表生成器和 SSRS）</span><span class="sxs-lookup"><span data-stu-id="ddc83-102">Add and Verify a Data Connection or Data Source (Report Builder and SSRS)</span></span>
  <span data-ttu-id="ddc83-103">在报表生成器中，您可以从报表服务器添加共享数据源或为您的报表创建嵌入数据源。</span><span class="sxs-lookup"><span data-stu-id="ddc83-103">In Report Builder, you can add a shared data source from the report server or create an embedded data source for your report.</span></span> <span data-ttu-id="ddc83-104">在报表设计器中，您可以创建共享数据源或嵌入数据源，并且将其部署到报表服务器上。</span><span class="sxs-lookup"><span data-stu-id="ddc83-104">In Report Designer, you can create a shared data source or an embedded data source and deploy it to a report server.</span></span>  
  
 <span data-ttu-id="ddc83-105">若要将共享数据源添加到报表，请浏览报表服务器并选择共享数据源。</span><span class="sxs-lookup"><span data-stu-id="ddc83-105">To add a shared data source to your report, browse to a report server and select a shared data source.</span></span> <span data-ttu-id="ddc83-106">报表中的共享数据源指向报表服务器上的共享数据源定义。</span><span class="sxs-lookup"><span data-stu-id="ddc83-106">The shared data source in your report points to the shared data source definition on the report server.</span></span>  
  
 <span data-ttu-id="ddc83-107">若要创建嵌入数据源，您必须具有到外部数据源的连接信息并知道需要何种权限才能访问数据。</span><span class="sxs-lookup"><span data-stu-id="ddc83-107">To create an embedded data source, you must have connection information to the external source of data and you must know which permissions you need to access the data.</span></span> <span data-ttu-id="ddc83-108">此信息通常来自数据源的所有者。</span><span class="sxs-lookup"><span data-stu-id="ddc83-108">This information usually comes from the owner of the data source.</span></span> <span data-ttu-id="ddc83-109">可以测试该连接以验证指定的凭据是否有效。</span><span class="sxs-lookup"><span data-stu-id="ddc83-109">You can test the connection to verify that the credentials that are specified are sufficient.</span></span>  
  
 <span data-ttu-id="ddc83-110">有关详细信息，请参阅[报表生成器中的数据连接、数据源和连接字符串](../data-connections-data-sources-and-connection-strings-in-report-builder.md)，以及[在报表生成器中指定凭据](../specify-credentials-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="ddc83-110">For more information, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md) and [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-create-a-reference-to-a-shared-data-source"></a><span data-ttu-id="ddc83-111">创建对共享数据源的引用</span><span class="sxs-lookup"><span data-stu-id="ddc83-111">To create a reference to a shared data source</span></span>  
  
1.  <span data-ttu-id="ddc83-112">在“报表数据”窗格的工具栏上，单击 **“新建”** ，然后单击 **“数据源”** 。</span><span class="sxs-lookup"><span data-stu-id="ddc83-112">On the toolbar in the Report Data pane, click **New,** and then click **Data Source**.</span></span> <span data-ttu-id="ddc83-113">此时将打开 **“数据源属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="ddc83-113">The **Data Source Properties** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="ddc83-114">在 **“名称”** 文本框中，键入数据源的名称。</span><span class="sxs-lookup"><span data-stu-id="ddc83-114">In the **Name** text box, type a name for the data source.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ddc83-115">此名称保存在本地报表定义中，</span><span class="sxs-lookup"><span data-stu-id="ddc83-115">This name is saved in the local report definition.</span></span> <span data-ttu-id="ddc83-116">它不是报表服务器上共享数据源的名称。</span><span class="sxs-lookup"><span data-stu-id="ddc83-116">This name is not the name of the shared data source on the report server.</span></span>  
  
3.  <span data-ttu-id="ddc83-117">选择 **“使用共享连接或报表模型”** 。</span><span class="sxs-lookup"><span data-stu-id="ddc83-117">Select **Use a shared connection or report model**.</span></span> <span data-ttu-id="ddc83-118">将显示最近使用的共享数据源和报表模型的列表。</span><span class="sxs-lookup"><span data-stu-id="ddc83-118">The list of recently used shared data sources and report models appears.</span></span> <span data-ttu-id="ddc83-119">若要从报表服务器选择一个共享数据源，请单击 **“浏览”** 并找到报表服务器上包含共享数据源的文件夹。</span><span class="sxs-lookup"><span data-stu-id="ddc83-119">To select one from a report server, click **Browse** and browse to the folder on the report server where shared data sources are available.</span></span>  
  
4.  <span data-ttu-id="ddc83-120">选择该共享数据源，然后单击 **“打开”** 。</span><span class="sxs-lookup"><span data-stu-id="ddc83-120">Select the shared data source and then click **Open**.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 <span data-ttu-id="ddc83-121">数据源将显示在“报表数据”窗格中。</span><span class="sxs-lookup"><span data-stu-id="ddc83-121">The data source appears in the Report Data pane.</span></span>  
  
### <a name="to-create-an-embedded-data-source"></a><span data-ttu-id="ddc83-122">创建嵌入数据源</span><span class="sxs-lookup"><span data-stu-id="ddc83-122">To create an embedded data source</span></span>  
  
1.  <span data-ttu-id="ddc83-123">在 "报表数据" 窗格的工具栏上，单击 "**新建**"，然后单击 "**数据源**"。</span><span class="sxs-lookup"><span data-stu-id="ddc83-123">On the toolbar in the Report Data pane, click **New**, and then click **Data Source**.</span></span> <span data-ttu-id="ddc83-124">此时将打开 **“数据源属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="ddc83-124">The **Data Source Properties** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="ddc83-125">在 **“名称”** 文本框中，键入数据源的名称，或接受默认值。</span><span class="sxs-lookup"><span data-stu-id="ddc83-125">In the **Name** text box, type a name for the data source or accept the default.</span></span>  
  
3.  <span data-ttu-id="ddc83-126">确认选中 **“使用嵌在我的报表中的连接”** 。</span><span class="sxs-lookup"><span data-stu-id="ddc83-126">Verify that **Use a connection embedded in my report** is selected.</span></span>  
  
    1.  <span data-ttu-id="ddc83-127">从“选择连接类型”下拉列表中，选择一个数据源类型，例如“Microsoft SQL Server”或“OLE DB”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ddc83-127">From the **Select connection type** drop-down list, select a data source type; for example, **Microsoft SQL Server** or **OLE DB**.</span></span>  
  
    2.  <span data-ttu-id="ddc83-128">采用以下备选方案之一指定连接字符串：</span><span class="sxs-lookup"><span data-stu-id="ddc83-128">Specify a connection string by using one of the following alternatives:</span></span>  
  
    -   <span data-ttu-id="ddc83-129">直接在 **“连接字符串”** 文本框中键入连接字符串。</span><span class="sxs-lookup"><span data-stu-id="ddc83-129">Type the connection string directly in the **Connection string** text box.</span></span> <span data-ttu-id="ddc83-130">有关示例连接字符串的列表，请参阅 [报表生成器中的数据连接、数据源和连接字符串](../data-connections-data-sources-and-connection-strings-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="ddc83-130">For a list of example connection strings, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md).</span></span>  
  
    -   <span data-ttu-id="ddc83-131">单击表达式 (**fx** ) 按钮创建计算结果为连接字符串的表达式。</span><span class="sxs-lookup"><span data-stu-id="ddc83-131">Click the expression (**fx)** button to create an expression that evaluates to a connection string.</span></span> <span data-ttu-id="ddc83-132">在 **“表达式”** 对话框的“表达式”窗格中，键入该表达式。</span><span class="sxs-lookup"><span data-stu-id="ddc83-132">In the **Expression** dialog box, type the expression in the Expression pane.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
    -   <span data-ttu-id="ddc83-133">单击 **“生成”** 打开在步骤 2 中选择的数据源类型的 **“连接属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="ddc83-133">Click **Build** to open the **Connection Properties** dialog box for the data source type that you chose in step 2.</span></span>  
  
         <span data-ttu-id="ddc83-134">根据需要，在 **“连接属性”** 对话框中为该数据源类型填写字段。</span><span class="sxs-lookup"><span data-stu-id="ddc83-134">Fill in the fields in the **Connection Properties** dialog box as appropriate for the data source type.</span></span> <span data-ttu-id="ddc83-135">连接属性包括数据源的类型、名称以及要使用的凭据。</span><span class="sxs-lookup"><span data-stu-id="ddc83-135">Connection properties include the type of data source, the name of the data source, and the credentials to use.</span></span> <span data-ttu-id="ddc83-136">在此对话框中指定值之后，单击 **“测试连接”** 以确保该数据源可用并且指定的凭据是正确的。</span><span class="sxs-lookup"><span data-stu-id="ddc83-136">After you specify values in this dialog box, click **Test Connection** to verify that the data source is available and that the credentials you specified are correct.</span></span>  
  
4.  <span data-ttu-id="ddc83-137">单击 **“凭据”**。</span><span class="sxs-lookup"><span data-stu-id="ddc83-137">Click **Credentials**.</span></span>  
  
     <span data-ttu-id="ddc83-138">指定用于此数据源的凭据。</span><span class="sxs-lookup"><span data-stu-id="ddc83-138">Specify the credentials to use for this data source.</span></span> <span data-ttu-id="ddc83-139">数据源所有者将选择支持的凭据类型。</span><span class="sxs-lookup"><span data-stu-id="ddc83-139">The owner of the data source chooses the type of credentials that are supported.</span></span> <span data-ttu-id="ddc83-140">在某些情况下，数据源所有者会维护报表服务器上的共享数据源并使用可用凭据配置该数据源。</span><span class="sxs-lookup"><span data-stu-id="ddc83-140">In some cases, the owner of the data source maintains a shared data source on a report server and configures the data source with credentials that you can use.</span></span> <span data-ttu-id="ddc83-141">有关此信息，请与数据源所有者联系。</span><span class="sxs-lookup"><span data-stu-id="ddc83-141">Contact the data source owner for this information.</span></span> <span data-ttu-id="ddc83-142">有关详细信息，请参阅 [在报表生成器中指定凭据](../specify-credentials-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="ddc83-142">For more information, see [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 <span data-ttu-id="ddc83-143">数据源将显示在“报表数据”窗格中。</span><span class="sxs-lookup"><span data-stu-id="ddc83-143">The data source appears in the Report Data pane.</span></span>  
  
### <a name="to-verify-a-data-connection"></a><span data-ttu-id="ddc83-144">验证数据连接</span><span class="sxs-lookup"><span data-stu-id="ddc83-144">To verify a data connection</span></span>  
  
1.  <span data-ttu-id="ddc83-145">在“报表数据”窗格的工具栏上，双击该数据源。</span><span class="sxs-lookup"><span data-stu-id="ddc83-145">On the toolbar in the Report Data pane, double-click the data source.</span></span> <span data-ttu-id="ddc83-146">此时将打开 **“数据源属性”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="ddc83-146">The **Data Source Properties** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="ddc83-147">单击 **“测试连接”** 。</span><span class="sxs-lookup"><span data-stu-id="ddc83-147">Click **Test Connection**.</span></span>  
  
3.  <span data-ttu-id="ddc83-148">如果连接成功，则显示以下消息：“已成功地创建连接”。</span><span class="sxs-lookup"><span data-stu-id="ddc83-148">If the connection is successful, the following message appears: "Connection created successfully".</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
4.  <span data-ttu-id="ddc83-149">如果连接失败，则显示以下消息：“无法连接到数据源”。</span><span class="sxs-lookup"><span data-stu-id="ddc83-149">If the connection is not successful, the following message appears: "Unable to connect to the data source."</span></span>  
  
5.  <span data-ttu-id="ddc83-150">单击 **“详细信息”**，然后使用该信息来解决问题。</span><span class="sxs-lookup"><span data-stu-id="ddc83-150">Click **Details**, and use the information to correct the issue.</span></span>  
  
     <span data-ttu-id="ddc83-151">有关详细信息，请参阅 [在报表生成器中指定凭据](../specify-credentials-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="ddc83-151">For more information, see [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ddc83-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ddc83-152">See Also</span></span>  
 <span data-ttu-id="ddc83-153">[将数据添加到报表 &#40;报表生成器和 SSRS&#41;](report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ddc83-153">[Add Data to a Report &#40;Report Builder and SSRS&#41;](report-datasets-ssrs.md) </span></span>  
 <span data-ttu-id="ddc83-154">[报表嵌入数据集和共享数据集 &#40;报表生成器和 SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ddc83-154">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ddc83-155">[查找、查看和管理 &#40;报表生成器和 SSRS 的报表 &#41;](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ddc83-155">[Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="ddc83-156">报表生成器中的数据连接、数据源和连接字符串</span><span class="sxs-lookup"><span data-stu-id="ddc83-156">Data Connections, Data Sources, and Connection Strings in Report Builder</span></span>](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
  
  
