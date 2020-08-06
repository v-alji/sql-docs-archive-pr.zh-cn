---
title: MSSQLSERVER_17832 | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17828 (Database Engine error)
- maxtokensize
- 17832 (Database Engine error)
- login packet (bad)
ms.assetid: bd56ffe4-0855-4ada-8aca-251fbc6ff2ce
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: dba214e2cce04ff2583e12ae7cee9b54373390a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687944"
---
# <a name="mssqlserver_17832"></a><span data-ttu-id="36489-102">MSSQLSERVER_17832</span><span class="sxs-lookup"><span data-stu-id="36489-102">MSSQLSERVER_17832</span></span>
    
## <a name="details"></a><span data-ttu-id="36489-103">详细信息</span><span class="sxs-lookup"><span data-stu-id="36489-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="36489-104">产品名称</span><span class="sxs-lookup"><span data-stu-id="36489-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="36489-105">事件 ID</span><span class="sxs-lookup"><span data-stu-id="36489-105">Event ID</span></span>|<span data-ttu-id="36489-106">17832</span><span class="sxs-lookup"><span data-stu-id="36489-106">17832</span></span>|  
|<span data-ttu-id="36489-107">事件源</span><span class="sxs-lookup"><span data-stu-id="36489-107">Event Source</span></span>|<span data-ttu-id="36489-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="36489-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="36489-109">组件</span><span class="sxs-lookup"><span data-stu-id="36489-109">Component</span></span>|<span data-ttu-id="36489-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="36489-110">SQLEngine</span></span>|  
|<span data-ttu-id="36489-111">符号名称</span><span class="sxs-lookup"><span data-stu-id="36489-111">Symbolic Name</span></span>|<span data-ttu-id="36489-112">SRV_BAD_LOGIN_PKT</span><span class="sxs-lookup"><span data-stu-id="36489-112">SRV_BAD_LOGIN_PKT</span></span>|  
|<span data-ttu-id="36489-113">消息正文</span><span class="sxs-lookup"><span data-stu-id="36489-113">Message Text</span></span>|<span data-ttu-id="36489-114">用于打开该连接的登录数据包的结构无效；该连接已关闭。</span><span class="sxs-lookup"><span data-stu-id="36489-114">The login packet used to open the connection is structurally invalid; the connection has been closed.</span></span> <span data-ttu-id="36489-115">请与客户端库的供应商联系。%.\*ls</span><span class="sxs-lookup"><span data-stu-id="36489-115">Please contact the vendor of the client library.%.\*ls</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="36489-116">说明</span><span class="sxs-lookup"><span data-stu-id="36489-116">Explanation</span></span>  
 <span data-ttu-id="36489-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 计算机无法处理客户端登录数据包。</span><span class="sxs-lookup"><span data-stu-id="36489-117">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] computer was unable to process the client login packet.</span></span> <span data-ttu-id="36489-118">这可能是由于未正确创建数据包或数据包在传输过程中受损造成的。</span><span class="sxs-lookup"><span data-stu-id="36489-118">This may be because the packet was created improperly or because the packet was damaged during transmission.</span></span> <span data-ttu-id="36489-119">也可能是由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 计算机的配置引起的。</span><span class="sxs-lookup"><span data-stu-id="36489-119">It can also be caused by the configuration of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] computer.</span></span> <span data-ttu-id="36489-120">所列出的 IP 地址为客户端计算机的地址。</span><span class="sxs-lookup"><span data-stu-id="36489-120">The IP address listed is the address of the client computer.</span></span>  
  
