---
title: 文件和版本号 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, versions
- components [SMO]
- files [SMO], components
- SMO [SQL Server], versions
- versions [SMO]
ms.assetid: 510907b6-e7a9-41bd-b892-d6d99a5118e1
author: stevestein
ms.author: sstein
ms.openlocfilehash: f1a7286f15af28f97e488b8b40fd745a0d320108
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586609"
---
# <a name="files-and-version-numbers"></a><span data-ttu-id="97e56-102">文件和版本号</span><span class="sxs-lookup"><span data-stu-id="97e56-102">Files and Version Numbers</span></span>
  <span data-ttu-id="97e56-103">所有必需 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的管理对象 (SMO) 组件作为 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 客户端或服务器实例的一部分进行安装。</span><span class="sxs-lookup"><span data-stu-id="97e56-103">All required [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO) components are installed as part of an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client or server.</span></span> <span data-ttu-id="97e56-104">SMO 实现于几个托管程序集中。</span><span class="sxs-lookup"><span data-stu-id="97e56-104">SMO is implemented in several managed assemblies.</span></span> <span data-ttu-id="97e56-105">您可以在客户端或服务器上开发 SMO 应用程序。</span><span class="sxs-lookup"><span data-stu-id="97e56-105">You can develop SMO applications on either a client or a server.</span></span>  
  
|<span data-ttu-id="97e56-106">目录</span><span class="sxs-lookup"><span data-stu-id="97e56-106">Directory</span></span>|<span data-ttu-id="97e56-107">文件</span><span class="sxs-lookup"><span data-stu-id="97e56-107">File</span></span>|<span data-ttu-id="97e56-108">说明</span><span class="sxs-lookup"><span data-stu-id="97e56-108">Description</span></span>|  
|---------------|----------|-----------------|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|<span data-ttu-id="97e56-109">Microsoft.SqlServer.ConnectionInfo.dll</span><span class="sxs-lookup"><span data-stu-id="97e56-109">Microsoft.SqlServer.ConnectionInfo.dll</span></span>|<span data-ttu-id="97e56-110">包含对连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的支持。</span><span class="sxs-lookup"><span data-stu-id="97e56-110">Contains support for connecting to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|<span data-ttu-id="97e56-111">Microsoft.SqlServer.ServiceBrokerEnum.dll</span><span class="sxs-lookup"><span data-stu-id="97e56-111">Microsoft.SqlServer.ServiceBrokerEnum.dll</span></span>|<span data-ttu-id="97e56-112">包含对编写 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Service Broker 的支持。</span><span class="sxs-lookup"><span data-stu-id="97e56-112">Contains support for programming the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Service Broker.</span></span> <span data-ttu-id="97e56-113">这仅在访问 Service Broker 的程序中是必需的。</span><span class="sxs-lookup"><span data-stu-id="97e56-113">This is required only in programs that access the Service Broker.</span></span>|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|<span data-ttu-id="97e56-114">Microsoft.SqlServer.Smo.dll</span><span class="sxs-lookup"><span data-stu-id="97e56-114">Microsoft.SqlServer.Smo.dll</span></span>|<span data-ttu-id="97e56-115">包含大多数 SMO 类。</span><span class="sxs-lookup"><span data-stu-id="97e56-115">Contains the most of the SMO classes.</span></span>|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|<span data-ttu-id="97e56-116">Microsoft.SqlServer.SmoExtended.dll</span><span class="sxs-lookup"><span data-stu-id="97e56-116">Microsoft.SqlServer.SmoExtended.dll</span></span><br /><br /> <span data-ttu-id="97e56-117">Microsoft.SqlServer.Management.Sdk.Sfc.dll</span><span class="sxs-lookup"><span data-stu-id="97e56-117">Microsoft.SqlServer.Management.Sdk.Sfc.dll</span></span><br /><br /> <span data-ttu-id="97e56-118">Microsoft.SqlServer.SqlEnum.dll</span><span class="sxs-lookup"><span data-stu-id="97e56-118">Microsoft.SqlServer.SqlEnum.dll</span></span>|<span data-ttu-id="97e56-119">包含对 SMO 类的支持。</span><span class="sxs-lookup"><span data-stu-id="97e56-119">Contains support for the SMO classes.</span></span>|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|<span data-ttu-id="97e56-120">Microsoft.SqlServer.WmiEnum.dll</span><span class="sxs-lookup"><span data-stu-id="97e56-120">Microsoft.SqlServer.WmiEnum.dll</span></span>|<span data-ttu-id="97e56-121">包含 Windows Management Instrumentation (WMI) 提供程序类。</span><span class="sxs-lookup"><span data-stu-id="97e56-121">Contains the Windows Management Instrumentation (WMI) Provider classes.</span></span> <span data-ttu-id="97e56-122">这仅对使用 WMI 提供程序类的程序是必需的。</span><span class="sxs-lookup"><span data-stu-id="97e56-122">This is required only for programs that use the WMI Provider classes.</span></span>|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|<span data-ttu-id="97e56-123">Microsoft.SqlServer.RegSvrEnum.dll</span><span class="sxs-lookup"><span data-stu-id="97e56-123">Microsoft.SqlServer.RegSvrEnum.dll</span></span>|<span data-ttu-id="97e56-124">包含注册服务器类。</span><span class="sxs-lookup"><span data-stu-id="97e56-124">Contains the Registered Server classes.</span></span> <span data-ttu-id="97e56-125">这仅对使用注册服务器类的程序是必需的。</span><span class="sxs-lookup"><span data-stu-id="97e56-125">This is required only for programs that use the Registered Server classes.</span></span>|  
  
  
