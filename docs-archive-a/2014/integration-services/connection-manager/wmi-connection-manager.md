---
title: WMI 连接管理器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], WMI
- connection managers [Integration Services], WMI
- WMI connection manager [Integration Services]
ms.assetid: fbfa4ba7-3d0d-4d6b-94ad-50741a88d03d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f15aefb0ed112f1d5b7bb05421750b6689a11339
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587561"
---
# <a name="wmi-connection-manager"></a><span data-ttu-id="9252b-102">WMI 连接管理器</span><span class="sxs-lookup"><span data-stu-id="9252b-102">WMI Connection Manager</span></span>
  <span data-ttu-id="9252b-103">WMI 连接管理器使得包可以使用 Windows Management Instrumentation (WMI) 来管理企业环境中的信息。</span><span class="sxs-lookup"><span data-stu-id="9252b-103">A WMI connection manager enables a package to use Windows Management Instrumentation (WMI) to manage information in an enterprise environment.</span></span> <span data-ttu-id="9252b-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包含的 Web 服务任务使用 WMI 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="9252b-104">The Web Service task that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] includes uses a WMI connection manager.</span></span>  
  
 <span data-ttu-id="9252b-105">将 WMI 连接管理器添加到包时， [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 将创建一个连接管理器，该连接管理器将在运行时解析为 WMI 连接，设置连接管理器属性，并将该连接管理器添加到 `Connections` 包上的集合。</span><span class="sxs-lookup"><span data-stu-id="9252b-105">When you add a WMI connection manager to a package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to a WMI connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span> <span data-ttu-id="9252b-106">该连接管理器的 `ConnectionManagerType` 属性设置为 `WMI`。</span><span class="sxs-lookup"><span data-stu-id="9252b-106">The `ConnectionManagerType` property of the connection manager is set to `WMI`.</span></span>  
  
## <a name="configuration-of-the-wmi-connection-manager"></a><span data-ttu-id="9252b-107">配置 WMI 连接管理器</span><span class="sxs-lookup"><span data-stu-id="9252b-107">Configuration of the WMI Connection Manager</span></span>  
 <span data-ttu-id="9252b-108">可按下列方式配置 WMI 连接管理器：</span><span class="sxs-lookup"><span data-stu-id="9252b-108">You can configure a WMI connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="9252b-109">指定服务器名称。</span><span class="sxs-lookup"><span data-stu-id="9252b-109">Specify the name of a server.</span></span>  
  
-   <span data-ttu-id="9252b-110">指定服务器上的命名空间。</span><span class="sxs-lookup"><span data-stu-id="9252b-110">Specify a namespace on the server.</span></span>  
  
-   <span data-ttu-id="9252b-111">为连接到服务器选择身份验证模式。</span><span class="sxs-lookup"><span data-stu-id="9252b-111">Select the authentication mode for connecting to the server.</span></span>  
  
 <span data-ttu-id="9252b-112">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="9252b-112">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="9252b-113">有关可以在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置的属性的信息，请参阅 [WMI 连接管理器编辑器](../wmi-connection-manager-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="9252b-113">For information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [WMI Connection Manager Editor](../wmi-connection-manager-editor.md).</span></span>  
  
 <span data-ttu-id="9252b-114">有关以编程方式配置连接管理器的信息，请参阅 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 和 [以编程方式添加连接](../building-packages-programmatically/adding-connections-programmatically.md)项目。</span><span class="sxs-lookup"><span data-stu-id="9252b-114">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9252b-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9252b-115">See Also</span></span>  
 <span data-ttu-id="9252b-116">[Web 服务任务](../control-flow/web-service-task.md) </span><span class="sxs-lookup"><span data-stu-id="9252b-116">[Web Service Task](../control-flow/web-service-task.md) </span></span>  
 [<span data-ttu-id="9252b-117">Integration Services (SSIS) 连接</span><span class="sxs-lookup"><span data-stu-id="9252b-117">Integration Services &#40;SSIS&#41; Connections</span></span>](integration-services-ssis-connections.md)  
  
  
