---
title: DQS 安全性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 921927f5-1b1e-452a-a79e-c691829fd826
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 3da3cdbe746b69c5c4cfe7c7c796827dd74a433c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689603"
---
# <a name="dqs-security"></a><span data-ttu-id="232d4-102">DQS 安全性</span><span class="sxs-lookup"><span data-stu-id="232d4-102">DQS Security</span></span>
  <span data-ttu-id="232d4-103">[!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 安全基础结构基于 SQL Server 安全基础结构。</span><span class="sxs-lookup"><span data-stu-id="232d4-103">The [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) security infrastructure is based upon the SQL Server security infrastructure.</span></span> <span data-ttu-id="232d4-104">数据库管理员通过将用户与 DQS 角色相关联，向用户授予一组权限。</span><span class="sxs-lookup"><span data-stu-id="232d4-104">A database administrator grants a user a set of permissions by associating the user with a DQS role.</span></span> <span data-ttu-id="232d4-105">这样，可以确定用户可访问的 DQS 资源以及允许用户执行的功能活动。</span><span class="sxs-lookup"><span data-stu-id="232d4-105">Doing so determines the DQS resources that the user has access to and the functional activities that the user is allowed to perform.</span></span>  
  
## <a name="dqs-roles"></a><span data-ttu-id="232d4-106">DQS 角色</span><span class="sxs-lookup"><span data-stu-id="232d4-106">DQS Roles</span></span>  
 <span data-ttu-id="232d4-107">有四种 DQS 角色。</span><span class="sxs-lookup"><span data-stu-id="232d4-107">There are four roles for DQS.</span></span> <span data-ttu-id="232d4-108">一种角色是数据库管理员 (DBA)，主要负责处理产品安装、数据库维护和用户管理等工作。</span><span class="sxs-lookup"><span data-stu-id="232d4-108">One is the database administrator (DBA) who deals primarily with product installation, database maintenance, and user management.</span></span> <span data-ttu-id="232d4-109">该角色主要使用 SQL Server Management Studio，而不是 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 应用程序。</span><span class="sxs-lookup"><span data-stu-id="232d4-109">This role primarily uses the SQL Server Management Studio, rather than within the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] application.</span></span> <span data-ttu-id="232d4-110">他们的服务器角色是 sysadmin。</span><span class="sxs-lookup"><span data-stu-id="232d4-110">Their server role is sysadmin.</span></span>  
  
 <span data-ttu-id="232d4-111">其他三个角色是信息工作者，即通过在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 应用程序中工作直接使用产品的数据专员。</span><span class="sxs-lookup"><span data-stu-id="232d4-111">The three other roles are information workers, data stewards who use the product directly by working in the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] application.</span></span> <span data-ttu-id="232d4-112">这些角色包括：</span><span class="sxs-lookup"><span data-stu-id="232d4-112">These roles include the following:</span></span>  
  
-   <span data-ttu-id="232d4-113">DQS 管理员 \*\*\*\* （dqs_administrator 角色）可以在产品范围内执行任何操作。</span><span class="sxs-lookup"><span data-stu-id="232d4-113">The **DQS Administrator** (dqs_administrator role) can do everything in the scope of the product.</span></span> <span data-ttu-id="232d4-114">该管理员可以编辑和执行项目、创建和编辑知识库、终止活动、停止活动中的过程，可以更改配置和 Reference Data Services 设置。</span><span class="sxs-lookup"><span data-stu-id="232d4-114">The administrator can edit and execute a project, create and edit a knowledge base, terminate an activity, stop a process within an activity, and can change the configuration and Reference Data Services settings.</span></span> <span data-ttu-id="232d4-115">但是，DQS 管理员无法安装服务器或添加新用户。</span><span class="sxs-lookup"><span data-stu-id="232d4-115">The DQS Administrator cannot, however, install the server or add new users.</span></span> <span data-ttu-id="232d4-116">必须由数据库管理员执行这些操作。</span><span class="sxs-lookup"><span data-stu-id="232d4-116">The database administrator must do that.</span></span>  
  
