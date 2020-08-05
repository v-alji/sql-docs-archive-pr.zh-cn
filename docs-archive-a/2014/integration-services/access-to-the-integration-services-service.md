---
title: 对 Integration Services 服务的访问 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS packages, security
- viewing packages while running
- displaying packacges while running
- security [Integration Services], running packages
- packages [Integration Services], security
- current packages running
- Integration Services packages, security
- SQL Server Integration Services packages, security
ms.assetid: 1088aafc-14c5-4e7d-9930-606a24c3049b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7dd6fbed4bedc285069306ab4c400f0f67f9f293
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579017"
---
# <a name="access-to-the-integration-services-service"></a><span data-ttu-id="c5102-102">访问 Integration Services 服务</span><span class="sxs-lookup"><span data-stu-id="c5102-102">Access to the Integration Services Service</span></span>
  <span data-ttu-id="c5102-103">包保护级别可以限制允许谁来编辑和执行包。</span><span class="sxs-lookup"><span data-stu-id="c5102-103">Package protection levels can limit who is allowed to edit and execute a package.</span></span> <span data-ttu-id="c5102-104">需要其他保护来限制谁可以查看当前正在服务器上运行的包列表以及谁可以在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中停止当前正在执行的包。</span><span class="sxs-lookup"><span data-stu-id="c5102-104">Additional protection is needed to limit who can view the list of packages currently running on a server and who can stop currently executing packages in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="c5102-105">使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 服务来列出正在运行的包。</span><span class="sxs-lookup"><span data-stu-id="c5102-105">uses the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] service to list running packages.</span></span> <span data-ttu-id="c5102-106">Windows Administrators 组的成员可以查看和停止所有当前正在运行的包。</span><span class="sxs-lookup"><span data-stu-id="c5102-106">Members of the Windows Administrators group can view and stop all currently running packages.</span></span> <span data-ttu-id="c5102-107">如果用户不属于 Administrators 组的成员，则只能查看和停止他们启动的包。</span><span class="sxs-lookup"><span data-stu-id="c5102-107">Users who are not members of the Administrators group can view and stop only packages that they started.</span></span>  
  
 <span data-ttu-id="c5102-108">请一定要限制对运行 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 服务（尤其是可以枚举远程文件夹的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 服务）的计算机的访问。</span><span class="sxs-lookup"><span data-stu-id="c5102-108">It is important to restrict access to computers that run an [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] service, especially an [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] service that can enumerate remote folders.</span></span> <span data-ttu-id="c5102-109">任何经过身份验证的用户都可以请求对包进行枚举。</span><span class="sxs-lookup"><span data-stu-id="c5102-109">Any authenticated user can request the enumeration of packages.</span></span> <span data-ttu-id="c5102-110">即使该服务没有发现，也会枚举这些文件夹。</span><span class="sxs-lookup"><span data-stu-id="c5102-110">Even if the service doesn not find the service, the service enumerates folders.</span></span> <span data-ttu-id="c5102-111">这些文件夹名称可能会对恶意用户非常有用。</span><span class="sxs-lookup"><span data-stu-id="c5102-111">These folder names may be useful to a malicious user.</span></span> <span data-ttu-id="c5102-112">如果管理员已经将该服务配置为枚举远程计算机上的文件夹，则用户也可能能够看到通常看不到的文件夹名称。</span><span class="sxs-lookup"><span data-stu-id="c5102-112">If an administrator has configured the service to enumerate folders on a remote machine, users may also be able to see folder names that they would normally not be able to see.</span></span>  
  
  
