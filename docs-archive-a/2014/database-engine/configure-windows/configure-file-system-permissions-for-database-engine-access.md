---
title: 配置数据库引擎访问的文件系统权限 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- file system permissions
- service account [SQL Server], file system permissions
- permissions [SQL Server], file system
ms.assetid: 78bba43c-4edb-4216-84ac-d6246ae5546d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1d9abbd095f2d5be7415ed28a17fb710ff8ab504
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591592"
---
# <a name="configure-file-system-permissions-for-database-engine-access"></a><span data-ttu-id="d9561-102">配置数据库引擎访问的文件系统权限</span><span class="sxs-lookup"><span data-stu-id="d9561-102">Configure File System Permissions for Database Engine Access</span></span>
  <span data-ttu-id="d9561-103">本主题说明如何授予 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]对存储数据库文件的位置的文件系统访问权限。</span><span class="sxs-lookup"><span data-stu-id="d9561-103">This topic describes how to grant the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], file system access to the location where database files are stored.</span></span> <span data-ttu-id="d9561-104">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 服务必须具有 Windows 文件系统的权限才能访问存储数据库文件的文件夹。</span><span class="sxs-lookup"><span data-stu-id="d9561-104">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] service must have permission of the Windows file system to access the file folder where database files are stored.</span></span> <span data-ttu-id="d9561-105">在安装过程中配置对默认位置的权限。</span><span class="sxs-lookup"><span data-stu-id="d9561-105">Permission to the default location is configured during setup.</span></span> <span data-ttu-id="d9561-106">如果您将数据库文件放在其他位置，可能需要按照这些步骤授予 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 对该位置的完全控制权限。</span><span class="sxs-lookup"><span data-stu-id="d9561-106">If you place your database files in a different location, you might need to follow these steps to grant the [!INCLUDE[ssDE](../../includes/ssde-md.md)] the full control permission to that location.</span></span>  
  
 <span data-ttu-id="d9561-107">从 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 开始，将权限分配给每个服务的服务 SID。</span><span class="sxs-lookup"><span data-stu-id="d9561-107">Beginning with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] permissions are assigned to the per-service SID for each of its services.</span></span> <span data-ttu-id="d9561-108">此系统可帮助提供更好的服务隔离和安全保护。</span><span class="sxs-lookup"><span data-stu-id="d9561-108">This system helps provide service isolation and defense in depth.</span></span> <span data-ttu-id="d9561-109">每个服务 SID 从服务名称派生得到，对每个服务是唯一的。</span><span class="sxs-lookup"><span data-stu-id="d9561-109">The per-service SID is derived from the service name and is unique to each service.</span></span> <span data-ttu-id="d9561-110">[配置 Windows 服务帐户和权限](configure-windows-service-accounts-and-permissions.md) 主题介绍了每个服务 SID，并提供 **Windows 特权和权限**一节中所述的名称。</span><span class="sxs-lookup"><span data-stu-id="d9561-110">The topic [Configure Windows Service Accounts and Permissions](configure-windows-service-accounts-and-permissions.md) describes the per-service SID and provides the names in the section **Windows Privileges and Rights**.</span></span> <span data-ttu-id="d9561-111">必须为每个服务 SID 分配对文件位置的访问权限。</span><span class="sxs-lookup"><span data-stu-id="d9561-111">It is the per-service SID that must be assigned the access permission on the file location.</span></span>  
  
## <a name="to-grant-file-system-permission-to-the-per-service-sid"></a><span data-ttu-id="d9561-112">将文件系统权限授予每个服务 SID</span><span class="sxs-lookup"><span data-stu-id="d9561-112">To Grant File System Permission to the Per-service SID</span></span>  
  
1.  <span data-ttu-id="d9561-113">使用 Windows 资源管理器，导航到存储数据库文件的文件系统位置。</span><span class="sxs-lookup"><span data-stu-id="d9561-113">Using Windows Explorer, navigate to the file system location where the database files are stored.</span></span> <span data-ttu-id="d9561-114">右键单击文件系统文件夹，然后单击“属性”。</span><span class="sxs-lookup"><span data-stu-id="d9561-114">Right-click the file system folder, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="d9561-115">在 **“安全性”** 选项卡上，单击 **“编辑”** ，然后单击 **“添加”** 。</span><span class="sxs-lookup"><span data-stu-id="d9561-115">On the **Security** tab, click **Edit**, and then **Add**.</span></span>  
  
