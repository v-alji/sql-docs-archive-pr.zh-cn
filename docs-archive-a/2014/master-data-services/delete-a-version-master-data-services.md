---
title: 删除版本 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- versions [Master Data Services], deleting
- deleting versions [Master Data Services]
ms.assetid: 2a4eeffe-8379-4744-ad44-c27d8c8ac9a8
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f83a3bc396b2a13ac7ac03ef653b16a0d556189a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590886"
---
# <a name="delete-a-version-master-data-services"></a><span data-ttu-id="a7157-102">删除版本 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="a7157-102">Delete a Version (Master Data Services)</span></span>
  <span data-ttu-id="a7157-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，当您确定您不再需要与某个版本关联的主数据时，可以删除此版本。</span><span class="sxs-lookup"><span data-stu-id="a7157-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], delete a version when you are sure you no longer need the master data associated with the version.</span></span> <span data-ttu-id="a7157-104">删除版本后，无法检索关联的主数据。</span><span class="sxs-lookup"><span data-stu-id="a7157-104">After you delete a version, you cannot retrieve the associated master data.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="a7157-105">如果模型只有一个版本而您删除它，则模型将变得不可用。</span><span class="sxs-lookup"><span data-stu-id="a7157-105">If a model has only one version and you delete it, the model becomes unusable.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a7157-106">先决条件</span><span class="sxs-lookup"><span data-stu-id="a7157-106">Prerequisites</span></span>  
 <span data-ttu-id="a7157-107">若要执行此过程：</span><span class="sxs-lookup"><span data-stu-id="a7157-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="a7157-108">您必须具有查看 mdm.viw_SYSTEM_SCHEMA_VERSION 视图的权限和在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 数据库中执行 mds.udpVersionDelete 存储过程的权限。</span><span class="sxs-lookup"><span data-stu-id="a7157-108">You must have permission to view the mdm.viw_SYSTEM_SCHEMA_VERSION view and to execute the mds.udpVersionDelete stored procedure in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="a7157-109">有关详细信息，请参阅[数据库对象安全性 (Master Data Services)](database-object-security-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="a7157-109">For more information, see [Database Object Security &#40;Master Data Services&#41;](database-object-security-master-data-services.md).</span></span>  
  
### <a name="to-delete-a-version"></a><span data-ttu-id="a7157-110">删除版本</span><span class="sxs-lookup"><span data-stu-id="a7157-110">To delete a version</span></span>  
  
1.  <span data-ttu-id="a7157-111">打开 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 并连接到 [!INCLUDE[ssDE](../includes/ssde-md.md)] 数据库的 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="a7157-111">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] and connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)] instance for your [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span>  
  
2.  <span data-ttu-id="a7157-112">打开 mdm.viw_SYSTEM_SCHEMA_VERSION 视图。</span><span class="sxs-lookup"><span data-stu-id="a7157-112">Open the mdm.viw_SYSTEM_SCHEMA_VERSION view.</span></span>  
  
3.  <span data-ttu-id="a7157-113">找到您要删除的模型的版本，并复制 **ID** 字段中的值。</span><span class="sxs-lookup"><span data-stu-id="a7157-113">Find the version of the model you want to delete and copy the value in the **ID** field.</span></span>  
  
4.  <span data-ttu-id="a7157-114">创建新查询。</span><span class="sxs-lookup"><span data-stu-id="a7157-114">Create a new query.</span></span>  
  
5.  <span data-ttu-id="a7157-115">键入以下文本，用在步骤 2 中复制的值替代 *version_ID* 。</span><span class="sxs-lookup"><span data-stu-id="a7157-115">Type the following text, replacing *version_ID* with the value you copied in step 2.</span></span>  
  
    ```  
    EXEC [mdm].[udpVersionDelete] @Version_ID='version_ID'  
    ```  
  
6.  <span data-ttu-id="a7157-116">运行查询。</span><span class="sxs-lookup"><span data-stu-id="a7157-116">Run the query.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a7157-117">您可能必须等待几分钟，然后 Web 应用程序才能反映此更改。</span><span class="sxs-lookup"><span data-stu-id="a7157-117">You may have to wait a few minutes before the Web application reflects the change.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7157-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a7157-118">See Also</span></span>  
 <span data-ttu-id="a7157-119">[版本 &#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="a7157-119">[Versions &#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md) </span></span>  
 [<span data-ttu-id="a7157-120">复制版本 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="a7157-120">Copy a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/copy-a-version-master-data-services.md)  
  
  
