---
title: 针对业务规则验证特定成员 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- applying business rules [Master Data Services]
- business rules [Master Data Services], applying to select members
ms.assetid: 2288ef43-5392-47ea-b651-ec25e5692a14
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 18af83146679eb77638dfbc98b31f198dc8e07b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87581351"
---
# <a name="validate-specific-members-against-business-rules-master-data-services"></a><span data-ttu-id="8af40-102">针对业务规则验证特定成员 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="8af40-102">Validate Specific Members against Business Rules (Master Data Services)</span></span>
  <span data-ttu-id="8af40-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，在您想要根据业务规则更新或验证成员的子级时，可以有选择地应用业务规则。</span><span class="sxs-lookup"><span data-stu-id="8af40-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], apply business rules selectively when you want to update or validate subsets of members against business rules.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8af40-104">如果想要将业务规则应用于某个模型版本中的所有成员，请参阅 [针对业务规则验证版本 (Master Data Services)](validate-a-version-against-business-rules-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="8af40-104">If you want to apply business rules to all members in a version of a model, see [Validate a Version against Business Rules &#40;Master Data Services&#41;](validate-a-version-against-business-rules-master-data-services.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8af40-105">先决条件</span><span class="sxs-lookup"><span data-stu-id="8af40-105">Prerequisites</span></span>  
 <span data-ttu-id="8af40-106">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="8af40-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="8af40-107">\*\*\*\* 您必须有权访问“资源管理器”功能区域。</span><span class="sxs-lookup"><span data-stu-id="8af40-107">You must have permission to access the **Explorer** functional area.</span></span>  
  
-   <span data-ttu-id="8af40-108">对于您要将业务规则应用于的模型对象，您必须至少具有 **“更新”** 权限。</span><span class="sxs-lookup"><span data-stu-id="8af40-108">You must have a minimum of **Update** permission to the model object you are applying business rules to.</span></span>  
  
### <a name="to-apply-business-rules-selectively"></a><span data-ttu-id="8af40-109">有选择地应用业务规则</span><span class="sxs-lookup"><span data-stu-id="8af40-109">To apply business rules selectively</span></span>  
  
1.  <span data-ttu-id="8af40-110">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 在 \*\*\*\* 主页上，从“模型”列表中，选择模型。</span><span class="sxs-lookup"><span data-stu-id="8af40-110">On the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] home page, from the **Model** list, select a model.</span></span>  
  
2.  <span data-ttu-id="8af40-111">\*\*\*\* 从“版本”列表中，选择某一版本。</span><span class="sxs-lookup"><span data-stu-id="8af40-111">From the **Version** list, select a version.</span></span>  
  
3.  <span data-ttu-id="8af40-112">单击 **“资源管理器”**。</span><span class="sxs-lookup"><span data-stu-id="8af40-112">Click **Explorer**.</span></span>  
  
4.  <span data-ttu-id="8af40-113">从菜单栏中指向 **“实体”** ，然后单击包含要将规则应用于的成员的实体名称。</span><span class="sxs-lookup"><span data-stu-id="8af40-113">From the menu bar, point to **Entities** and click the name of the entity that contains members you want to apply rules to.</span></span>  
  
5.  <span data-ttu-id="8af40-114">单击“应用业务规则”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8af40-114">Click **Apply business rules**.</span></span> <span data-ttu-id="8af40-115">业务规则仅应用于在网格中显示的成员。</span><span class="sxs-lookup"><span data-stu-id="8af40-115">Business rules are applied only to the members displayed in the grid.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8af40-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8af40-116">See Also</span></span>  
 <span data-ttu-id="8af40-117">[针对业务规则验证版本 &#40;Master Data Services&#41;](validate-a-version-against-business-rules-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="8af40-117">[Validate a Version against Business Rules &#40;Master Data Services&#41;](validate-a-version-against-business-rules-master-data-services.md) </span></span>  
 [<span data-ttu-id="8af40-118">业务规则 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="8af40-118">Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/business-rules-master-data-services.md)  
  
  