-   <span data-ttu-id="232d4-117">**DQS KB 编辑人员** （dqs_kb_editor 角色）可以执行所有 DQS 活动，但管理除外。</span><span class="sxs-lookup"><span data-stu-id="232d4-117">The **DQS KB Editor** (dqs_kb_editor role) can perform all of the DQS activities, except for administration.</span></span> <span data-ttu-id="232d4-118">KB 编辑人员可以编辑和执行项目，以及创建和编辑知识库。</span><span class="sxs-lookup"><span data-stu-id="232d4-118">The KB Editor can edit and execute a project, and create and edit a knowledge base.</span></span> <span data-ttu-id="232d4-119">他们可以查看活动监视数据，但不能终止或停止活动或履行管理职责。</span><span class="sxs-lookup"><span data-stu-id="232d4-119">They can see the activity monitoring data, but cannot terminate or stop an activity or perform administrative duties.</span></span>  
  
-   <span data-ttu-id="232d4-120">**DQS KB 操作员** （dqs_kb_operator 角色）可以编辑和执行项目。</span><span class="sxs-lookup"><span data-stu-id="232d4-120">The **DQS KB Operator** (dqs_kb_operator role) can edit and execute a project.</span></span> <span data-ttu-id="232d4-121">他们不能执行任何形式的知识管理；也不能创建或更改知识库。</span><span class="sxs-lookup"><span data-stu-id="232d4-121">They cannot perform any kind of knowledge management; they cannot create or change a knowledge base.</span></span> <span data-ttu-id="232d4-122">他们可以查看活动监视数据，但不能终止活动或履行管理职责。</span><span class="sxs-lookup"><span data-stu-id="232d4-122">They can see the activity monitoring data, but cannot terminate an activity or perform administrative duties.</span></span>  
  
## <a name="user-management"></a><span data-ttu-id="232d4-123">用户管理</span><span class="sxs-lookup"><span data-stu-id="232d4-123">User Management</span></span>  
 <span data-ttu-id="232d4-124">数据库管理员 (DBA) 可以创建 DQS 用户，并将用户与 SQL Server Management Studio 中的 DQS 角色相关联。</span><span class="sxs-lookup"><span data-stu-id="232d4-124">The database administrator (DBA) creates DQS users and associates them with DQS roles in SQL Server Management Studio.</span></span> <span data-ttu-id="232d4-125">DBA 通过将 SQL 登录名添加为 DQS_MAIN 数据库的用户，并将每个用户与其中一个 DQS 角色相关联，以管理其权限。</span><span class="sxs-lookup"><span data-stu-id="232d4-125">The DBA manages their permissions by adding SQL Logins as users of the DQS_MAIN database, and associating each user with one of the DQS roles.</span></span> <span data-ttu-id="232d4-126">每个角色都会被授予针对 DQS_MAIN 数据库的一组存储过程的权限。</span><span class="sxs-lookup"><span data-stu-id="232d4-126">Each role is granted permissions to a set of stored procedures on the DQS_MAIN database.</span></span> <span data-ttu-id="232d4-127">这三个 DQS 角色不适用于 DQS_PROJECTS 和 DQS_STAGING_DATA 数据库。</span><span class="sxs-lookup"><span data-stu-id="232d4-127">The three DQS roles are not available for the DQS_PROJECTS and DQS_STAGING_DATA databases.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="232d4-128">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="232d4-128">Related Tasks</span></span>  
  
|<span data-ttu-id="232d4-129">任务说明</span><span class="sxs-lookup"><span data-stu-id="232d4-129">Task Description</span></span>|<span data-ttu-id="232d4-130">主题</span><span class="sxs-lookup"><span data-stu-id="232d4-130">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="232d4-131">介绍如何使用 SQL Server Management Studio 创建用户并授予 DQS 角色。</span><span class="sxs-lookup"><span data-stu-id="232d4-131">Describes how to create a user and grant DQS roles using SQL Server Management Studio.</span></span>|[<span data-ttu-id="232d4-132">在 SSMS 中管理 DQS 用户</span><span class="sxs-lookup"><span data-stu-id="232d4-132">Manage DQS Users in SSMS</span></span>](../../2014/data-quality-services/manage-dqs-users-in-ssms.md)|  
  
  
