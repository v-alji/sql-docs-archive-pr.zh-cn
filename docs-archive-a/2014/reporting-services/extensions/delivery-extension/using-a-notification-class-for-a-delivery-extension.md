---
title: 将 Notification 类用于传递扩展插件 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], notifications
- notifications [Reporting Services]
- retry queues
- Nofication class
ms.assetid: 549c40c4-d33d-46c2-9d6a-7bbb671ac67a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8b274eb50405a02f4995b953611e50a234b11eab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591779"
---
# <a name="using-a-notification-class-for-a-delivery-extension"></a><span data-ttu-id="fc81f-102">将通知类用于传递扩展插件</span><span class="sxs-lookup"><span data-stu-id="fc81f-102">Using a Notification Class for a Delivery Extension</span></span>
  <span data-ttu-id="fc81f-103"><xref:Microsoft.ReportingServices.Interfaces.Notification> 类位于 <xref:Microsoft.ReportingServices.Interfaces> 命名空间中，表示传递扩展插件用于传递报表的订阅信息。</span><span class="sxs-lookup"><span data-stu-id="fc81f-103">The <xref:Microsoft.ReportingServices.Interfaces.Notification> class is located in the <xref:Microsoft.ReportingServices.Interfaces> namespace and represents subscription information that delivery extensions use for delivering reports.</span></span> <span data-ttu-id="fc81f-104"><xref:Microsoft.ReportingServices.Interfaces.Notification> 类提供多种属性，这些属性可用于呈现用于传递的报表、确定通知的状态和设置用户数据。</span><span class="sxs-lookup"><span data-stu-id="fc81f-104">The <xref:Microsoft.ReportingServices.Interfaces.Notification> class provides a number of properties that can be used to render the reports for delivery, determine the status of the notification, and set user data.</span></span>

 <span data-ttu-id="fc81f-105">![报表通知过程](../../media/bk-ext-03.gif "报表通知进程")通知是任何传递的中心对象</span><span class="sxs-lookup"><span data-stu-id="fc81f-105">![Report notification process](../../media/bk-ext-03.gif "Report notification process") The notification is the central object of any delivery</span></span>

 <span data-ttu-id="fc81f-106">在引发与某一订阅关联的事件时，如果该订阅使用您的自定义传递扩展插件，则将创建包含 <xref:Microsoft.ReportingServices.Interfaces.Report> 对象的通知。</span><span class="sxs-lookup"><span data-stu-id="fc81f-106">When an event fires that is associated with a subscription that uses your custom delivery extension, a notification is created that contains a <xref:Microsoft.ReportingServices.Interfaces.Report> object.</span></span> <span data-ttu-id="fc81f-107"><xref:Microsoft.ReportingServices.Interfaces.Report> 对象封装将给定报表呈现给支持的呈现格式所需的功能，并且包含特定于报表的属性，例如指向服务器上报表的 URL 和报表的名称。</span><span class="sxs-lookup"><span data-stu-id="fc81f-107">The <xref:Microsoft.ReportingServices.Interfaces.Report> object encapsulates the functionality needed to render a given report to a supported rendering format and contains report-specific properties, such as the URL to the report on the server and the name of the report.</span></span> <span data-ttu-id="fc81f-108">有关 <xref:Microsoft.ReportingServices.Interfaces.Report> 类的详细信息，请参阅[将 Report 类用于传递扩展插件](../delivery-extension/using-the-report-class-for-a-delivery-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="fc81f-108">For more information about the <xref:Microsoft.ReportingServices.Interfaces.Report> class, see [Using the Report Class for a Delivery Extension](../delivery-extension/using-the-report-class-for-a-delivery-extension.md).</span></span>

 <span data-ttu-id="fc81f-109">您将 <xref:Microsoft.ReportingServices.Interfaces.Notification> 对象传递到传递扩展插件的 <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="fc81f-109">You pass the <xref:Microsoft.ReportingServices.Interfaces.Notification> object to the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> method of your delivery extension.</span></span> <span data-ttu-id="fc81f-110">您的 <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> 方法应包含用于处理通知和传递报表的特定代码。</span><span class="sxs-lookup"><span data-stu-id="fc81f-110">Your <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> method should contain specific code to process the notification and to deliver the report.</span></span>

 <span data-ttu-id="fc81f-111">有关如何使用 <xref:Microsoft.ReportingServices.Interfaces.Notification> 类的示例，请参阅 [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889)（SQL Server Reporting Services 产品示例）。</span><span class="sxs-lookup"><span data-stu-id="fc81f-111">For an example of how to use the <xref:Microsoft.ReportingServices.Interfaces.Notification> class, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>

## <a name="retry-functionality"></a><span data-ttu-id="fc81f-112">重试功能</span><span class="sxs-lookup"><span data-stu-id="fc81f-112">Retry Functionality</span></span>
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="fc81f-113">允许您为无法立即传递的通知创建重试队列。</span><span class="sxs-lookup"><span data-stu-id="fc81f-113">allows you to create a retry queue for notifications that cannot immediately be delivered.</span></span> <span data-ttu-id="fc81f-114">在报表服务器调用某一传递扩展插件的 <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> 方法后，该传递扩展可以请求报表服务器在以后的某个时间点重试该传递。</span><span class="sxs-lookup"><span data-stu-id="fc81f-114">After the report server invokes the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> method of a delivery extension, the delivery extension can request that the report server retry the delivery at a later point in time.</span></span> <span data-ttu-id="fc81f-115">如果发生此情况，则报表服务器将把通知置于内部队列中，并且在经过了特定的时间段后重试该传递。</span><span class="sxs-lookup"><span data-stu-id="fc81f-115">If this occurs, the report server places the notification in an internal queue and retries the delivery after a specific period of time has elapsed.</span></span> <span data-ttu-id="fc81f-116">管理员可以使用 MaxNumberOfRetries XML 元素和 PeriodBetweenRetries XML 元素，在 RSReportServer.config 文件的传递扩展插件部分中配置报表服务器执行的重试尝试的最大次数以及两次重试之间的时间段\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fc81f-116">Administrators can configure the maximum number of retry attempts that the report server performs and the period between retries in the delivery extension section of the RSReportServer.config file using the **MaxNumberOfRetries** XML element and the **PeriodBetweenRetries** XML element.</span></span> <span data-ttu-id="fc81f-117">如果传递在以后成功，或者达到最大重试尝试数目，则通知将从重试队列中删除。</span><span class="sxs-lookup"><span data-stu-id="fc81f-117">Notifications are removed from the retry queue if delivery later succeeds or if the maximum number of retry attempts is reached.</span></span> <span data-ttu-id="fc81f-118">如果传递在尝试了最大重试数目后仍失败，则通知将被放弃。</span><span class="sxs-lookup"><span data-stu-id="fc81f-118">If delivery fails after the maximum number of retries, the notification is discarded.</span></span>

## <a name="see-also"></a><span data-ttu-id="fc81f-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fc81f-119">See Also</span></span>
 <span data-ttu-id="fc81f-120">[Reporting Services 扩展库](../reporting-services-extension-library.md)[实现传递扩展插件](../delivery-extension/implementing-a-delivery-extension.md)</span><span class="sxs-lookup"><span data-stu-id="fc81f-120">[Implementing a Delivery Extension](../delivery-extension/implementing-a-delivery-extension.md) [Reporting Services Extension Library](../reporting-services-extension-library.md)</span></span>