### <a name="more-information"></a><span data-ttu-id="36489-121">更多信息</span><span class="sxs-lookup"><span data-stu-id="36489-121">More Information</span></span>  
 <span data-ttu-id="36489-122">当在 Kerberos 环境中使用 Windows 身份验证时，客户端会接收包含特权属性证书 (PAC) 的 Kerberos 票证。</span><span class="sxs-lookup"><span data-stu-id="36489-122">When using Windows Authentication in a Kerberos environment, a client receives a Kerberos ticket that contains a Privilege Attribute Certificate (PAC).</span></span> <span data-ttu-id="36489-123">PAC 包含各种类型的身份验证数据，包括用户所在的组、用户拥有的权限以及对用户应用的策略。</span><span class="sxs-lookup"><span data-stu-id="36489-123">The PAC contains various types of authorization data including groups that the user is a member of, rights the user has, and what policies apply to the user.</span></span> <span data-ttu-id="36489-124">当客户端接收 Kerberos 票证时，包含在 PAC 中的信息将用于生成用户的访问标记。</span><span class="sxs-lookup"><span data-stu-id="36489-124">When the client receives the Kerberos ticket, the information contained in the PAC is used to generate the user's access token.</span></span> <span data-ttu-id="36489-125">客户端会将该标记作为登录数据包的组成部分提交给 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 计算机。</span><span class="sxs-lookup"><span data-stu-id="36489-125">The client presents the token to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] computer as part of the login packet.</span></span>  
  
 <span data-ttu-id="36489-126">如果未正确创建该标记或该标记在传输过程中受损，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 无法提供有关此问题的其他信息。</span><span class="sxs-lookup"><span data-stu-id="36489-126">If the token was improperly created or damaged during transmission, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot offer additional information about the problem.</span></span>  
  
 <span data-ttu-id="36489-127">如果用户是多个组的成员或具有多个策略，则该标记的长度可能会比正常标记大一些以全部列出这些信息。</span><span class="sxs-lookup"><span data-stu-id="36489-127">When the user is a member of many groups or has many policies, the token may grow larger than normal to list them all.</span></span> <span data-ttu-id="36489-128">如果该标记的长度大于服务器计算机的 **MaxTokenSize** 值，则客户端将无法连接并显示常规网络错误 (GNE)，且会出现错误 17832。</span><span class="sxs-lookup"><span data-stu-id="36489-128">If the token grows larger than the **MaxTokenSize** value of the server computer, the client fails to connect with a General Network Error (GNE) and error 17832 can occur.</span></span> <span data-ttu-id="36489-129">此问题可能只会影响某些用户，即拥有多个组的成员身份或具有多个策略的用户。</span><span class="sxs-lookup"><span data-stu-id="36489-129">This problem may affect only some users: users with many groups or policies.</span></span> <span data-ttu-id="36489-130">当问题在于服务器计算机的 **MaxTokenSize** 值时，在出现 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志中的错误 17832 的同时还会出现状态为 9 的错误。</span><span class="sxs-lookup"><span data-stu-id="36489-130">When the problem is the **MaxTokenSize** value of the server computer, error 17832 in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log will be accompanied by an error with state 9.</span></span> <span data-ttu-id="36489-131">有关 Kerberos 和 **MaxTokenSize** 的其他详细信息，请参阅 [KB327825](https://support.microsoft.com/kb/327825)。</span><span class="sxs-lookup"><span data-stu-id="36489-131">For additional details about the Kerberos and **MaxTokenSize**, see [KB327825](https://support.microsoft.com/kb/327825).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="36489-132">用户操作</span><span class="sxs-lookup"><span data-stu-id="36489-132">User Action</span></span>  
 <span data-ttu-id="36489-133">若要解决此问题，请将服务器计算机的 **MaxTokenSize** 值增大到足以包含单位中任一用户的最长标记的大小。</span><span class="sxs-lookup"><span data-stu-id="36489-133">To resolve this problem, increase the **MaxTokenSize** value of the server computer, to a size large enough to contain the largest token of any user in your organization.</span></span> <span data-ttu-id="36489-134">若要研究适合于您单位的正确标记长度，请考虑使用 **Tokensz** 应用程序。</span><span class="sxs-lookup"><span data-stu-id="36489-134">To research the correct token size for your organization, consider using the **Tokensz** application.</span></span>   
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry-md.md)]  
  
 <span data-ttu-id="36489-135">**更改服务器计算机上的 MaxTokenSize**</span><span class="sxs-lookup"><span data-stu-id="36489-135">**To change the MaxTokenSize  on the server computer**</span></span>  
  
1.  <span data-ttu-id="36489-136">在 **“开始”** 菜单上，单击 **“运行”** 。</span><span class="sxs-lookup"><span data-stu-id="36489-136">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="36489-137">键入 `regedit` ，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="36489-137">Type `regedit`, and then click **OK**.</span></span> <span data-ttu-id="36489-138">（如果此时出现“用户帐户控制”对话框，请单击“继续”。） </span><span class="sxs-lookup"><span data-stu-id="36489-138">(If the **User Account Control** dialog box appears, click **Continue**.)</span></span>  
  
3.  <span data-ttu-id="36489-139">导航到 **HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Lsa\Kerberos\Parameters**。</span><span class="sxs-lookup"><span data-stu-id="36489-139">Navigate to **HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Lsa\Kerberos\Parameters**.</span></span>  
  
4.  <span data-ttu-id="36489-140">如果 **MaxTokenSize** 参数不存在，请右键单击“参数”，指向“新建”，然后单击“DWORD (32 位)”值。  </span><span class="sxs-lookup"><span data-stu-id="36489-140">If the **MaxTokenSize** parameter is not present, right-click **Parameters**, point to **New**, and then click **DWORD (32-bit)** Value.</span></span> <span data-ttu-id="36489-141">将注册表项命名为 **MaxTokenSize**。</span><span class="sxs-lookup"><span data-stu-id="36489-141">Name the registry entry **MaxTokenSize**.</span></span>  
  
5.  <span data-ttu-id="36489-142">右键单击 **MaxTokenSize**，然后单击“修改”。</span><span class="sxs-lookup"><span data-stu-id="36489-142">Right-click **MaxTokenSize**, and then click **Modify**.</span></span>  
  
6.  <span data-ttu-id="36489-143">在“数值数据”框中键入所需的 **MaxTokenSize** 值。</span><span class="sxs-lookup"><span data-stu-id="36489-143">In the **Value data** box type the desired **MaxTokenSize** value.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="36489-144">建议使用的最大标记长度为十六进制值 ffff（十进制值 65535）。</span><span class="sxs-lookup"><span data-stu-id="36489-144">Hexadecimal value ffff (decimal value 65535) is the maximum recommended token size.</span></span> <span data-ttu-id="36489-145">提供此值后很可能会解决问题，但可能会对计算机的性能产生负面影响。</span><span class="sxs-lookup"><span data-stu-id="36489-145">Providing this value would probably solve the problem, but could have negative computer-wide effects with regard to performance.</span></span> <span data-ttu-id="36489-146">建议您建立可包含单位中任一用户最长标记的最小 **MaxTokenSize** 值并输入该值。</span><span class="sxs-lookup"><span data-stu-id="36489-146">We recommend that you establish the minimum **MaxTokenSize** value that allows for the largest token of any user in your organization and enter that value.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="36489-147">关闭**注册表编辑器**。</span><span class="sxs-lookup"><span data-stu-id="36489-147">Close **Registry Editor**.</span></span>  
  
9. <span data-ttu-id="36489-148">重新启动计算机。</span><span class="sxs-lookup"><span data-stu-id="36489-148">Restart the computer.</span></span>  
  
  
