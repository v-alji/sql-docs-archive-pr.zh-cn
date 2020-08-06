---
title: 访问 CDC 设计器控制台 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- accMsDes
ms.assetid: b168c64e-c1b5-42d4-a92a-84de1dd0324e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7f4f6e4df0a514cb29e36bcd1270b2537dc3ba68
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693438"
---
# <a name="access-the-cdc-designer-console"></a><span data-ttu-id="5d0d3-102">访问 CDC 设计器控制台</span><span class="sxs-lookup"><span data-stu-id="5d0d3-102">Access the CDC Designer Console</span></span>
  <span data-ttu-id="5d0d3-103">您可以从安装了 CDC 设计器控制台的计算机访问该控制台。</span><span class="sxs-lookup"><span data-stu-id="5d0d3-103">You can access the CDC Designer Console from the computer where you installed the console.</span></span> <span data-ttu-id="5d0d3-104">有关安装的详细信息，请参阅“安装”。</span><span class="sxs-lookup"><span data-stu-id="5d0d3-104">For more information about installation, see Installation.</span></span>  
  
 <span data-ttu-id="5d0d3-105">在您打开 CDC 设计器控制台时，“连接到 SQL Server”对话框将打开。</span><span class="sxs-lookup"><span data-stu-id="5d0d3-105">When you open the CDC Designer Console, the Connect to SQL Server dialog box opens.</span></span>  
  
 <span data-ttu-id="5d0d3-106">访问该 CDC 设计器的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名必须对 MSXDBCDC 数据库具有 UPDATE 权限。</span><span class="sxs-lookup"><span data-stu-id="5d0d3-106">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login that accesses the CDC Designer must have UPDATE permissions on the MSXDBCDC database.</span></span> <span data-ttu-id="5d0d3-107">此外，该登录名还必须具有 `dbcreator` 固定服务器角色，以便创建新的 Oracle CDC 实例。</span><span class="sxs-lookup"><span data-stu-id="5d0d3-107">In addition, the login must also have the `dbcreator` fixed-server role to create new Oracle CDC Instances.</span></span> <span data-ttu-id="5d0d3-108">建议该登录名还具有对要使用的 CDC 数据库的 SELECT 权限，否则，该用户将无法查看这些数据库的状态。</span><span class="sxs-lookup"><span data-stu-id="5d0d3-108">It is recommended that the login also have SELECT access to the CDC databases being used or the user will not be able to view the state of those databases.</span></span>  
  
 <span data-ttu-id="5d0d3-109">在“连接到 SQL Server”对话框中输入以下信息。</span><span class="sxs-lookup"><span data-stu-id="5d0d3-109">Enter the following information in the Connect to SQL Server dialog box.</span></span>  
  
### <a name="server-name"></a><span data-ttu-id="5d0d3-110">服务器名称</span><span class="sxs-lookup"><span data-stu-id="5d0d3-110">Server Name</span></span>  
 <span data-ttu-id="5d0d3-111">键入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所在的服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="5d0d3-111">Type the name of the server where the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is located.</span></span>  
  
### <a name="authentication"></a><span data-ttu-id="5d0d3-112">身份验证</span><span class="sxs-lookup"><span data-stu-id="5d0d3-112">Authentication</span></span>  
 <span data-ttu-id="5d0d3-113">选择以下方案之一：</span><span class="sxs-lookup"><span data-stu-id="5d0d3-113">Select one of the following:</span></span>  
  
-   <span data-ttu-id="5d0d3-114">**Windows 身份验证**</span><span class="sxs-lookup"><span data-stu-id="5d0d3-114">**Windows Authentication**</span></span>  
  
-   <span data-ttu-id="5d0d3-115">**SQL Server 身份验证**：如果选择此选项，则必须在连接到的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中为用户键入“登录名”  和“密码”  。</span><span class="sxs-lookup"><span data-stu-id="5d0d3-115">**SQL Server Authentication**: If you select this option, you must type the **Login** and **Password** for the user in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] you are connecting to.</span></span>  
  
 <span data-ttu-id="5d0d3-116">该登录名必须具有允许访问 MSXCDCDB 数据库的数据库角色。</span><span class="sxs-lookup"><span data-stu-id="5d0d3-116">The login must have a database role that allows access to the MSXCDCDB database.</span></span> <span data-ttu-id="5d0d3-117">建议该登录名还具有访问要使用的任何其他数据库的权限，否则，该用户将无法查看这些数据库中的数据。</span><span class="sxs-lookup"><span data-stu-id="5d0d3-117">It is recommended that the login also have access to any additional databases being used or the user will not be able to view the data in those databases.</span></span>  
  
