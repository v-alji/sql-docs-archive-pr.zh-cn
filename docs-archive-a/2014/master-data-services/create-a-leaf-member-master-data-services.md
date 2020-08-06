---
title: 创建叶成员 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- leaf members [Master Data Services], creating
- creating leaf members [Master Data Services]
- members [Master Data Services], creating leaf members
ms.assetid: 0499d3b3-d508-4d43-a740-19cf53ade9f1
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: fe0245dd30019e1cb9112754bd8b8eeafed93aa5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87576872"
---
# <a name="create-a-leaf-member-master-data-services"></a><span data-ttu-id="fa3a4-102">创建叶成员 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="fa3a4-102">Create a Leaf Member (Master Data Services)</span></span>
  <span data-ttu-id="fa3a4-103">在中 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ，当你想要向系统中添加主数据并且未使用临时表或 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] 以导入数据时，创建叶成员。</span><span class="sxs-lookup"><span data-stu-id="fa3a4-103">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], create a leaf member when you want to add master data to your system and are not using staging tables or the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] to import data.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="fa3a4-104">先决条件</span><span class="sxs-lookup"><span data-stu-id="fa3a4-104">Prerequisites</span></span>  
 <span data-ttu-id="fa3a4-105">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="fa3a4-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="fa3a4-106">\*\*\*\* 您必须有权访问“资源管理器”功能区域。</span><span class="sxs-lookup"><span data-stu-id="fa3a4-106">You must have permission to access the **Explorer** functional area.</span></span>  
  
-   <span data-ttu-id="fa3a4-107">对于要向其中添加成员的实体，您必须至少具有对叶模型对象的 "**更新**" 权限。</span><span class="sxs-lookup"><span data-stu-id="fa3a4-107">You must have a minimum of **Update** permission to the leaf model object for the entity you are adding a member to.</span></span>  
  
### <a name="to-create-a-leaf-member"></a><span data-ttu-id="fa3a4-108">创建叶成员</span><span class="sxs-lookup"><span data-stu-id="fa3a4-108">To create a leaf member</span></span>  
  
1.  <span data-ttu-id="fa3a4-109">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 在 \*\*\*\* 主页上，从“模型”列表中，选择模型。</span><span class="sxs-lookup"><span data-stu-id="fa3a4-109">On the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] home page, from the **Model** list, select a model.</span></span>  
  
2.  <span data-ttu-id="fa3a4-110">如果您是用户，则从 **“版本”** 列表中选择某一打开的版本。</span><span class="sxs-lookup"><span data-stu-id="fa3a4-110">If you are a user, select an open version from the **Version** list.</span></span> <span data-ttu-id="fa3a4-111">如果您是管理员，则从 **“版本”** 列表中选择某一状态为打开或已锁定的版本。</span><span class="sxs-lookup"><span data-stu-id="fa3a4-111">If you are an administrator, select a version with open or locked status from the **Version** list.</span></span>  
  
3.  <span data-ttu-id="fa3a4-112">单击 **“资源管理器”**。</span><span class="sxs-lookup"><span data-stu-id="fa3a4-112">Click **Explorer**.</span></span>  
  
4.  <span data-ttu-id="fa3a4-113">从菜单栏中，指向 **“实体”** ，然后单击您要将成员添加到的实体的名称。</span><span class="sxs-lookup"><span data-stu-id="fa3a4-113">From the menu bar, point to **Entities** and click the name of the entity you want to add a member to.</span></span>  
  
5.  <span data-ttu-id="fa3a4-114">单击 "**添加成员**"。</span><span class="sxs-lookup"><span data-stu-id="fa3a4-114">Click **Add member**.</span></span>  
  
6.  <span data-ttu-id="fa3a4-115">在 **“详细信息”** 窗格中，填写字段。</span><span class="sxs-lookup"><span data-stu-id="fa3a4-115">In the **Details** pane, complete the fields.</span></span>  
  
7.  <span data-ttu-id="fa3a4-116">可选。</span><span class="sxs-lookup"><span data-stu-id="fa3a4-116">Optional.</span></span> <span data-ttu-id="fa3a4-117">\*\*\*\* 在“批注”框中，键入有关添加成员原因的注释。</span><span class="sxs-lookup"><span data-stu-id="fa3a4-117">In the **Annotations** box, type a comment about why the member was added.</span></span> <span data-ttu-id="fa3a4-118">有权访问成员的所有用户都可以查看批注。</span><span class="sxs-lookup"><span data-stu-id="fa3a4-118">All users who have access to the member can view the annotation.</span></span>  
  
8.  <span data-ttu-id="fa3a4-119">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="fa3a4-119">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa3a4-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fa3a4-120">See Also</span></span>  
 <span data-ttu-id="fa3a4-121">[通过使用临时过程在 Master Data Services 中加载或更新成员](add-update-and-delete-data-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="fa3a4-121">[Load or Update Members in Master Data Services by Using the Staging Process](add-update-and-delete-data-master-data-services.md) </span></span>  
 <span data-ttu-id="fa3a4-122">[Master Data Services 创建合并成员 &#40;&#41;](../../2014/master-data-services/create-a-consolidated-member-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="fa3a4-122">[Create a Consolidated Member &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-consolidated-member-master-data-services.md) </span></span>  
 [<span data-ttu-id="fa3a4-123">成员 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="fa3a4-123">Members &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/members-master-data-services.md)  
  
  
