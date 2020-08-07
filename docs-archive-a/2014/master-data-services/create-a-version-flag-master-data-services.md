---
title: 创建版本标志 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- creating version flags [Master Data Services]
- version flags [Master Data Services], creating
- versions [Master Data Services], creating flags
ms.assetid: 3067e1e3-05b7-4f11-9206-c612ef4e7e42
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f04c93f8315ccd5b53e07db169783da53afe0156
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588587"
---
# <a name="create-a-version-flag-master-data-services"></a><span data-ttu-id="990ea-102">创建版本标志 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="990ea-102">Create a Version Flag (Master Data Services)</span></span>
  <span data-ttu-id="990ea-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，创建要分配给某一版本的标志。</span><span class="sxs-lookup"><span data-stu-id="990ea-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create a version flag to assign to a version.</span></span> <span data-ttu-id="990ea-104">该标志可以指示用户或订阅系统应使用的版本。</span><span class="sxs-lookup"><span data-stu-id="990ea-104">The flag can indicate the version that users or subscribing systems should use.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="990ea-105">必备条件</span><span class="sxs-lookup"><span data-stu-id="990ea-105">Prerequisites</span></span>  
 <span data-ttu-id="990ea-106">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="990ea-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="990ea-107">您必须有权访问 **“版本管理”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="990ea-107">You must have permission to access the **Version Management** functional area.</span></span>  
  
-   <span data-ttu-id="990ea-108">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="990ea-108">You must be a model administrator.</span></span> <span data-ttu-id="990ea-109">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="990ea-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-create-a-version-flag"></a><span data-ttu-id="990ea-110">创建版本标志</span><span class="sxs-lookup"><span data-stu-id="990ea-110">To create a version flag</span></span>  
  
1.  <span data-ttu-id="990ea-111">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“版本管理”**。</span><span class="sxs-lookup"><span data-stu-id="990ea-111">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **Version Management**.</span></span>  
  
2.  <span data-ttu-id="990ea-112">在 **“管理版本”** 页上，从菜单栏中，指向 **“管理”** ，然后单击 **“标志”**。</span><span class="sxs-lookup"><span data-stu-id="990ea-112">On the **Manage Versions** page, from the menu bar, point to **Manage** and then click **Flags**.</span></span>  
  
3.  <span data-ttu-id="990ea-113">在 **“管理版本标志”** 页上，从 **“模型”** 字段中，选择要为其创建标志的模型。</span><span class="sxs-lookup"><span data-stu-id="990ea-113">On the **Manage Version Flags** page, from the **Model** field, select the model for which you want to create a flag.</span></span>  
  
4.  <span data-ttu-id="990ea-114">单击 **添加**。</span><span class="sxs-lookup"><span data-stu-id="990ea-114">Click **Add**.</span></span>  
  
5.  <span data-ttu-id="990ea-115">在 **“名称”** 框中，键入名称。</span><span class="sxs-lookup"><span data-stu-id="990ea-115">In the **Name** box, type a name.</span></span>  
  
6.  <span data-ttu-id="990ea-116">在 **“描述”** 框中，键入描述。</span><span class="sxs-lookup"><span data-stu-id="990ea-116">In the **Description** box, type a description.</span></span>  
  
7.  <span data-ttu-id="990ea-117">在 **“仅提交的版本”** 字段中，选择 **True** 以便指示只能将标志分配给状态为 **“已提交”** 的版本。</span><span class="sxs-lookup"><span data-stu-id="990ea-117">In the **Committed Versions Only** field, select **True** to indicate that the flag can be assigned to versions with a status of **Committed** only.</span></span> <span data-ttu-id="990ea-118">选择 **False** 以便指示可以将标志分配给具有任何状态的版本。</span><span class="sxs-lookup"><span data-stu-id="990ea-118">Select **False** to indicate that the flag can be assigned to versions with any status.</span></span>  
  
8.  <span data-ttu-id="990ea-119">单击 **“保存”** 。</span><span class="sxs-lookup"><span data-stu-id="990ea-119">Click **Save**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="990ea-120">后续步骤</span><span class="sxs-lookup"><span data-stu-id="990ea-120">Next Steps</span></span>  
  
-   [<span data-ttu-id="990ea-121">向版本分配标志 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="990ea-121">Assign a Flag to a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/assign-a-flag-to-a-version-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="990ea-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="990ea-122">See Also</span></span>  
 <span data-ttu-id="990ea-123">[版本 &#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="990ea-123">[Versions &#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md) </span></span>  
 [<span data-ttu-id="990ea-124">更改版本标志名称 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="990ea-124">Change a Version Flag Name &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/change-a-version-flag-name-master-data-services.md)  
  
  
