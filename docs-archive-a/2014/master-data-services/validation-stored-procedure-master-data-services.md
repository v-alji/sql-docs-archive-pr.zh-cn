---
title: 验证存储过程 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 332d3c86-4440-4f12-a6cb-ffbfbccde52c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 8fa6b01d950c87768d10b0252c1ccbab2b932fe1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586764"
---
# <a name="validation-stored-procedure-master-data-services"></a><span data-ttu-id="b5496-102">验证存储过程 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="b5496-102">Validation Stored Procedure (Master Data Services)</span></span>
  <span data-ttu-id="b5496-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，对某一版本进行验证以便将业务规则应用于该模型版本中的所有成员。</span><span class="sxs-lookup"><span data-stu-id="b5496-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], validate a version to apply business rules to all members in the model version.</span></span>  
  
 <span data-ttu-id="b5496-104">本主题说明如何使用 **mdm.udpValidateModel** 存储过程来验证数据。</span><span class="sxs-lookup"><span data-stu-id="b5496-104">This topic explains how to use the **mdm.udpValidateModel** stored procedure to validate data.</span></span> <span data-ttu-id="b5496-105">如果您是 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web 应用程序的管理员，可以在 UI 中进行验证。</span><span class="sxs-lookup"><span data-stu-id="b5496-105">If you are an administrator in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application, you can do validation in the UI instead.</span></span> <span data-ttu-id="b5496-106">有关详细信息，请参阅 [针对业务规则验证版本 (Master Data Services)](validate-a-version-against-business-rules-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="b5496-106">For more information, see [Validate a Version against Business Rules &#40;Master Data Services&#41;](validate-a-version-against-business-rules-master-data-services.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b5496-107">如果在临时过程完成前调用验证，将不验证未完成暂存的成员。</span><span class="sxs-lookup"><span data-stu-id="b5496-107">If you invoke validation before the staging process is complete, members that have not finished staging will not be validated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5496-108">示例</span><span class="sxs-lookup"><span data-stu-id="b5496-108">Example</span></span>  
  
```  
DECLARE @ModelName nVarchar(50) = 'Customer'   
DECLARE @Model_id int   
DECLARE @UserName nvarchar(50)= 'DOMAIN\user_name'   
DECLARE @User_ID int   
DECLARE @Version_ID int   
  
SET @User_ID = (SELECT ID    
                 FROM mdm.tblUser u   
                 WHERE u.UserName = @UserName)   
SET @Model_ID = (SELECT Top 1 Model_ID   
                 FROM mdm.viw_SYSTEM_SCHEMA_VERSION   
                 WHERE Model_Name = @ModelName)   
SET @Version_ID = (SELECT MAX(ID)   
                 FROM mdm.viw_SYSTEM_SCHEMA_VERSION   
                 WHERE Model_ID = @Model_ID)  
  
EXECUTE mdm.udpValidateModel @User_ID, @Model_ID, @Version_ID, 1  
  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5496-109">参数</span><span class="sxs-lookup"><span data-stu-id="b5496-109">Parameters</span></span>  
 <span data-ttu-id="b5496-110">此过程的参数如下所示：</span><span class="sxs-lookup"><span data-stu-id="b5496-110">The parameters of this procedure are as follows:</span></span>  
  
|<span data-ttu-id="b5496-111">参数</span><span class="sxs-lookup"><span data-stu-id="b5496-111">Parameter</span></span>|<span data-ttu-id="b5496-112">说明</span><span class="sxs-lookup"><span data-stu-id="b5496-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b5496-113">UserID</span><span class="sxs-lookup"><span data-stu-id="b5496-113">UserID</span></span>|<span data-ttu-id="b5496-114">用户 ID。</span><span class="sxs-lookup"><span data-stu-id="b5496-114">The user ID.</span></span>|  
|<span data-ttu-id="b5496-115">Model_ID</span><span class="sxs-lookup"><span data-stu-id="b5496-115">Model_ID</span></span>|<span data-ttu-id="b5496-116">模型 ID。</span><span class="sxs-lookup"><span data-stu-id="b5496-116">The model ID.</span></span>|  
|<span data-ttu-id="b5496-117">Version_ID</span><span class="sxs-lookup"><span data-stu-id="b5496-117">Version_ID</span></span>|<span data-ttu-id="b5496-118">版本 ID。</span><span class="sxs-lookup"><span data-stu-id="b5496-118">The version ID.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b5496-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b5496-119">See Also</span></span>  
 <span data-ttu-id="b5496-120">[数据导入 &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="b5496-120">[Data Import &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md) </span></span>  
 [<span data-ttu-id="b5496-121">针对业务规则验证版本 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="b5496-121">Validate a Version against Business Rules &#40;Master Data Services&#41;</span></span>](validate-a-version-against-business-rules-master-data-services.md)  
  
  
