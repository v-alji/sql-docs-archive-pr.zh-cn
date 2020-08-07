---
title: 数据警报消息 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 6819720c-d848-4b90-9b51-89501b4f4645
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d50c3dd24c0057f695a9318c5eef7ad9e7540a45
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588348"
---
# <a name="data-alert-messages"></a><span data-ttu-id="49d84-102">数据警报消息</span><span class="sxs-lookup"><span data-stu-id="49d84-102">Data Alert Messages</span></span>
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="49d84-103">数据警报通过电子邮件传递两种类型的数据警报消息：具有数据警报结果的消息和具有错误说明的消息。</span><span class="sxs-lookup"><span data-stu-id="49d84-103">data alerts deliver two types of data alert messages by email: Messages with data alert results and messages with error descriptions.</span></span> <span data-ttu-id="49d84-104">具有结果的消息向所有收件人告知有关报表数据中共同感兴趣的和对业务决策至关重要的更改。</span><span class="sxs-lookup"><span data-stu-id="49d84-104">Messages with results keep all recipients informed about changes in report data that is of common interest and important to business decisions.</span></span> <span data-ttu-id="49d84-105">如果由于某种原因导致错误且结果不可用，则发送错误消息。</span><span class="sxs-lookup"><span data-stu-id="49d84-105">If for some reason an error occurs and the results are not available, the error message is sent instead.</span></span>

 <span data-ttu-id="49d84-106">数据警报定义的所有者还可以在数据警报管理器中查看有关数据警报实例的信息。</span><span class="sxs-lookup"><span data-stu-id="49d84-106">The owner of the data alert definition also can view information about the data alert instance in Data Alert Manager.</span></span> <span data-ttu-id="49d84-107">有关详细信息，请参阅 [Data Alert Manager for SharePoint Users](../../2014/reporting-services/data-alert-manager-for-sharepoint-users.md)。</span><span class="sxs-lookup"><span data-stu-id="49d84-107">For more information, see [Data Alert Manager for SharePoint Users](../../2014/reporting-services/data-alert-manager-for-sharepoint-users.md).</span></span>

##  <a name="data-alert-messages"></a><a name="DataAlertMessages"></a><span data-ttu-id="49d84-108">数据警报消息</span><span class="sxs-lookup"><span data-stu-id="49d84-108">Data Alert Messages</span></span>
 <span data-ttu-id="49d84-109">下图显示具有结果的数据警报消息和具有错误说明的警报消息。</span><span class="sxs-lookup"><span data-stu-id="49d84-109">The following pictures show a data alert message with results and an alert message with an error description.</span></span>

 <span data-ttu-id="49d84-110">**结果消息**</span><span class="sxs-lookup"><span data-stu-id="49d84-110">**Results message**</span></span>

 <span data-ttu-id="49d84-111">![包含结果的数据警报电子邮件](media/rs-alertmessageresults.gif "包含结果的数据警报电子邮件")</span><span class="sxs-lookup"><span data-stu-id="49d84-111">![Data alert e-mail message with results](media/rs-alertmessageresults.gif "Data alert e-mail message with results")</span></span>

 <span data-ttu-id="49d84-112">**错误消息**</span><span class="sxs-lookup"><span data-stu-id="49d84-112">**Error message**</span></span>

 <span data-ttu-id="49d84-113">![包含错误消息的数据警报消息](media/rs-alertmessageerrror.gif "包含错误消息的数据警报消息")</span><span class="sxs-lookup"><span data-stu-id="49d84-113">![Data alert message with error message](media/rs-alertmessageerrror.gif "Data alert message with error message")</span></span>

 <span data-ttu-id="49d84-114">这些消息包含相同类型的信息。</span><span class="sxs-lookup"><span data-stu-id="49d84-114">The messages include the same types of information.</span></span>

1.  <span data-ttu-id="49d84-115">**代表** 包含创建数据警报定义的人员姓名。</span><span class="sxs-lookup"><span data-stu-id="49d84-115">**On behalf of** contains the name of the person who created the data alert definition.</span></span>

2.  <span data-ttu-id="49d84-116">如果您在报表定义中提供了说明，则它会在 **代表**下显示。</span><span class="sxs-lookup"><span data-stu-id="49d84-116">If you provided a description in the alert definition, it displays below **On behalf of**.</span></span>

3.  <span data-ttu-id="49d84-117">**警报结果** 显示报表数据馈送中符合在警报定义中以表格格式指定的规则的行，或显示错误说明。</span><span class="sxs-lookup"><span data-stu-id="49d84-117">**Alert Results** display the rows in the report data feed that satisfy the rules specified in the alert definition in a tabular format or display an error description.</span></span> <span data-ttu-id="49d84-118">对于显示的行数没有限制。</span><span class="sxs-lookup"><span data-stu-id="49d84-118">There is no limit on the number of rows that displays.</span></span>

