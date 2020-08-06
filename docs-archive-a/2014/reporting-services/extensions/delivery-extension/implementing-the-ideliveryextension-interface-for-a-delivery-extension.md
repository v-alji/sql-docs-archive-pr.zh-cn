---
title: 为传递扩展插件实现 IDeliveryExtension 接口 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], attributes
- delivery extensions [Reporting Services], class creation
- IDeliveryExtension interface
ms.assetid: ab0344db-510b-403f-8dbf-b9831553765d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a0f9ab0767a09016d4f4bc1158988965bfc13b27
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591786"
---
# <a name="implementing-the-ideliveryextension-interface-for-a-delivery-extension"></a><span data-ttu-id="fdd22-102">为传递扩展插件实现 IDeliveryExtension 接口</span><span class="sxs-lookup"><span data-stu-id="fdd22-102">Implementing the IDeliveryExtension Interface for a Delivery Extension</span></span>
  <span data-ttu-id="fdd22-103">传递扩展插件类用于根据报表通知的内容将通知传递给用户。</span><span class="sxs-lookup"><span data-stu-id="fdd22-103">Your delivery extension class is used to deliver report notifications to users based on the contents of the notifications.</span></span> <span data-ttu-id="fdd22-104">传递扩展插件类还提供了基础结构，用于验证传递到传递扩展插件的用户设置。</span><span class="sxs-lookup"><span data-stu-id="fdd22-104">The delivery extension class also provides infrastructure for validating user settings that are passed to the delivery extension.</span></span> <span data-ttu-id="fdd22-105">此外，传递扩展插件类应包含特定的属性，客户端可以使用这些属性获得有关扩展插件的名称、扩展插件支持的设置以及可用于传递扩展插件的呈现格式的信息。</span><span class="sxs-lookup"><span data-stu-id="fdd22-105">In addition, your delivery extension class should contain specific properties that clients can use to gain information about the name of the extension, the settings that the extension supports, and the rendering formats that are available to the delivery extension.</span></span>  
  
 <span data-ttu-id="fdd22-106">![IDeliveryExtension 接口进程](../../media/bk-ext-02.gif "IDeliveryExtension 接口进程")</span><span class="sxs-lookup"><span data-stu-id="fdd22-106">![IDeliveryExtension interface process](../../media/bk-ext-02.gif "IDeliveryExtension interface process")</span></span>  
<span data-ttu-id="fdd22-107">IDeliveryExtension 接口允许对用户数据进行验证，以及使客户端能够了解所需的传递设置</span><span class="sxs-lookup"><span data-stu-id="fdd22-107">The IDeliveryExtension interface allows validation of user data as well as for clients to learn about the required delivery settings</span></span>  
  
 <span data-ttu-id="fdd22-108">若要创建传递扩展插件类，应实现 <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> 和 <xref:Microsoft.ReportingServices.Interfaces.IExtension>。</span><span class="sxs-lookup"><span data-stu-id="fdd22-108">To create a delivery extension class, implement <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> and <xref:Microsoft.ReportingServices.Interfaces.IExtension>.</span></span> <span data-ttu-id="fdd22-109">借助于 IDeliveryExtension 接口，传递扩展插件可以使用 <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> 方法传递报表通知，并使用 <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ValidateUserData%2A> 方法验证传入的扩展插件设置。</span><span class="sxs-lookup"><span data-stu-id="fdd22-109">The **IDeliveryExtension** interface enables your delivery extension to deliver report notifications using the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> method and to validate incoming extension settings using the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ValidateUserData%2A> method.</span></span> <span data-ttu-id="fdd22-110">借助于 IExtension 接口，传递扩展插件可以实现本地化的扩展插件名称并处理存储在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 配置文件中的扩展插件特定的配置信息。</span><span class="sxs-lookup"><span data-stu-id="fdd22-110">The **IExtension** interface enables your delivery extension to implement a localized extension name and to process extension-specific configuration information stored in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] configuration file.</span></span> <span data-ttu-id="fdd22-111">通过实现 IExtension，传递扩展插件可以包含 <xref:Microsoft.ReportingServices.Interfaces.Extension.LocalizedName%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="fdd22-111">By implementing **IExtension**, your delivery extension contains the <xref:Microsoft.ReportingServices.Interfaces.Extension.LocalizedName%2A> property.</span></span> <span data-ttu-id="fdd22-112">强烈建议 [!INCLUDE[ssRS](../../../includes/ssrs.md)] 传递扩展插件支持 LocalizedName 属性，以便用户在用户界面（如报表管理器）中对于该扩展插件看到熟悉的名称  。</span><span class="sxs-lookup"><span data-stu-id="fdd22-112">It is strongly recommended that [!INCLUDE[ssRS](../../../includes/ssrs.md)] delivery extensions support the **LocalizedName** property, so that users encounter a familiar name for the extension in a user interface, such as Report Manager.</span></span>  
  
 <span data-ttu-id="fdd22-113">传递扩展插件还必须实现 IDeliveryExtension 接口的 ExtensionSettings 属性   。</span><span class="sxs-lookup"><span data-stu-id="fdd22-113">Your delivery extension must also implement the **ExtensionSettings** property of the **IDeliveryExtension** interface.</span></span> <span data-ttu-id="fdd22-114">报表服务器使用由 <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ExtensionSettings%2A> 属性返回的值以评估传递扩展插件所要求的设置。</span><span class="sxs-lookup"><span data-stu-id="fdd22-114">The report server uses the value returned by the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ExtensionSettings%2A> property to evaluate the settings that a delivery extension requires.</span></span> <span data-ttu-id="fdd22-115">与传递扩展插件交互的客户端使用报表服务器 Web 服务的 <xref:ReportService2010.ReportingService2010.GetExtensionSettings%2A> 方法为传递扩展插件返回设置列表。</span><span class="sxs-lookup"><span data-stu-id="fdd22-115">Clients that interact with delivery extensions use the <xref:ReportService2010.ReportingService2010.GetExtensionSettings%2A> method of the Report Server Web service to return a list of settings for the delivery extension.</span></span>  
  
 <span data-ttu-id="fdd22-116">还可以使用传递扩展插件类检索和处理存储在 RSReportServer.config 文件中的自定义配置数据。</span><span class="sxs-lookup"><span data-stu-id="fdd22-116">You can also use your delivery extension class to retrieve and process custom configuration data stored in the RSReportServer.config file.</span></span> <span data-ttu-id="fdd22-117">有关处理自定义配置数据的详细信息，请参阅 <xref:Microsoft.ReportingServices.Interfaces.IExtension.SetConfiguration%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="fdd22-117">For more information about processing custom configuration data, see the <xref:Microsoft.ReportingServices.Interfaces.IExtension.SetConfiguration%2A> method.</span></span>  
  
 <span data-ttu-id="fdd22-118">有关示例 IDeliveryExtension 类实现，请参阅 [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889)（SQL Server Reporting Services 产品示例）。</span><span class="sxs-lookup"><span data-stu-id="fdd22-118">For a sample **IDeliveryExtension** class implementation, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdd22-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fdd22-119">See Also</span></span>  
 <span data-ttu-id="fdd22-120">[实现传递扩展插件](../delivery-extension/implementing-a-delivery-extension.md) </span><span class="sxs-lookup"><span data-stu-id="fdd22-120">[Implementing a Delivery Extension](../delivery-extension/implementing-a-delivery-extension.md) </span></span>  
 [<span data-ttu-id="fdd22-121">Reporting Services 扩展插件库</span><span class="sxs-lookup"><span data-stu-id="fdd22-121">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
