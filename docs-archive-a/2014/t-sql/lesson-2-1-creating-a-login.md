---
title: 创建登录名 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- creating a login
ms.assetid: a2512310-bdb6-41dc-858a-e866b2b58afc
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 400a57693fbea10270a51f5735a19b9639112ce9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692064"
---
# <a name="creating-a-login"></a><span data-ttu-id="d5c41-102">创建登录名</span><span class="sxs-lookup"><span data-stu-id="d5c41-102">Creating a Login</span></span>
  <span data-ttu-id="d5c41-103">若要访问 [!INCLUDE[ssDE](../includes/ssde-md.md)]，用户需要有登录名。</span><span class="sxs-lookup"><span data-stu-id="d5c41-103">To access the [!INCLUDE[ssDE](../includes/ssde-md.md)], users require a login.</span></span> <span data-ttu-id="d5c41-104">登录名可以将用户身份表示为 Windows 帐户或 Windows 组成员，登录名也可以是仅存在于 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 中的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]登录名。</span><span class="sxs-lookup"><span data-stu-id="d5c41-104">The login can represent the user's identity as a Windows account or as a member of a Windows group, or the login can be a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] login that exists only in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d5c41-105">应该尽可能使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="d5c41-105">Whenever possible you should use Windows Authentication.</span></span>  
  
 <span data-ttu-id="d5c41-106">默认情况下，计算机上的管理员具有对 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的完全访问权限。</span><span class="sxs-lookup"><span data-stu-id="d5c41-106">By default, administrators on your computer have full access to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d5c41-107">在本课中，我们需要一个具有更少特权的用户；因此，您将在计算机上创建一个新的本地 Windows 身份验证帐户。</span><span class="sxs-lookup"><span data-stu-id="d5c41-107">For this lesson, we want to have a less privileged user; therefore, you will create a new local Windows Authentication account on your computer.</span></span> <span data-ttu-id="d5c41-108">为此，您必须是计算机上的管理员。</span><span class="sxs-lookup"><span data-stu-id="d5c41-108">To do this, you must be an administrator on your computer.</span></span> <span data-ttu-id="d5c41-109">然后您将授予该新用户访问 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的权限。</span><span class="sxs-lookup"><span data-stu-id="d5c41-109">Then you will grant that new user access to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
### <a name="to-create-a-new-windows-account"></a><span data-ttu-id="d5c41-110">创建新的 Windows 帐户</span><span class="sxs-lookup"><span data-stu-id="d5c41-110">To create a new Windows account</span></span>  
  
1.  <span data-ttu-id="d5c41-111">单击 "**开始**"，再单击 "**运行**"，在 "**打开**" 框中键入 `%SystemRoot%\system32\compmgmt.msc /s` ，然后单击 **"确定"** 以打开 "计算机管理" 程序。</span><span class="sxs-lookup"><span data-stu-id="d5c41-111">Click **Start**, click **Run**, in the **Open** box, type `%SystemRoot%\system32\compmgmt.msc /s`, and then click **OK** to open the Computer Management program.</span></span>  
  
2.  <span data-ttu-id="d5c41-112">在“系统工具”下，展开“本地用户和组”，右键单击“用户”，再单击“新建用户”。\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="d5c41-112">Under **System Tools**, expand **Local Users and Groups**, right-click **Users**, and then click **New User**.</span></span>  
  
3.  <span data-ttu-id="d5c41-113">在“用户名”框中，键入“Mary”。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="d5c41-113">In the **User name** box type **Mary**.</span></span>  
  
4.  <span data-ttu-id="d5c41-114">在“密码”和“确认密码”框中，键入强密码，再单击“创建”创建新的本地 Windows 用户。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="d5c41-114">In the **Password** and **Confirm password** box, type a strong password, and then click **Create** to create a new local Windows user.</span></span>  
  
### <a name="to-create-a-login"></a><span data-ttu-id="d5c41-115">创建登录名</span><span class="sxs-lookup"><span data-stu-id="d5c41-115">To create a login</span></span>  
  
1.  <span data-ttu-id="d5c41-116">在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]的查询编辑器窗口中，键入并执行以下代码（将 `computer_name` 替换为您计算机的名称）。</span><span class="sxs-lookup"><span data-stu-id="d5c41-116">In a Query Editor window of [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], type and execute the following code replacing `computer_name` with the name of your computer.</span></span> <span data-ttu-id="d5c41-117">`FROM WINDOWS` 表示 Windows 对用户进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="d5c41-117">`FROM WINDOWS` indicates that Windows will authenticate the user.</span></span> <span data-ttu-id="d5c41-118">除非连接字符串指示其他数据库，否则可选的 `DEFAULT_DATABASE` 参数将 `Mary` 连接到 `TestData` 数据库。</span><span class="sxs-lookup"><span data-stu-id="d5c41-118">The optional `DEFAULT_DATABASE` argument connects `Mary` to the `TestData` database, unless her connection string indicates another database.</span></span> <span data-ttu-id="d5c41-119">此语句引入了分号作为 [!INCLUDE[tsql](../includes/tsql-md.md)] 语句的可选结束符。</span><span class="sxs-lookup"><span data-stu-id="d5c41-119">This statement introduces the semicolon as an optional termination for a [!INCLUDE[tsql](../includes/tsql-md.md)] statement.</span></span>  
  
    ```  
    CREATE LOGIN [computer_name\Mary]  
        FROM WINDOWS  
        WITH DEFAULT_DATABASE = [TestData];  
    GO  
    ```  
  
     <span data-ttu-id="d5c41-120">这将授权通过计算机的身份验证的用户名 `Mary`访问此 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="d5c41-120">This authorizes a user name `Mary`, authenticated by your computer, to access this instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d5c41-121">如果计算机上存在多个 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例，则必须在 `Mary` 必须访问的每个实例上创建登录名。</span><span class="sxs-lookup"><span data-stu-id="d5c41-121">If there is more than one instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on the computer, you must create the login on each instance that `Mary` must access.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d5c41-122">因为 `Mary` 不是域帐户，所以此用户名只能在此计算机上进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="d5c41-122">Because `Mary` is not a domain account, this user name can only be authenticated on this computer.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="d5c41-123">课程中的下一个任务</span><span class="sxs-lookup"><span data-stu-id="d5c41-123">Next Task in Lesson</span></span>  
 [<span data-ttu-id="d5c41-124">授予访问数据库的权限</span><span class="sxs-lookup"><span data-stu-id="d5c41-124">Granting Access to a Database</span></span>](lesson-2-2-granting-access-to-a-database.md)  
  
## <a name="see-also"></a><span data-ttu-id="d5c41-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d5c41-125">See Also</span></span>  
 <span data-ttu-id="d5c41-126">[CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d5c41-126">[CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql) </span></span>  
 [<span data-ttu-id="d5c41-127">选择身份验证模式</span><span class="sxs-lookup"><span data-stu-id="d5c41-127">Choose an Authentication Mode</span></span>](../relational-databases/security/choose-an-authentication-mode.md)  
  
  
