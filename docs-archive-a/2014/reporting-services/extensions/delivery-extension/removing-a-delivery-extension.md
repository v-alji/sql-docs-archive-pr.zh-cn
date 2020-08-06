---
title: 删除传递扩展插件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- removing delivery extensions
- deleting delivery extensions
- delivery extensions [Reporting Services], removing
ms.assetid: dcb7caf2-d19a-4bc5-afb3-2b61ad11cac5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7c4320f46b5013b0fa2accbc81792748c2d9f384
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591780"
---
# <a name="removing-a-delivery-extension"></a><span data-ttu-id="d4ce3-102">删除传递扩展插件</span><span class="sxs-lookup"><span data-stu-id="d4ce3-102">Removing a Delivery Extension</span></span>
  <span data-ttu-id="d4ce3-103">要删除 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 传递扩展插件，只需从配置文件中删除传递扩展插件的 Extension 元素  。</span><span class="sxs-lookup"><span data-stu-id="d4ce3-103">To remove a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] delivery extension, simply remove the **Extension** element for your delivery extension from the configuration file.</span></span> <span data-ttu-id="d4ce3-104">删除配置信息之后，传递扩展插件对于报表服务器将不再可用。</span><span class="sxs-lookup"><span data-stu-id="d4ce3-104">After the configuration information is removed, the delivery extension is no longer available to the report server.</span></span>  
  
 <span data-ttu-id="d4ce3-105">从配置文件中删除传递扩展插件的相应 Extension 元素后，它不再向报表服务器注册  。</span><span class="sxs-lookup"><span data-stu-id="d4ce3-105">Once a delivery extension's corresponding **Extension** element is removed from the configuration file, it is no longer registered with the report server.</span></span> <span data-ttu-id="d4ce3-106">报表服务器从传递扩展插件的列表中删除此项，并停用使用该传递扩展插件的任何订阅。</span><span class="sxs-lookup"><span data-stu-id="d4ce3-106">The report server removes the entry from the list of delivery extensions and deactivates any subscriptions which use that delivery extension.</span></span> <span data-ttu-id="d4ce3-107">当删除某个传递扩展插件后，用户不再能够选择它作为通知方法。</span><span class="sxs-lookup"><span data-stu-id="d4ce3-107">When a delivery extension is removed, users are no longer able to select it as a method of notification.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4ce3-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d4ce3-108">See Also</span></span>  
 <span data-ttu-id="d4ce3-109">[实现传递扩展插件](implementing-a-delivery-extension.md) </span><span class="sxs-lookup"><span data-stu-id="d4ce3-109">[Implementing a Delivery Extension](implementing-a-delivery-extension.md) </span></span>  
 [<span data-ttu-id="d4ce3-110">Reporting Services 扩展插件库</span><span class="sxs-lookup"><span data-stu-id="d4ce3-110">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
