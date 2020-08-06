---
title: 向版本分配标志 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- version flags [Master Data Services], assigning flags
- versions [Master Data Services], assigning flags
ms.assetid: 6629ec7e-32e7-4a1e-8b31-eb43c5923766
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 2de0d0d8d8ea96814e13b9123fe4fcd4782d6bef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590890"
---
# <a name="assign-a-flag-to-a-version-master-data-services"></a><span data-ttu-id="216c9-102">向版本分配标志 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="216c9-102">Assign a Flag to a Version (Master Data Services)</span></span>
  <span data-ttu-id="216c9-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，向版本分配标志以便指示用户或订阅系统应使用的版本。</span><span class="sxs-lookup"><span data-stu-id="216c9-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], assign a flag to a version to indicate the version that users or subscribing systems should use.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="216c9-104">版本标志一次只能分配给一个版本。</span><span class="sxs-lookup"><span data-stu-id="216c9-104">Version flags can be assigned to only one version at a time.</span></span> <span data-ttu-id="216c9-105">如果您分配的标志已分配给另一个版本，则该标志将移到您选择的版本。</span><span class="sxs-lookup"><span data-stu-id="216c9-105">If you assign a flag that is already assigned to another version, the flag is moved to the version you selected.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="216c9-106">先决条件</span><span class="sxs-lookup"><span data-stu-id="216c9-106">Prerequisites</span></span>  
 <span data-ttu-id="216c9-107">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="216c9-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="216c9-108">您必须有权访问 **“版本管理”** 功能区域。</span><span class="sxs-lookup"><span data-stu-id="216c9-108">You must have permission to access the **Version Management** functional area.</span></span>  
  
-   <span data-ttu-id="216c9-109">您必须是模型管理员。</span><span class="sxs-lookup"><span data-stu-id="216c9-109">You must be a model administrator.</span></span> <span data-ttu-id="216c9-110">有关详细信息，请参阅[管理员 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="216c9-110">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="216c9-111">您必须已创建要分配的版本标志。</span><span class="sxs-lookup"><span data-stu-id="216c9-111">You must have created a version flag to assign.</span></span> <span data-ttu-id="216c9-112">有关详细信息，请参阅 [创建版本标志 (Master Data Services)](../../2014/master-data-services/create-a-version-flag-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="216c9-112">For more information, see [Create a Version Flag &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-version-flag-master-data-services.md).</span></span>  
  
### <a name="to-assign-a-flag-to-a-version"></a><span data-ttu-id="216c9-113">向版本分配标志</span><span class="sxs-lookup"><span data-stu-id="216c9-113">To assign a flag to a version</span></span>  
  
1.  <span data-ttu-id="216c9-114">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“版本管理”**。</span><span class="sxs-lookup"><span data-stu-id="216c9-114">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **Version Management**.</span></span>  
  
2.  <span data-ttu-id="216c9-115">在“管理版本”\*\*\*\* 页上，在与你要分配标志的版本相对应的行中，双击“标志”\*\*\*\* 列中的单元格。</span><span class="sxs-lookup"><span data-stu-id="216c9-115">On the **Manage Versions** page, in the row for the version to which you want to assign a flag, double-click the cell in the **Flag** column.</span></span>  
  
3.  <span data-ttu-id="216c9-116">从列表中，选择要分配的标志。</span><span class="sxs-lookup"><span data-stu-id="216c9-116">From the list, select the flag you want to assign.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="216c9-117">如果您想要的标志不可用，则该标志可能仅可用于 **“已提交”** 版本。</span><span class="sxs-lookup"><span data-stu-id="216c9-117">If the flag you want is not available, the flag might be available for **Committed** versions only.</span></span> <span data-ttu-id="216c9-118">若要确认，请转到 **“管理版本标志”** 页并查看标志的 **“仅提交的版本”** 字段。</span><span class="sxs-lookup"><span data-stu-id="216c9-118">To confirm, go to the **Manage Version Flags** page and view the **Committed Versions Only** field for the flag.</span></span>  
  
4.  <span data-ttu-id="216c9-119">按 Enter 以保存更改。</span><span class="sxs-lookup"><span data-stu-id="216c9-119">Press ENTER to save the change.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="216c9-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="216c9-120">See Also</span></span>  
 <span data-ttu-id="216c9-121">[&#40;Master Data Services 创建版本标志&#41;](../../2014/master-data-services/create-a-version-flag-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="216c9-121">[Create a Version Flag &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-version-flag-master-data-services.md) </span></span>  
 [<span data-ttu-id="216c9-122">版本 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="216c9-122">Versions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/versions-master-data-services.md)  
  
  
