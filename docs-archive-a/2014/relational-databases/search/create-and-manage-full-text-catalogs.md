---
title: 创建和管理全文目录 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text catalogs [SQL Server], creating
- full-text search [SQL Server], using SQL Server Management Studio
ms.assetid: 824b7131-44a6-4815-89e6-62b7bab060e3
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 18efd79bc34beee94d4edc61e9165a986edba90b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591215"
---
# <a name="create-and-manage-full-text-catalogs"></a><span data-ttu-id="4f10b-102">创建和管理全文索引目录</span><span class="sxs-lookup"><span data-stu-id="4f10b-102">Create and Manage Full-Text Catalogs</span></span>
  <span data-ttu-id="4f10b-103">全文目录是虚拟对象，并不属于任何文件组；它是表示一组全文索引的逻辑概念。</span><span class="sxs-lookup"><span data-stu-id="4f10b-103">A full-text catalog is a virtual object that does not belong to any filegroup; it is a logical concept that refers to a group of full-text indexes.</span></span>  
  
##  <a name="creating-a-full-text-catalog"></a><a name="creating"></a><span data-ttu-id="4f10b-104">创建全文目录</span><span class="sxs-lookup"><span data-stu-id="4f10b-104">Creating a Full-Text Catalog</span></span>  
  
#### <a name="to-create-a-full-text-catalog"></a><span data-ttu-id="4f10b-105">创建全文目录</span><span class="sxs-lookup"><span data-stu-id="4f10b-105">To create a full-text catalog</span></span>  
  
1.  <span data-ttu-id="4f10b-106">在对象资源管理器中，展开服务器，展开“数据库”\*\*\*\*，然后展开要在其中创建全文目录的数据库。</span><span class="sxs-lookup"><span data-stu-id="4f10b-106">In Object Explorer, expand the server, expand **Databases**, and expand the database in which you want to create the full-text catalog.</span></span>  
  
2.  <span data-ttu-id="4f10b-107">展开“存储”\*\*\*\*，然后右键单击“全文目录”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4f10b-107">Expand **Storage**, and then right-click **Full Text Catalogs**.</span></span>  
  
3.  <span data-ttu-id="4f10b-108">选择“新建全文目录”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4f10b-108">Select **New Full-Text Catalog**.</span></span>  
  
