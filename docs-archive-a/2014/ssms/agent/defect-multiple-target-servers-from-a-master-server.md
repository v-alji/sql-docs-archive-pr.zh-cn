---
title: 将多个目标服务器与主服务器脱离 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, target servers
- target servers [SQL Server], defecting
- SQL Server Agent jobs, master servers
- master servers [SQL Server], defecting target servers
- defecting target servers
- multiple target server defections
ms.assetid: 61a3713b-403a-4806-bfc4-66db72ca1156
author: stevestein
ms.author: sstein
ms.openlocfilehash: b31a8bc38968733de0a23f67a71772721c8baedd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689252"
---
# <a name="defect-multiple-target-servers-from-a-master-server"></a><span data-ttu-id="10a2a-102">Defect Multiple Target Servers from a Master Server</span><span class="sxs-lookup"><span data-stu-id="10a2a-102">Defect Multiple Target Servers from a Master Server</span></span>
  <span data-ttu-id="10a2a-103">本主题介绍如何通过使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中使多台目标服务器脱离多服务器管理配置。</span><span class="sxs-lookup"><span data-stu-id="10a2a-103">This topic describes how to defect multiple target servers from a multiserver administration configuration in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="10a2a-104">从主服务器运行此过程。</span><span class="sxs-lookup"><span data-stu-id="10a2a-104">Run this procedure from the master server.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="10a2a-105">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="10a2a-105">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-defect-multiple-target-servers-from-a-master-server"></a><span data-ttu-id="10a2a-106">使多台目标服务器脱离主服务器</span><span class="sxs-lookup"><span data-stu-id="10a2a-106">To defect multiple target servers from a master server</span></span>  
  
1.  <span data-ttu-id="10a2a-107">在对象资源管理器中，展开配置为主服务器的服务器。 </span><span class="sxs-lookup"><span data-stu-id="10a2a-107">In **Object Explorer**, expand a server that is configured as a master server.</span></span>  
  
2.  <span data-ttu-id="10a2a-108">右键单击“SQL Server 代理”\*\*\*\*，指向“多服务器管理”\*\*\*\*，再单击“管理目标服务器”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="10a2a-108">Right-click **SQL Server Agent**, point to **Multi Server Administration**, and then click **Manage Target Servers**.</span></span>  
  
3.  <span data-ttu-id="10a2a-109">单击 **“发布指令”**，然后在 **“指令类型”** 列表中选择 **“脱离”**。</span><span class="sxs-lookup"><span data-stu-id="10a2a-109">Click **Post Instructions**, and then in the **Instruction type** list, select **Defect**.</span></span>  
  
4.  <span data-ttu-id="10a2a-110">在 **“收件人”** 下，执行以下操作之一：</span><span class="sxs-lookup"><span data-stu-id="10a2a-110">Under **Recipients**, do one of the following:</span></span>  
  
    -   <span data-ttu-id="10a2a-111">单击 **“所有目标服务器”** ，脱离此主服务器的所有目标服务器。</span><span class="sxs-lookup"><span data-stu-id="10a2a-111">Click **All target servers** to defect all target servers of this master server.</span></span> <span data-ttu-id="10a2a-112">如果要完全卸载当前多服务器管理配置，则使用此选项。</span><span class="sxs-lookup"><span data-stu-id="10a2a-112">Use this option if you want to completely uninstall the current multiserver administration configuration.</span></span>  
  
    -   <span data-ttu-id="10a2a-113">单击 **“以下目标服务器”**，再单击相应的 **“选择”** 框，脱离此主服务器的部分（而不是全部）目标服务器。</span><span class="sxs-lookup"><span data-stu-id="10a2a-113">Click **These target servers**, and then click the corresponding **Select** box, to defect some, but not all, target servers of this master server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10a2a-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="10a2a-114">See Also</span></span>  
 <span data-ttu-id="10a2a-115">[创建多服务器环境](create-a-multiserver-environment.md) </span><span class="sxs-lookup"><span data-stu-id="10a2a-115">[Create a Multiserver Environment](create-a-multiserver-environment.md) </span></span>  
 <span data-ttu-id="10a2a-116">[企业范围的自动化管理](automated-administration-across-an-enterprise.md) </span><span class="sxs-lookup"><span data-stu-id="10a2a-116">[Automated Administration Across an Enterprise](automated-administration-across-an-enterprise.md) </span></span>  
 [<span data-ttu-id="10a2a-117">将目标服务器从主服务器脱离</span><span class="sxs-lookup"><span data-stu-id="10a2a-117">Defect a Target Server from a Master Server</span></span>](defect-a-target-server-from-a-master-server.md)  
  
  
