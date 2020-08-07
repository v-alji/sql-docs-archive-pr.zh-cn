---
title: 在警报设计器中编辑数据警报 | Microsoft Docs
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
ms.assetid: dde3664d-90b5-4b12-969e-39152c86e58a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9906b33ae50d51733eaec1bf5c201c9f5b5d120e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691109"
---
# <a name="edit-a-data-alert-in-alert-designer"></a><span data-ttu-id="d4230-102">在警报设计器中编辑数据警报</span><span class="sxs-lookup"><span data-stu-id="d4230-102">Edit a Data Alert in Alert Designer</span></span>
  <span data-ttu-id="d4230-103">打开要从数据警报管理器中进行编辑的数据警报定义。</span><span class="sxs-lookup"><span data-stu-id="d4230-103">You open the data alert definition that you want to edit from Data Alert Manager.</span></span> <span data-ttu-id="d4230-104">只有创建了警报定义的用户才能对其进行编辑。</span><span class="sxs-lookup"><span data-stu-id="d4230-104">Only the user that created the alert definition can edit it.</span></span> <span data-ttu-id="d4230-105">有关打开数据警报管理器的详细信息，请参阅 [在数据警报管理器中管理我的数据警报](manage-my-data-alerts-in-data-alert-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="d4230-105">For more information about opening Data Alert Manager, see [Manage My Data Alerts in Data Alert Manager](manage-my-data-alerts-in-data-alert-manager.md).</span></span>

 <span data-ttu-id="d4230-106">下图显示了数据警报管理器中数据警报上的上下文菜单。</span><span class="sxs-lookup"><span data-stu-id="d4230-106">The following picture shows you the context menu on a data alert in Data Alert Manager.</span></span>

 <span data-ttu-id="d4230-107">![通过单击“编辑”打开数据警报设计器](media/rs-alertmanageriwopendesigner.gif "通过单击“编辑”打开数据警报设计器")</span><span class="sxs-lookup"><span data-stu-id="d4230-107">![Open Data Alert Designer by clicking Edit](media/rs-alertmanageriwopendesigner.gif "Open Data Alert Designer by clicking Edit")</span></span>

 <span data-ttu-id="d4230-108">下面的过程包括打开警报定义以便从数据警报管理器的数据警报设计器中进行编辑的步骤。</span><span class="sxs-lookup"><span data-stu-id="d4230-108">The following procedure includes the steps to open the alert definition for editing in Data Alert Designer from Data Alert Manager.</span></span>

### <a name="to-edit-a-data-alert-definition-in-data-alert-designer"></a><span data-ttu-id="d4230-109">在数据警报设计器中编辑数据警报定义</span><span class="sxs-lookup"><span data-stu-id="d4230-109">To edit a data alert definition in Data Alert Designer</span></span>

1.  <span data-ttu-id="d4230-110">在数据警报管理器中，右键单击要编辑的数据警报定义，然后单击“编辑”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d4230-110">In Data Alert Manager, right-click the data alert definition that you want to edit and click **Edit**.</span></span>

     <span data-ttu-id="d4230-111">该警报定义将在数据警报设计器中打开。</span><span class="sxs-lookup"><span data-stu-id="d4230-111">The alert definition opens in Data Alert Designer.</span></span>

2.  <span data-ttu-id="d4230-112">更新规则、计划设置和电子邮件设置。</span><span class="sxs-lookup"><span data-stu-id="d4230-112">Update the rules, schedule settings, and email settings.</span></span> <span data-ttu-id="d4230-113">有关详细信息，请参阅 [数据警报设计器](../../2014/reporting-services/data-alert-designer.md) 和 [在数据警报设计器中创建数据警报](create-a-data-alert-in-data-alert-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="d4230-113">For more information, see [Data Alert Designer](../../2014/reporting-services/data-alert-designer.md) and [Create a Data Alert in Data Alert Designer](create-a-data-alert-in-data-alert-designer.md).</span></span>

    > [!NOTE]
    >  <span data-ttu-id="d4230-114">不能选择其他数据馈送。</span><span class="sxs-lookup"><span data-stu-id="d4230-114">You cannot choose a different data feed.</span></span> <span data-ttu-id="d4230-115">若要使用不同的数据馈送，则必须创建一个新的数据警报定义。</span><span class="sxs-lookup"><span data-stu-id="d4230-115">To use a different data feed, you must create a new data alert definition.</span></span>

3.  <span data-ttu-id="d4230-116">单击 **“保存”** 。</span><span class="sxs-lookup"><span data-stu-id="d4230-116">Click **Save**.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="d4230-117">如果报表已更改并且从该报表生成的数据馈送已更改，则警报定义将不再有效。</span><span class="sxs-lookup"><span data-stu-id="d4230-117">If the report has changed and the data feeds generated from the report have changed the alert definition might no longer be valid.</span></span> <span data-ttu-id="d4230-118">在发生以下情况之一时警报定义将不再有效：警报定义在其规则中引用的列从报表中删除、或更改了数据类型、或删除或移动了报表。</span><span class="sxs-lookup"><span data-stu-id="d4230-118">This occurs when a column that the alert definition references in its rules is deleted from the report or changes data type or the report is deleted or moved.</span></span> <span data-ttu-id="d4230-119">您可以打开无效的警报定义，但在其根据报表数据馈送所基于的当前版本变为有效之前无法重新保存。</span><span class="sxs-lookup"><span data-stu-id="d4230-119">You can open an alert definition that is not valid, but you cannot resave it until it is valid based on the current version of the report data feed that it is built upon.</span></span> <span data-ttu-id="d4230-120">若要深入了解如何从报表中生成数据馈送，请参阅[基于报表生成数据馈送（报表生成器和 SSRS）](report-builder/generating-data-feeds-from-reports-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="d4230-120">To learn more about how data feeds are generated from reports, see [Generating Data Feeds from Reports &#40;Report Builder and SSRS&#41;](report-builder/generating-data-feeds-from-reports-report-builder-and-ssrs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d4230-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d4230-121">See Also</span></span>
 <span data-ttu-id="d4230-122">[用于警报管理员的数据警报管理器](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md) [Reporting Services 数据警报](../ssms/agent/alerts.md)</span><span class="sxs-lookup"><span data-stu-id="d4230-122">[Data Alert Manager for Alerting Administrators](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md) [Reporting Services Data Alerts](../ssms/agent/alerts.md)</span></span>


