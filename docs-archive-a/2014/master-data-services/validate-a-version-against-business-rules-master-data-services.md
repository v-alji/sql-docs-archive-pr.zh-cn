---
title: 针对业务规则验证版本 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- validating versions [Master Data Services]
- validating versions [Master Data Services], about validating versions
- versions [Master Data Services], validating
- business rules [Master Data Services], applying to all members
ms.assetid: 5aee7901-6d05-41d4-8bbb-c6f26791d1df
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 085fa071ca511c9d838c140547419bf87fb857bb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581352"
---
# <a name="validate-a-version-against-business-rules-master-data-services"></a><span data-ttu-id="d9dbc-102">针对业务规则验证版本 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d9dbc-102">Validate a Version against Business Rules (Master Data Services)</span></span>
  <span data-ttu-id="d9dbc-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，对某一版本进行验证以便将业务规则应用于该模型版本中的所有成员。</span><span class="sxs-lookup"><span data-stu-id="d9dbc-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], validate a version to apply business rules to all members in the model version.</span></span>  
  
 <span data-ttu-id="d9dbc-104">此过程说明如何使用 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web 应用程序来验证数据。</span><span class="sxs-lookup"><span data-stu-id="d9dbc-104">This procedure explains how to use the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application to validate data.</span></span> <span data-ttu-id="d9dbc-105">如果您在 MDS 数据库中具有权限，可以改用存储过程。</span><span class="sxs-lookup"><span data-stu-id="d9dbc-105">If you have permission in the MDS database, you can use a stored procedure instead.</span></span> <span data-ttu-id="d9dbc-106">有关详细信息，请参阅 [验证存储过程 (Master Data Services)](validation-stored-procedure-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="d9dbc-106">For more information, see [Validation Stored Procedure &#40;Master Data Services&#41;](validation-stored-procedure-master-data-services.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d9dbc-107">所有成员必须通过验证后，才能提交版本。</span><span class="sxs-lookup"><span data-stu-id="d9dbc-107">All members must pass validation before a version can be committed.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d9dbc-108">先决条件</span><span class="sxs-lookup"><span data-stu-id="d9dbc-108">Prerequisites</span></span>  
 <span data-ttu-id="d9dbc-109">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="d9dbc-109">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="d9dbc-110">您必须有权访问 **“版本管理”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="d9dbc-110">You must have permission to access the **Version Management** functional area.</span></span>  
  
-   <span data-ttu-id="d9dbc-111">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="d9dbc-111">You must be a model administrator.</span></span> <span data-ttu-id="d9dbc-112">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="d9dbc-112">For more information, see [Administrators &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="d9dbc-113">版本的状态必须是 **“打开”** 或 **“已锁定”**。</span><span class="sxs-lookup"><span data-stu-id="d9dbc-113">The version's status must be **Open** or **Locked**.</span></span>  
  
-   <span data-ttu-id="d9dbc-114">在 **“验证版本”** 页上，存在的成员必须具有并非 **“验证已成功”** 的其他状态。</span><span class="sxs-lookup"><span data-stu-id="d9dbc-114">On the **Validate Versions** page, members must exist with a status other than **Validation succeeded**.</span></span>  
  
### <a name="to-validate-a-version"></a><span data-ttu-id="d9dbc-115">验证版本</span><span class="sxs-lookup"><span data-stu-id="d9dbc-115">To validate a version</span></span>  
  
1.  <span data-ttu-id="d9dbc-116">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“版本管理”**。</span><span class="sxs-lookup"><span data-stu-id="d9dbc-116">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **Version Management**.</span></span>  
  
2.  <span data-ttu-id="d9dbc-117">在 **“管理版本”** 页上，从菜单栏中，单击 **“验证版本”**。</span><span class="sxs-lookup"><span data-stu-id="d9dbc-117">On the **Manage Versions** page, from the menu bar, click **Validate Version**.</span></span>  
  
3.  <span data-ttu-id="d9dbc-118">在 **“验证版本”** 页上，选择要验证的模型和版本。</span><span class="sxs-lookup"><span data-stu-id="d9dbc-118">On the **Validate Versions** page, select the model and version you want to validate.</span></span>  
  
4.  <span data-ttu-id="d9dbc-119">单击 **“验证”** 。</span><span class="sxs-lookup"><span data-stu-id="d9dbc-119">Click **Validate**.</span></span>  
  
5.  <span data-ttu-id="d9dbc-120">在确认对话框中，单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="d9dbc-120">In the confirmation dialog box, click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d9dbc-121">一旦不再显示进度指示器，则表明该版本已完成验证。</span><span class="sxs-lookup"><span data-stu-id="d9dbc-121">When the progress indicator is no longer displayed, the version has finished validation.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="d9dbc-122">后续步骤</span><span class="sxs-lookup"><span data-stu-id="d9dbc-122">Next Steps</span></span>  
  
-   [<span data-ttu-id="d9dbc-123">锁定版本 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d9dbc-123">Lock a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/lock-a-version-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="d9dbc-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d9dbc-124">See Also</span></span>  
 <span data-ttu-id="d9dbc-125">[验证状态 &#40;Master Data Services&#41;](../../2014/master-data-services/validation-statuses-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d9dbc-125">[Validation Statuses &#40;Master Data Services&#41;](../../2014/master-data-services/validation-statuses-master-data-services.md) </span></span>  
 <span data-ttu-id="d9dbc-126">[验证存储过程 &#40;Master Data Services&#41;](validation-stored-procedure-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d9dbc-126">[Validation Stored Procedure &#40;Master Data Services&#41;](validation-stored-procedure-master-data-services.md) </span></span>  
 <span data-ttu-id="d9dbc-127">[版本 &#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d9dbc-127">[Versions &#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md) </span></span>  
 <span data-ttu-id="d9dbc-128">[业务规则 &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d9dbc-128">[Business Rules &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md) </span></span>  
 [<span data-ttu-id="d9dbc-129">针对业务规则验证特定成员 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d9dbc-129">Validate Specific Members against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
  
