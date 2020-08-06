---
title: 为自定义日志提供程序开发用户界面 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom user interface [Integration Services], custom log providers
- custom log providers [Integration Services], developing custom user interface
ms.assetid: 6fd2d269-d87a-4134-82a1-40a09b3b5453
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c3ce6cf5ad744e307bbb049347047bf94fc5a908
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578360"
---
# <a name="developing-a-user-interface-for-a-custom-log-provider"></a><span data-ttu-id="1e89d-102">为自定义日志提供程序开发用户界面</span><span class="sxs-lookup"><span data-stu-id="1e89d-102">Developing a User Interface for a Custom Log Provider</span></span>
  <span data-ttu-id="1e89d-103">许多 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 日志提供程序都有一个自定义用户界面，该界面实现 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsLogProviderUI>，并用已筛选的可用连接管理器下拉列表替换“配置 SSIS 日志”对话框中的“配置”文本框   。</span><span class="sxs-lookup"><span data-stu-id="1e89d-103">Many [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] log providers have a custom user interface that implements <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsLogProviderUI> and replaces the **Configuration** text box in the **Configure SSIS Logs** dialog box with a filtered dropdown list of available connection managers.</span></span> <span data-ttu-id="1e89d-104">但是，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中不实现自定义日志提供程序的自定义用户界面。</span><span class="sxs-lookup"><span data-stu-id="1e89d-104">However, custom user interfaces for custom log providers are not implemented in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].</span></span>  
  
<span data-ttu-id="1e89d-105">![Integration Services 图标 (小型) ](../../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="1e89d-105">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="1e89d-106">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="1e89d-106">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="1e89d-107">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="1e89d-107">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="1e89d-108">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="1e89d-108">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e89d-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1e89d-109">See Also</span></span>  
 <span data-ttu-id="1e89d-110">[创建自定义日志提供程序](creating-a-custom-log-provider.md) </span><span class="sxs-lookup"><span data-stu-id="1e89d-110">[Creating a Custom Log Provider](creating-a-custom-log-provider.md) </span></span>  
 [<span data-ttu-id="1e89d-111">编写自定义日志提供程序代码</span><span class="sxs-lookup"><span data-stu-id="1e89d-111">Coding a Custom Log Provider</span></span>](coding-a-custom-log-provider.md)  
  
  
