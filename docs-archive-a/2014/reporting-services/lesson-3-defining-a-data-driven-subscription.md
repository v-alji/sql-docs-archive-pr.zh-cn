---
title: 第 3 课：定义数据驱动订阅 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 89197b9b-7502-4fe2-bea3-ed7943eebf3b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d1bbc25bdd08b369180e31378a6d25a595badbcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694288"
---
# <a name="lesson-3-defining-a-data-driven-subscription"></a><span data-ttu-id="d0457-102">Lesson 3: Defining a Data-Driven Subscription</span><span class="sxs-lookup"><span data-stu-id="d0457-102">Lesson 3: Defining a Data-Driven Subscription</span></span>
  <span data-ttu-id="d0457-103">在本课程中，您将使用数据驱动订阅页来连接订阅数据源，生成一个检索订阅数据的查询，然后将结果集映射到报表和传递选项。</span><span class="sxs-lookup"><span data-stu-id="d0457-103">In this lesson, you use the data-driven subscription pages to connect to a subscription data source, build a query that retrieves subscription data, and map the result set to report and delivery options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d0457-104">开始操作之前，请确认 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 代理服务正在运行。</span><span class="sxs-lookup"><span data-stu-id="d0457-104">Before you start, verify that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent service is running.</span></span> <span data-ttu-id="d0457-105">如果该代理服务未运行，则无法保存订阅。</span><span class="sxs-lookup"><span data-stu-id="d0457-105">If it is not running, you cannot save the subscription.</span></span>  
  
 <span data-ttu-id="d0457-106">本课程假设您已经完成了第 1 课和第 2 课，并且报表数据源使用存储的凭据。</span><span class="sxs-lookup"><span data-stu-id="d0457-106">This lesson assumes you completed Lesson 1 and Lesson 2 and that the report data source uses stored credentials.</span></span>  <span data-ttu-id="d0457-107">有关详细信息，请参阅 [第 2 课：修改报表数据源属性](../reporting-services/lesson-2-modifying-the-report-data-source-properties.md)</span><span class="sxs-lookup"><span data-stu-id="d0457-107">For more information, see [Lesson 2: Modifying the Report Data Source Properties](../reporting-services/lesson-2-modifying-the-report-data-source-properties.md)</span></span>  
  
 <span data-ttu-id="d0457-108">本主题内容：</span><span class="sxs-lookup"><span data-stu-id="d0457-108">In this topic:</span></span>  
  
