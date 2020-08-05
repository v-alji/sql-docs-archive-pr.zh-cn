---
title: 针对 CDC 服务的 SQL Server 连接所需权限 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: d9e968f9-180c-4fa0-a849-98f2b1942330
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e63b98ffd0371bd5b70ecc0ac843ad40a4a5d03e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580829"
---
# <a name="sql-server-connection-required-permissions-for-the-cdc-service"></a><span data-ttu-id="d543e-102">针对 CDC 服务的 SQL Server 连接所需权限</span><span class="sxs-lookup"><span data-stu-id="d543e-102">SQL Server Connection Required Permissions for the CDC Service</span></span>
  <span data-ttu-id="d543e-103">CDC 服务配置控制台要求与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的连接信息以便执行其任务。</span><span class="sxs-lookup"><span data-stu-id="d543e-103">The CDC Service Configuration Console requires connection information to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to perform their tasks.</span></span> <span data-ttu-id="d543e-104">本主题介绍可在“连接到 SQL Server”对话框中为设置与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的连接而提供的信息。</span><span class="sxs-lookup"><span data-stu-id="d543e-104">This topic describes the information that can be provided in the Connect to SQL Server dialog box for setting up the connection to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="d543e-105">“连接到 SQL Server”对话框将在需要时打开，例如在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 连接信息不可用时或者在该信息存在但连接没有所需权限时。</span><span class="sxs-lookup"><span data-stu-id="d543e-105">The Connect to SQL Server dialog box opens when necessary, such as when the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connection information is not available or when the information exists but the connection does not have the required permissions.</span></span>  
  
 <span data-ttu-id="d543e-106">下表介绍需要连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的不同任务以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名/用户的所需权限。</span><span class="sxs-lookup"><span data-stu-id="d543e-106">The following table describes the various tasks where a connection to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is required and the required permissions from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login/user.</span></span>  
  
|<span data-ttu-id="d543e-107">任务</span><span class="sxs-lookup"><span data-stu-id="d543e-107">Task</span></span>|<span data-ttu-id="d543e-108">最低权限</span><span class="sxs-lookup"><span data-stu-id="d543e-108">Minimum Permissions</span></span>|  
|----------|-------------------------|  
|<span data-ttu-id="d543e-109">准备 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="d543e-109">Prepare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instance.</span></span>|<span data-ttu-id="d543e-110">`dbcreator` 固定服务器角色</span><span class="sxs-lookup"><span data-stu-id="d543e-110">`dbcreator` fixed-server role</span></span>|  
|<span data-ttu-id="d543e-111">创建供 Oracle CDC 服务使用的 Oracle CDC 服务-SQL Server 登录名。</span><span class="sxs-lookup"><span data-stu-id="d543e-111">Create an Oracle CDC Service-SQL Server login for use by the Oracle CDC service.</span></span>|<span data-ttu-id="d543e-112">`public` 固定服务器角色</span><span class="sxs-lookup"><span data-stu-id="d543e-112">`public` fixed-server role</span></span>|  
|<span data-ttu-id="d543e-113">创建 Oracle CDC 服务登录名以便用于在 MSXDBCDC 中注册新服务。</span><span class="sxs-lookup"><span data-stu-id="d543e-113">Create an Oracle CDC Service-login to use for registering the new service in MSXDBCDC.</span></span>|<span data-ttu-id="d543e-114">`db_datareader` 和 `db_datawriter` 角色</span><span class="sxs-lookup"><span data-stu-id="d543e-114">`db_datareader` and `db_datawriter` roles on MSXDBCDC</span></span>|  
|<span data-ttu-id="d543e-115">编辑 Oracle CDC 服务登录名以便用于在 MSXDBCDC 中更新服务注册。</span><span class="sxs-lookup"><span data-stu-id="d543e-115">Edit an Oracle CDC Service-login to use for updating the registration of the service in MSXDBCDC.</span></span>|<span data-ttu-id="d543e-116">`db_datareader` 和 `db_datawriter` 角色</span><span class="sxs-lookup"><span data-stu-id="d543e-116">`db_datareader` and `db_datawriter` roles on MSXDBCDC</span></span>|  
|<span data-ttu-id="d543e-117">删除 Oracle CDC 服务登录名以便用于在 MSXDBCDC 中更新服务注册。</span><span class="sxs-lookup"><span data-stu-id="d543e-117">Delete an Oracle CDC Service-login to use for updating the registration of the service in MSXDBCDC.</span></span>|<span data-ttu-id="d543e-118">`db_datareader` 和 `db_datawriter` 角色</span><span class="sxs-lookup"><span data-stu-id="d543e-118">`db_datareader` and `db_datawriter` roles on MSXDBCDC</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d543e-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d543e-119">See Also</span></span>  
 <span data-ttu-id="d543e-120">[连接到 SQL Server](connection-to-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d543e-120">[Connection to SQL Server](connection-to-sql-server.md) </span></span>  
 [<span data-ttu-id="d543e-121">删除与 SQL Server 的连接</span><span class="sxs-lookup"><span data-stu-id="d543e-121">Connection to SQL Server for Delete</span></span>](connection-to-sql-server-for-delete.md)  
  
  
