---
title: 数据警报设计器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- editing, data alerts
- updating, data alerts
- editing, alerts
- updating, alerts
- creating, data alerts
- creating, alerts
ms.assetid: b2018116-cf1a-4e54-b29c-39e0ca2bda77
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 47640a086ab85d0cb150bef66881684e2a9a774a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588354"
---
# <a name="data-alert-designer"></a><span data-ttu-id="ed96f-102">数据警报设计器</span><span class="sxs-lookup"><span data-stu-id="ed96f-102">Data Alert Designer</span></span>
  <span data-ttu-id="ed96f-103">使用数据警报设计器创建和编辑数据警报定义。</span><span class="sxs-lookup"><span data-stu-id="ed96f-103">You create and edit data alert definitions in Data Alert Designer.</span></span> <span data-ttu-id="ed96f-104">警报定义是元数据的一个集合，包括您感兴趣的报表数据、报表数据必须满足才能创建数据警报实例和发送数据警报消息的规则、警报消息的收件人等。</span><span class="sxs-lookup"><span data-stu-id="ed96f-104">An alert definition is a collection of metadata, including the report data that you are interested in, the rules that report data must satisfy to create data alert instances and send data alert messages, the recipients of the alert message, and so forth.</span></span>

 <span data-ttu-id="ed96f-105">若要创建警报定义，您需要执行许多相关任务：</span><span class="sxs-lookup"><span data-stu-id="ed96f-105">To create an alert definition you do a number of related tasks:</span></span>

-   <span data-ttu-id="ed96f-106">选择包含您要使用的数据的报表和报表数据馈送。</span><span class="sxs-lookup"><span data-stu-id="ed96f-106">Select the report and the report data feed that includes data that you want to use.</span></span>

-   <span data-ttu-id="ed96f-107">定义导致发送警报的规则和子句。</span><span class="sxs-lookup"><span data-stu-id="ed96f-107">Define the rules and clauses that cause an alert to be sent.</span></span> <span data-ttu-id="ed96f-108">通过使用由 AND 运算符组合的多个子句，这些规则可以简单或复杂。</span><span class="sxs-lookup"><span data-stu-id="ed96f-108">The rules can be simple or complex, using multiple clauses combined by AND operators.</span></span>

-   <span data-ttu-id="ed96f-109">定义发送警报消息的频率以及警报开始和停止的日期和时间。</span><span class="sxs-lookup"><span data-stu-id="ed96f-109">Define the frequency that the alert message is sent and the date and time the alert starts and stops.</span></span> <span data-ttu-id="ed96f-110">仅当结果更改时才发送警报消息。</span><span class="sxs-lookup"><span data-stu-id="ed96f-110">Alert messages can be sent only when results change.</span></span>

-   <span data-ttu-id="ed96f-111">指定警报消息收件人的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="ed96f-111">Specify the email addresses of alert message recipients.</span></span>

-   <span data-ttu-id="ed96f-112">自定义警报消息的 **“主题”** 行。</span><span class="sxs-lookup"><span data-stu-id="ed96f-112">Customize the **Subject** line of the alert message.</span></span>

-   <span data-ttu-id="ed96f-113">提供要在警报消息中包括的警报说明。</span><span class="sxs-lookup"><span data-stu-id="ed96f-113">Provide a description of alert to include in alert message.</span></span>