4.  <span data-ttu-id="49d84-119">**转到报表** 是指向警报定义所基于的报表的链接。</span><span class="sxs-lookup"><span data-stu-id="49d84-119">**Go to report** is a link to the report that the alert definition is built upon.</span></span> <span data-ttu-id="49d84-120">如果因为报表移动或删除而导致此链接无效，则显示一条错误消息。</span><span class="sxs-lookup"><span data-stu-id="49d84-120">If the link is not valid because the report was moved or deleted, an error message displays.</span></span>

5.  <span data-ttu-id="49d84-121">**规则** 列出了警报定义中的规则和子句。</span><span class="sxs-lookup"><span data-stu-id="49d84-121">**Rule(s)** lists the rules and clauses in the alert definition.</span></span> <span data-ttu-id="49d84-122">此信息帮助您验证和了解警报结果，并确定数据警报定义中您可能希望更改以缩小或扩大结果的规则。</span><span class="sxs-lookup"><span data-stu-id="49d84-122">This information helps you verify and understand the alert results and identify rules in the data alert definition that you might want to change to narrow or broaden results.</span></span>

6.  <span data-ttu-id="49d84-123">**报表参数** 列出在运行报表时所使用的参数和参数值。</span><span class="sxs-lookup"><span data-stu-id="49d84-123">**Report parameters** list the parameters and parameter values that were used when the report was run.</span></span> <span data-ttu-id="49d84-124">参数及参数值可帮助您了解警报结果。</span><span class="sxs-lookup"><span data-stu-id="49d84-124">Parameters and parameter values help you understand the alert results.</span></span>

7.  <span data-ttu-id="49d84-125">**上下文值** 列出报表数据区域之外的报表项的名称和值。</span><span class="sxs-lookup"><span data-stu-id="49d84-125">**Contextual values** list the names and values of report items that are outside of the report data regions.</span></span> <span data-ttu-id="49d84-126">这些项通常为文本框。</span><span class="sxs-lookup"><span data-stu-id="49d84-126">The items are typically text boxes.</span></span> <span data-ttu-id="49d84-127">例如，带常量值的文本框（如报表主题或报表说明）。</span><span class="sxs-lookup"><span data-stu-id="49d84-127">For example, a text box with a constant value such as the subject or description of a report.</span></span>

 <span data-ttu-id="49d84-128">两种消息类型的唯一区别在于项 5，即 **警报结果**。</span><span class="sxs-lookup"><span data-stu-id="49d84-128">The only difference between the two message types is item 5, **Alert Results**.</span></span> <span data-ttu-id="49d84-129">如果在创建数据警报实例或数据警报消息时发生错误，则 **警报结果** 显示一条描述问题的错误消息。</span><span class="sxs-lookup"><span data-stu-id="49d84-129">If an error occurs when a data alert instance or data alert message is created, **Alert Results** displays an error message that describes the problem.</span></span> <span data-ttu-id="49d84-130">此错误消息将发送给所有收件人，让他们知道他们预期和可能依赖来制定业务决策的警报结果不可用。</span><span class="sxs-lookup"><span data-stu-id="49d84-130">The error message, sent to all recipients, let them know that the alert results that they are expecting and might rely on to make business decisions are not available.</span></span>

 

##  <a name="related-tasks"></a><a name="HowTo"></a> <span data-ttu-id="49d84-131">相关任务</span><span class="sxs-lookup"><span data-stu-id="49d84-131">Related Tasks</span></span>
 <span data-ttu-id="49d84-132">本部分列出的过程说明如何创建和编辑数据警报定义，这些定义可提供您在数据警报消息中看到的大量信息。</span><span class="sxs-lookup"><span data-stu-id="49d84-132">This section lists procedures that show you how to create and edit the data alert definitions that provide much of the information that you see in data alert messages.</span></span>

-   [<span data-ttu-id="49d84-133">在数据警报设计器中创建数据警报</span><span class="sxs-lookup"><span data-stu-id="49d84-133">Create a Data Alert in Data Alert Designer</span></span>](create-a-data-alert-in-data-alert-designer.md)

-   [<span data-ttu-id="49d84-134">在警报设计器中编辑数据警报</span><span class="sxs-lookup"><span data-stu-id="49d84-134">Edit a Data Alert in Alert Designer</span></span>](edit-a-data-alert-in-alert-designer.md)



## <a name="see-also"></a><span data-ttu-id="49d84-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="49d84-135">See Also</span></span>
 <span data-ttu-id="49d84-136">[数据警报设计器](../../2014/reporting-services/data-alert-designer.md) [Reporting Services 数据警报](../ssms/agent/alerts.md)</span><span class="sxs-lookup"><span data-stu-id="49d84-136">[Data Alert Designer](../../2014/reporting-services/data-alert-designer.md) [Reporting Services Data Alerts](../ssms/agent/alerts.md)</span></span>


