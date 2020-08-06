---
title: 更改系统管理员帐户 (Master Data Services) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- administrators [Master Data Services], changing
ms.assetid: cf30312e-4338-49a7-90f0-6e4f7b431ff8
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 1d13cdc19c70c9e16c92dfd290393739d7e4f5e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690685"
---
# <a name="change-the-system-administrator-account-master-data-services"></a><span data-ttu-id="d9184-102">更改系统管理员帐户 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d9184-102">Change the System Administrator Account (Master Data Services)</span></span>
  <span data-ttu-id="d9184-103">你可以更改指定为系统管理员的用户帐户 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d9184-103">You can change the user account that is designated as the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] system administrator.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="d9184-104">当您完成此过程后，将删除旧系统管理员用户帐户。</span><span class="sxs-lookup"><span data-stu-id="d9184-104">When you complete this procedure, the former system administrator user account is deleted.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d9184-105">先决条件</span><span class="sxs-lookup"><span data-stu-id="d9184-105">Prerequisites</span></span>  
 <span data-ttu-id="d9184-106">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="d9184-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="d9184-107">必须将新管理员的用户名添加到[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]的“用户”列表中。</span><span class="sxs-lookup"><span data-stu-id="d9184-107">You must add the new administrator's user name to the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Users list.</span></span> <span data-ttu-id="d9184-108">有关详细信息，请参阅[Add a User &#40;Master Data Services&#41;](add-a-user-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="d9184-108">For more information, see [Add a User &#40;Master Data Services&#41;](add-a-user-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="d9184-109">您必须有权查看 mdm.tblUser 和在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 数据库中执行 mdm.udpSecurityMemberProcessRebuildModel 存储过程。</span><span class="sxs-lookup"><span data-stu-id="d9184-109">You must have permission to view mdm.tblUser and to execute the mdm.udpSecurityMemberProcessRebuildModel stored procedure in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="d9184-110">有关详细信息，请参阅[数据库对象安全性 (Master Data Services)](../../2014/master-data-services/database-object-security-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="d9184-110">For more information, see [Database Object Security &#40;Master Data Services&#41;](../../2014/master-data-services/database-object-security-master-data-services.md).</span></span>  
  
### <a name="to-change-the-administrator-account"></a><span data-ttu-id="d9184-111">更改管理员帐户</span><span class="sxs-lookup"><span data-stu-id="d9184-111">To change the administrator account</span></span>  
  
1.  <span data-ttu-id="d9184-112">打开 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 并连接到 [!INCLUDE[ssDE](../includes/ssde-md.md)] 数据库的 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="d9184-112">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] and connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)] instance for your [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span>  
  
2.  <span data-ttu-id="d9184-113">在 tblUser 中，找到要成为新管理员的用户，并复制列中的值 `SID` 。</span><span class="sxs-lookup"><span data-stu-id="d9184-113">In mdm.tblUser, find the user that will be the new administrator and copy the value in the `SID` column.</span></span>  
  
3.  <span data-ttu-id="d9184-114">创建新查询。</span><span class="sxs-lookup"><span data-stu-id="d9184-114">Create a new query.</span></span>  
  
4.  <span data-ttu-id="d9184-115">键入以下文本，将*DOMAIN \ user_name*替换为新管理员的用户名，将*SID*替换为在步骤2中复制的值。</span><span class="sxs-lookup"><span data-stu-id="d9184-115">Type the following text, replacing *DOMAIN\user_name* with the new administrator's user name and *SID* with the value you copied in step 2.</span></span>  
  
    ```  
    EXEC [mdm].[udpSecuritySetAdministrator] @UserName='DOMAIN\user_name', @SID = 'SID', @PromoteNonAdmin = 1  
    ```  
  
5.  <span data-ttu-id="d9184-116">运行查询。</span><span class="sxs-lookup"><span data-stu-id="d9184-116">Run the query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9184-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d9184-117">See Also</span></span>  
 [<span data-ttu-id="d9184-118">管理员 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d9184-118">Administrators &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/administrators-master-data-services.md)  
  
  
