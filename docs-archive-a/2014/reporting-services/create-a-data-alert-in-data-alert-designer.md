---
title: 在数据警报设计器中创建数据警报| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 8464ab9d-afe1-4490-955f-9f3319bcbf8d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 19c3001d4663848c009a353baa068f237d4a0b5b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691135"
---
# <a name="create-a-data-alert-in-data-alert-designer"></a><span data-ttu-id="4f4c4-102">在数据警报设计器中创建数据警报</span><span class="sxs-lookup"><span data-stu-id="4f4c4-102">Create a Data Alert in Data Alert Designer</span></span>
  <span data-ttu-id="4f4c4-103">您在数据警报设计器中创建数据警报定义。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-103">You create data alert definitions in Data Alert Designer.</span></span> <span data-ttu-id="4f4c4-104">在您保存警报定义后，可以在数据警报设计器中重新打开、编辑和重新保存它们。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-104">After you save the alert definitions, you can reopen, edit, and then resave them in Data Alert Designer.</span></span> <span data-ttu-id="4f4c4-105">有关编辑警报定义的信息，请参阅 [在数据警报管理器中管理我的数据警报](manage-my-data-alerts-in-data-alert-manager.md) 和 [在警报设计器中编辑数据警报](edit-a-data-alert-in-alert-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-105">For information about editing alert definitions, see [Manage My Data Alerts in Data Alert Manager](manage-my-data-alerts-in-data-alert-manager.md) and [Edit a Data Alert in Alert Designer](edit-a-data-alert-in-alert-designer.md).</span></span>

### <a name="to-create-a-data-alert-definition"></a><span data-ttu-id="4f4c4-106">创建数据警报定义</span><span class="sxs-lookup"><span data-stu-id="4f4c4-106">To create a data alert definition</span></span>

1.  <span data-ttu-id="4f4c4-107">找到包含您要为其创建数据警报定义的报表的 SharePoint 库。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-107">Locate the SharePoint library that contains the report that you want to create a data alert definition for.</span></span>

2.  <span data-ttu-id="4f4c4-108">单击该报表。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-108">Click the report.</span></span>

     <span data-ttu-id="4f4c4-109">该报表将运行。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-109">The report runs.</span></span> <span data-ttu-id="4f4c4-110">如果对该报表进行参数化，则确认该报表显示您要接收有关其警报消息的数据。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-110">If the report is parameterized, verify that the report shows the data that you want to receive alert messages about.</span></span> <span data-ttu-id="4f4c4-111">如果您看不到感兴趣的列或值，则可能要使用不同的参数值重新运行报表。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-111">If you do not see the columns or values you are interested in, you might want to rerun the report, using different parameter values.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="4f4c4-112">您选择运行报表的参数值保存在警报定义中，并在作为处理警报定义的一个步骤重新运行报表时使用。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-112">The parameter values you chose to run the report are saved in the alert definition and will be used when report is rerun as a step in processing the alert definition.</span></span> <span data-ttu-id="4f4c4-113">若要使用不同的参数值，您必须创建一个新的警报定义。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-113">To use different parameter values, you must create a new alert definition.</span></span>

3.  <span data-ttu-id="4f4c4-114">在 **“操作”** 菜单上，单击 **“新建数据警报”**。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-114">On the **Actions** menu, click **New Data Alert**.</span></span>

     <span data-ttu-id="4f4c4-115">下图显示该 **“操作”** 菜单。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-115">The following picture shows the **Actions** menu.</span></span>

     <span data-ttu-id="4f4c4-116">![从 SharePoint 库打开警报设计器](media/rs-openalertdesigneriw.gif "从 SharePoint 库打开警报设计器")</span><span class="sxs-lookup"><span data-stu-id="4f4c4-116">![Open Alert Designer from SharePoint library](media/rs-openalertdesigneriw.gif "Open Alert Designer from SharePoint library")</span></span>

     <span data-ttu-id="4f4c4-117">数据警报设计器将打开，并且显示报表在表中生成的第一个数据馈送的前 100 行。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-117">The Data Alert Designer opens, showing the first 100 rows of the first data feed that the report generates in a table.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="4f4c4-118">如果看不到 **“新建数据警报”** 选项，则未在 SharePoint 站点上配置警报服务，或 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 版本不包含数据警报。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-118">If you do not see the **New Data Alert** option, the alerting service is not configured on the SharePoint site or the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] edition does not include data alerts.</span></span> <span data-ttu-id="4f4c4-119">有关详细信息，请参阅 [Reporting Services SharePoint 服务和服务应用程序](../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-119">For more information, see [Reporting Services SharePoint Service and Service Applications](../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md).</span></span>
    > 
    >  <span data-ttu-id="4f4c4-120">如果 **“新建数据警报”** 选项灰显，则报表数据源配置为使用集成的安全凭据或提示输入凭据。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-120">If the **New Data Alert** option is grayed, the report data source is configured to use integrated security credentials or prompt for credentials.</span></span> <span data-ttu-id="4f4c4-121">若要使 **“新建数据警报”** 选项可用，则必须更新数据源以使用存储的凭据或无凭据。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-121">To make the **New Data Alert** option available, you must update the data source to use stored credentials or no credentials.</span></span>

     <span data-ttu-id="4f4c4-122">数据馈送的名称将出现在“报表数据名称”下拉列表中\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-122">The name of the data feed appears in **Report data name** drop-down list.</span></span>

4.  <span data-ttu-id="4f4c4-123">还可以在“报表数据名称”下拉列表中选择其他数据馈送\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-123">Optionally, select a different data feed in the **Report data name** drop-down list.</span></span>

     <span data-ttu-id="4f4c4-124">如果没有从报表生成任何数据馈送，您无法为报表创建警报定义。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-124">If no data feed is generated from the report, you cannot create an alert definition for the report.</span></span> <span data-ttu-id="4f4c4-125">报表的布局确定每个数据馈送的内容。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-125">The layout of the report determines the content of each data feed.</span></span> <span data-ttu-id="4f4c4-126">有关详细信息，请参阅[基于报表生成数据馈送（报表生成器和 SSRS）](report-builder/generating-data-feeds-from-reports-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-126">For more information see, [Generating Data Feeds from Reports &#40;Report Builder and SSRS&#41;](report-builder/generating-data-feeds-from-reports-report-builder-and-ssrs.md).</span></span>

5.  <span data-ttu-id="4f4c4-127">或者在 **“警报名称”** 文本框中，将默认名称更新为更有意义的名称。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-127">Optionally, in the **Alert name** text box, update the default name to be more meaningful.</span></span>

     <span data-ttu-id="4f4c4-128">警报定义的默认名称即为报表的名称。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-128">The default name of the alert definition is the name of the report.</span></span> <span data-ttu-id="4f4c4-129">警报定义名称不一定是唯一的，因此，在您以后在数据警报管理器中查看警报的列表时，可能很难区分这些警报。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-129">Alert definition names do not have to be unique, which can make it difficult to tell them apart when you later view the list of your alerts in Data Alert Manager.</span></span> <span data-ttu-id="4f4c4-130">建议使用有意义且唯一的警报定义名称。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-130">It is recommended that you use meaningful and unique names for your alert definitions.</span></span>

6.  <span data-ttu-id="4f4c4-131">或者，将默认数据选项从“在数据馈送中具有任何数据”更改为“在数据馈送中没有任何数据”\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-131">Optionally, change the default data option from **any data in the data feed has** to **no data in the data feed has**.</span></span>

7.  <span data-ttu-id="4f4c4-132">单击 "**添加规则**"。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-132">Click **Add rule**.</span></span>

     <span data-ttu-id="4f4c4-133">将显示数据馈送中列的列表。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-133">A list of the columns in the data feed appears.</span></span>

8.  <span data-ttu-id="4f4c4-134">在此列表中，选择要在规则中使用的列，然后选择比较运算符并输入阈值。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-134">In the list, select the column that you want to use in the rule, and then select a comparison operator and enter the threshold value.</span></span>

     <span data-ttu-id="4f4c4-135">根据所选列的数据类型，将列出不同的比较运算符。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-135">Depending on the data type of the selected column, different comparison operators are listed.</span></span> <span data-ttu-id="4f4c4-136">如果该列具有日期数据类型，则在规则的阈值旁将显示一个日历图标。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-136">If the column has a date data type, a calendar icon displays next to threshold value for the rule.</span></span> <span data-ttu-id="4f4c4-137">您可以通过单击日历中的日期或者键入日期，输入数据。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-137">You can enter a data by clicking a date in the calendar or typing the date.</span></span>

     <span data-ttu-id="4f4c4-138">数据警报设计器提供了两种比较模式： **“值输入模式”** 和 **“字段选择模式”**。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-138">Data Alert Designer provides two comparison modes: **Value Entry Mode** and **Field Selection Mode**.</span></span> <span data-ttu-id="4f4c4-139">默认模式为 **“值输入模式”**。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-139">The default mode is **Value Entry Mode**.</span></span> <span data-ttu-id="4f4c4-140">仅当处于 **“值输入模式”** 且正在使用 **“是”** 比较时，才可添加 OR 子句。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-140">You can add OR clauses only when you are in **Value Entry Mode** and are using the **is** comparison.</span></span>

9. <span data-ttu-id="4f4c4-141">若要添加 OR 子句，请单击向下箭头，然后单击“值输入模式”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-141">To add an OR clause, click the down-arrow, and then click **Value Entry Mode**.</span></span>

10. <span data-ttu-id="4f4c4-142">键入比较值。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-142">Type the comparison value.</span></span>

11. <span data-ttu-id="4f4c4-143">也可以再次单击省略号 (…)\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-143">Optionally, click the ellipsis **(...)** again.</span></span>

     <span data-ttu-id="4f4c4-144">省略号 (…) 将显示在包含第一个子句的行中\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-144">The ellipsis **(...)** appears on the line that contains the first clause.</span></span>

     <span data-ttu-id="4f4c4-145">OR 子句将添加在 AND 规则下面和内部。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-145">An OR clause is added below and within the AND rule.</span></span>

12. <span data-ttu-id="4f4c4-146">还可以单击向下箭头，选择“字段选择模式”，然后选择该列表中的列\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-146">Optionally, click the down-arrow, select **Field Selection Mode**, and then select a column in the list.</span></span>

     <span data-ttu-id="4f4c4-147">你将会发现单击以添加 OR 子句的省略号 (…) 已消失\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-147">You will notice that the ellipsis **(...)** that you click to add OR clauses has disappeared.</span></span>

13. <span data-ttu-id="4f4c4-148">或者，再次单击 **“添加规则”** 以便添加其他规则。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-148">Optionally, click **Add rule** again to add additional rules.</span></span>

     <span data-ttu-id="4f4c4-149">这些规则由使用 AND 逻辑运算符组合在一起。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-149">The rules are combined by using the AND logical operator.</span></span>

14. <span data-ttu-id="4f4c4-150">在重复执行列表中选择一个选项。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-150">Select an option in the recurrence list.</span></span> <span data-ttu-id="4f4c4-151">根据重复执行的类型，输入一个间隔。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-151">Depending on the type of recurrence, enter an interval.</span></span>

15. <span data-ttu-id="4f4c4-152">或者，单击 **“高级”**。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-152">Optionally, click **Advanced**.</span></span>

16. <span data-ttu-id="4f4c4-153">还可以通过键入不同的日期，或通过打开日历然后在日历中单击某个日期，更改警报消息开始的日期。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-153">Optionally, change the date that the alert message starts on by typing a different date or opening the calendar, and then clicking a date in the calendar.</span></span>

     <span data-ttu-id="4f4c4-154">默认开始日期为当前日期。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-154">The default start date is the current date.</span></span>

17. <span data-ttu-id="4f4c4-155">或者，选中 **“停止警报时间”** 旁的复选框，然后选择用于停止警报消息的日期。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-155">Optionally, select the checkbox located next to **Stop alert on**, and then choose a date to stop the alert message.</span></span>

     <span data-ttu-id="4f4c4-156">默认情况下，警报消息没有停止日期。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-156">By default, an alert message has no stop date.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="4f4c4-157">停止警报消息并不会删除警报定义。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-157">Stopping an alert message does not delete the alert definition.</span></span> <span data-ttu-id="4f4c4-158">停止警报消息之后，可以通过更新开始日期和停止日期来重新启动警报消息。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-158">After you stop an alert message, you can restart it by updating the start and stop dates.</span></span> <span data-ttu-id="4f4c4-159">有关删除警报定义的信息，请参阅 [在数据警报管理器中管理我的数据警报](manage-my-data-alerts-in-data-alert-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-159">For information about deleting alert definitions, see [Manage My Data Alerts in Data Alert Manager](manage-my-data-alerts-in-data-alert-manager.md).</span></span>

18. <span data-ttu-id="4f4c4-160">还可以清除 **“仅当结果更改时才发送消息”** 复选框。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-160">Optionally, clear the **Send message only if results change** checkbox.</span></span>

     <span data-ttu-id="4f4c4-161">如果频繁地发送警报消息，则不欢迎冗余信息，您不应清除此复选框。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-161">If you send alert messages frequently, redundant information might not be welcome and you should not clear this checkbox.</span></span>

19. <span data-ttu-id="4f4c4-162">输入警报消息收件人的电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-162">Enter the email addresses of alert message recipients.</span></span> <span data-ttu-id="4f4c4-163">用分号分隔地址。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-163">Separate addresses with semicolons.</span></span>

     <span data-ttu-id="4f4c4-164">如果创建了警报定义的人士的电子邮件地址可用，则该地址将添加到“收件人”框中\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-164">If the email address of the person who created the alert definition is available, it is added to the **Recipient(s)** box.</span></span>

20. <span data-ttu-id="4f4c4-165">或者，在 **“主题”** 文本框中，更新警报消息的“主题”行。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-165">Optionally, in the **Subject** text box, update the Subject line of the alert message.</span></span>

     <span data-ttu-id="4f4c4-166">默认主题为的\*\*数据警报 \<data alert name> \*\*。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-166">The default Subject is **Data alert for \<data alert name>**.</span></span>

21. <span data-ttu-id="4f4c4-167">还可以在 **“说明”** 文本框中键入对警报消息的说明。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-167">Optionally, in the **Description** text box, type a description of the alert message.</span></span>

22. <span data-ttu-id="4f4c4-168">单击“ **保存**”。</span><span class="sxs-lookup"><span data-stu-id="4f4c4-168">Click **Save**.</span></span>

## <a name="see-also"></a><span data-ttu-id="4f4c4-169">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4f4c4-169">See Also</span></span>
 <span data-ttu-id="4f4c4-170">[用于警报管理员的](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md)[数据警报设计器](../../2014/reporting-services/data-alert-designer.md)数据警报管理器[Reporting Services 数据警报](../ssms/agent/alerts.md)</span><span class="sxs-lookup"><span data-stu-id="4f4c4-170">[Data Alert Designer](../../2014/reporting-services/data-alert-designer.md) [Data Alert Manager for Alerting Administrators](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md) [Reporting Services Data Alerts](../ssms/agent/alerts.md)</span></span>