4.  <span data-ttu-id="4f10b-109">在“新建全文目录”\*\*\*\* 对话框中，指定要重新创建的目录的信息。</span><span class="sxs-lookup"><span data-stu-id="4f10b-109">In the **New Full-Text Catalog** dialog box, specify the information for the catalog that you are re-creating.</span></span> <span data-ttu-id="4f10b-110">有关详细信息，请参阅[新建全文目录（常规页）](../../integration-services/general-page-of-integration-services-designers-options.md)。</span><span class="sxs-lookup"><span data-stu-id="4f10b-110">For more information, see [New Full-Text Catalog &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4f10b-111">全文目录 ID 从 00005 开始，每创建一个新目录，其 ID 值就会递增 1。</span><span class="sxs-lookup"><span data-stu-id="4f10b-111">Full-text catalog IDs begin at 00005 and are incremented by one for each new catalog created.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
  
  
##  <a name="viewing-the-properties-of-a-full-text-catalog"></a><a name="props"></a><span data-ttu-id="4f10b-112">查看全文目录的属性</span><span class="sxs-lookup"><span data-stu-id="4f10b-112">Viewing the Properties of a Full-Text Catalog</span></span>  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="4f10b-113">函数（例如 FULLTEXTCATALOGPROPERTY）可用来获取与全文索引相关的各种属性的值。</span><span class="sxs-lookup"><span data-stu-id="4f10b-113">functions such as FULLTEXTCATALOGPROPERTY can be used to obtain the value of various properties related to full-text indexing.</span></span> <span data-ttu-id="4f10b-114">此信息可用于全文搜索的管理和故障排除。</span><span class="sxs-lookup"><span data-stu-id="4f10b-114">This information is useful for administering and troubleshooting full-text search.</span></span>  
  
 <span data-ttu-id="4f10b-115">下表列出了与全文目录相关的属性。</span><span class="sxs-lookup"><span data-stu-id="4f10b-115">The following table lists the properties that are related to full-text catalogs.</span></span>  
  
|<span data-ttu-id="4f10b-116">属性</span><span class="sxs-lookup"><span data-stu-id="4f10b-116">Property</span></span>|<span data-ttu-id="4f10b-117">说明</span><span class="sxs-lookup"><span data-stu-id="4f10b-117">Description</span></span>|<span data-ttu-id="4f10b-118">函数</span><span class="sxs-lookup"><span data-stu-id="4f10b-118">Function</span></span>|  
|--------------|-----------------|--------------|  
|`AccentSensitivity`|<span data-ttu-id="4f10b-119">区分重音设置。</span><span class="sxs-lookup"><span data-stu-id="4f10b-119">Accent-sensitivity setting.</span></span>|[<span data-ttu-id="4f10b-120">FULLTEXTCATALOGPROPERTY</span><span class="sxs-lookup"><span data-stu-id="4f10b-120">FULLTEXTCATALOGPROPERTY</span></span>](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql)|  
|`ImportStatus`|<span data-ttu-id="4f10b-121">是否将导入全文目录。</span><span class="sxs-lookup"><span data-stu-id="4f10b-121">Whether the full-text catalog is being imported.</span></span>|<span data-ttu-id="4f10b-122">FULLTEXTCATALOGPROPERTY</span><span class="sxs-lookup"><span data-stu-id="4f10b-122">FULLTEXTCATALOGPROPERTY</span></span>|  
|`IndexSize`|<span data-ttu-id="4f10b-123">全文目录的大小，以 MB 为单位。</span><span class="sxs-lookup"><span data-stu-id="4f10b-123">Size of the full-text catalog in megabytes (MB).</span></span>|<span data-ttu-id="4f10b-124">FULLTEXTCATALOGPROPERTY</span><span class="sxs-lookup"><span data-stu-id="4f10b-124">FULLTEXTCATALOGPROPERTY</span></span>|  
|`ItemCount`|<span data-ttu-id="4f10b-125">全文目录中当前包含的全文索引项的数目。</span><span class="sxs-lookup"><span data-stu-id="4f10b-125">Number of full-text indexed items currently in the full-text catalog.</span></span>|<span data-ttu-id="4f10b-126">FULLTEXTCATALOGPROPERTY</span><span class="sxs-lookup"><span data-stu-id="4f10b-126">FULLTEXTCATALOGPROPERTY</span></span>|  
|`MergeStatus`|<span data-ttu-id="4f10b-127">是否正在进行主合并。</span><span class="sxs-lookup"><span data-stu-id="4f10b-127">Whether a master merge is in progress.</span></span>|<span data-ttu-id="4f10b-128">FULLTEXTCATALOGPROPERTY</span><span class="sxs-lookup"><span data-stu-id="4f10b-128">FULLTEXTCATALOGPROPERTY</span></span>|  
|`PopulateCompletionAge`|<span data-ttu-id="4f10b-129">上一次全文索引填充的完成时间与 01/01/1990 00:00:00 之间的时间差（秒）。</span><span class="sxs-lookup"><span data-stu-id="4f10b-129">Difference in seconds between the completion of the last full-text index population and 01/01/1990 00:00:00.</span></span>|<span data-ttu-id="4f10b-130">FULLTEXTCATALOGPROPERTY</span><span class="sxs-lookup"><span data-stu-id="4f10b-130">FULLTEXTCATALOGPROPERTY</span></span>|  
|`PopulateStatus`|<span data-ttu-id="4f10b-131">填充状态。</span><span class="sxs-lookup"><span data-stu-id="4f10b-131">Populate status.</span></span><br /><br /> [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]|<span data-ttu-id="4f10b-132">FULLTEXTCATALOGPROPERTY</span><span class="sxs-lookup"><span data-stu-id="4f10b-132">FULLTEXTCATALOGPROPERTY</span></span>|  
|`UniqueKeyCount`|<span data-ttu-id="4f10b-133">全文目录中的唯一键数。</span><span class="sxs-lookup"><span data-stu-id="4f10b-133">Number of unique keys in the full-text catalog.</span></span>|<span data-ttu-id="4f10b-134">FULLTEXTCATALOGPROPERTY</span><span class="sxs-lookup"><span data-stu-id="4f10b-134">FULLTEXTCATALOGPROPERTY</span></span>|  
  
  
  
##  <a name="rebuilding-a-full-text-catalog"></a><a name="rebuildone"></a><span data-ttu-id="4f10b-135">重新生成全文目录</span><span class="sxs-lookup"><span data-stu-id="4f10b-135">Rebuilding a Full-Text Catalog</span></span>  
  
#### <a name="to-rebuild-a-full-text-catalog"></a><span data-ttu-id="4f10b-136">重新生成全文目录</span><span class="sxs-lookup"><span data-stu-id="4f10b-136">To rebuild a full-text catalog</span></span>  
  
1.  <span data-ttu-id="4f10b-137">在对象资源管理器中，展开服务器，展开“数据库”\*\*\*\*，然后展开包含要重新生成的全文目录的数据库。</span><span class="sxs-lookup"><span data-stu-id="4f10b-137">In Object Explorer, expand the server, expand **Databases**, and then expand the database that contains the full-text catalog that you want to rebuild.</span></span>  
  
2.  <span data-ttu-id="4f10b-138">展开 **“存储”**，然后展开 **“全文目录”**。</span><span class="sxs-lookup"><span data-stu-id="4f10b-138">Expand **Storage**, and then expand **Full Text Catalogs**.</span></span>  
  
3.  <span data-ttu-id="4f10b-139">右键单击要重新生成的全文目录的名称，并选择“重新生成”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4f10b-139">Right-click the name of the full-text catalog that you want to rebuild, and select **Rebuild**.</span></span>  
  
4.  <span data-ttu-id="4f10b-140">对于问题**是否要删除并重新生成全文目录?**，请单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4f10b-140">To the question **Do you want to delete the full-text catalog and rebuild it?**, click **OK**.</span></span>  
  
5.  <span data-ttu-id="4f10b-141">在“重新生成全文目录”\*\*\*\* 对话框中，单击“关闭”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4f10b-141">In the **Rebuild Full-Text Catalog** dialog box, click **Close**.</span></span>  
  
  
  
##  <a name="rebuilding-all-full-text-catalogs-for-a-database"></a><a name="rebuildall"></a><span data-ttu-id="4f10b-142">为数据库重新生成所有全文目录</span><span class="sxs-lookup"><span data-stu-id="4f10b-142">Rebuilding All Full-Text Catalogs for a Database</span></span>  
  
#### <a name="to-rebuild-the-full-text-catalogs-for-a-database"></a><span data-ttu-id="4f10b-143">为数据库重新生成全文目录</span><span class="sxs-lookup"><span data-stu-id="4f10b-143">To rebuild the full-text catalogs for a database</span></span>  
  
1.  <span data-ttu-id="4f10b-144">在对象资源管理器中，展开服务器，展开“数据库”\*\*\*\*，然后展开包含要重新生成的全文目录的数据库。</span><span class="sxs-lookup"><span data-stu-id="4f10b-144">In Object Explorer, expand the server, expand **Databases**, and then expand the database that contains the full-text catalogs that you want to rebuild.</span></span>  
  
2.  <span data-ttu-id="4f10b-145">展开“存储”\*\*\*\*，然后右键单击“全文目录”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4f10b-145">Expand **Storage**, and then right-click **Full Text Catalogs**.</span></span>  
  
3.  <span data-ttu-id="4f10b-146">选择 **“全部重新生成”**。</span><span class="sxs-lookup"><span data-stu-id="4f10b-146">Select **Rebuild All**.</span></span>  
  
4.  <span data-ttu-id="4f10b-147">对于问题**是否要删除并重新生成所有全文目录?**，请单击“确定”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4f10b-147">To the question, **Do you want to delete all full-text catalogs and rebuild them?**, click **OK**.</span></span>  
  
5.  <span data-ttu-id="4f10b-148">在“重新生成所有全文目录”\*\*\*\* 对话框中，单击“关闭”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4f10b-148">In the **Rebuild All Full-Text Catalogs** dialog box, click **Close**.</span></span>  
  
  
  
##  <a name="removing-a-full-text-catalog-from-a-database"></a><a name="removing"></a><span data-ttu-id="4f10b-149">从数据库中删除全文目录</span><span class="sxs-lookup"><span data-stu-id="4f10b-149">Removing a Full-Text Catalog from a Database</span></span>  
  
#### <a name="to-remove-a-full-text-catalog-from-a-database"></a><span data-ttu-id="4f10b-150">从数据库中删除全文目录</span><span class="sxs-lookup"><span data-stu-id="4f10b-150">To remove a full-text catalog from a database</span></span>  
  
1.  <span data-ttu-id="4f10b-151">在对象资源管理器中，展开服务器，展开“数据库”\*\*\*\*，然后展开要删除的全文目录所在的数据库。</span><span class="sxs-lookup"><span data-stu-id="4f10b-151">In Object Explorer, expand the server, expand **Databases**, and expand the database that contains the full-text catalog you want to remove.</span></span>  
  
2.  <span data-ttu-id="4f10b-152">展开 **“存储”**，然后展开 **“全文目录”**。</span><span class="sxs-lookup"><span data-stu-id="4f10b-152">Expand **Storage**, and expand **Full Text Catalogs**.</span></span>  
  
3.  <span data-ttu-id="4f10b-153">右键单击要删除的全文目录，然后选择“删除”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4f10b-153">Right-click the full-text catalog that you want to remove, and then select **Delete**.</span></span>  
  
4.  <span data-ttu-id="4f10b-154">在 **“删除对象”** 对话框中，单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="4f10b-154">In the **Delete Objects** dialog box, click **OK**.</span></span>  
  
  
  
## <a name="see-also"></a><span data-ttu-id="4f10b-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4f10b-155">See Also</span></span>  
 [<span data-ttu-id="4f10b-156">CREATE FULLTEXT CATALOG (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4f10b-156">CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-fulltext-catalog-transact-sql)  
  
  
