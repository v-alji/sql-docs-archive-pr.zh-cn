---
title: 验证数据 (MDS Add-in for Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 71eda98f-01a4-4fff-8246-be3133782523
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f8e97ff6481996b2e16436e1f78478bd234fe6ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586778"
---
# <a name="validating-data-mds-add-in-for-excel"></a><span data-ttu-id="eb81c-102">验证数据（用于 Excel 的 MDS 外接程序）</span><span class="sxs-lookup"><span data-stu-id="eb81c-102">Validating Data (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="eb81c-103">在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，当你发布数据时，将进行两种类型的验证：</span><span class="sxs-lookup"><span data-stu-id="eb81c-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], when you publish data, two types of validation take place:</span></span>  
  
-   <span data-ttu-id="eb81c-104">任何已定义的业务规则将应用于数据。</span><span class="sxs-lookup"><span data-stu-id="eb81c-104">Any defined business rules are applied to the data.</span></span>  
  
-   <span data-ttu-id="eb81c-105">根据允许的属性值（例如，字符数或数据类型）对数据进行检查。</span><span class="sxs-lookup"><span data-stu-id="eb81c-105">Data is checked against allowed attribute values (for example, number of characters or type of data).</span></span>  
  
 <span data-ttu-id="eb81c-106">在每种情况下，有效数据都发布到 MDS 存储库中。</span><span class="sxs-lookup"><span data-stu-id="eb81c-106">In each case, valid data is published to the MDS repository.</span></span> <span data-ttu-id="eb81c-107">无效数据将被突出显示，并且错误的详细信息可能会显示在状态列中。</span><span class="sxs-lookup"><span data-stu-id="eb81c-107">Data that is not valid is highlighted, and details of the error can be shown in status columns.</span></span>  
  
## <a name="when-validation-occurs"></a><span data-ttu-id="eb81c-108">在发生验证时</span><span class="sxs-lookup"><span data-stu-id="eb81c-108">When Validation Occurs</span></span>  
 <span data-ttu-id="eb81c-109">在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，在发布新数据或更改的数据时，或者在手动应用业务规则时，将发生验证。</span><span class="sxs-lookup"><span data-stu-id="eb81c-109">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], validation occurs when you publish new or changed data, or when you manually apply business rules.</span></span>  
  
 <span data-ttu-id="eb81c-110">在业务规则失败时，数据仍发布到 MDS 存储库中。</span><span class="sxs-lookup"><span data-stu-id="eb81c-110">When business rules fail, the data is still published to the MDS repository.</span></span> <span data-ttu-id="eb81c-111">在输入验证失败时，数据将不会发布到该存储库。</span><span class="sxs-lookup"><span data-stu-id="eb81c-111">When input validation fails, the data is not published to the repository.</span></span>  
  
## <a name="validation-statuses"></a><span data-ttu-id="eb81c-112">验证状态</span><span class="sxs-lookup"><span data-stu-id="eb81c-112">Validation Statuses</span></span>  
 <span data-ttu-id="eb81c-113">在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，以下验证状态是可能的。</span><span class="sxs-lookup"><span data-stu-id="eb81c-113">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], the following validation statuses are possible.</span></span>  
  
|<span data-ttu-id="eb81c-114">状态</span><span class="sxs-lookup"><span data-stu-id="eb81c-114">Status</span></span>|<span data-ttu-id="eb81c-115">说明</span><span class="sxs-lookup"><span data-stu-id="eb81c-115">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="eb81c-116">错误</span><span class="sxs-lookup"><span data-stu-id="eb81c-116">Error</span></span>|<span data-ttu-id="eb81c-117">行中的一个或多个值未通过针对 MDS 管理员定义的业务规则的验证。</span><span class="sxs-lookup"><span data-stu-id="eb81c-117">One or more values in the row failed validation against business rules defined by an MDS administrator.</span></span>|  
|<span data-ttu-id="eb81c-118">未验证</span><span class="sxs-lookup"><span data-stu-id="eb81c-118">Not Validated</span></span>|<span data-ttu-id="eb81c-119">行中的值尚未根据业务规则进行验证。</span><span class="sxs-lookup"><span data-stu-id="eb81c-119">Values in the row have not yet been validated against business rules.</span></span>|  
|<span data-ttu-id="eb81c-120">Success</span><span class="sxs-lookup"><span data-stu-id="eb81c-120">Success</span></span>|<span data-ttu-id="eb81c-121">行中的所有值都已根据业务规则通过了验证。</span><span class="sxs-lookup"><span data-stu-id="eb81c-121">All values in the row have passed validation against business rules.</span></span>|  
  
## <a name="input-statuses"></a><span data-ttu-id="eb81c-122">输入状态</span><span class="sxs-lookup"><span data-stu-id="eb81c-122">Input Statuses</span></span>  
 <span data-ttu-id="eb81c-123">在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，以下输入状态是可能的</span><span class="sxs-lookup"><span data-stu-id="eb81c-123">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], the following input statuses are possible</span></span>  
  
