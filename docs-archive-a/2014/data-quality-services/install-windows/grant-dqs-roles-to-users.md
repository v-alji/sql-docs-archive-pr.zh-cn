---
title: 授予用户 DQS 角色 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: afb445b5-bdbe-4bfe-844f-344766cdc2b2
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 62ff5eb03fa46279ee1b8a1329c58bd69361ef82
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691876"
---
# <a name="grant-dqs-roles-to-users"></a><span data-ttu-id="9651f-102">将 DQS 角色授予用户</span><span class="sxs-lookup"><span data-stu-id="9651f-102">Grant DQS Roles to Users</span></span>
  <span data-ttu-id="9651f-103">本主题介绍如何基于 Windows 主体创建 SQL 登录名，以及如何授予针对 DQS_MAIN 数据库的 [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) 角色。</span><span class="sxs-lookup"><span data-stu-id="9651f-103">This topic describes how to create SQL logins based on a Windows principal, and grant [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) roles on the DQS_MAIN database.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9651f-104">先决条件</span><span class="sxs-lookup"><span data-stu-id="9651f-104">Prerequisites</span></span>  
  
-   <span data-ttu-id="9651f-105">您必须已通过运行 DQSInstaller.exe 文件完成了 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 安装。</span><span class="sxs-lookup"><span data-stu-id="9651f-105">You must have completed the [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] installation by running the DQSInstaller.exe file.</span></span> <span data-ttu-id="9651f-106">有关详细信息，请参阅 [运行 DQSInstaller.exe 以便完成数据质量服务器安装](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md)。</span><span class="sxs-lookup"><span data-stu-id="9651f-106">For more information, see [Run DQSInstaller.exe to Complete Data Quality Server Installation](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).</span></span>  
  
-   <span data-ttu-id="9651f-107">若要创建 SQL 登录名以及授予他们 DQS 角色，您的 Windows 用户帐户必须是适当固定服务器角色的成员（例如 securityadmin、serveradmin 或 sysadmin）。</span><span class="sxs-lookup"><span data-stu-id="9651f-107">Your Windows user account must be a member of the appropriate fixed server role (such as securityadmin, serveradmin, or sysadmin) to create SQL login, and grant them DQS roles.</span></span>  
  
### <a name="to-create-sql-login-and-grant-dqs-roles"></a><span data-ttu-id="9651f-108">创建 SQL 登录名并授予 DQS 角色</span><span class="sxs-lookup"><span data-stu-id="9651f-108">To create SQL login and grant DQS roles</span></span>  
  
1.  <span data-ttu-id="9651f-109">启动 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9651f-109">Start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="9651f-110">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，展开您的 SQL Server 实例，然后展开 **“安全性”**。</span><span class="sxs-lookup"><span data-stu-id="9651f-110">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand your SQL Server instance, and then expand **Security**.</span></span>  
  
3.  <span data-ttu-id="9651f-111">右键单击“安全性”文件夹，指向“新建”，然后单击“登录名”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9651f-111">Right-click the **Security** folder, point to **New**, and then click **Login**.</span></span>  
  
4.  <span data-ttu-id="9651f-112">在“登录名 - 新建”对话框中，在“登录名”框中指定 Windows 用户的名称，将身份验证类型指定为“Windows 身份验证”，然后单击“搜索”以验证此用户\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9651f-112">In the **Login - New** dialog box, specify the name of a Windows user in the **Login name** box, specify the type of authentication as **Windows authentication**, and click **Search** to validate the user.</span></span>  
  
5.  <span data-ttu-id="9651f-113">在验证该用户后，在左侧窗格中单击 **“用户映射”** 。</span><span class="sxs-lookup"><span data-stu-id="9651f-113">After the user is validated, click the **User Mapping** page in the left pane.</span></span>  
  
6.  <span data-ttu-id="9651f-114">在右侧窗格中，选中 **DQS_MAIN** 数据库的“映射”\*\*\*\* 列下的复选框，然后根据用户所需的访问级别，在“数据库角色成员身份: DQS_MAIN”\*\*\*\* 窗格中选中 **dqs_administrator**、**dqs_kb_editor** 或 **dqs_kb_operator** 复选框。</span><span class="sxs-lookup"><span data-stu-id="9651f-114">In the right pane, select the check box under the **Map** column for the **DQS_MAIN** database, and then select the **dqs_administrator**, **dqs_kb_editor**, or **dqs_kb_operator** check box in the **Database role membership for: DQS_MAIN** pane, depending on the access level needed for the user.</span></span> <span data-ttu-id="9651f-115">有关这三个 DQS 角色的信息，请参阅 [DQS 安全](../dqs-security.md)。</span><span class="sxs-lookup"><span data-stu-id="9651f-115">For information about the three DQS roles, see [DQS Security](../dqs-security.md).</span></span>  
  
7.  <span data-ttu-id="9651f-116">在“登录名 - 新建”对话框中，单击“确定”以便应用更改\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9651f-116">In the **Login - New** dialog box, click **OK** to apply the changes.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9651f-117">如果你向某一用户授予 **dqs_administrator** 角色，应用更改，然后重新选中用户权限，则其他两个 DQS 角色复选框（**dq_kb_editor** 和 **dqs_kb_operator**）也将被选中。</span><span class="sxs-lookup"><span data-stu-id="9651f-117">If you grant the **dqs_administrator** role to a user, apply the changes, and then recheck the user permissions, the other two DQS roles check boxes (**dq_kb_editor** and **dqs_kb_operator**) are also selected.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="9651f-118">后续步骤</span><span class="sxs-lookup"><span data-stu-id="9651f-118">Next Steps</span></span>  
 <span data-ttu-id="9651f-119">尝试通过使用您刚刚为其创建了 SQL 登录名并授予了 DQS 角色的 Windows 用户帐户登录到 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="9651f-119">Try logging on to [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] by using the Windows user account for which you just created a SQL login, and granted a DQS role.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9651f-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9651f-120">See Also</span></span>  
 <span data-ttu-id="9651f-121">[安装 Data Quality Services](install-data-quality-services.md) </span><span class="sxs-lookup"><span data-stu-id="9651f-121">[Install Data Quality Services](install-data-quality-services.md) </span></span>  
 [<span data-ttu-id="9651f-122">创建登录名</span><span class="sxs-lookup"><span data-stu-id="9651f-122">Create a Login</span></span>](../../relational-databases/security/authentication-access/create-a-login.md)  
  
  
