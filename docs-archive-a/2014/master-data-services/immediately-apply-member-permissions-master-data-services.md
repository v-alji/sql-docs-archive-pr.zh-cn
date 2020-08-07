---
title: 立即应用成员权限 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- members [Master Data Services], applying permissions immediately
- permissions [Master Data Services], applying member permissions immediately
ms.assetid: 5b16de66-5c39-49f5-992f-402a9eb319aa
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: e960ad06213b7c5057a6249b72ce225a6abe35e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587873"
---
# <a name="immediately-apply-member-permissions-master-data-services"></a><span data-ttu-id="5a4d9-102">立即应用成员权限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="5a4d9-102">Immediately Apply Member Permissions (Master Data Services)</span></span>
  <span data-ttu-id="5a4d9-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，您可以立即应用成员权限，而不必等待定期应用的成员安全性。</span><span class="sxs-lookup"><span data-stu-id="5a4d9-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], instead of waiting for member security to be applied at regular intervals, you can apply member permissions immediately.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5a4d9-104">必备条件</span><span class="sxs-lookup"><span data-stu-id="5a4d9-104">Prerequisites</span></span>  
 <span data-ttu-id="5a4d9-105">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="5a4d9-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="5a4d9-106">您必须具有在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 数据库中执行 mdm.udpSecurityMemberProcessRebuildModel 存储过程的权限。</span><span class="sxs-lookup"><span data-stu-id="5a4d9-106">You must have permission to execute the mdm.udpSecurityMemberProcessRebuildModel stored procedure in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="5a4d9-107">有关详细信息，请参阅[数据库对象安全性 (Master Data Services)](database-object-security-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="5a4d9-107">For more information, see [Database Object Security &#40;Master Data Services&#41;](database-object-security-master-data-services.md).</span></span>  
  
### <a name="to-immediately-apply-hierarchy-member-permissions"></a><span data-ttu-id="5a4d9-108">立即应用层次结构成员权限</span><span class="sxs-lookup"><span data-stu-id="5a4d9-108">To immediately apply hierarchy member permissions</span></span>  
  
1.  <span data-ttu-id="5a4d9-109">打开 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 并连接到 [!INCLUDE[ssDE](../includes/ssde-md.md)] 数据库的 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="5a4d9-109">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] and connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)] instance for your [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span>  
  
2.  <span data-ttu-id="5a4d9-110">创建新查询。</span><span class="sxs-lookup"><span data-stu-id="5a4d9-110">Create a new query.</span></span>  
  
3.  <span data-ttu-id="5a4d9-111">键入以下文本，用数据库名称替换 database**，用模型名称替换 Model_Name**。</span><span class="sxs-lookup"><span data-stu-id="5a4d9-111">Type the following text, replacing *database* with the name of your database and *Model_Name* with the name of the model.</span></span>  
  
    ```  
    USE [database];  
    GO  
  
    DECLARE @Model_ID INT;  
    SELECT @Model_ID = ID FROM mdm.tblModel WHERE [Name] = N'Model_Name';  
    EXEC [mdm].[udpSecurityMemberProcessRebuildModel] @Model_ID=@Model_ID, @ProcessNow=1;  
    GO  
    ```  
  
4.  <span data-ttu-id="5a4d9-112">运行查询。</span><span class="sxs-lookup"><span data-stu-id="5a4d9-112">Run the query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a4d9-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5a4d9-113">See Also</span></span>  
 <span data-ttu-id="5a4d9-114">[将层次结构成员权限分配 &#40;Master Data Services&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="5a4d9-114">[Assign Hierarchy Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md) </span></span>  
 [<span data-ttu-id="5a4d9-115">层次结构成员权限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="5a4d9-115">Hierarchy Member Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md)  
  
  
