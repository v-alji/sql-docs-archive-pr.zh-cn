---
title: 针对 CDC 设计器的 SQL Server 连接所需权限 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 80334de2-17c1-43c9-951e-21a9f864e9cb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0815a5d8f1cb66dee0d290a45166ebb395c8efa8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577773"
---
# <a name="sql-server-connection-required-permissions-for-the-cdc-designer"></a><span data-ttu-id="0849b-102">针对 CDC 设计器的 SQL Server 连接所需权限</span><span class="sxs-lookup"><span data-stu-id="0849b-102">SQL Server Connection Required Permissions for the CDC Designer</span></span>
  <span data-ttu-id="0849b-103">CDC 设计器控制台需要 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的连接信息以便执行其任务。</span><span class="sxs-lookup"><span data-stu-id="0849b-103">The CDC Designer Console requires connection information to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to perform its tasks.</span></span> <span data-ttu-id="0849b-104">本主题介绍可在 **“连接到 SQL Server”** 对话框中为设置与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的连接而提供的信息。</span><span class="sxs-lookup"><span data-stu-id="0849b-104">This topic describes the information that can be provided in the **Connect to SQL Server** dialog box for setting up the connection to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="0849b-105">**“连接到 SQL Server”** 对话框将在需要时打开，例如在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 连接信息不可用时或者在该信息存在但连接没有所需权限时。</span><span class="sxs-lookup"><span data-stu-id="0849b-105">The **Connect to SQL Server** dialog box opens when necessary, such as when the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connection information is not available or when the information exists but the connection does not have the required permissions.</span></span>  
  
 <span data-ttu-id="0849b-106">下表介绍需要连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的不同任务以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名/用户的所需权限。</span><span class="sxs-lookup"><span data-stu-id="0849b-106">The following table describes the various tasks where a connection to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is required and the required permissions from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login/user.</span></span>  
  
|<span data-ttu-id="0849b-107">任务</span><span class="sxs-lookup"><span data-stu-id="0849b-107">Task</span></span>|<span data-ttu-id="0849b-108">最低权限</span><span class="sxs-lookup"><span data-stu-id="0849b-108">Minimum Permissions</span></span>|  
|----------|-------------------------|  
|<span data-ttu-id="0849b-109">查看使用关联的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的 CDC 服务和实例的列表。</span><span class="sxs-lookup"><span data-stu-id="0849b-109">View the list of CDC Services and Instances using the associated [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>|<span data-ttu-id="0849b-110">`db_datareader` 角色</span><span class="sxs-lookup"><span data-stu-id="0849b-110">`db_datareader` role on MSXDBCDC</span></span>|  
|<span data-ttu-id="0849b-111">启动/停止 CDC 实例</span><span class="sxs-lookup"><span data-stu-id="0849b-111">Start/Stop CDC Instance(s)</span></span>|<span data-ttu-id="0849b-112">`db_datareader` 和 `db_datawriter` 角色</span><span class="sxs-lookup"><span data-stu-id="0849b-112">`db_datareader` and `db_datawriter` roles on MSXDBCDC</span></span>|  
|<span data-ttu-id="0849b-113">查看 CDC 实例状态。</span><span class="sxs-lookup"><span data-stu-id="0849b-113">View the CDC Instance status.</span></span>|<span data-ttu-id="0849b-114">`db_owner` 角色</span><span class="sxs-lookup"><span data-stu-id="0849b-114">`db_owner` role on the CDC Instance database</span></span>|  
|<span data-ttu-id="0849b-115">创建新的 Oracle CDC 实例数据库。</span><span class="sxs-lookup"><span data-stu-id="0849b-115">Create a new Oracle CDC Instance database.</span></span>|<span data-ttu-id="0849b-116">`dbcreator` 固定服务器角色</span><span class="sxs-lookup"><span data-stu-id="0849b-116">`dbcreator` fixed-server role</span></span>|  
|<span data-ttu-id="0849b-117">创建新的 Oracle CDC 实例。</span><span class="sxs-lookup"><span data-stu-id="0849b-117">Create a new Oracle CDC Instance.</span></span>|<span data-ttu-id="0849b-118">`db_datareader` 角色</span><span class="sxs-lookup"><span data-stu-id="0849b-118">`db_datareader` role on MSXDBCDC</span></span><br /><br /> <span data-ttu-id="0849b-119">`db_owner` 角色。</span><span class="sxs-lookup"><span data-stu-id="0849b-119">`db_owner` role on the CDC database that was created.</span></span>|  
|<span data-ttu-id="0849b-120">获取部署脚本。</span><span class="sxs-lookup"><span data-stu-id="0849b-120">Get deployment scripts.</span></span>|<span data-ttu-id="0849b-121">`db_datareader` 和 `db_datawriter` 角色</span><span class="sxs-lookup"><span data-stu-id="0849b-121">`db_datareader` and `db_datawriter` roles on MSXDBCDC</span></span><br /><br /> <span data-ttu-id="0849b-122">`db_owner` 角色</span><span class="sxs-lookup"><span data-stu-id="0849b-122">`db_owner` role on the relatedCDC database</span></span>|  
|<span data-ttu-id="0849b-123">更改配置和添加/删除捕获实例。</span><span class="sxs-lookup"><span data-stu-id="0849b-123">Change configuration and add/remove capture instances.</span></span>|<span data-ttu-id="0849b-124">`db_datareader` 和 `db_datawriter` 角色</span><span class="sxs-lookup"><span data-stu-id="0849b-124">`db_datareader` and `db_datawriter` roles on MSXDBCDC</span></span><br /><br /> <span data-ttu-id="0849b-125">`db_owner` 角色</span><span class="sxs-lookup"><span data-stu-id="0849b-125">`db_owner` role on the related CDC database</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0849b-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0849b-126">See Also</span></span>  
 <span data-ttu-id="0849b-127">[访问 CDC 设计器控制台](access-the-cdc-designer-console.md) </span><span class="sxs-lookup"><span data-stu-id="0849b-127">[Access the CDC Designer Console](access-the-cdc-designer-console.md) </span></span>  
 [<span data-ttu-id="0849b-128">用于实例创建的 SQL Server 连接</span><span class="sxs-lookup"><span data-stu-id="0849b-128">SQL Server Connection for Instance Creation</span></span>](sql-server-connection-for-instance-creation.md)  
  
  