### <a name="options"></a><span data-ttu-id="5d0d3-118">选项</span><span class="sxs-lookup"><span data-stu-id="5d0d3-118">Options</span></span>  
 <span data-ttu-id="5d0d3-119">单击箭头可以查看要配置的可用选项。</span><span class="sxs-lookup"><span data-stu-id="5d0d3-119">Click the arrow to view available options to be configured.</span></span> <span data-ttu-id="5d0d3-120">您可以选择保留这些选项不变，使用其默认值。</span><span class="sxs-lookup"><span data-stu-id="5d0d3-120">You can choose to leave these options with their default value.</span></span> <span data-ttu-id="5d0d3-121">可用选项是：</span><span class="sxs-lookup"><span data-stu-id="5d0d3-121">The available options are:</span></span>  
  
 <span data-ttu-id="5d0d3-122">**连接超时值**</span><span class="sxs-lookup"><span data-stu-id="5d0d3-122">**Connection Timeout**</span></span>  
 <span data-ttu-id="5d0d3-123">键入一个时间（秒钟），未超过该时间，Oracle CDC 服务将等待与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的连接，超过该时间后即超时。默认值为 **15**。</span><span class="sxs-lookup"><span data-stu-id="5d0d3-123">Type the time (in seconds) that the CDC Service for Oracle waits for a connection to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before timing out. The default value is **15**.</span></span>  
  
 <span data-ttu-id="5d0d3-124">**执行超时值**</span><span class="sxs-lookup"><span data-stu-id="5d0d3-124">**Execution Timeout**</span></span>  
 <span data-ttu-id="5d0d3-125">键入一个时间（秒钟），未超过该时间，Oracle CDC Windows 服务将等待命令执行，超过该时间后即超时。默认值为 **30**。</span><span class="sxs-lookup"><span data-stu-id="5d0d3-125">Type the time (in seconds) that the Oracle CDC Windows Service waits for a command to execute before timing out. The default value is **30**.</span></span>  
  
 <span data-ttu-id="5d0d3-126">**加密连接**</span><span class="sxs-lookup"><span data-stu-id="5d0d3-126">**Encrypt Connection**</span></span>  
 <span data-ttu-id="5d0d3-127">选择“加密连接”  将使用加密连接进行 Oracle CDC 服务和目标 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例之间的通信。**高级**：单击“高级”  并根据需要在“高级连接属性”对话框中键入任何附加的连接属性。</span><span class="sxs-lookup"><span data-stu-id="5d0d3-127">Select **Encrypt Connection** for communication between the Oracle CDC Service and the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance using an encrypted connection.**Advanced**: Click **Advanced** and type any additional connection properties into the Advanced Connection Properties dialog box, if necessary.</span></span>  
  
 <span data-ttu-id="5d0d3-128">**高级**</span><span class="sxs-lookup"><span data-stu-id="5d0d3-128">**Advanced**</span></span>  
 <span data-ttu-id="5d0d3-129">单击“高级”  并根据需要在“高级连接属性”对话框中键入任何附加的连接属性。</span><span class="sxs-lookup"><span data-stu-id="5d0d3-129">Click **Advanced** and type any additional connection properties into the Advanced Connection Properties dialog box, if necessary.</span></span>  
  
 <span data-ttu-id="5d0d3-130">有关“高级连接属性”对话框的信息，请参阅 [高级连接属性](advanced-connection-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="5d0d3-130">For information about the Advanced Connection Properties dialog box, see [Advanced Connection Properties](advanced-connection-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d0d3-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5d0d3-131">See Also</span></span>  
 [<span data-ttu-id="5d0d3-132">针对 CDC 设计器的 SQL Server 连接所需权限</span><span class="sxs-lookup"><span data-stu-id="5d0d3-132">SQL Server Connection Required Permissions for the CDC Designer</span></span>](sql-server-connection-required-permissions-for-the-cdc-designer.md)  
  
  
