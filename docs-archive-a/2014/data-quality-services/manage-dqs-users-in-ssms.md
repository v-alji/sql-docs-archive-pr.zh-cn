---
title: 在 SSMS 中管理 DQS 用户 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 955af01d-00da-4c51-9311-f3848749df54
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: bf8789abb59d168f39562f6486bb5c54bfc0fc50
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590373"
---
# <a name="manage-dqs-users-in-ssms"></a><span data-ttu-id="ea1e2-102">在 SSMS 中管理 DQS 用户</span><span class="sxs-lookup"><span data-stu-id="ea1e2-102">Manage DQS Users in SSMS</span></span>
  <span data-ttu-id="ea1e2-103">本主题介绍如何使用 SQL Server Management Studio 在 SQL Server 实例中创建其他用户，并向这些用户授予针对 DQS_MAIN 数据库的适当 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 角色。</span><span class="sxs-lookup"><span data-stu-id="ea1e2-103">This topic describes how to create additional users in the SQL Server instance using SQL Server Management Studio, and grant them appropriate [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) roles on the DQS_MAIN database.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ea1e2-104">开始之前</span><span class="sxs-lookup"><span data-stu-id="ea1e2-104">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ea1e2-105">Security</span><span class="sxs-lookup"><span data-stu-id="ea1e2-105">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ea1e2-106">权限</span><span class="sxs-lookup"><span data-stu-id="ea1e2-106">Permissions</span></span>  
 <span data-ttu-id="ea1e2-107">若要创建 SQL 登录名以及授予适当的 DQS 角色，您的 Windows 用户帐户必须是相应固定服务器角色（例如 securityadmin、serveradmin 或 sysadmin）的成员。</span><span class="sxs-lookup"><span data-stu-id="ea1e2-107">Your Windows user account must be a member of the appropriate fixed server role (such as securityadmin, serveradmin, or sysadmin) to create SQL login, and grant appropriate DQS roles.</span></span>  
  
##  <a name="create-a-sql-login-and-grant-dqs-role"></a><a name="GrantRoles"></a><span data-ttu-id="ea1e2-108">创建 SQL 登录名并授予 DQS 角色</span><span class="sxs-lookup"><span data-stu-id="ea1e2-108">Create a SQL Login and Grant DQS Role</span></span>  
  
1.  <span data-ttu-id="ea1e2-109">启动 Microsoft SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="ea1e2-109">Start Microsoft SQL Server Management Studio.</span></span>  
  
2.  <span data-ttu-id="ea1e2-110">在 Microsoft SQL Server Management Studio 中，展开您的 SQL Server 实例，然后展开 **“安全性”**。</span><span class="sxs-lookup"><span data-stu-id="ea1e2-110">In Microsoft SQL Server Management Studio, expand your SQL Server instance, and then expand **Security**.</span></span>  
  
3.  <span data-ttu-id="ea1e2-111">右键单击“安全性”文件夹，指向“新建”，然后单击“登录名”\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ea1e2-111">Right-click the **Security** folder, point to **New**, and then click **Login**.</span></span>  
  
4.  <span data-ttu-id="ea1e2-112">在“登录名 - 新建”对话框中，在“登录名”框中指定 Windows 用户的名称，将身份验证类型指定为“Windows 身份验证”，然后单击“搜索”以验证此用户\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ea1e2-112">In the **Login - New** dialog box, specify the name of a Windows user in the **Login name** box, specify the type of authentication as **Windows authentication**, and click **Search** to validate the user.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ea1e2-113">DQS 只支持 Windows 身份验证；不支持 SQL Server 身份验证。</span><span class="sxs-lookup"><span data-stu-id="ea1e2-113">DQS only supports Windows authentication; SQL Server authentication is not supported.</span></span>  
  
5.  <span data-ttu-id="ea1e2-114">在验证该用户后，在左侧窗格中单击 **“用户映射”** 。</span><span class="sxs-lookup"><span data-stu-id="ea1e2-114">After the user is validated, click the **User Mapping** page in the left pane.</span></span>  
  
6.  <span data-ttu-id="ea1e2-115">在右侧窗格中，选中 **DQS_MAIN** 数据库的“映射”\*\*\*\* 列下的复选框，然后根据用户所需的访问级别，在“数据库角色成员身份: DQS_MAIN”\*\*\*\* 窗格中选中 **dqs_administrator**、**dqs_kb_editor** 或 **dqs_kb_operator** 复选框。</span><span class="sxs-lookup"><span data-stu-id="ea1e2-115">In the right pane, select the check box under the **Map** column for the **DQS_MAIN** database, and then select the **dqs_administrator**, **dqs_kb_editor**, or **dqs_kb_operator** check box in the **Database role membership for: DQS_MAIN** pane, depending on the access level needed for the user.</span></span>  
  
7.  <span data-ttu-id="ea1e2-116">在“登录名 - 新建”对话框中，单击“确定”以便应用更改\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ea1e2-116">In the **Login - New** dialog box, click **OK** to apply the changes.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ea1e2-117">如果你向某一用户授予 **dqs_administrator** 角色，应用更改，然后重新选中用户权限，则其他两个 DQS 角色复选框（**dq_kb_editor** 和 **dqs_kb_operator**）也将被选中。</span><span class="sxs-lookup"><span data-stu-id="ea1e2-117">If you grant the **dqs_administrator** role to a user, apply the changes, and then recheck the user permissions, the other two DQS roles check boxes (**dq_kb_editor** and **dqs_kb_operator**) are also selected.</span></span>  
  
  