-   [<span data-ttu-id="d0457-109">启动数据驱动订阅向导</span><span class="sxs-lookup"><span data-stu-id="d0457-109">Start the Data-Driven Subscription Wizard</span></span>](#bkmk_startwizard)  
  
-   [<span data-ttu-id="d0457-110">步骤 1 - 定义说明</span><span class="sxs-lookup"><span data-stu-id="d0457-110">Step 1 - Define a description</span></span>](#bkmk_definesubscription)  
  
-   [<span data-ttu-id="d0457-111">步骤 2 - 定义与订阅服务器数据源的连接</span><span class="sxs-lookup"><span data-stu-id="d0457-111">Step 2 - Define a Connection to the Subscriber Data Source</span></span>](#bkmk_defineconnectiontosubscriber)  
  
-   [<span data-ttu-id="d0457-112">步骤 3 - 定义检索订阅服务器数据的查询</span><span class="sxs-lookup"><span data-stu-id="d0457-112">Step 3 - Define a Query to Retrieve Subscriber data</span></span>](#bkmk_definequery)  
  
-   [<span data-ttu-id="d0457-113">步骤 4 - 设置传递选项</span><span class="sxs-lookup"><span data-stu-id="d0457-113">Step 4 - Set Delivery Options</span></span>](#bkmk_set_deliveryoptions)  
  
-   [<span data-ttu-id="d0457-114">步骤 5 - 配置参数值以改变报表输出</span><span class="sxs-lookup"><span data-stu-id="d0457-114">Step 5 - Configure a Parameter Value to Very Report Output</span></span>](#bkmk_configure_parameter)  
  
-   [<span data-ttu-id="d0457-115">步骤 6 - 计划订阅</span><span class="sxs-lookup"><span data-stu-id="d0457-115">Step 6 - To Schedule a Subscription</span></span>](#bkmk_schedule_subscription)  
  
##  <a name="start-the-data-driven-subscription-wizard"></a><a name="bkmk_startwizard"></a><span data-ttu-id="d0457-116">启动数据驱动订阅向导</span><span class="sxs-lookup"><span data-stu-id="d0457-116">Start the Data-Driven Subscription Wizard</span></span>  
  
1.  <span data-ttu-id="d0457-117">在报表管理器中，单击 **“主文件夹”**，导航到包含 **Sales Orders** 报表的文件夹。</span><span class="sxs-lookup"><span data-stu-id="d0457-117">In Report Manager, click **Home**, and navigate to the folder containing the **Sales Orders** report.</span></span>  
  
2.  <span data-ttu-id="d0457-118">在该报表的上下文菜单中，单击 **“管理”**，然后单击 **“订阅”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="d0457-118">In the context menu of the report, click **Manage**, and then click the **Subscriptions** tab.</span></span>  
  
3.  <span data-ttu-id="d0457-119">单击 "**新建数据驱动订阅**"。</span><span class="sxs-lookup"><span data-stu-id="d0457-119">Click **New Data-driven Subscription**.</span></span> <span data-ttu-id="d0457-120">如果看不到此按钮，则说明您不具备“内容管理员”权限。</span><span class="sxs-lookup"><span data-stu-id="d0457-120">If you do not see this button, you do not have Content Manager permissions.</span></span>  
  
##  <a name="step-1---define-a-description"></a><a name="bkmk_definesubscription"></a><span data-ttu-id="d0457-121">步骤 1-定义说明</span><span class="sxs-lookup"><span data-stu-id="d0457-121">Step 1 - Define a description</span></span>  
  
1.  <span data-ttu-id="d0457-122">在说明中键入 **销售订单传递** 。</span><span class="sxs-lookup"><span data-stu-id="d0457-122">Type **Sales Order delivery** in description.</span></span>  
  
2.  <span data-ttu-id="d0457-123">为 **“指定通知收件人的方式”** 选择 **“Windows 文件共享”**。</span><span class="sxs-lookup"><span data-stu-id="d0457-123">Select **Windows FileShare** for **Specify how recipients are notified**.</span></span>  
  
3.  <span data-ttu-id="d0457-124">选中 **“仅为此订阅指定”**，然后单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="d0457-124">Select **Specify for this subscription only**, and then click **Next**.</span></span>  
  
##  <a name="step-2---define-a-connection-to-the-subscriber-data-source"></a><a name="bkmk_defineconnectiontosubscriber"></a><span data-ttu-id="d0457-125">步骤 2-定义与订阅服务器数据源的连接</span><span class="sxs-lookup"><span data-stu-id="d0457-125">Step 2 - Define a Connection to the Subscriber Data Source</span></span>  
  
1.  <span data-ttu-id="d0457-126">选择 **“Microsoft SQL Server”** 作为数据源类型。</span><span class="sxs-lookup"><span data-stu-id="d0457-126">Select **Microsoft SQL Server** as the data source type.</span></span>  
  
2.  <span data-ttu-id="d0457-127">在“连接字符串”中，键入以下连接字符串：</span><span class="sxs-lookup"><span data-stu-id="d0457-127">In Connection string, type the following connection string:</span></span>  
  
    ```  
    data source=localhost; initial catalog=Subscribers  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="d0457-128"> 订阅服务器是您在第 1 课中创建的数据库。</span><span class="sxs-lookup"><span data-stu-id="d0457-128">Subscribers is the database you created in lesson 1.</span></span>  
  
3.  <span data-ttu-id="d0457-129">单击 **“安全存储在报表服务器中的凭据”**。</span><span class="sxs-lookup"><span data-stu-id="d0457-129">Click **Credentials stored securely in the report server**.</span></span>  
  
4.  <span data-ttu-id="d0457-130">在 **“用户名”** 和 **“密码”** 中，键入您的域用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="d0457-130">In **User Name** and **Password**, type your domain user name and password.</span></span> <span data-ttu-id="d0457-131">请在指定 **“用户名”** 时同时包括域和用户帐户。</span><span class="sxs-lookup"><span data-stu-id="d0457-131">Include both the domain and user account when specifying **User Name**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d0457-132">用于连接到订阅服务器数据源的凭据不会传递回 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d0457-132">Credentials used to connect to a subscriber data source are not passed back to [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="d0457-133">如果以后修改了该订阅，则必须重新键入连接到该数据源所用的密码。</span><span class="sxs-lookup"><span data-stu-id="d0457-133">If you modify the subscription later, you must retype the password used to connect to the data source.</span></span>  
  
5.  <span data-ttu-id="d0457-134">选择 **“在与数据源建立连接时用作 Windows 凭据”**，再单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="d0457-134">Select **Use as windows credentials when connecting to the data source**, and then click **Next**.</span></span>  
  
##  <a name="step-3---define-a-query-to-retrieve-subscriber-data"></a><a name="bkmk_definequery"></a><span data-ttu-id="d0457-135">步骤 3-定义检索订阅服务器数据的查询</span><span class="sxs-lookup"><span data-stu-id="d0457-135">Step 3 - Define a Query to Retrieve Subscriber data</span></span>  
  
1.  <span data-ttu-id="d0457-136">在查询框中，键入以下查询：</span><span class="sxs-lookup"><span data-stu-id="d0457-136">In the query box, type the following query:</span></span>  
  
    ```  
    Select * from OrderInfo  
    ```  
  
2.  <span data-ttu-id="d0457-137">指定 30 秒的超时。</span><span class="sxs-lookup"><span data-stu-id="d0457-137">Specify a time-out of 30 seconds.</span></span>  
  
3.  <span data-ttu-id="d0457-138">单击 **“验证”**，再单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="d0457-138">Click **Validate**, and then click **Next**.</span></span>  
  
##  <a name="step-4---set-delivery-options"></a><a name="bkmk_set_deliveryoptions"></a><span data-ttu-id="d0457-139">步骤 4-设置传递选项</span><span class="sxs-lookup"><span data-stu-id="d0457-139">Step 4 - Set Delivery Options</span></span>  
  
1.  <span data-ttu-id="d0457-140">对于 **“文件名”**，请选择 **“从数据库获取该值”**。</span><span class="sxs-lookup"><span data-stu-id="d0457-140">For **File name**, select **Get the value from the database**.</span></span> <span data-ttu-id="d0457-141">选择字段 **Order**。</span><span class="sxs-lookup"><span data-stu-id="d0457-141">Select the field **Order**.</span></span>  
  
2.  <span data-ttu-id="d0457-142">对于 **“路径”**，请选择 **“指定静态值”**。</span><span class="sxs-lookup"><span data-stu-id="d0457-142">For **Path**, select **Specify a static value**.</span></span> <span data-ttu-id="d0457-143">在“设置值”中，键入您拥有写入权限的公共文件共享的名称（例如，`\\mycomputer\public\myreports`）。</span><span class="sxs-lookup"><span data-stu-id="d0457-143">In Setting Value, type the name of a public file share for which you have write permissions (for example, `\\mycomputer\public\myreports`).</span></span>  
  
3.  <span data-ttu-id="d0457-144">对于 **“呈现格式”**，请选择 **“从数据库获取该值”**。</span><span class="sxs-lookup"><span data-stu-id="d0457-144">For **Render Format**, select **Get the value from the database**.</span></span> <span data-ttu-id="d0457-145">选择 "**格式**"。</span><span class="sxs-lookup"><span data-stu-id="d0457-145">Select **Format**.</span></span>  
  
4.  <span data-ttu-id="d0457-146">对于 **“写入模式”**，请选择 **“指定静态值”** 并且选择 **AutoIncrement**。</span><span class="sxs-lookup"><span data-stu-id="d0457-146">For **Write mode**, select **Specify a static value** and select **AutoIncrement**.</span></span>  
  
5.  <span data-ttu-id="d0457-147">对于 **“文件扩展名”**，请选择 **“指定静态值”** 并且选择 **True**。</span><span class="sxs-lookup"><span data-stu-id="d0457-147">For **File Extension**, select **Specify a static value** and select **True**.</span></span>  
  
6.  <span data-ttu-id="d0457-148">对于 **“用户名”**，请选择 **“指定静态值”**。</span><span class="sxs-lookup"><span data-stu-id="d0457-148">For **User name**, select **Specify a static value**.</span></span> <span data-ttu-id="d0457-149">键入您的域用户帐户。</span><span class="sxs-lookup"><span data-stu-id="d0457-149">Type your domain user account.</span></span> <span data-ttu-id="d0457-150">按以下格式输入： `<domain>\<account>`。</span><span class="sxs-lookup"><span data-stu-id="d0457-150">Enter it in this format: `<domain>\<account>`.</span></span> <span data-ttu-id="d0457-151">用户帐户需要对您在前面的步骤中配置的路径具有权限。</span><span class="sxs-lookup"><span data-stu-id="d0457-151">The user account needs to have permissions to the path you configured in the previous steps.</span></span>  
  
7.  <span data-ttu-id="d0457-152">对于 **“密码”**，请选择 **“指定静态值”**。</span><span class="sxs-lookup"><span data-stu-id="d0457-152">For **Password**, select **Specify a static value**.</span></span> <span data-ttu-id="d0457-153">键入您的密码。</span><span class="sxs-lookup"><span data-stu-id="d0457-153">Type your password.</span></span> <span data-ttu-id="d0457-154">请务必仔细键入密码。</span><span class="sxs-lookup"><span data-stu-id="d0457-154">Be sure that you type the password carefully.</span></span> <span data-ttu-id="d0457-155">向导不会对密码进行验证。</span><span class="sxs-lookup"><span data-stu-id="d0457-155">The wizard does not validate the password.</span></span>  
  
8.  <span data-ttu-id="d0457-156">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="d0457-156">Click **Next.**</span></span>  
  
##  <a name="step-5---configure-a-parameter-value-to-very-report-output"></a><a name="bkmk_configure_parameter"></a><span data-ttu-id="d0457-157">步骤 5-将参数值配置为非常报告输出</span><span class="sxs-lookup"><span data-stu-id="d0457-157">Step 5 - Configure a Parameter Value to Very Report Output</span></span>  
  
1.  <span data-ttu-id="d0457-158">对于 **OrderNumber**，请选择 **“从数据库获取该值”**。</span><span class="sxs-lookup"><span data-stu-id="d0457-158">For **OrderNumber**, select **Get the value from the database**.</span></span> <span data-ttu-id="d0457-159">在“值”中，选择 **Order**。</span><span class="sxs-lookup"><span data-stu-id="d0457-159">In Value, select **Order**.</span></span> <span data-ttu-id="d0457-160">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="d0457-160">Click **Next.**</span></span>  
  
##  <a name="step-6---to-schedule-a-subscription"></a><a name="bkmk_schedule_subscription"></a><span data-ttu-id="d0457-161">步骤 6-计划订阅</span><span class="sxs-lookup"><span data-stu-id="d0457-161">Step 6 - To Schedule a Subscription</span></span>  
  
1.  <span data-ttu-id="d0457-162">单击 **“根据为此订阅创建的计划”**，再单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="d0457-162">Click **On a schedule created for this subscription**, and then click **Next**.</span></span>  
  
2.  <span data-ttu-id="d0457-163">在 **“计划详细信息”** 中，单击 **“一次”**。</span><span class="sxs-lookup"><span data-stu-id="d0457-163">In **Schedule Details**, click **Once**.</span></span>  
  
3.  <span data-ttu-id="d0457-164">将开始时间指定为当前时间的前几分钟。</span><span class="sxs-lookup"><span data-stu-id="d0457-164">Specify a start time that is a few minutes ahead of the current time.</span></span>  
  
4.  <span data-ttu-id="d0457-165">单击“完成”。</span><span class="sxs-lookup"><span data-stu-id="d0457-165">Click **Finish**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="d0457-166">后续步骤</span><span class="sxs-lookup"><span data-stu-id="d0457-166">Next Steps</span></span>  
 <span data-ttu-id="d0457-167">订阅运行时，将有四个报表文件（分别属于 *Subscribers* 数据源中的各订单）发送到指定的文件共享中。</span><span class="sxs-lookup"><span data-stu-id="d0457-167">When the subscription runs, four report files will be delivered to the file share you specified, one for each order in the *Subscribers* data source.</span></span> <span data-ttu-id="d0457-168">每个发送的报表在数据（数据应当是订单特定的）、呈现格式和文件格式方面都将是唯一的。</span><span class="sxs-lookup"><span data-stu-id="d0457-168">Each delivery should be unique in terms of data (the data should be order-specific), rendering format, and file format.</span></span> <span data-ttu-id="d0457-169">可以打开共享文件夹中的每一个报表以验证是否每个版本都是根据您定义的订阅选项来自定义的。</span><span class="sxs-lookup"><span data-stu-id="d0457-169">You can open each report from the shared folder to verify that each version is customized based on the subscription options you defined.</span></span>  
  
 <span data-ttu-id="d0457-170">![按订阅创建的文件列表](../../2014/tutorials/media/ssrs-tutorial-datadriven-subscription-filelist.gif "按订阅创建的文件列表")</span><span class="sxs-lookup"><span data-stu-id="d0457-170">![List of files created by the subscription](../../2014/tutorials/media/ssrs-tutorial-datadriven-subscription-filelist.gif "List of files created by the subscription")</span></span>  
  
 <span data-ttu-id="d0457-171">报表管理器中的订阅页将包含订阅的 **“上次运行时间”** 日期和 **“状态”** 。</span><span class="sxs-lookup"><span data-stu-id="d0457-171">The subscription page in Report Manager will contain the **Last Run** date and **Status** of the subscription.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d0457-172">在订阅运行后刷新该页可查看更新后的信息。</span><span class="sxs-lookup"><span data-stu-id="d0457-172">Refresh the page after the subscription runs to see the updated information.</span></span>  
  
 <span data-ttu-id="d0457-173">![报表管理器中的订阅结果](../../2014/tutorials/media/ssrs-tutorial-datadriven-subscription-status-reportmanager.gif "报表管理器中的订阅结果")</span><span class="sxs-lookup"><span data-stu-id="d0457-173">![Subscription results in Report Manager](../../2014/tutorials/media/ssrs-tutorial-datadriven-subscription-status-reportmanager.gif "Subscription results in Report Manager")</span></span>  
  
 <span data-ttu-id="d0457-174">此步骤将结束“定义数据驱动订阅”教程。</span><span class="sxs-lookup"><span data-stu-id="d0457-174">This step concludes the tutorial "Defining a Data-Driven Subscription".</span></span> <span data-ttu-id="d0457-175">若要详细了解其他 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 教程，请参阅[SSRS&#41;Reporting Services 教程 &#40;](../reporting-services/reporting-services-tutorials-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="d0457-175">To learn more about other [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] tutorials, see [Reporting Services Tutorials &#40;SSRS&#41;](../reporting-services/reporting-services-tutorials-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0457-176">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d0457-176">See Also</span></span>  
 <span data-ttu-id="d0457-177">[创建数据驱动订阅（SSRS 教程）](../reporting-services/create-a-data-driven-subscription-ssrs-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="d0457-177">[Create a Data-Driven Subscription &#40;SSRS Tutorial&#41;](../reporting-services/create-a-data-driven-subscription-ssrs-tutorial.md) </span></span>  
 <span data-ttu-id="d0457-178">[订阅和传递 (Reporting Services)](subscriptions/subscriptions-and-delivery-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="d0457-178">[Subscriptions and Delivery &#40;Reporting Services&#41;](subscriptions/subscriptions-and-delivery-reporting-services.md) </span></span>  
 <span data-ttu-id="d0457-179">[Data-Driven Subscriptions](subscriptions/data-driven-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="d0457-179">[Data-Driven Subscriptions](subscriptions/data-driven-subscriptions.md) </span></span>  
 <span data-ttu-id="d0457-180">[创建、修改和删除数据驱动订阅](subscriptions/create-modify-and-delete-data-driven-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="d0457-180">[Create, Modify, and Delete a Data-Driven Subscription](subscriptions/create-modify-and-delete-data-driven-subscriptions.md) </span></span>  
 [<span data-ttu-id="d0457-181">使用外部数据源提供订阅方数据（数据驱动订阅）</span><span class="sxs-lookup"><span data-stu-id="d0457-181">Use an External Data Source for Subscriber Data &#40;Data-Driven Subscription&#41;</span></span>](subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md)  
  
  
