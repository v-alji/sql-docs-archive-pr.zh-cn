---
title: SQL Server Browser 属性（“高级”选项卡）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: ba79137a-cb72-4bf3-a650-e11d02cfce10
author: stevestein
ms.author: sstein
ms.openlocfilehash: 480cd93c3feca44dd455a1a9ce2fd12994ca6100
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589988"
---
# <a name="sql-server-browser-properties-advanced-tab"></a><span data-ttu-id="eacb3-102">SQL Server 浏览器属性（“高级”选项卡）</span><span class="sxs-lookup"><span data-stu-id="eacb3-102">SQL Server Browser Properties (Advanced Tab)</span></span>
  <span data-ttu-id="eacb3-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 浏览器程序以服务的形式在服务器上运行。</span><span class="sxs-lookup"><span data-stu-id="eacb3-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser program runs as a service on the server.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="eacb3-104">浏览器侦听对 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 资源的传入请求，并提供计算机上安装的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的相关信息。</span><span class="sxs-lookup"><span data-stu-id="eacb3-104">Browser listens for incoming requests for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resources and provides information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances installed on the computer.</span></span>  
  
## <a name="options"></a><span data-ttu-id="eacb3-105">选项</span><span class="sxs-lookup"><span data-stu-id="eacb3-105">Options</span></span>  
 <span data-ttu-id="eacb3-106">**群集**</span><span class="sxs-lookup"><span data-stu-id="eacb3-106">**Clustered**</span></span>  
 <span data-ttu-id="eacb3-107">指示此服务是否作为群集服务器的资源进行安装。</span><span class="sxs-lookup"><span data-stu-id="eacb3-107">Indicates if this service is installed as a resource of a clustered server.</span></span>  
  
 <span data-ttu-id="eacb3-108">**客户反馈报告**</span><span class="sxs-lookup"><span data-stu-id="eacb3-108">**Customer Feedback Reporting**</span></span>  
 <span data-ttu-id="eacb3-109">指示是否已对此服务启用服务质量监视。</span><span class="sxs-lookup"><span data-stu-id="eacb3-109">Indicates whether Service Quality Monitoring has been enabled on this service.</span></span> <span data-ttu-id="eacb3-110">有关客户反馈报告的详细信息，请在联机丛书中搜索主题“错误和使用报告设置”。</span><span class="sxs-lookup"><span data-stu-id="eacb3-110">For more information on Customer Feedback Reporting, search Books Online for the topic, "Error and Usage Report Settings."</span></span>  
  
 <span data-ttu-id="eacb3-111">**转储目录**</span><span class="sxs-lookup"><span data-stu-id="eacb3-111">**Dump Directory**</span></span>  
 <span data-ttu-id="eacb3-112">显示发生错误时内存转储的存放位置。</span><span class="sxs-lookup"><span data-stu-id="eacb3-112">The location where memory dumps are placed in case of an error.</span></span>  
  
 <span data-ttu-id="eacb3-113">**错误报告**</span><span class="sxs-lookup"><span data-stu-id="eacb3-113">**Error Reporting**</span></span>  
 <span data-ttu-id="eacb3-114">当设置为 **“是”** 时，如果发生严重错误，Dr. Watson 程序将把相关信息转发给 [!INCLUDE[msCoName](../../includes/msconame-md.md)] ，或转发给错误服务器。</span><span class="sxs-lookup"><span data-stu-id="eacb3-114">When set to **Yes**, the Dr. Watson program forwards information to either [!INCLUDE[msCoName](../../includes/msconame-md.md)] or your error server if a serious failure occurs.</span></span> <span data-ttu-id="eacb3-115">有关错误报告的详细信息，请在联机丛书中搜索主题“错误和使用报告设置”。</span><span class="sxs-lookup"><span data-stu-id="eacb3-115">For more information on Error Reporting, search Books Online for the topic, "Error and Usage Report Settings."</span></span>  
  
 <span data-ttu-id="eacb3-116">**实例 ID**</span><span class="sxs-lookup"><span data-stu-id="eacb3-116">**Instance ID**</span></span>  
 <span data-ttu-id="eacb3-117">指示使用此 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理实例的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="eacb3-117">Indicates the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that used this [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent instance.</span></span> <span data-ttu-id="eacb3-118">默认实例为 **MSSQL10_50.MSSQLSERVER**。</span><span class="sxs-lookup"><span data-stu-id="eacb3-118">The default instance is **MSSQL10_50.MSSQLSERVER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eacb3-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="eacb3-119">See Also</span></span>  
 [<span data-ttu-id="eacb3-120">SQL Server Browser 服务</span><span class="sxs-lookup"><span data-stu-id="eacb3-120">SQL Server Browser Service</span></span>](../../../2014/tools/configuration-manager/sql-server-browser-service.md)  
  
  