> [!NOTE]
>  <span data-ttu-id="ed96f-114">因为只有在 SharePoint 模式下安装了 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 后， [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 数据警报功能才可用，所以，你想要对其创建警报的报表必须保存、部署或上传到 SharePoint 文档库中。</span><span class="sxs-lookup"><span data-stu-id="ed96f-114">Because the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] data alerts feature is available only when you install [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in SharePoint mode, the report on which you want to create an alert must be saved, deployed, or uploaded to a SharePoint document library.</span></span>
> 
>  <span data-ttu-id="ed96f-115">不能针对使用 Windows 集成身份验证或提示输入凭据的报表创建数据警报。</span><span class="sxs-lookup"><span data-stu-id="ed96f-115">Data alerts cannot be created on reports that use Windows Integrated authentication or prompts for credentials.</span></span> <span data-ttu-id="ed96f-116">报表必须使用已存储的凭据。</span><span class="sxs-lookup"><span data-stu-id="ed96f-116">The reports must use stored credentials.</span></span> <span data-ttu-id="ed96f-117">有关详细信息，请参阅[为报表数据源指定凭据和连接信息](report-data/specify-credential-and-connection-information-for-report-data-sources.md)</span><span class="sxs-lookup"><span data-stu-id="ed96f-117">For more information, see [Specify Credential and Connection Information for Report Data Sources](report-data/specify-credential-and-connection-information-for-report-data-sources.md).</span></span>

 <span data-ttu-id="ed96f-118">若要打开数据警报设计器，请单击报表工具栏上 **“操作”** 菜单中的 **“新建数据警报”** 选项。</span><span class="sxs-lookup"><span data-stu-id="ed96f-118">To open Data Alert Designer, you click the **New Data Alert** option on the **Actions** menu on the report toolbar.</span></span> <span data-ttu-id="ed96f-119">如果您看不到 **“新建数据警报”** 选项，则此报表未配置为使用存储的凭据。</span><span class="sxs-lookup"><span data-stu-id="ed96f-119">If you do not see the **New Data Alert** option, the report is not configured to use stored credentials.</span></span> <span data-ttu-id="ed96f-120">您可以通过从 SharePoint 库更新报表数据源来更新凭据类型。</span><span class="sxs-lookup"><span data-stu-id="ed96f-120">You can update the credential type by updating the report data source from the SharePoint library.</span></span>

##  <a name="data-alert-designer-user-interface"></a><a name="AlertDesigner"></a> <span data-ttu-id="ed96f-121">数据警报设计器用户界面</span><span class="sxs-lookup"><span data-stu-id="ed96f-121">Data Alert Designer User Interface</span></span>
 <span data-ttu-id="ed96f-122">数据警报设计器分为若干区域。</span><span class="sxs-lookup"><span data-stu-id="ed96f-122">The Data Alert Designer is divided into areas.</span></span> <span data-ttu-id="ed96f-123">其中包括用于选择报表数据馈送的区域、通过向条件添加规则来创建简单或复杂条件的区域等区域。</span><span class="sxs-lookup"><span data-stu-id="ed96f-123">The area where you select the report data feed, the area where you create simple or complex conditions by adding rules to conditions, and so on.</span></span> <span data-ttu-id="ed96f-124">下图显示数据警报设计器中的区域。</span><span class="sxs-lookup"><span data-stu-id="ed96f-124">The following picture shows the areas in Data Alert Designer.</span></span>

 <span data-ttu-id="ed96f-125">![“警报设计器”用户界面中的区域](media/rs-alertdesigner.gif "“警报设计器”用户界面中的区域")</span><span class="sxs-lookup"><span data-stu-id="ed96f-125">![Areas within the Alert Designer user interface](media/rs-alertdesigner.gif "Areas within the Alert Designer user interface")</span></span>
 

### <a name="alert-data"></a><span data-ttu-id="ed96f-126">警报数据</span><span class="sxs-lookup"><span data-stu-id="ed96f-126">Alert Data</span></span>
 <span data-ttu-id="ed96f-127">在打开数据警报设计器时，它将从报表生成所有数据馈送并使它们变得可用，并且“报表数据名称”下拉列表将包含各个馈送的名称\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ed96f-127">When you open Data Alert Designer, it generates and makes available all the data feeds from the report and the **Report data name** drop-down list contains the names of the feeds.</span></span> <span data-ttu-id="ed96f-128">在您创建警报定义时数据馈送将缓存在内存中，并且当您在数据馈送之间切换以便浏览报表数据时将快速填充显示数据馈送数据的表。</span><span class="sxs-lookup"><span data-stu-id="ed96f-128">The data feeds are cached in memory while you are creating the alert definition and the table that display the data feed data is populated quickly when you switch between data feeds to explore the report data.</span></span>

 <span data-ttu-id="ed96f-129">创建数据警报定义的第一步是选择包含您希望监视警报的数据的报表数据馈送。</span><span class="sxs-lookup"><span data-stu-id="ed96f-129">The first step in creating a data alert definition is to select the report data feed that contains the data that you want the alert to monitor.</span></span> <span data-ttu-id="ed96f-130">报表可以有零个或多个数据馈送。</span><span class="sxs-lookup"><span data-stu-id="ed96f-130">Reports can have zero or multiple data feeds.</span></span> <span data-ttu-id="ed96f-131">如果某个报表没有数据馈送，则无法对其创建警报。</span><span class="sxs-lookup"><span data-stu-id="ed96f-131">If a report has no data feeds, you cannot create alerts on it.</span></span> <span data-ttu-id="ed96f-132">数据馈送可由任何数据区域生成，包括所有类型的图表、仪表、指示器以及表、矩阵和列表。</span><span class="sxs-lookup"><span data-stu-id="ed96f-132">A data feed can be generated by any data region, including all types of charts, gauges, indicators as well as tables, matrices, and lists.</span></span>

 <span data-ttu-id="ed96f-133">如果报表已参数化，并且您在报表数据馈送中看不到预期的数据和列，则使用适当的参数值重新运行该报表。</span><span class="sxs-lookup"><span data-stu-id="ed96f-133">If the report is parameterized and you do not see the data and columns that you expect in the report data feed, rerun the report using the appropriate parameter values.</span></span> <span data-ttu-id="ed96f-134">这些列和值必须存在于要包括在数据馈送中的报表中。</span><span class="sxs-lookup"><span data-stu-id="ed96f-134">The columns and values must be present in the report to be included in the data feed.</span></span>

 <span data-ttu-id="ed96f-135">根据报表的布局，您不见得能够直观地看到一个报表具有多少数据馈送以及数据馈送中包含哪些数据。</span><span class="sxs-lookup"><span data-stu-id="ed96f-135">Depending on the layout of the report, it might not be intuitive how many data feeds a report has, nor what data is included in which data feed.</span></span> <span data-ttu-id="ed96f-136">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]Atom 呈现扩展插件将生成你要用于警报的数据馈送。</span><span class="sxs-lookup"><span data-stu-id="ed96f-136">The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]Atom rendering extension generates the data feeds that you use with alerts.</span></span> <span data-ttu-id="ed96f-137">该 Atom 呈现扩展插件将报表数据作为平展的行集提供，这是一种所有列都具有相同行数的表格格式。</span><span class="sxs-lookup"><span data-stu-id="ed96f-137">The Atom rendering extension provides report data as flattened rowsets, a tabular format in which all columns have the same number of rows.</span></span> <span data-ttu-id="ed96f-138">这些行集是数据馈送的内容。</span><span class="sxs-lookup"><span data-stu-id="ed96f-138">These rowsets are the contents of the data feeds.</span></span> <span data-ttu-id="ed96f-139">因为报表布局通常比较复杂并且包含多个对等或嵌套的数据区域，所以，需要多个数据馈送以便可供所有报表数据使用。</span><span class="sxs-lookup"><span data-stu-id="ed96f-139">Because report layout is often complex and contains multiple peer or nested data regions, multiple data feeds are needed to make available all the report data..</span></span> <span data-ttu-id="ed96f-140">有关如何从报表生成数据馈送的详细信息，请参阅[基于报表生成数据馈送（报表生成器和 SSRS）](report-builder/generating-data-feeds-from-reports-report-builder-and-ssrs.md)和[从报表生成数据馈送（报表生成器和 SSRS）](report-builder/generate-data-feeds-from-a-report-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="ed96f-140">For more information about how data feeds are generated from reports, see [Generating Data Feeds from Reports &#40;Report Builder and SSRS&#41;](report-builder/generating-data-feeds-from-reports-report-builder-and-ssrs.md) and see [Generate Data Feeds from a Report &#40;Report Builder and SSRS&#41;](report-builder/generate-data-feeds-from-a-report-report-builder-and-ssrs.md).</span></span>

 <span data-ttu-id="ed96f-141">在您选择某一数据馈送时，来自该数据馈送的数据将显示在一个具有行和列的表中（显示在数据警报设计器的警报数据窗格中）。</span><span class="sxs-lookup"><span data-stu-id="ed96f-141">When you choose a data feed, the data from the feed displays in a table with rows and columns in the alert data pane of Data Alert Designer.</span></span> <span data-ttu-id="ed96f-142">来自报表使用的数据源或报表本身的元数据指定列名，并且数据馈送填充您用于在数据条件中定义规则的字段列表。</span><span class="sxs-lookup"><span data-stu-id="ed96f-142">The metadata from the data source that the report uses or the report itself specifies the column names and the data feed populates the field list that you use to define rules in the data condition.</span></span> <span data-ttu-id="ed96f-143">该数据馈送还提供元数据，例如用于限制值的表列的数据类型以及在您创建规则时可用于字段的比较运算符。</span><span class="sxs-lookup"><span data-stu-id="ed96f-143">The data feed also provides metadata such as the data types of table columns that restrict the values and comparison operators that you can use with fields when you create the rules.</span></span>

 <span data-ttu-id="ed96f-144">某些报表具有数百万行数据。</span><span class="sxs-lookup"><span data-stu-id="ed96f-144">Some reports have millions of rows of data.</span></span> <span data-ttu-id="ed96f-145">该表仅显示数据馈送中的前 100 行数据。</span><span class="sxs-lookup"><span data-stu-id="ed96f-145">The table shows only the first 100 rows of data in the feed.</span></span>

### <a name="alert-name"></a><span data-ttu-id="ed96f-146">警报名称</span><span class="sxs-lookup"><span data-stu-id="ed96f-146">Alert Name</span></span>
 <span data-ttu-id="ed96f-147">默认情况下，警报定义具有与报表相同的名称。</span><span class="sxs-lookup"><span data-stu-id="ed96f-147">By default, the alert definition has the same name as the report.</span></span> <span data-ttu-id="ed96f-148">您可以将此警报名称更改为更有意义的名称。</span><span class="sxs-lookup"><span data-stu-id="ed96f-148">You can change the alert name to be more meaningful.</span></span> <span data-ttu-id="ed96f-149">这便于您管理警报，以及确定要用于更新、删除等操作的警报。</span><span class="sxs-lookup"><span data-stu-id="ed96f-149">This makes it easier for you to manage your alerts, determining which alerts to update, delete and so on.</span></span>

 <span data-ttu-id="ed96f-150">您可以对一个报表创建多个警报。</span><span class="sxs-lookup"><span data-stu-id="ed96f-150">You can create multiple alerts on a report.</span></span> <span data-ttu-id="ed96f-151">可以具有同名的多个警报定义，但建议您保持警报名称唯一。</span><span class="sxs-lookup"><span data-stu-id="ed96f-151">It is possible to have multiple alert definitions with the same name, but it is recommended that you make alert names unique.</span></span> <span data-ttu-id="ed96f-152">这样可便于区分和管理警报定义。</span><span class="sxs-lookup"><span data-stu-id="ed96f-152">It makes it easier to differentiate and manage alert definitions.</span></span> <span data-ttu-id="ed96f-153">您可以在数据警报管理器中查看所创建的所有警报的列表。</span><span class="sxs-lookup"><span data-stu-id="ed96f-153">You can view a list of all the alerts you created in Data Alert Manager.</span></span> <span data-ttu-id="ed96f-154">有关详细信息，请参阅 [向管理员提出警报的数据警报管理器](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md) 和 [在数据警报管理器中管理我的数据警报](manage-my-data-alerts-in-data-alert-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="ed96f-154">For more information, see [Data Alert Manager for Alerting Administrators](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md) and [Manage My Data Alerts in Data Alert Manager](manage-my-data-alerts-in-data-alert-manager.md).</span></span>

### <a name="rules-and-clauses"></a><span data-ttu-id="ed96f-155">规则和子句</span><span class="sxs-lookup"><span data-stu-id="ed96f-155">Rules and Clauses</span></span>
 <span data-ttu-id="ed96f-156">数据更改的作用域以及警报规则中的规则定义触发警报的数据更改。</span><span class="sxs-lookup"><span data-stu-id="ed96f-156">The scope of data changes and the in the alert rules define the data changes that trigger the alert.</span></span> <span data-ttu-id="ed96f-157">数据更改的作用域如下：</span><span class="sxs-lookup"><span data-stu-id="ed96f-157">The scope of the data changes are as follow:</span></span>

-   <span data-ttu-id="ed96f-158">**任何数据都具有**-数据中至少有一个值满足条件指定的规则。</span><span class="sxs-lookup"><span data-stu-id="ed96f-158">**Any data has**-at least one value in the data satisfies the rules that the condition specifies.</span></span>

-   <span data-ttu-id="ed96f-159">**无数据**：数据中没有值满足条件指定的规则。</span><span class="sxs-lookup"><span data-stu-id="ed96f-159">**No data has**-no value in the data satisfied the rules that the condition specifies.</span></span>

 <span data-ttu-id="ed96f-160">一个规则可包含零个、一个或多个子句。</span><span class="sxs-lookup"><span data-stu-id="ed96f-160">A rule contains zero, one, or many clauses.</span></span> <span data-ttu-id="ed96f-161">多个规则由 AND 逻辑运算符组合在一起。</span><span class="sxs-lookup"><span data-stu-id="ed96f-161">Multiple rules are combined by the AND logical operator.</span></span> <span data-ttu-id="ed96f-162">如果该列具有字符串数据类型，则规则可包含使用 OR 运算符组合的多个子句。</span><span class="sxs-lookup"><span data-stu-id="ed96f-162">A rule can include multiple clause combined by the OR operator if the column has the string data type.</span></span> <span data-ttu-id="ed96f-163">下面的内容显示仅使用一个子句的基本规则、使用 AND 运算符组合的多个规则、使用一个或多个 OR 子句的多个规则。</span><span class="sxs-lookup"><span data-stu-id="ed96f-163">The following shows basic rules that use only one clause, multiple rules combined by using the AND operator, multiple rules that with one or more OR clauses.</span></span>

 <span data-ttu-id="ed96f-164">**简单规则**</span><span class="sxs-lookup"><span data-stu-id="ed96f-164">**Simple rules**</span></span>

-   <span data-ttu-id="ed96f-165">净销售额 **“大于”** 100000</span><span class="sxs-lookup"><span data-stu-id="ed96f-165">Net sales **is greater than** 100000</span></span>

-   <span data-ttu-id="ed96f-166">销售日期“晚于”2010/6/1\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="ed96f-166">Sales date **is after** 6/1/2010</span></span>

-   <span data-ttu-id="ed96f-167">公司名称 **“不是”** Contoso</span><span class="sxs-lookup"><span data-stu-id="ed96f-167">Company Name **is not** Contoso</span></span>

 <span data-ttu-id="ed96f-168">**AND 运算符组合的规则**</span><span class="sxs-lookup"><span data-stu-id="ed96f-168">**Rules combined by AND operator**</span></span>

-   <span data-ttu-id="ed96f-169">销售额 **“大于”** 1500.00</span><span class="sxs-lookup"><span data-stu-id="ed96f-169">Sales **is greater than** 1500.00</span></span>

     <span data-ttu-id="ed96f-170">**“并且”** 已销售的单位数 **“小于”** 500</span><span class="sxs-lookup"><span data-stu-id="ed96f-170">**and** Units Sold **is less than** 500</span></span>

     <span data-ttu-id="ed96f-171">返回日期“早于”2010/1/1\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="ed96f-171">Return date **is before** 1/1/2010</span></span>

-   <span data-ttu-id="ed96f-172">销售额 **“大于或等于”** 1500.00</span><span class="sxs-lookup"><span data-stu-id="ed96f-172">Sales **is greater than or equal to** 1500.00</span></span>

     <span data-ttu-id="ed96f-173">“并且”返回日期“晚于”2010/1/1\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="ed96f-173">**and** Return date **is after** 1/1/2010</span></span>

     <span data-ttu-id="ed96f-174">**“并且”** 已销售的单位数 **“大于”** 500</span><span class="sxs-lookup"><span data-stu-id="ed96f-174">**and** Units Sold **is greater than** 500</span></span>

-   <span data-ttu-id="ed96f-175">促销名称 **“包含”** 春季</span><span class="sxs-lookup"><span data-stu-id="ed96f-175">Promotion name **contains** Spring</span></span>

     <span data-ttu-id="ed96f-176">**“并且”** 已销售的单位数 **“大于”** 500</span><span class="sxs-lookup"><span data-stu-id="ed96f-176">**and** Units Sold **is greater than** 500</span></span>

     <span data-ttu-id="ed96f-177">**“并且”** 返回 **“是”**  0</span><span class="sxs-lookup"><span data-stu-id="ed96f-177">**and** Returns **is**  0</span></span>

 <span data-ttu-id="ed96f-178">**使用 OR 子句的规则**</span><span class="sxs-lookup"><span data-stu-id="ed96f-178">**Rules with OR clauses**</span></span>

-   <span data-ttu-id="ed96f-179">最后名称 **“是”** Blythe</span><span class="sxs-lookup"><span data-stu-id="ed96f-179">Last Name **is** Blythe</span></span>

     <span data-ttu-id="ed96f-180">**“或者”**  Petulescu</span><span class="sxs-lookup"><span data-stu-id="ed96f-180">**Or**  Petulescu</span></span>

     <span data-ttu-id="ed96f-181">**“或者”**  Martin</span><span class="sxs-lookup"><span data-stu-id="ed96f-181">**Or**  Martin</span></span>

-   <span data-ttu-id="ed96f-182">返回日期“晚于”2010/1/1\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="ed96f-182">Return date **is after** 1/1/2010</span></span>

     <span data-ttu-id="ed96f-183">**“并且”** 销售区域 **“是”**  中央</span><span class="sxs-lookup"><span data-stu-id="ed96f-183">**and** Sales Territory **is**  Central</span></span>

     <span data-ttu-id="ed96f-184">**“或者”**  南方</span><span class="sxs-lookup"><span data-stu-id="ed96f-184">**Or**  South</span></span>

     <span data-ttu-id="ed96f-185">**“或者”**  北方</span><span class="sxs-lookup"><span data-stu-id="ed96f-185">**Or**  North</span></span>

 <span data-ttu-id="ed96f-186">根据字段的数据类型，数据警报设计器提供了不同的比较。</span><span class="sxs-lookup"><span data-stu-id="ed96f-186">Depending on the data type of the field, Data Alert Designer provides different comparisons.</span></span> <span data-ttu-id="ed96f-187">数据警报设计器根据要进行比较值的字段的数据类型提供比较。</span><span class="sxs-lookup"><span data-stu-id="ed96f-187">Data Alert Designer provides comparisons that are tailored to the data type of the field to which values are compared.</span></span> <span data-ttu-id="ed96f-188">下表列出了适用于不同数据类型的比较。</span><span class="sxs-lookup"><span data-stu-id="ed96f-188">The following lists comparisons available for different data types.</span></span> <span data-ttu-id="ed96f-189">规则中不支持 `Boolean` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="ed96f-189">The `Boolean` data type is not supported in rules.</span></span>

-   <span data-ttu-id="ed96f-190">日期时间数据类型比较是： **“是”**、 **“不是”**、 **“早于”** 和 **“晚于”**</span><span class="sxs-lookup"><span data-stu-id="ed96f-190">Date time data type comparisons are: **is**, **is not**, **is before**, and **is after**</span></span>

-   <span data-ttu-id="ed96f-191">数值数据类型比较是： **“是”**、 **“不是”**、 **“小于”**、 **“小于或等于”** 和 **“大于”** 以及 **“大于或等于”**</span><span class="sxs-lookup"><span data-stu-id="ed96f-191">Numeric data type comparisons are: **is**, **is not**, **is less than**, **is less than or equal to**, and **is greater than**, and **is greater than or equal to**</span></span>

-   <span data-ttu-id="ed96f-192">字符串数据类型比较是： **“是”**、 **“不是”** 和 **“包含”**</span><span class="sxs-lookup"><span data-stu-id="ed96f-192">String data type comparisons are: **is**, **is not**, and **contains**</span></span>

 <span data-ttu-id="ed96f-193">在创建规则时，通过选中 **“值输入模式”** 或者 **“字段选择模式”** 来确定在比较中使用值还是字段。</span><span class="sxs-lookup"><span data-stu-id="ed96f-193">When you create a rule, you specify whether to use to use a value or field in the comparison by choosing **Value Entry Mode** or **Field Selection Mode**.</span></span> <span data-ttu-id="ed96f-194">如果您选中 **“值输入模式”**，则提供要比较的值列表。</span><span class="sxs-lookup"><span data-stu-id="ed96f-194">If you choose **Value Entry Mode**, you provide a list of values to compare to.</span></span> <span data-ttu-id="ed96f-195">包含多个 OR 子句的比较与 [!INCLUDE[tsql](../includes/tsql-md.md)]中的 IN 逻辑比较非常类似，后者是用来测试匹配的值列表。</span><span class="sxs-lookup"><span data-stu-id="ed96f-195">A comparison that includes multiple OR clauses is very similar to the IN logical comparison in [!INCLUDE[tsql](../includes/tsql-md.md)], which is a list of values to test for a match.</span></span> <span data-ttu-id="ed96f-196">有关详细信息，请参阅 [IN (Transact-SQL)](/sql/t-sql/language-elements/in-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="ed96f-196">For more information, see [IN &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/in-transact-sql).</span></span>

 <span data-ttu-id="ed96f-197">如果选中 **“字段选择模式”**，则在两个字段之间逐行进行比较。</span><span class="sxs-lookup"><span data-stu-id="ed96f-197">If you choose **Field Selection Mode**, the comparison is between two fields, row by row.</span></span> <span data-ttu-id="ed96f-198">这两个字段必须具有兼容的数据类型（例如，两个数字字段），否则比较无效。</span><span class="sxs-lookup"><span data-stu-id="ed96f-198">The two fields must have compatible data types (for example, two numeric fields) or the comparison is not valid.</span></span> <span data-ttu-id="ed96f-199">当您选中 **“字段选择模式”** 时，会自动显示一个字段列表。</span><span class="sxs-lookup"><span data-stu-id="ed96f-199">A list of fields displays automatically when you choose **Field Selection Mode**.</span></span>

 <span data-ttu-id="ed96f-200">没有规则的数据警报也是有效的。</span><span class="sxs-lookup"><span data-stu-id="ed96f-200">Data alerts without rules are also valid.</span></span> <span data-ttu-id="ed96f-201">这种类型的警报可能非常有用。</span><span class="sxs-lookup"><span data-stu-id="ed96f-201">This type of alert can be very useful.</span></span> <span data-ttu-id="ed96f-202">假设一种应用场景，只有在报表数据馈送具有数据时才会通知您。</span><span class="sxs-lookup"><span data-stu-id="ed96f-202">Imagine a scenario in which you want only to be notified when the report data feed has data.</span></span> <span data-ttu-id="ed96f-203">该数据馈送包含参加者信息并且在参加者取消前该数据馈送为空。</span><span class="sxs-lookup"><span data-stu-id="ed96f-203">The data feed contains attendee information and the feed is empty until an attendee cancels.</span></span> <span data-ttu-id="ed96f-204">在这个应用场景中，您将收到一个警报，从第一个取消开始。</span><span class="sxs-lookup"><span data-stu-id="ed96f-204">In this scenario, you would receive an alert, starting with the first cancellation.</span></span>

 <span data-ttu-id="ed96f-205">您可以删除各规则和子句。</span><span class="sxs-lookup"><span data-stu-id="ed96f-205">You can delete individual rules and clauses.</span></span>

 <span data-ttu-id="ed96f-206">数据警报消息中包含规则和子句。</span><span class="sxs-lookup"><span data-stu-id="ed96f-206">Rules and clauses are included in the data alert message.</span></span>

### <a name="schedule-settings"></a><span data-ttu-id="ed96f-207">计划设置</span><span class="sxs-lookup"><span data-stu-id="ed96f-207">Schedule Settings</span></span>
 <span data-ttu-id="ed96f-208">您为数据警报定义的计划将定义用于发送数据警报消息的重复执行模式以及何时开始和停止发送警报消息。</span><span class="sxs-lookup"><span data-stu-id="ed96f-208">The schedule that you define for the data alert defines the recurrence pattern for sending the data alert message and when to start and stop sending the alert messages.</span></span> <span data-ttu-id="ed96f-209">该模式为：一次、每分钟、每天和每周。</span><span class="sxs-lookup"><span data-stu-id="ed96f-209">The patterns are: once, minute, daily, and weekly.</span></span> <span data-ttu-id="ed96f-210">尽管一个警报只有一个计划，但您可以通过使用这些时间间隔创建满足大多数业务需要的复杂的重复执行模式。</span><span class="sxs-lookup"><span data-stu-id="ed96f-210">Although an alert has only one schedule you can create complex recurrence patterns that meet most business needs by using these intervals.</span></span> <span data-ttu-id="ed96f-211">下面是在计划中常用的重复执行模式的示例：</span><span class="sxs-lookup"><span data-stu-id="ed96f-211">The following are examples of common recurrence patterns to use in schedules:</span></span>

-   <span data-ttu-id="ed96f-212">每\*\*隔10天 (s) \*\* -每隔10天发送一次警报一次。</span><span class="sxs-lookup"><span data-stu-id="ed96f-212">**Daily every 10 day(s)** - sends alerts once a day, every 10 days.</span></span>

-   <span data-ttu-id="ed96f-213">每**隔2周，每2周 (s) 星期一**-仅每两周在星期一发送警报。</span><span class="sxs-lookup"><span data-stu-id="ed96f-213">**Weekly every 2 week(s) on Monday** - sends alerts every two weeks on Mondays only.</span></span>

-   <span data-ttu-id="ed96f-214">每\*\*小时 () \*\* -每隔12小时发送警报一次。</span><span class="sxs-lookup"><span data-stu-id="ed96f-214">**Hourly every 12 hour(s)** - sends alerts every 12 hours.</span></span>

-   <span data-ttu-id="ed96f-215">\*\*每30分钟 () \*\* -每隔30分钟发送警报一次。</span><span class="sxs-lookup"><span data-stu-id="ed96f-215">**Minute every 30 minute(s)** - sends alerts every 30 minutes.</span></span>

 <span data-ttu-id="ed96f-216">重复执行模式指定何时发送警报。</span><span class="sxs-lookup"><span data-stu-id="ed96f-216">The recurrence pattern specifies when the alert is sent.</span></span> <span data-ttu-id="ed96f-217">如果在该模式指定的间隔期间满足规则，则在该间隔结束前将不发送警报。</span><span class="sxs-lookup"><span data-stu-id="ed96f-217">If the rules are met during the interval that the pattern specifies, the alert is not sent until the end of the interval.</span></span>

 <span data-ttu-id="ed96f-218">如果想在报表数据遵循指定的规则时尽快接收数据警报消息，则可计划经常运行警报。</span><span class="sxs-lookup"><span data-stu-id="ed96f-218">If you want to receive a data alert message as soon as possible when report data follow the specified rules, you can schedule the alert to run often.</span></span> <span data-ttu-id="ed96f-219">如果报表数据没有更改，则您和其他收件人可能收到许多冗余消息。</span><span class="sxs-lookup"><span data-stu-id="ed96f-219">When the report data does not change, you and other recipients might receive many redundant messages.</span></span> <span data-ttu-id="ed96f-220">如果想在来自应用该规则的结果更改时才接收消息，则选择 **“仅当结果更改时才发送消息”** 选项。</span><span class="sxs-lookup"><span data-stu-id="ed96f-220">If you want to receive messages only, when the results from applying the rules change, select the **Send message only if results change** option.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="ed96f-221">建议您不要以高于每天一次的频率使用重复执行模式，除非有重要的业务原因需要这么做。</span><span class="sxs-lookup"><span data-stu-id="ed96f-221">It is recommended that you do not use a recurrence pattern that is more frequent than daily unless you have an important business reason to do so.</span></span> <span data-ttu-id="ed96f-222">不支持实时处理数据警报定义。</span><span class="sxs-lookup"><span data-stu-id="ed96f-222">Processing data alert definition in real time is not a supported scenario.</span></span> <span data-ttu-id="ed96f-223">过于频繁地处理数据警报定义会影响报表服务器和总体 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 部署的性能。</span><span class="sxs-lookup"><span data-stu-id="ed96f-223">Processing data alert definitions too frequently impacts the performance of the report server and the overall [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] deployment.</span></span>

### <a name="email-settings"></a><span data-ttu-id="ed96f-224">电子邮件设置</span><span class="sxs-lookup"><span data-stu-id="ed96f-224">Email Settings</span></span>
 <span data-ttu-id="ed96f-225">在“收件人”选项中，指定通过电子邮件接收数据警报消息的收件人的电子邮件地址\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ed96f-225">You specify the email addresses of recipients to receive data alert messages by email in the **Recipient(s)** option.</span></span> <span data-ttu-id="ed96f-226">多个电子邮件地址由分号分隔，与在 Microsoft Office Outlook 电子邮件中的操作方式相同。</span><span class="sxs-lookup"><span data-stu-id="ed96f-226">Multiple email addresses are separated by semicolons, the same way that you do in Microsoft Office Outlook email messages.</span></span> <span data-ttu-id="ed96f-227">还可以指定分发组作为收件人，以便更容易和更有效地管理收件人列表。</span><span class="sxs-lookup"><span data-stu-id="ed96f-227">You can also specify distribution groups as recipients, which makes it easier and more efficient to manage the recipient list.</span></span> <span data-ttu-id="ed96f-228">如果在您创建警报定义时 SharePoint 可以确定您的电子邮件地址，则您的电子邮件地址将自动添加到收件人列表中；否则，您需要显式将您自己作为收件人添加。</span><span class="sxs-lookup"><span data-stu-id="ed96f-228">If SharePoint can determine your email address when you are creating an alert definition, your email address is automatically added to the recipients list; otherwise, you need to explicitly add yourself as a recipient.</span></span>

 <span data-ttu-id="ed96f-229">电子邮件的默认主题为的\*\*数据警报 \<alert name> \*\*。</span><span class="sxs-lookup"><span data-stu-id="ed96f-229">The default subject of the email is **Data alert for \<alert name>**.</span></span> <span data-ttu-id="ed96f-230">您可以更改主题以适合您的需要。</span><span class="sxs-lookup"><span data-stu-id="ed96f-230">You can change the subject to fit your needs.</span></span>

 <span data-ttu-id="ed96f-231">还可以提供一个说明以包含在 **“说明”** 选项的数据警报消息中。</span><span class="sxs-lookup"><span data-stu-id="ed96f-231">You can also provide a description to include in the data alert message in the **Description** option.</span></span> <span data-ttu-id="ed96f-232">包含说明（尤其如果您具有类似的数据警报）将帮助您快速区分和了解您的警报消息。</span><span class="sxs-lookup"><span data-stu-id="ed96f-232">Including a description, especially if you have data alerts that are similar, will help you quickly differentiate and understand your alert messages.</span></span> <span data-ttu-id="ed96f-233">除了在报表服务器满足指定规则时发送的警报消息之外，在发生错误时还向所有收件人发送一条警报消息。</span><span class="sxs-lookup"><span data-stu-id="ed96f-233">In addition to the alert message that is sent when report data satisfied the specified rules, an alert message is sent to all recipients when an error occurs.</span></span> <span data-ttu-id="ed96f-234">有关详细信息，请参阅 [Data Alert Messages](../../2014/reporting-services/data-alert-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="ed96f-234">For more information, see [Data Alert Messages](../../2014/reporting-services/data-alert-messages.md).</span></span>

 <span data-ttu-id="ed96f-235">有关如何生成电子邮件的详细信息，请参阅 [Reporting Services 数据警报](../ssms/agent/alerts.md)。</span><span class="sxs-lookup"><span data-stu-id="ed96f-235">For more information about how the email is generated, see [Reporting Services Data Alerts](../ssms/agent/alerts.md).</span></span>

##  <a name="create-a-data-alert-definition"></a><a name="CreateAlert"></a> <span data-ttu-id="ed96f-236">创建数据警报定义</span><span class="sxs-lookup"><span data-stu-id="ed96f-236">Create a Data Alert Definition</span></span>
 <span data-ttu-id="ed96f-237">如果您被授予了 SharePoint 的“查看项”和“创建警报”权限，只要报表使用存储的凭据或没有凭据，您就可以为您有权查看的任何报表创建数据警报定义。</span><span class="sxs-lookup"><span data-stu-id="ed96f-237">If you are granted the SharePoint View Items and Create Alerts permissions you can create a data alert definition for any report that you have permission to view as long as the report uses stored credentials or no credentials.</span></span> <span data-ttu-id="ed96f-238">您从 SharePoint 库运行该报表。</span><span class="sxs-lookup"><span data-stu-id="ed96f-238">You run the report from a SharePoint library.</span></span> <span data-ttu-id="ed96f-239">您可在数据警报设计器中使用的数据来自该报表。</span><span class="sxs-lookup"><span data-stu-id="ed96f-239">The data that is available for you to use in Data Alert Designer comes from the report.</span></span> <span data-ttu-id="ed96f-240">如果对此报表进行参数化，你可能需要使用不同的参数值来运行此报表，从而确保你感兴趣的数据出现在此报表中。</span><span class="sxs-lookup"><span data-stu-id="ed96f-240">If the report is parameterized, you might need to run the report using different parameter values to ensure the data that you are interested in appears in the report.</span></span> <span data-ttu-id="ed96f-241">在该报表打开后，单击报表工具栏上 **“操作”** 菜单中的 **“新建数据警报”** 选项，以便打开数据警报设计器。</span><span class="sxs-lookup"><span data-stu-id="ed96f-241">After the report is open, you click the **New Data Alert** option on the **Actions** menu on the report toolbar to open Data Alert Designer.</span></span> <span data-ttu-id="ed96f-242">下图显示如何打开数据警报设计器。</span><span class="sxs-lookup"><span data-stu-id="ed96f-242">The following picture shows you how to open Data Alert Designer.</span></span>

 <span data-ttu-id="ed96f-243">![从 SharePoint 库打开警报设计器](media/rs-openalertdesigneriw.gif "从 SharePoint 库打开警报设计器")</span><span class="sxs-lookup"><span data-stu-id="ed96f-243">![Open Alert Designer from SharePoint library](media/rs-openalertdesigneriw.gif "Open Alert Designer from SharePoint library")</span></span>

 <span data-ttu-id="ed96f-244">有关详细信息，请参阅 [在数据警报设计器中创建数据警报](create-a-data-alert-in-data-alert-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="ed96f-244">For more information, see [Create a Data Alert in Data Alert Designer](create-a-data-alert-in-data-alert-designer.md).</span></span>


##  <a name="save-a-data-alert-definition"></a><a name="SaveAlert"></a> <span data-ttu-id="ed96f-245">保存数据警报定义</span><span class="sxs-lookup"><span data-stu-id="ed96f-245">Save a Data Alert Definition</span></span>
 <span data-ttu-id="ed96f-246">数据警报设计器显示将保存数据警报定义的站点的 URL。</span><span class="sxs-lookup"><span data-stu-id="ed96f-246">Data Alert Designer displays the URL of the site where the data alert definition will be saved.</span></span> <span data-ttu-id="ed96f-247">数据警报定义始终作为报表保存到相同的站点。</span><span class="sxs-lookup"><span data-stu-id="ed96f-247">Data alert definitions are always saved to the same site as the reports.</span></span>

> [!NOTE]
>  <span data-ttu-id="ed96f-248">您选择运行报表的参数值保存在警报定义中，并在作为处理警报定义的一个步骤重新运行报表时使用。</span><span class="sxs-lookup"><span data-stu-id="ed96f-248">The parameter values you chose to run the report are saved in the alert definition and will be used when report is rerun as a step in processing the alert definition.</span></span> <span data-ttu-id="ed96f-249">若要使用不同的参数值，您必须创建一个新的警报定义。</span><span class="sxs-lookup"><span data-stu-id="ed96f-249">To use different parameter values, you must create a new alert definition.</span></span>

 <span data-ttu-id="ed96f-250">在保存警报定义前，要对该定义进行验证。</span><span class="sxs-lookup"><span data-stu-id="ed96f-250">Before the alert definition is saved, it is validated.</span></span> <span data-ttu-id="ed96f-251">您必须首先纠正所有错误，然后才能成功保存警报定义。</span><span class="sxs-lookup"><span data-stu-id="ed96f-251">You must correct any errors before the alert definition can be saved successfully.</span></span> <span data-ttu-id="ed96f-252">有关详细信息，请参阅 [在数据警报设计器中创建数据警报](create-a-data-alert-in-data-alert-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="ed96f-252">For more information, see [Create a Data Alert in Data Alert Designer](create-a-data-alert-in-data-alert-designer.md).</span></span>


##  <a name="edit-a-data-alert-definition"></a><a name="EditAlert"></a> <span data-ttu-id="ed96f-253">编辑数据警报定义</span><span class="sxs-lookup"><span data-stu-id="ed96f-253">Edit a Data Alert Definition</span></span>
 <span data-ttu-id="ed96f-254">在保存数据警报定义后，可以在数据警报设计器中重新打开和编辑该定义。</span><span class="sxs-lookup"><span data-stu-id="ed96f-254">After you save your data alert definition, you can reopen and then edit it in Data Alert Designer.</span></span> <span data-ttu-id="ed96f-255">您可以添加、更改或删除规则和子句以及更改计划和电子邮件设置。</span><span class="sxs-lookup"><span data-stu-id="ed96f-255">You can add, change, or delete rules and clauses and change the schedule and email settings.</span></span> <span data-ttu-id="ed96f-256">如果警报使用的报表数据馈送已更改，并且不再提供警报规则引用的字段，或者这些字段的数据类型或其他元数据已更改，则该警报定义将不再有效，您必须纠正错误后才能重新保存它。</span><span class="sxs-lookup"><span data-stu-id="ed96f-256">If the report data feed that the alert uses has changed and no longer provides the fields that the alert rules reference or the data types or other metadata of the fields have changed, the alert definition is no longer valid, and you must correct it before you can resave it.</span></span> <span data-ttu-id="ed96f-257">如果您要使用不同的数据馈送，则必须创建一个新的警报定义。</span><span class="sxs-lookup"><span data-stu-id="ed96f-257">If you want to use a different data feed, you must create a new alert definition.</span></span>

 <span data-ttu-id="ed96f-258">若要编辑数据警报定义，请在警报管理器中右键单击，然后单击 **“编辑”**。</span><span class="sxs-lookup"><span data-stu-id="ed96f-258">To edit a data alert definition, you right click it in Data Alert Manager and click **Edit**.</span></span> <span data-ttu-id="ed96f-259">下图显示了数据警报管理器中数据警报上的上下文菜单。</span><span class="sxs-lookup"><span data-stu-id="ed96f-259">The following picture shows you the context menu on a data alert in Data Alert Manager.</span></span>

 <span data-ttu-id="ed96f-260">![通过单击“编辑”打开数据警报设计器](media/rs-alertmanageriwopendesigner.gif "通过单击“编辑”打开数据警报设计器")</span><span class="sxs-lookup"><span data-stu-id="ed96f-260">![Open Data Alert Designer by clicking Edit](media/rs-alertmanageriwopendesigner.gif "Open Data Alert Designer by clicking Edit")</span></span>

 <span data-ttu-id="ed96f-261">有关详细信息，请参阅 [在警报设计器中编辑数据警报](edit-a-data-alert-in-alert-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="ed96f-261">For more information, see [Edit a Data Alert in Alert Designer](edit-a-data-alert-in-alert-designer.md).</span></span>


##  <a name="related-tasks"></a><a name="HowTo"></a> <span data-ttu-id="ed96f-262">相关任务</span><span class="sxs-lookup"><span data-stu-id="ed96f-262">Related Tasks</span></span>
 <span data-ttu-id="ed96f-263">本节列出的过程介绍如何创建和编辑警报。</span><span class="sxs-lookup"><span data-stu-id="ed96f-263">This section lists procedures that show you how to create and edit alerts.</span></span>

-   [<span data-ttu-id="ed96f-264">在警报设计器中编辑数据警报</span><span class="sxs-lookup"><span data-stu-id="ed96f-264">Edit a Data Alert in Alert Designer</span></span>](edit-a-data-alert-in-alert-designer.md)

-   [<span data-ttu-id="ed96f-265">在数据警报设计器中创建数据警报</span><span class="sxs-lookup"><span data-stu-id="ed96f-265">Create a Data Alert in Data Alert Designer</span></span>](create-a-data-alert-in-data-alert-designer.md)


## <a name="see-also"></a><span data-ttu-id="ed96f-266">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ed96f-266">See Also</span></span>
 <span data-ttu-id="ed96f-267">[Reporting Services 数据警报](../ssms/agent/alerts.md)[管理器警报管理员](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md)</span><span class="sxs-lookup"><span data-stu-id="ed96f-267">[Reporting Services Data Alerts](../ssms/agent/alerts.md) [Data Alert Manager for Alerting Administrators](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md)</span></span>


