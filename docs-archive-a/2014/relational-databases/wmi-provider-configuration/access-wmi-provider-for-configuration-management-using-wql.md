---
title: 使用 WQL 访问用于配置管理的 WMI 提供程序 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- query language [WMI]
- WMI Query Language [WMI]
- WQL [WMI]
- WMI Provider for Configuration Management, WQL
ms.assetid: 26499530-d93b-452b-bbe4-217ef1d11e68
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b58297c5e292ceb18a6e2e50e2b25b9aa352e2fa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576559"
---
# <a name="access-wmi-provider-for-configuration-management-using-wql"></a><span data-ttu-id="3ac68-102">使用 WQL 访问用于配置管理的 WMI 提供程序</span><span class="sxs-lookup"><span data-stu-id="3ac68-102">Access WMI Provider for Configuration Management using WQL</span></span>
  <span data-ttu-id="3ac68-103">本节描述如何根据用于计算机管理的 WMI 提供程序执行 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Management Instrumentation 查询语言 (WQL) 语句。</span><span class="sxs-lookup"><span data-stu-id="3ac68-103">This section describes how to execute [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Management Instrumentation Query Language (WQL) statements against the WMI Provider for Computer Management.</span></span>  
  
 <span data-ttu-id="3ac68-104">该示例使用 WQL 编辑器 WBEMtest.exe 根据 WMI 提供程序运行 WQL 查询，以枚举 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服务、网络协议和别名。</span><span class="sxs-lookup"><span data-stu-id="3ac68-104">The example uses a WQL editor, WBEMtest.exe, to run WQL queries against the WMI Provider to enumerate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services, network protocols, and aliases.</span></span>  
  
### <a name="querying-services-using-wbemtest"></a><span data-ttu-id="3ac68-105">使用 WBEMtest 查询服务</span><span class="sxs-lookup"><span data-stu-id="3ac68-105">Querying services using WBEMtest</span></span>  
  
1.  <span data-ttu-id="3ac68-106">从 "**开始**" 菜单中，单击 "**运行**"，然后输入 `WBEMtest` 。</span><span class="sxs-lookup"><span data-stu-id="3ac68-106">From the **Start** menu, click **Run**, and then enter `WBEMtest`.</span></span>  
  
2.  <span data-ttu-id="3ac68-107">将出现 WBEMtest.exe 对话框。</span><span class="sxs-lookup"><span data-stu-id="3ac68-107">The WBEMtest.exe dialog appears.</span></span> <span data-ttu-id="3ac68-108">单击“连接” 。</span><span class="sxs-lookup"><span data-stu-id="3ac68-108">Click **Connect**.</span></span>  
  
3.  <span data-ttu-id="3ac68-109">在第一个文本字段中，键入计算机管理命名空间的 WMI 提供程序：root\Microsoft\SqlServer\ComputerManagement11。</span><span class="sxs-lookup"><span data-stu-id="3ac68-109">In the first text field, type the WMI Provider for Computer Management namespace: root\Microsoft\SqlServer\ComputerManagement11.</span></span> <span data-ttu-id="3ac68-110">单击“连接” 。</span><span class="sxs-lookup"><span data-stu-id="3ac68-110">Click **Connect**.</span></span>  
  
4.  <span data-ttu-id="3ac68-111">单击 **“查询”**。</span><span class="sxs-lookup"><span data-stu-id="3ac68-111">Click **Query**.</span></span> <span data-ttu-id="3ac68-112">键入返回本地计算机上运行的当前服务的查询： \*\* \* 从 SqlService 中选择。\*\*</span><span class="sxs-lookup"><span data-stu-id="3ac68-112">Type a query that returns the current services running on the local computer: **SELECT \* FROM SqlService.**</span></span> <span data-ttu-id="3ac68-113">单击“应用”。</span><span class="sxs-lookup"><span data-stu-id="3ac68-113">Click **Apply**.</span></span>  
  
5.  <span data-ttu-id="3ac68-114">通过添加 `WHERE ServiceName = "MSSQLSERVER"`，进一步细化查询。</span><span class="sxs-lookup"><span data-stu-id="3ac68-114">Further refine the query by adding `WHERE ServiceName = "MSSQLSERVER"`.</span></span>  
  
  
