---
title: WMI 连接管理器编辑器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.wmiconnection.f1
helpviewer_keywords:
- WMI Connection Manager Editor
ms.assetid: 0ef2c913-0779-4a07-989e-3361cd83170b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e85cdd2157c8ebe4cb9e6b53f8c3b47ff102a7b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590252"
---
# <a name="wmi-connection-manager-editor"></a><span data-ttu-id="f1b90-102">WMI 连接管理器编辑器</span><span class="sxs-lookup"><span data-stu-id="f1b90-102">WMI Connection Manager Editor</span></span>
  <span data-ttu-id="f1b90-103">可以使用“WMI 连接管理器”\*\*\*\* 对话框指定到服务器的 Microsoft Windows Management Instrumentation (WMI) 连接。</span><span class="sxs-lookup"><span data-stu-id="f1b90-103">Use the **WMI Connection Manager** dialog box to specify a Microsoft Windows Management Instrumentation (WMI) connection to a server.</span></span>  
  
 <span data-ttu-id="f1b90-104">若要了解有关 WMI 连接管理器的详细信息，请参阅 [WMI Connection Manager](connection-manager/wmi-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="f1b90-104">To learn more about the WMI connection manager, see [WMI Connection Manager](connection-manager/wmi-connection-manager.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="f1b90-105">选项</span><span class="sxs-lookup"><span data-stu-id="f1b90-105">Options</span></span>  
 <span data-ttu-id="f1b90-106">**名称**</span><span class="sxs-lookup"><span data-stu-id="f1b90-106">**Name**</span></span>  
 <span data-ttu-id="f1b90-107">为连接管理器提供唯一的名称。</span><span class="sxs-lookup"><span data-stu-id="f1b90-107">Provide a unique name for the connection manager.</span></span>  
  
 <span data-ttu-id="f1b90-108">**说明**</span><span class="sxs-lookup"><span data-stu-id="f1b90-108">**Description**</span></span>  
 <span data-ttu-id="f1b90-109">描述连接管理器。</span><span class="sxs-lookup"><span data-stu-id="f1b90-109">Describe the connection manager.</span></span> <span data-ttu-id="f1b90-110">最好按照连接管理器的用途对其进行说明，使包的说明一目了然，且更便于维护。</span><span class="sxs-lookup"><span data-stu-id="f1b90-110">As a best practice, describe the connection manager in terms of its purpose, to make packages self-documenting and easier to maintain.</span></span>  
  
 <span data-ttu-id="f1b90-111">**服务器名称**</span><span class="sxs-lookup"><span data-stu-id="f1b90-111">**Server name**</span></span>  
 <span data-ttu-id="f1b90-112">提供要进行 WMI 连接的服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="f1b90-112">Provide the name of the server to which you want to make the WMI connection.</span></span>  
  
 <span data-ttu-id="f1b90-113">**命名空间**</span><span class="sxs-lookup"><span data-stu-id="f1b90-113">**Namespace**</span></span>  
 <span data-ttu-id="f1b90-114">指定 WMI 命名空间。</span><span class="sxs-lookup"><span data-stu-id="f1b90-114">Specify the WMI namespace.</span></span>  
  
 <span data-ttu-id="f1b90-115">**使用 Windows 身份验证**</span><span class="sxs-lookup"><span data-stu-id="f1b90-115">**Use Windows authentication**</span></span>  
 <span data-ttu-id="f1b90-116">选择此项可以使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="f1b90-116">Select to use Windows Authentication.</span></span> <span data-ttu-id="f1b90-117">如果使用 Windows 身份验证，则不需要提供连接所用的用户名或密码。</span><span class="sxs-lookup"><span data-stu-id="f1b90-117">If you use Windows Authentication, you do not need to provide a user name or password for the connection.</span></span>  
  
 <span data-ttu-id="f1b90-118">**用户名**</span><span class="sxs-lookup"><span data-stu-id="f1b90-118">**User name**</span></span>  
 <span data-ttu-id="f1b90-119">如果不使用 Windows 身份验证，则必须提供连接所用的用户名。</span><span class="sxs-lookup"><span data-stu-id="f1b90-119">If you do not use Windows Authentication, you must provide a user name for the connection.</span></span>  
  
 <span data-ttu-id="f1b90-120">**密码**</span><span class="sxs-lookup"><span data-stu-id="f1b90-120">**Password**</span></span>  
 <span data-ttu-id="f1b90-121">如果不使用 Windows 身份验证，则必须提供连接所用的密码。</span><span class="sxs-lookup"><span data-stu-id="f1b90-121">If you do not use Windows Authentication, you must provide the password for the connection.</span></span>  
  
 <span data-ttu-id="f1b90-122">**Test**</span><span class="sxs-lookup"><span data-stu-id="f1b90-122">**Test**</span></span>  
 <span data-ttu-id="f1b90-123">测试连接管理器设置。</span><span class="sxs-lookup"><span data-stu-id="f1b90-123">Test the connection manager settings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1b90-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f1b90-124">See Also</span></span>  
 <span data-ttu-id="f1b90-125">[Integration Services 错误和消息引用](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="f1b90-125">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="f1b90-126">[用于配置管理的 WMI 提供程序概念](../relational-databases/wmi-provider-configuration/wmi-provider-for-configuration-management.md) </span><span class="sxs-lookup"><span data-stu-id="f1b90-126">[WMI Provider for Configuration Management Concepts](../relational-databases/wmi-provider-configuration/wmi-provider-for-configuration-management.md) </span></span>  
 [<span data-ttu-id="f1b90-127">WMI Provider for Server Events 的概念</span><span class="sxs-lookup"><span data-stu-id="f1b90-127">WMI Provider for Server Events Concepts</span></span>](../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-concepts.md)  
  
  
