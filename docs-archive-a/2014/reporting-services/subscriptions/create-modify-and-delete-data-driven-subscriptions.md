---
title: 创建、修改和删除数据驱动订阅 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- query-based subscriptions [Reporting Services]
- queries [Reporting Services], data-driven subscriptions
- subscriptions [Reporting Services], data-driven
- data-driven subscriptions
ms.assetid: 0ba2093e-9393-4eb6-af06-9da10988cfaf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0ec7fad729e5a7bd0f75d7a524ba315b4511a7a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589429"
---
# <a name="create-modify-and-delete-a-data-driven-subscription"></a><span data-ttu-id="4d37f-102">Create, Modify, and Delete a Data-Driven Subscription</span><span class="sxs-lookup"><span data-stu-id="4d37f-102">Create, Modify, and Delete a Data-Driven Subscription</span></span>
  <span data-ttu-id="4d37f-103">数据驱动订阅是一种基于查询的订阅，可以在运行时获取用于处理该订阅的数据值。</span><span class="sxs-lookup"><span data-stu-id="4d37f-103">A data-driven subscription is a query-based subscription that gets the data values used for processing the subscription at run time.</span></span> <span data-ttu-id="4d37f-104">当触发订阅时，会处理一个查询以获取有关收件人、报表传递选项、呈现格式和参数设置的最新信息。</span><span class="sxs-lookup"><span data-stu-id="4d37f-104">When the subscription is triggered, a query is processed to get up-to-date information about recipients, report delivery options, rendering formats, and parameter settings.</span></span> <span data-ttu-id="4d37f-105">将查询结果与订阅定义相结合，以创建动态订阅，该订阅使用了已在雇员数据库、客户数据库或任何其他数据库（包含可用作订阅服务器数据的信息）中维护的数据。</span><span class="sxs-lookup"><span data-stu-id="4d37f-105">The query results are combined with the subscription definition to create a dynamic subscription that uses data you already maintain in an employee database, a customer database, or any other database that contains information that can be used as subscriber data.</span></span>  
  
||  
|-|  
|<span data-ttu-id="4d37f-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 本机模式 | SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="4d37f-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode &#124; SharePoint mode</span></span>|  
  
 <span data-ttu-id="4d37f-107">**本主题内容：**</span><span class="sxs-lookup"><span data-stu-id="4d37f-107">**In this topic:**</span></span>  
  