3.  <span data-ttu-id="d9561-116">在 **“选择用户、计算机、服务帐户或组”** 对话框中，单击 **“位置”** ，在位置列表的顶部选择您的计算机名称，然后单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="d9561-116">In the **Select Users, Computer, Service Account, or Groups** dialog box, click **Locations**, at the top of the location list, select your computer name, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="d9561-117">在 "**输入要选择的对象名称**" 框中，键入联机丛书主题 "**配置 Windows 服务帐户和权限**" 中列出的每个服务 SID 的名称。</span><span class="sxs-lookup"><span data-stu-id="d9561-117">In the **Enter the object names to select** box, type the name of the per-service SID listed in the Books Online topic **Configure Windows Service Accounts and Permissions**.</span></span> <span data-ttu-id="d9561-118"> ("对于 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 每个服务 SID"，请将**nt SERVICE\MSSQLSERVER**用于默认实例，或将 Nt **SERVICE\MSSQL $ InstanceName**用于命名实例。 ) </span><span class="sxs-lookup"><span data-stu-id="d9561-118">(For the [!INCLUDE[ssDE](../../includes/ssde-md.md)] per service SID, use **NT SERVICE\MSSQLSERVER** for a default instance, or **NT SERVICE\MSSQL$InstanceName** for a named instance.)</span></span>  
  
5.  <span data-ttu-id="d9561-119">单击 **“检查名称”** 以验证该条目。</span><span class="sxs-lookup"><span data-stu-id="d9561-119">Click **Check Names** to validate the entry.</span></span> <span data-ttu-id="d9561-120">验证经常失败，而且可能告知您找不到该名称。</span><span class="sxs-lookup"><span data-stu-id="d9561-120">The validation often fails, and might advise you that the name was not found.</span></span> <span data-ttu-id="d9561-121">单击 **“确定”** 时，将显示 **“找到多个名称”** 对话框。</span><span class="sxs-lookup"><span data-stu-id="d9561-121">When you click **OK**, a **Multiple Names Found** dialog box appears.</span></span>  
  
6.  <span data-ttu-id="d9561-122">现在选择每个服务 SID， **MSSQLSERVER**或**NT SERVICE\MSSQL $ InstanceName**，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="d9561-122">Now select the per-service SID, either **MSSQLSERVER** or **NT SERVICE\MSSQL$InstanceName**, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="d9561-123">再次单击 **"确定"** 以返回 "**权限**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="d9561-123">Click **OK** again to return to the **Permissions** dialog box.</span></span>  
  
8.  <span data-ttu-id="d9561-124">在 "**组或用户名**" 框中，选择 "每服务 SID"，然后在 "**权限**" \<name> 框中，选中 "**允许**" 复选框以进行**完全控制**。</span><span class="sxs-lookup"><span data-stu-id="d9561-124">In the **Group or user** names box, select the per-service SID, and then in the **Permissions for** \<name> box, select the **Allow** check box for **Full control**.</span></span>  
  
9. <span data-ttu-id="d9561-125">单击 **“应用”** ，然后单击 **“确定”** 两次以退出。</span><span class="sxs-lookup"><span data-stu-id="d9561-125">Click **Apply**, and then click **OK** twice to exit.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9561-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d9561-126">See Also</span></span>  
 <span data-ttu-id="d9561-127">[管理数据库引擎服务](manage-the-database-engine-services.md) </span><span class="sxs-lookup"><span data-stu-id="d9561-127">[Manage the Database Engine Services](manage-the-database-engine-services.md) </span></span>  
 <span data-ttu-id="d9561-128">[移动系统数据库](../../relational-databases/databases/system-databases.md) </span><span class="sxs-lookup"><span data-stu-id="d9561-128">[Move System Databases](../../relational-databases/databases/system-databases.md) </span></span>  
 [<span data-ttu-id="d9561-129">移动用户数据库</span><span class="sxs-lookup"><span data-stu-id="d9561-129">Move User Databases</span></span>](../../relational-databases/databases/move-user-databases.md)  
  
  
