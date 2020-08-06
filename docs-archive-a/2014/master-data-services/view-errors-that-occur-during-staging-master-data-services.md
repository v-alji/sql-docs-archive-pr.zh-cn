---
title: 查看临时过程中发生的错误 (Master Data Services) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- staging process [Master Data Services], viewing errors
ms.assetid: 6d2bff84-624b-47fc-a4a5-d9ea01d13412
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 3b39d039b29090f3021c764126ebb782ce25cbfe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87689470"
---
# <a name="view-errors-that-occur-during-the-staging-process-master-data-services"></a><span data-ttu-id="cfecb-102">查看临时过程中出现的错误 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="cfecb-102">View Errors that Occur During the Staging Process (Master Data Services)</span></span>
  <span data-ttu-id="cfecb-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，您可以查看在临时过程中出现的错误。</span><span class="sxs-lookup"><span data-stu-id="cfecb-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], you can view errors that occur during the staging process.</span></span> <span data-ttu-id="cfecb-104">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 数据库中，有两个视图显示错误：</span><span class="sxs-lookup"><span data-stu-id="cfecb-104">In the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database, there are two views that show errors:</span></span>  
  
-   <span data-ttu-id="cfecb-105">stg.viw_name_MemberErrorDetails 用于叶成员或合并成员更新。</span><span class="sxs-lookup"><span data-stu-id="cfecb-105">stg.viw_name_MemberErrorDetails for leaf or consolidated member updates.</span></span>  
  
-   <span data-ttu-id="cfecb-106">stg.viw_name_RelationshipErrorDetails 用于层次结构关系更新。</span><span class="sxs-lookup"><span data-stu-id="cfecb-106">stg.viw_name_RelationshipErrorDetails for hierarchy relationship updates.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="cfecb-107">先决条件</span><span class="sxs-lookup"><span data-stu-id="cfecb-107">Prerequisites</span></span>  
 <span data-ttu-id="cfecb-108">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="cfecb-108">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="cfecb-109">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 数据库中，必须具有对 stg.viw_name_MemberErrorDetails 或 stg.viw_name_RelationshipErrorDetails 视图的 SELECT 权限。</span><span class="sxs-lookup"><span data-stu-id="cfecb-109">In the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database, you must have SELECT permissions to either the stg.viw_name_MemberErrorDetails or stg.viw_name_RelationshipErrorDetails view.</span></span>  
  
-   <span data-ttu-id="cfecb-110">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="cfecb-110">You must be a model administrator.</span></span> <span data-ttu-id="cfecb-111">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="cfecb-111">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-view-staging-errors"></a><span data-ttu-id="cfecb-112">查看临时错误</span><span class="sxs-lookup"><span data-stu-id="cfecb-112">To view staging errors</span></span>  
  
1.  <span data-ttu-id="cfecb-113">打开 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 并连接到 [!INCLUDE[ssDE](../includes/ssde-md.md)] 数据库的 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="cfecb-113">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] and connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)] instance for your [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span>  
  
2.  <span data-ttu-id="cfecb-114">打开新查询。</span><span class="sxs-lookup"><span data-stu-id="cfecb-114">Open a new query.</span></span>  
  
3.  <span data-ttu-id="cfecb-115">键入以下文本，用您的临时表名称（例如 viw_Product_MemberErrorDetails）替换该名称。</span><span class="sxs-lookup"><span data-stu-id="cfecb-115">Type the following text, replacing name with the name of your staging table, for example, viw_Product_MemberErrorDetails.</span></span>  
  
     `SELECT * FROM stg.viw_name_MemberErrorDetails`  
  
4.  <span data-ttu-id="cfecb-116">执行该查询。</span><span class="sxs-lookup"><span data-stu-id="cfecb-116">Excecute the query.</span></span> <span data-ttu-id="cfecb-117">错误详细信息显示在 **ErrorDescription** 字段中。</span><span class="sxs-lookup"><span data-stu-id="cfecb-117">Error details are displayed in the **ErrorDescription** field.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="cfecb-118">后续步骤</span><span class="sxs-lookup"><span data-stu-id="cfecb-118">Next Steps</span></span>  
 <span data-ttu-id="cfecb-119">有关错误消息的详细信息，请参阅[临时过程错误 (Master Data Services)](../../2014/master-data-services/staging-process-errors-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="cfecb-119">For more details on error messages, see [Staging Process Errors &#40;Master Data Services&#41;](../../2014/master-data-services/staging-process-errors-master-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfecb-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cfecb-120">See Also</span></span>  
 <span data-ttu-id="cfecb-121">[数据导入 &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="cfecb-121">[Data Import &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md) </span></span>  
 [<span data-ttu-id="cfecb-122">临时过程故障排除 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="cfecb-122">Troubleshooting the Staging Process (Master Data Services)</span></span>](https://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-the-staging-process-master-data-services.aspx)  
  
  
