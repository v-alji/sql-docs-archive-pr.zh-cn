---
title: 高级连接属性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 4edfab68-7e68-45e8-a3f3-a0049ff7eb9e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8dc844d1fdfb1e82f0ffa8de93a6a1060ef190cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588682"
---
# <a name="advanced-connection-properties"></a><span data-ttu-id="2a0f8-102">高级连接属性</span><span class="sxs-lookup"><span data-stu-id="2a0f8-102">Advanced Connection Properties</span></span>
  <span data-ttu-id="2a0f8-103">使用 **“高级连接属性”** 对话框可以将更多连接参数添加到连接字符串。</span><span class="sxs-lookup"><span data-stu-id="2a0f8-103">Use the **Advanced Connection Properties** dialog box to add more connection parameters to the connection string.</span></span>  
  
 <span data-ttu-id="2a0f8-104">其他连接参数可以是您正在使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库实例支持的任何 ODBC 连接参数。</span><span class="sxs-lookup"><span data-stu-id="2a0f8-104">The additional connection parameters can be any ODBC connection parameter that is supported by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database instance you are using.</span></span>  
  
 <span data-ttu-id="2a0f8-105">使用 **“高级连接属性”** 对话框添加的参数将添加到在 **“连接到 SQL Server”** 对话框中选择的参数上。</span><span class="sxs-lookup"><span data-stu-id="2a0f8-105">The parameters added using the **Advanced Connection Properties** dialog box are added to the parameters selected in the **Connect to SQL Server** dialog box.</span></span>  
  
 <span data-ttu-id="2a0f8-106">所提供的各个参数的最后一个实例均覆盖该参数的任何以前的实例。</span><span class="sxs-lookup"><span data-stu-id="2a0f8-106">The last instance of each parameter provided overrides any previous instances of the parameter.</span></span> <span data-ttu-id="2a0f8-107">使用 **“高级连接参数”** 添加的参数将跟踪并替换 **“SQL Server 连接”** 对话框中提供的参数。</span><span class="sxs-lookup"><span data-stu-id="2a0f8-107">Parameters added using the **Advanced Connection Parameters** dialog box follow and replace the parameters provided in the **SQL Server Connection** dialog box.</span></span> <span data-ttu-id="2a0f8-108">例如，如果“SQL Server 连接”  对话框将服务器名称指定为 SERVER1，而“其他连接参数”  页包含 ;SERVER=SERVER2，则会连接到 SERVER2。</span><span class="sxs-lookup"><span data-stu-id="2a0f8-108">For example, if the **SQL Server Connection** dialog box specifies SERVER1 as the Server name, and the **Additional Connection Parameters** page contains ;SERVER=SERVER2, the connection will be made to SERVER2.</span></span>  
  
 <span data-ttu-id="2a0f8-109">使用 **“高级连接属性”** 对话框添加的参数将作为纯文本传递。</span><span class="sxs-lookup"><span data-stu-id="2a0f8-109">Parameters added using the **Advanced Connection Properties** dialog box are passed as plain text.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2a0f8-110">不要在 **“高级连接属性”** 对话框中包含登录凭据。</span><span class="sxs-lookup"><span data-stu-id="2a0f8-110">Do not include login credentials in the **Advanced Connection Properties** dialog box.</span></span> <span data-ttu-id="2a0f8-111">否则，它们将在没有加密的情况下通过网络传递。</span><span class="sxs-lookup"><span data-stu-id="2a0f8-111">They will not be encrypted when they are passed across the network.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a0f8-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2a0f8-112">See Also</span></span>  
 <span data-ttu-id="2a0f8-113">[访问 CDC 设计器控制台](access-the-cdc-designer-console.md) </span><span class="sxs-lookup"><span data-stu-id="2a0f8-113">[Access the CDC Designer Console](access-the-cdc-designer-console.md) </span></span>  
 [<span data-ttu-id="2a0f8-114">用于实例创建的 SQL Server 连接</span><span class="sxs-lookup"><span data-stu-id="2a0f8-114">SQL Server Connection for Instance Creation</span></span>](sql-server-connection-for-instance-creation.md)  
  
  
