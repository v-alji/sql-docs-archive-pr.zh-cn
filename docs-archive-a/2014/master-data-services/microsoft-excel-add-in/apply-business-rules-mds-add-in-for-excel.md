---
title: 应用业务规则 (MDS Add-in for Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: cd106345-f561-4966-88d3-a69139b2bd78
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: aad5ce6bcebb635fa4659c32654d67406d4ba0dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688976"
---
# <a name="apply-business-rules-mds-add-in-for-excel"></a><span data-ttu-id="57aca-102">应用业务规则（用于 Excel 的 MDS 外接程序）</span><span class="sxs-lookup"><span data-stu-id="57aca-102">Apply Business Rules (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="57aca-103">在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] 中，如果需要验证数据并确认其有效，可应用业务规则。</span><span class="sxs-lookup"><span data-stu-id="57aca-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] apply business rules when you want to validate data and confirm that it is valid.</span></span> <span data-ttu-id="57aca-104">您可以更正验证结果并重新发布数据。</span><span class="sxs-lookup"><span data-stu-id="57aca-104">You can correct validations and re-publish the data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="57aca-105">发布数据时会自动验证数据。</span><span class="sxs-lookup"><span data-stu-id="57aca-105">Data validation occurs automatically when you publish data.</span></span> <span data-ttu-id="57aca-106">有关详细信息，请参阅 [验证存储过程 (Master Data Services)](../validation-stored-procedure-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="57aca-106">For more information, see [Validation Stored Procedure &#40;Master Data Services&#41;](../validation-stored-procedure-master-data-services.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="57aca-107">先决条件</span><span class="sxs-lookup"><span data-stu-id="57aca-107">Prerequisites</span></span>  
 <span data-ttu-id="57aca-108">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="57aca-108">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="57aca-109">您必须有权访问 **“资源管理器”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="57aca-109">You must have access to the **Explorer** functional area.</span></span>  
  
-   <span data-ttu-id="57aca-110">必须具有包含 MDS 管理的数据的活动工作表。</span><span class="sxs-lookup"><span data-stu-id="57aca-110">You must have an active worksheet that contains MDS-managed data.</span></span>  
  
### <a name="to-apply-business-rules"></a><span data-ttu-id="57aca-111">应用业务规则</span><span class="sxs-lookup"><span data-stu-id="57aca-111">To apply business rules</span></span>  
  
1.  <span data-ttu-id="57aca-112">在 **“发布并验证”** 组中，单击 **“应用规则”**。</span><span class="sxs-lookup"><span data-stu-id="57aca-112">In the **Publish and Validate** group, click **Apply Rules**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="57aca-113">一次验证的成员（行）的数目取决于 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]中的设置。</span><span class="sxs-lookup"><span data-stu-id="57aca-113">The number of members (rows) that are validated at one time depends on a setting in [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].</span></span> <span data-ttu-id="57aca-114">有关详细信息，请参阅 [Business Rule Settings](../system-settings-master-data-services.md#BusinessRules)。</span><span class="sxs-lookup"><span data-stu-id="57aca-114">For more information, see [Business Rule Settings](../system-settings-master-data-services.md#BusinessRules).</span></span>  
  
2.  <span data-ttu-id="57aca-115">根据业务规则对数据进行验证后，将显示两个状态列。</span><span class="sxs-lookup"><span data-stu-id="57aca-115">The data is validated against business rules and two status columns are displayed.</span></span> <span data-ttu-id="57aca-116">如果不自动显示这些列，请在 **“发布并验证”** 组中，单击 **“显示状态”** 以查看这些列。</span><span class="sxs-lookup"><span data-stu-id="57aca-116">If these columns are not displayed automatically, in the **Publish and Validate** group, click **Show Status** to view them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57aca-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="57aca-117">See Also</span></span>  
 [<span data-ttu-id="57aca-118">MDS Add-in for Excel&#41;发布数据 &#40;</span><span class="sxs-lookup"><span data-stu-id="57aca-118">Publishing Data &#40;MDS Add-in for Excel&#41;</span></span>](overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  