-   [<span data-ttu-id="4d37f-108">创建和修改数据驱动订阅</span><span class="sxs-lookup"><span data-stu-id="4d37f-108">Create and Modify a Data-Driven Subscription</span></span>](#bkmk_create_and_modify)  
  
-   [<span data-ttu-id="4d37f-109">定义检索订阅信息的查询</span><span class="sxs-lookup"><span data-stu-id="4d37f-109">Define a query that retrieves subscription information</span></span>](#bkmk_define_query)  
  
-   [<span data-ttu-id="4d37f-110">运行订阅</span><span class="sxs-lookup"><span data-stu-id="4d37f-110">Run a subscription</span></span>](#bkmk_run_subscription)  
  
-   [<span data-ttu-id="4d37f-111">管理和删除数据驱动订阅</span><span class="sxs-lookup"><span data-stu-id="4d37f-111">Manage and delete a data-driven subscription</span></span>](#bkmk_manage_and_delete)  
  
##  <a name="create-and-modify-a-data-driven-subscription"></a><a name="bkmk_create_and_modify"></a><span data-ttu-id="4d37f-112">创建和修改数据驱动订阅</span><span class="sxs-lookup"><span data-stu-id="4d37f-112">Create and Modify a Data-Driven Subscription</span></span>  
 <span data-ttu-id="4d37f-113">若要创建新的数据驱动订阅或修改现有订阅，请使用报表管理器中的“创建数据驱动订阅”页。</span><span class="sxs-lookup"><span data-stu-id="4d37f-113">To create a new data-driven subscription or modify an existing subscription, use the Create Data-Driven Subscription pages in Report Manager.</span></span> <span data-ttu-id="4d37f-114">这些页面将引导您完成创建或修改订阅的每一个步骤。</span><span class="sxs-lookup"><span data-stu-id="4d37f-114">These pages walk you through each step of creating or modifying a subscription.</span></span> <span data-ttu-id="4d37f-115">若要在创建订阅后访问该订阅，请使用“我的订阅”页和报表的“订阅”列表。</span><span class="sxs-lookup"><span data-stu-id="4d37f-115">To access a subscription after it is created, use the My Subscriptions page and the Subscriptions list of a report.</span></span> <span data-ttu-id="4d37f-116">若要了解如何创建数据驱动订阅，请参阅[创建数据驱动订阅（SSRS 教程）](../create-a-data-driven-subscription-ssrs-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="4d37f-116">To learn how to create a data-driven subscription, see [Create a Data-Driven Subscription &#40;SSRS Tutorial&#41;](../create-a-data-driven-subscription-ssrs-tutorial.md).</span></span>  
  
 <span data-ttu-id="4d37f-117">若要创建数据驱动订阅，请选择一个使用存储的凭据或不使用任何凭据的报表。</span><span class="sxs-lookup"><span data-stu-id="4d37f-117">To create a data-driven subscription, select a report that uses stored credentials or no credentials.</span></span> <span data-ttu-id="4d37f-118">在您创建数据驱动订阅时，请考虑将命名约定用于说明字段，以便可以轻松地将标准说明与数据驱动说明区分开来。</span><span class="sxs-lookup"><span data-stu-id="4d37f-118">When you create the data-driven subscription, consider using a naming convention for the description field so you can easily differentiate standard subscriptions from data-driven subscriptions.</span></span>  
  
#### <a name="to-create-a-data-driven-subscription-native-mode"></a><span data-ttu-id="4d37f-119">创建数据驱动订阅（本机模式）</span><span class="sxs-lookup"><span data-stu-id="4d37f-119">To create a data-driven subscription (Native Mode)</span></span>  
  
1.  <span data-ttu-id="4d37f-120">在报表管理器中，导航到包含该报表的文件夹，将鼠标悬停在该报表上，打开选项菜单并单击 **“管理”**。</span><span class="sxs-lookup"><span data-stu-id="4d37f-120">In Report Manager navigate to the folder containing the report, hover over the report, open the options menu and Click the **Manage.**</span></span>  
  
2.  <span data-ttu-id="4d37f-121">单击 **“订阅”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="4d37f-121">Click the **Subscriptions** tab.</span></span>  
  
3.  <span data-ttu-id="4d37f-122">单击 **“新建数据驱动订阅”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="4d37f-122">Click the **New Data-Driven Subscription** button.</span></span>  
  
#### <a name="to-create-a-data-driven-subscription-sharepoint-mode"></a><span data-ttu-id="4d37f-123">创建数据驱动订阅（SharePoint 模式）</span><span class="sxs-lookup"><span data-stu-id="4d37f-123">To create a data-driven subscription (SharePoint Mode)</span></span>  
  
1.  <span data-ttu-id="4d37f-124">在 SharePoint 文档库中，将鼠标悬停在该报表上，打开选项菜单并单击 **“管理订阅”** 。</span><span class="sxs-lookup"><span data-stu-id="4d37f-124">In the SharePoint document library, hover over the report, open the options menu and Click **Manage Subscriptions**.</span></span>  
  
2.  <span data-ttu-id="4d37f-125">单击 **“添加数据驱动订阅”** 。</span><span class="sxs-lookup"><span data-stu-id="4d37f-125">Click **Add Data-Driven Subscription**.</span></span>  
  
#### <a name="to-modify-an-existing-data-driven-subscription-native-mode"></a><span data-ttu-id="4d37f-126">修改现有的数据驱动订阅（本机模式）</span><span class="sxs-lookup"><span data-stu-id="4d37f-126">To modify an existing data-driven subscription (Native Mode)</span></span>  
  
1.  <span data-ttu-id="4d37f-127">在报表管理器导航到包含该报表的文件夹，将鼠标悬停在该报表上，打开 "选项" 菜单，然后单击 "**管理**"。</span><span class="sxs-lookup"><span data-stu-id="4d37f-127">In Report Manager navigate to the folder containing the report, hover over the report, open the options menu and Click the **Manage**.</span></span>  
  
2.  <span data-ttu-id="4d37f-128">单击 "**订阅**" 选项卡。或者单击报表管理器顶部的 "**我的订阅**" 链接</span><span class="sxs-lookup"><span data-stu-id="4d37f-128">Click the **Subscriptions** tab. Alternatively click the **My Subscriptions** link on at the tope of report manager</span></span>  
  
3.  <span data-ttu-id="4d37f-129">选择要修改的订阅。</span><span class="sxs-lookup"><span data-stu-id="4d37f-129">Select the subscription you want to modify.</span></span> <span data-ttu-id="4d37f-130">以下图标表示数据驱动订阅：![数据驱动订阅图标](../media/hlp-16subscriptiondd.gif "数据驱动订阅图标")</span><span class="sxs-lookup"><span data-stu-id="4d37f-130">The following icon indicates a data-driven subscription: ![Data-driven subscription icon](../media/hlp-16subscriptiondd.gif "Data-driven subscription icon")</span></span>  
  
#### <a name="to-modify-an-existing-data-driven-subscription-sharepoint-mode"></a><span data-ttu-id="4d37f-131">修改现有的数据驱动订阅（SharePoint 模式）</span><span class="sxs-lookup"><span data-stu-id="4d37f-131">To modify an existing data-driven subscription (SharePoint Mode)</span></span>  
  
1.  <span data-ttu-id="4d37f-132">在 SharePoint 文档库中，将鼠标悬停在该报表上，打开选项菜单并单击 **“管理订阅”** 。</span><span class="sxs-lookup"><span data-stu-id="4d37f-132">In the SharePoint document library, hover over the report, open the options menu and Click **Manage Subscriptions**.</span></span>  
  
2.  <span data-ttu-id="4d37f-133">选择要修改的订阅。</span><span class="sxs-lookup"><span data-stu-id="4d37f-133">Select the subscription you want to modify.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4d37f-134">您可以修改任何已指定的值。</span><span class="sxs-lookup"><span data-stu-id="4d37f-134">You can modify any value that is already specified.</span></span> <span data-ttu-id="4d37f-135">除了用来访问订阅服务器数据存储区的密码外，所有值都以最初创建时的形式显示。</span><span class="sxs-lookup"><span data-stu-id="4d37f-135">All values are presented as they were first created, except for the password that is used to access the subscriber data store.</span></span> <span data-ttu-id="4d37f-136">每次修改第二页或任何后续页上的值时，都必须重新键入密码。</span><span class="sxs-lookup"><span data-stu-id="4d37f-136">You must retype the password every time you modify values on the second page or any subsequent page.</span></span>  
  
 <span data-ttu-id="4d37f-137">创建数据驱动订阅之前，请确保满足下列要求：</span><span class="sxs-lookup"><span data-stu-id="4d37f-137">Before you can create a data-driven subscription, ensure that you satisfy the following requirements:</span></span>  
  
-   <span data-ttu-id="4d37f-138">**报表要求**。</span><span class="sxs-lookup"><span data-stu-id="4d37f-138">**Report requirements**.</span></span> <span data-ttu-id="4d37f-139">报表必须使用已存储的凭据或不使用任何凭据在运行时检索数据。</span><span class="sxs-lookup"><span data-stu-id="4d37f-139">The report must use stored credentials or no credentials to retrieve data at run time.</span></span> <span data-ttu-id="4d37f-140">不能订阅使用模拟凭据或委托凭据连接至外部数据源的报表；处理订阅时将无法使用创建或拥有订阅的用户的凭据。</span><span class="sxs-lookup"><span data-stu-id="4d37f-140">You cannot subscribe to a report that uses impersonated or delegated credentials to connect to an external data source; the credentials of the user who creates or owns the subscription will not be available when the subscription is processed.</span></span> <span data-ttu-id="4d37f-141">已存储的凭据可以是 Windows 帐户或数据库用户帐户。</span><span class="sxs-lookup"><span data-stu-id="4d37f-141">The stored credentials can be a Windows account or a database user account.</span></span> <span data-ttu-id="4d37f-142">有关详细信息，请参阅[为报表数据源指定凭据和连接信息](../report-data/specify-credential-and-connection-information-for-report-data-sources.md)</span><span class="sxs-lookup"><span data-stu-id="4d37f-142">For more information, see [Specify Credential and Connection Information for Report Data Sources](../report-data/specify-credential-and-connection-information-for-report-data-sources.md).</span></span>  
  
     <span data-ttu-id="4d37f-143">无法订阅使用了作为数据源的模型或包含模型项安全设置的模型的报表生成器报表。</span><span class="sxs-lookup"><span data-stu-id="4d37f-143">You cannot subscribe to a Report Builder report that uses a model as a data source and the model contains model item security settings.</span></span> <span data-ttu-id="4d37f-144">此限制仅适用于使用模型项安全性的报表。</span><span class="sxs-lookup"><span data-stu-id="4d37f-144">Only reports that use model item security are included in this restriction.</span></span>  
  
     <span data-ttu-id="4d37f-145">对于包含 `User!UserID` 表达式的报表，您无法创建数据驱动订阅。</span><span class="sxs-lookup"><span data-stu-id="4d37f-145">You cannot create a data-driven subscription on a report that contains the `User!UserID` expression.</span></span>  
  
-   <span data-ttu-id="4d37f-146">**数据要求**。</span><span class="sxs-lookup"><span data-stu-id="4d37f-146">**Data requirements**.</span></span> <span data-ttu-id="4d37f-147">必须具有包含订阅服务器数据的可访问外部数据源。</span><span class="sxs-lookup"><span data-stu-id="4d37f-147">You must have an accessible external data source that contains subscriber data.</span></span>  
  
-   <span data-ttu-id="4d37f-148">**用户要求**。</span><span class="sxs-lookup"><span data-stu-id="4d37f-148">**User requirements**.</span></span> <span data-ttu-id="4d37f-149">订阅的作者必须具有“管理报表”和“管理所有订阅”的权限。</span><span class="sxs-lookup"><span data-stu-id="4d37f-149">The author of the subscription must have permission to "Manage reports" and "Manage all subscriptions."</span></span> <span data-ttu-id="4d37f-150">有关项级任务权限的详细信息，请参阅 [任务和权限](../security/tasks-and-permissions.md)。</span><span class="sxs-lookup"><span data-stu-id="4d37f-150">For more information about item-level task permissions, see [Tasks and Permissions](../security/tasks-and-permissions.md).</span></span> <span data-ttu-id="4d37f-151">作者还须具有访问包含订阅服务器数据的外部数据源所需的凭据。</span><span class="sxs-lookup"><span data-stu-id="4d37f-151">The author must also have the necessary credentials to access the external data source that contains subscriber data.</span></span>  
  
##  <a name="define-a-query-that-retrieves-subscription-information"></a><a name="bkmk_define_query"></a><span data-ttu-id="4d37f-152">定义用于检索订阅信息的查询</span><span class="sxs-lookup"><span data-stu-id="4d37f-152">Define a query that retrieves subscription information</span></span>  
 <span data-ttu-id="4d37f-153">数据驱动订阅必须指定一个用于检索订阅服务器数据的查询或命令。</span><span class="sxs-lookup"><span data-stu-id="4d37f-153">A data-driven subscription must specify a query or command that retrieves subscriber data.</span></span> <span data-ttu-id="4d37f-154">查询应为每个订阅服务器生成一行。</span><span class="sxs-lookup"><span data-stu-id="4d37f-154">The query should produce one row for each subscriber.</span></span> <span data-ttu-id="4d37f-155">如果使用的是电子邮件传递扩展插件，则查询应为每个订阅服务器返回一个有效的电子邮件别名。</span><span class="sxs-lookup"><span data-stu-id="4d37f-155">If you are using the e-mail delivery extension, the query should return a valid e-mail alias for each subscriber.</span></span> <span data-ttu-id="4d37f-156">所执行的传递的数量取决于查询所返回的行数。</span><span class="sxs-lookup"><span data-stu-id="4d37f-156">The number of deliveries that are made is based on the number of rows returned by the query.</span></span> <span data-ttu-id="4d37f-157">如果行集中包含 10,000 行，则该订阅将传递 10,000 个报表。</span><span class="sxs-lookup"><span data-stu-id="4d37f-157">If the row set consists of 10,000 rows, the subscription delivers 10,000 reports.</span></span>  
  
 <span data-ttu-id="4d37f-158">如果执行查询很耗时，则可以增加超时值以允许进行其他处理。</span><span class="sxs-lookup"><span data-stu-id="4d37f-158">If executing the query is time-consuming, you can increase the time-out value to accommodate additional processing.</span></span>  
  
 <span data-ttu-id="4d37f-159">必须在此步骤中对查询进行验证才能继续。</span><span class="sxs-lookup"><span data-stu-id="4d37f-159">For this step, the query must be validated before you continue.</span></span> <span data-ttu-id="4d37f-160">验证操作并不处理查询，但它的确会返回行集中所有列的列表，以便可以在后续选择中引用这些列。</span><span class="sxs-lookup"><span data-stu-id="4d37f-160">Validation does not process the query, but it does return a list of all columns that are in the row set so that you can reference the columns in subsequent selections.</span></span> <span data-ttu-id="4d37f-161">如果查询未能通过验证，则将无法继续操作。</span><span class="sxs-lookup"><span data-stu-id="4d37f-161">If the query fails to validate, you cannot continue.</span></span> <span data-ttu-id="4d37f-162">如果查询语法不正确或者如果与数据源的连接无效，则查询将无法通过验证。</span><span class="sxs-lookup"><span data-stu-id="4d37f-162">A query fails to validate if the query syntax is incorrect or if the connection to the data source is not valid.</span></span> <span data-ttu-id="4d37f-163">可使用 **“上一步”** 按钮更正数据源。</span><span class="sxs-lookup"><span data-stu-id="4d37f-163">Use the **Back** button to make corrections to the data source.</span></span>  
  
##  <a name="run-a-subscription"></a><a name="bkmk_run_subscription"></a><span data-ttu-id="4d37f-164">运行订阅</span><span class="sxs-lookup"><span data-stu-id="4d37f-164">Run a subscription</span></span>  
 <span data-ttu-id="4d37f-165">配置订阅处理的条件。</span><span class="sxs-lookup"><span data-stu-id="4d37f-165">You configure the conditions for subscription processing.</span></span> <span data-ttu-id="4d37f-166">你可以配置一个计划，也可以触发订阅以便与报表执行快照的更新保持一致。</span><span class="sxs-lookup"><span data-stu-id="4d37f-166">You can configure a schedule, or you can trigger the subscription to coincide with updates to a report execution snapshot.</span></span>  
  
 <span data-ttu-id="4d37f-167">![注意](../media/rs-fyinote.png "注意")虽然用户界面中没有可用于立即运行订阅的功能，但你可以使用一个简单的 Windows PowerShell 脚本来触发订阅运行。</span><span class="sxs-lookup"><span data-stu-id="4d37f-167">![note](../media/rs-fyinote.png "note") While there is no feature in the user interface that you can use to immediately run a subscription, you can use a simple Windows PowerShell script to trigger a subscription to run.</span></span> <span data-ttu-id="4d37f-168">有关详细信息，请参阅[使用 PowerShell 更改和列出 Reporting Services 订阅所有者和运行订阅](manage-subscription-owners-and-run-subscription-powershell.md)中的 "脚本：运行 (火灾) 单个订阅" 部分。</span><span class="sxs-lookup"><span data-stu-id="4d37f-168">For more information, see the "Script: Run (fire) a single subscription" section of [Use PowerShell to Change and List Reporting Services Subscription Owners and Run a Subscription](manage-subscription-owners-and-run-subscription-powershell.md).</span></span>  
  
 <span data-ttu-id="4d37f-169">运行数据驱动订阅的计划和条件与处理标准订阅相同。</span><span class="sxs-lookup"><span data-stu-id="4d37f-169">Schedule and conditions for running a data-driven subscriptions is the same as processing for standard subscriptions.</span></span>  
  
##  <a name="manage-and-delete-a-data-driven-subscription"></a><a name="bkmk_manage_and_delete"></a><span data-ttu-id="4d37f-170">管理和删除数据驱动订阅</span><span class="sxs-lookup"><span data-stu-id="4d37f-170">Manage and delete a data-driven subscription</span></span>  
 <span data-ttu-id="4d37f-171">不能通过报表管理器的“管理作业”页来停止或删除正在进行的数据驱动订阅。</span><span class="sxs-lookup"><span data-stu-id="4d37f-171">A data-driven subscription that is in progress cannot be stopped or deleted through the Manage Jobs page of Report Manager.</span></span> <span data-ttu-id="4d37f-172">因此，使用共享计划触发数据驱动订阅是有利的。</span><span class="sxs-lookup"><span data-stu-id="4d37f-172">For this reason, it is advantageous to use a shared schedule to trigger data-driven subscription.</span></span> <span data-ttu-id="4d37f-173">在这种情况下，如果要暂时禁止处理某个订阅，只需暂停触发该订阅的计划即可。</span><span class="sxs-lookup"><span data-stu-id="4d37f-173">That way, if you want to temporarily prevent a subscription from processing, you can pause the schedule that triggers the subscription.</span></span> <span data-ttu-id="4d37f-174">有关详细信息，请参阅 [创建和管理本机模式报表服务器的订阅](../create-manage-subscriptions-native-mode-report-servers.md)。</span><span class="sxs-lookup"><span data-stu-id="4d37f-174">For more information, see [Create and Manage Subscriptions for Native Mode Report Servers](../create-manage-subscriptions-native-mode-report-servers.md).</span></span>  
  
 <span data-ttu-id="4d37f-175">若要删除数据驱动订阅，请从“我的订阅”页或报表的“订阅”页中选定该订阅，再单击 **“删除”**。</span><span class="sxs-lookup"><span data-stu-id="4d37f-175">To delete a data-driven subscription, select it from the My Subscriptions page or the Subscriptions page of a report and then click **Delete**.</span></span>  
  
 <span data-ttu-id="4d37f-176">有关如何取消数据驱动订阅的说明，请参阅 [管理运行中的进程](manage-a-running-process.md)。</span><span class="sxs-lookup"><span data-stu-id="4d37f-176">For instructions on how to cancel a data-driven subscription, see [Manage a Running Process](manage-a-running-process.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d37f-177">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4d37f-177">See Also</span></span>  
 <span data-ttu-id="4d37f-178">[在纯模式下创建、修改和删除标准订阅 &#40;Reporting Services&#41;](create-and-manage-subscriptions-for-native-mode-report-servers.md) </span><span class="sxs-lookup"><span data-stu-id="4d37f-178">[Create, Modify, and Delete Standard Subscriptions &#40;Reporting Services in Native Mode&#41;](create-and-manage-subscriptions-for-native-mode-report-servers.md) </span></span>  
 <span data-ttu-id="4d37f-179">[订阅和传递 (Reporting Services)](subscriptions-and-delivery-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="4d37f-179">[Subscriptions and Delivery &#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md) </span></span>  
 <span data-ttu-id="4d37f-180">[报表管理器（SSRS 本机模式）](../report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="4d37f-180">[Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="4d37f-181">[创建和管理本机模式报表服务器的订阅](../create-manage-subscriptions-native-mode-report-servers.md) </span><span class="sxs-lookup"><span data-stu-id="4d37f-181">[Create and Manage Subscriptions for Native Mode Report Servers](../create-manage-subscriptions-native-mode-report-servers.md) </span></span>  
 <span data-ttu-id="4d37f-182">[订阅页 &#40;报表管理器&#41;](../subscriptions-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="4d37f-182">[Subscriptions Page &#40;Report Manager&#41;](../subscriptions-page-report-manager.md) </span></span>  
 [<span data-ttu-id="4d37f-183">“我的订阅”页（报表管理器）</span><span class="sxs-lookup"><span data-stu-id="4d37f-183">My Subscriptions Page &#40;Report Manager&#41;</span></span>](../my-subscriptions-page-report-manager.md)  
  
  
