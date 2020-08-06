---
title: SMO 连接管理器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], SMO
- SMO connection manager
- connection managers [Integration Services], SMO
ms.assetid: d273f1fb-a6a8-4f2f-a5ff-55c2e3de4723
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 988eef214608399bc3ec483d9976c2f5d52acb2a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693433"
---
# <a name="smo-connection-manager"></a><span data-ttu-id="4e8cc-102">SMO 连接管理器</span><span class="sxs-lookup"><span data-stu-id="4e8cc-102">SMO Connection Manager</span></span>
  <span data-ttu-id="4e8cc-103">SMO 连接管理器使得包能够连接到 SQL 管理对象 (SMO) 服务器。</span><span class="sxs-lookup"><span data-stu-id="4e8cc-103">An SMO connection manager enables a package to connect to a SQL Management Object (SMO) server.</span></span> <span data-ttu-id="4e8cc-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包括的传输任务使用 SMO 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="4e8cc-104">The transfer tasks that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] includes use an SMO connection manager.</span></span> <span data-ttu-id="4e8cc-105">例如，传输 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名的传输登录任务使用 SMO 连接管理器。</span><span class="sxs-lookup"><span data-stu-id="4e8cc-105">For example, the Transfer Logins task that transfers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins uses an SMO connection manager.</span></span>  
  
 <span data-ttu-id="4e8cc-106">将 SMO 连接管理器添加到包时，[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 会创建将在运行时决定 SMO 连接的连接管理器，设置该连接管理器的属性，并将该连接管理器添加到包上的 `Connections` 集合。</span><span class="sxs-lookup"><span data-stu-id="4e8cc-106">When you add an SMO connection manager to a package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to an SMO connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span> <span data-ttu-id="4e8cc-107">该连接管理器的 `ConnectionManagerType` 属性设置为 `SMOServer`。</span><span class="sxs-lookup"><span data-stu-id="4e8cc-107">The `ConnectionManagerType` property of the connection manager is set to `SMOServer`.</span></span>  
  
 <span data-ttu-id="4e8cc-108">可以按下列方式配置 SMO 连接管理器：</span><span class="sxs-lookup"><span data-stu-id="4e8cc-108">You can configure an SMO connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="4e8cc-109">指定安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="4e8cc-109">Specify the name of a server on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed.</span></span>  
  
-   <span data-ttu-id="4e8cc-110">为连接到服务器选择身份验证模式。</span><span class="sxs-lookup"><span data-stu-id="4e8cc-110">Select the authentication mode for connecting to the server.</span></span>  
  
## <a name="configuration-of-the-smo-connection-manager"></a><span data-ttu-id="4e8cc-111">SMO 连接管理器的配置</span><span class="sxs-lookup"><span data-stu-id="4e8cc-111">Configuration of the SMO Connection Manager</span></span>  
 <span data-ttu-id="4e8cc-112">可以通过 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。</span><span class="sxs-lookup"><span data-stu-id="4e8cc-112">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="4e8cc-113">有关可以在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 设计器中设置的属性的详细信息，请参阅 [SMO 连接管理器编辑器](../smo-connection-manager-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="4e8cc-113">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [SMO Connection Manager Editor](../smo-connection-manager-editor.md).</span></span>  
  
 <span data-ttu-id="4e8cc-114">有关以编程方式配置连接管理器的信息，请参阅 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 和 [以编程方式添加连接](../building-packages-programmatically/adding-connections-programmatically.md)项目。</span><span class="sxs-lookup"><span data-stu-id="4e8cc-114">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e8cc-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4e8cc-115">See Also</span></span>  
 [<span data-ttu-id="4e8cc-116">Integration Services (SSIS) 连接</span><span class="sxs-lookup"><span data-stu-id="4e8cc-116">Integration Services &#40;SSIS&#41; Connections</span></span>](integration-services-ssis-connections.md)  
  
  
