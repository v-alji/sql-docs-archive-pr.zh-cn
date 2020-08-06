---
title: 连接到 SQL Server 实用工具 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: b9b90b8d-241f-4b74-ac14-de7b10ea1821
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e8e59a28e083fc302faebbcba932c18a04e73a7c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578880"
---
# <a name="connect-to-a-sql-server-utility"></a><span data-ttu-id="a8c3b-102">连接到 SQL Server 实用工具</span><span class="sxs-lookup"><span data-stu-id="a8c3b-102">Connect to a SQL Server Utility</span></span>
  <span data-ttu-id="a8c3b-103">必须先创建实用工具控制点 (UCP)，然后才能连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具。</span><span class="sxs-lookup"><span data-stu-id="a8c3b-103">Before you can connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility, you must create a utility control point (UCP).</span></span> <span data-ttu-id="a8c3b-104">有关详细信息，请参阅 [SQL Server 实用工具功能和任务](sql-server-utility-features-and-tasks.md)。</span><span class="sxs-lookup"><span data-stu-id="a8c3b-104">For more information, see [SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md).</span></span>

 <span data-ttu-id="a8c3b-105">若要查看和管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 资源运行状况，请使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] (SSMS) 连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具。</span><span class="sxs-lookup"><span data-stu-id="a8c3b-105">To view and manage [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resource health, use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] (SSMS) to connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span>

 <span data-ttu-id="a8c3b-106">通过 SSMS 连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具：</span><span class="sxs-lookup"><span data-stu-id="a8c3b-106">To connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility through SSMS:</span></span>

1.  <span data-ttu-id="a8c3b-107">启动 SSMS。</span><span class="sxs-lookup"><span data-stu-id="a8c3b-107">Launch SSMS.</span></span>

2.  <span data-ttu-id="a8c3b-108">在 SSMS 中，连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的某一实例。</span><span class="sxs-lookup"><span data-stu-id="a8c3b-108">In SSMS, connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>

3.  <span data-ttu-id="a8c3b-109">单击 **“视图”** ，然后单击 **“实用工具资源管理器”** 。</span><span class="sxs-lookup"><span data-stu-id="a8c3b-109">Click **View** and then **Utility Explorer**.</span></span>

4.  <span data-ttu-id="a8c3b-110">在实用工具资源管理器导航窗格中，单击 ![](../../database-engine/media/connect-to-utility.gif "Connect_to_Utility")“连接到实用工具”。</span><span class="sxs-lookup"><span data-stu-id="a8c3b-110">In the Utility Explorer navigation pane, click ![](../../database-engine/media/connect-to-utility.gif "Connect_to_Utility")**Connect to Utility**.</span></span>

5.  <span data-ttu-id="a8c3b-111">在 **“连接到服务器”** 对话框中，指定 UCP 实例名称，再单击 **“连接”** 。</span><span class="sxs-lookup"><span data-stu-id="a8c3b-111">In the **Connect to Server** dialog box, specify the UCP instance name, then click **Connect**.</span></span>

6.  <span data-ttu-id="a8c3b-112">查看实用工具资源管理器导航窗格，以便查看 UCP 中 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 资源的树视图。</span><span class="sxs-lookup"><span data-stu-id="a8c3b-112">View the Utility Explorer Navigation Pane to see a tree view of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resources in the UCP.</span></span>

 <span data-ttu-id="a8c3b-113">创建一个新的 UCP 也将您连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实用工具。</span><span class="sxs-lookup"><span data-stu-id="a8c3b-113">Creating a new UCP also connects you to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span> <span data-ttu-id="a8c3b-114">有关详细信息，请参阅[创建 SQL Server 实用工具控制点（SQL Server 实用工具）](create-a-sql-server-utility-control-point-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="a8c3b-114">For more information, see [Create a SQL Server Utility Control Point &#40;SQL Server Utility&#41;](create-a-sql-server-utility-control-point-sql-server-utility.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a8c3b-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a8c3b-115">See Also</span></span>
 <span data-ttu-id="a8c3b-116">[SQL Server 实用工具功能和任务](sql-server-utility-features-and-tasks.md)"[查看资源运行状况策略结果 &#40;SQL Server 实用工具&#41;](view-resource-health-policy-results-sql-server-utility.md)</span><span class="sxs-lookup"><span data-stu-id="a8c3b-116">[SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md) [View Resource Health Policy Results &#40;SQL Server Utility&#41;](view-resource-health-policy-results-sql-server-utility.md)</span></span>