|<span data-ttu-id="eb81c-124">状态</span><span class="sxs-lookup"><span data-stu-id="eb81c-124">Status</span></span>|<span data-ttu-id="eb81c-125">说明</span><span class="sxs-lookup"><span data-stu-id="eb81c-125">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="eb81c-126">错误</span><span class="sxs-lookup"><span data-stu-id="eb81c-126">Error</span></span>|<span data-ttu-id="eb81c-127">行中的一个或多个值不符合长度或数据类型之类的系统要求。</span><span class="sxs-lookup"><span data-stu-id="eb81c-127">One or more values in the row don't meet system requirements like length or data type.</span></span> <span data-ttu-id="eb81c-128">值在 MDS 存储库中不更新。</span><span class="sxs-lookup"><span data-stu-id="eb81c-128">The value is not updated in the MDS repository.</span></span>|  
|<span data-ttu-id="eb81c-129">新行</span><span class="sxs-lookup"><span data-stu-id="eb81c-129">New Row</span></span>|<span data-ttu-id="eb81c-130">该行中的值尚未发布到 MDS 存储库中。</span><span class="sxs-lookup"><span data-stu-id="eb81c-130">The values in the row have not yet been published to the MDS repository.</span></span>|  
|<span data-ttu-id="eb81c-131">只读</span><span class="sxs-lookup"><span data-stu-id="eb81c-131">Read Only</span></span>|<span data-ttu-id="eb81c-132">登录用户对该行中的一个或多个值具有只读权限，并且这些值不能更新。</span><span class="sxs-lookup"><span data-stu-id="eb81c-132">The logged in user has Read-only permissions to one or more values in the row and the value(s) cannot be updated.</span></span>|  
|<span data-ttu-id="eb81c-133">不变</span><span class="sxs-lookup"><span data-stu-id="eb81c-133">Unchanged</span></span>|<span data-ttu-id="eb81c-134">行中没有任何值在工作表中进行了更改。</span><span class="sxs-lookup"><span data-stu-id="eb81c-134">No values in the row have been changed in the worksheet.</span></span> <span data-ttu-id="eb81c-135">这并不意味着存储库中的值已更改；若要获取工作表中的最新数据，请在 **“连接并加载”** 组中单击 **“加载或刷新”**。</span><span class="sxs-lookup"><span data-stu-id="eb81c-135">This does not mean the values in the repository have not changed; to get the latest data in the sheet, in the **Connect and Load** group, click **Load or Refresh**.</span></span><br /><br /> <span data-ttu-id="eb81c-136">这是每一行的默认设置。</span><span class="sxs-lookup"><span data-stu-id="eb81c-136">This is the default setting for each row.</span></span>|  
  
## <a name="related-tasks"></a><span data-ttu-id="eb81c-137">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="eb81c-137">Related Tasks</span></span>  
  
|<span data-ttu-id="eb81c-138">任务说明</span><span class="sxs-lookup"><span data-stu-id="eb81c-138">Task Description</span></span>|<span data-ttu-id="eb81c-139">主题</span><span class="sxs-lookup"><span data-stu-id="eb81c-139">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="eb81c-140">确定哪些值未通过定义的业务规则。</span><span class="sxs-lookup"><span data-stu-id="eb81c-140">Determine which values do not pass the defined business rules.</span></span>|[<span data-ttu-id="eb81c-141">应用业务规则（用于 Excel 的 MDS 外接程序）</span><span class="sxs-lookup"><span data-stu-id="eb81c-141">Apply Business Rules &#40;MDS Add-in for Excel&#41;</span></span>](apply-business-rules-mds-add-in-for-excel.md)|  
|<span data-ttu-id="eb81c-142">为了帮助纠正验证错误，请查看某一成员发生的所有事务。</span><span class="sxs-lookup"><span data-stu-id="eb81c-142">To help correct validation errors, view all transactions that have taken place for a member.</span></span>|[<span data-ttu-id="eb81c-143">查看成员的所有批注或事务（用于 Excel 的 MDS 外接程序）</span><span class="sxs-lookup"><span data-stu-id="eb81c-143">View All Annotations or Transactions for a Member &#40;MDS Add-in for Excel&#41;</span></span>](view-all-annotations-or-transactions-for-a-member-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a><span data-ttu-id="eb81c-144">相关内容</span><span class="sxs-lookup"><span data-stu-id="eb81c-144">Related Content</span></span>  
  
-   [<span data-ttu-id="eb81c-145">MDS Add-in for Excel&#41;发布数据 &#40;</span><span class="sxs-lookup"><span data-stu-id="eb81c-145">Publishing Data &#40;MDS Add-in for Excel&#41;</span></span>](overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  
