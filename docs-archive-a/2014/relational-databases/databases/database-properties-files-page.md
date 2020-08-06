---
title: 数据库属性（“文件”页）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.databaseproperties.files.f1
ms.assetid: 3c030e51-db82-4b43-b1e5-8547ddd3de87
author: stevestein
ms.author: sstein
ms.openlocfilehash: 955a17857ce0d847fb712473dddd581a072ab83d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87682880"
---
# <a name="database-properties-files-page"></a><span data-ttu-id="3ac9b-102">数据库属性（“文件”页）</span><span class="sxs-lookup"><span data-stu-id="3ac9b-102">Database Properties (Files Page)</span></span>
  <span data-ttu-id="3ac9b-103">使用此页可以创建新的数据库，也可以查看或修改所选数据库的属性。</span><span class="sxs-lookup"><span data-stu-id="3ac9b-103">Use this page to create a new database, or view or modify properties for the selected database.</span></span> <span data-ttu-id="3ac9b-104">对于现有数据库，本主题适用于 **数据库属性（“文件”页）** ；另外，本主题还适用于 **新建数据库（“常规”页）** 。</span><span class="sxs-lookup"><span data-stu-id="3ac9b-104">This topic applies to the **Database Properties (Files Page)** for existing databases, and to the **New Database (General Page)**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="3ac9b-105">UI 元素列表</span><span class="sxs-lookup"><span data-stu-id="3ac9b-105">UI element list</span></span>  
 <span data-ttu-id="3ac9b-106">**数据库名称**</span><span class="sxs-lookup"><span data-stu-id="3ac9b-106">**Database name**</span></span>  
 <span data-ttu-id="3ac9b-107">添加或显示数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="3ac9b-107">Add or display the name of the database.</span></span>  
  
 <span data-ttu-id="3ac9b-108">**所有者**</span><span class="sxs-lookup"><span data-stu-id="3ac9b-108">**Owner**</span></span>  
 <span data-ttu-id="3ac9b-109">通过从列表中进行选择来指定数据库的所有者。</span><span class="sxs-lookup"><span data-stu-id="3ac9b-109">Specify the owner of the database by selecting from the list.</span></span>  
  
 <span data-ttu-id="3ac9b-110">**使用全文索引**</span><span class="sxs-lookup"><span data-stu-id="3ac9b-110">**Use full-text indexing**</span></span>  
 <span data-ttu-id="3ac9b-111">由于全文检索在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中始终处于启用状态，因此该复选框处于选中状态并被禁用。</span><span class="sxs-lookup"><span data-stu-id="3ac9b-111">This check box is checked and disabled because full-text indexing is always enabled in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="3ac9b-112">有关详细信息，请参阅 [全文搜索](../search/full-text-search.md)。</span><span class="sxs-lookup"><span data-stu-id="3ac9b-112">For more information, see [Full-Text Search](../search/full-text-search.md).</span></span>  
  
 <span data-ttu-id="3ac9b-113">**数据库文件**</span><span class="sxs-lookup"><span data-stu-id="3ac9b-113">**Database Files**</span></span>  
 <span data-ttu-id="3ac9b-114">添加、查看、修改或移除相关联数据库的数据库文件。</span><span class="sxs-lookup"><span data-stu-id="3ac9b-114">Add, view, modify, or remove database files for the associated database.</span></span> <span data-ttu-id="3ac9b-115">数据库文件具有以下属性：</span><span class="sxs-lookup"><span data-stu-id="3ac9b-115">Database files have the following properties:</span></span>  
  
 <span data-ttu-id="3ac9b-116">**逻辑名称**</span><span class="sxs-lookup"><span data-stu-id="3ac9b-116">**Logical Name**</span></span>  
 <span data-ttu-id="3ac9b-117">输入或修改文件的名称。</span><span class="sxs-lookup"><span data-stu-id="3ac9b-117">Enter or modify the name of the file.</span></span>  
  
 <span data-ttu-id="3ac9b-118">**文件类型**</span><span class="sxs-lookup"><span data-stu-id="3ac9b-118">**File Type**</span></span>  
 <span data-ttu-id="3ac9b-119">从列表中选择文件类型。</span><span class="sxs-lookup"><span data-stu-id="3ac9b-119">Select the file type from the list.</span></span> <span data-ttu-id="3ac9b-120">文件类型可以为 **“数据”** 、 **“日志”** 或 **“Filestream 数据”** 。</span><span class="sxs-lookup"><span data-stu-id="3ac9b-120">The file type can be **Data**, **Log**, or **Filestream Data**.</span></span> <span data-ttu-id="3ac9b-121">您无法修改现有文件的文件类型。</span><span class="sxs-lookup"><span data-stu-id="3ac9b-121">You cannot modify the file type of an existing file.</span></span>  
  
 <span data-ttu-id="3ac9b-122">如果要将文件（容器）添加到内存优化文件组，请选择“Filestream 数据”。</span><span class="sxs-lookup"><span data-stu-id="3ac9b-122">Select **Filestream Data** if you are adding files (containers) to a memory-optimized filegroup.</span></span>  
  
 <span data-ttu-id="3ac9b-123">要将文件（容器）添加到 Filestream 数据文件组，必须启用 FILESTREAM。</span><span class="sxs-lookup"><span data-stu-id="3ac9b-123">To add files (containers) to a Filestream data filegroup, FILESTREAM must be enabled.</span></span> <span data-ttu-id="3ac9b-124">可以通过 [服务器属性（“高级”页）](../../database-engine/configure-windows/server-properties-advanced-page.md) 对话框启用 FILESTREAM。</span><span class="sxs-lookup"><span data-stu-id="3ac9b-124">You can enable FILESTREAM by using the [Server Properties (Advanced Page)](../../database-engine/configure-windows/server-properties-advanced-page.md) dialog box.</span></span>  
  
 <span data-ttu-id="3ac9b-125">**文件组**</span><span class="sxs-lookup"><span data-stu-id="3ac9b-125">**Filegroup**</span></span>  
 <span data-ttu-id="3ac9b-126">从列表中为文件选择文件组。</span><span class="sxs-lookup"><span data-stu-id="3ac9b-126">Select the filegroup for the file from the list.</span></span> <span data-ttu-id="3ac9b-127">默认情况下，文件组为 PRIMARY。</span><span class="sxs-lookup"><span data-stu-id="3ac9b-127">By default, the filegroup is PRIMARY.</span></span> <span data-ttu-id="3ac9b-128">通过选择 \<new filegroup>，然后在“新建文件组”对话框中输入有关文件组的信息，可以创建新的文件组。</span><span class="sxs-lookup"><span data-stu-id="3ac9b-128">You can create a new filegroup by selecting **\<new filegroup>** and entering information about the filegroup in the **New Filegroup** dialog box.</span></span> <span data-ttu-id="3ac9b-129">您也可以在 **“文件组”** 页上创建新的文件组。</span><span class="sxs-lookup"><span data-stu-id="3ac9b-129">A new filegroup can also be created on the **Filegroup** page.</span></span> <span data-ttu-id="3ac9b-130">您无法修改现有文件的文件组。</span><span class="sxs-lookup"><span data-stu-id="3ac9b-130">You cannot modify the filegroup of an existing file.</span></span>  
  
 <span data-ttu-id="3ac9b-131">将文件（容器）添加到内存优化文件组时，“文件组”字段将填充数据库的内存优化文件组的名称。</span><span class="sxs-lookup"><span data-stu-id="3ac9b-131">When adding files (containers) to a memory-optimized filegroup, the **Filegroup** field will be populated with the name of the database's memory-optimized filegroup.</span></span>  
  
 <span data-ttu-id="3ac9b-132">**初始大小**</span><span class="sxs-lookup"><span data-stu-id="3ac9b-132">**Initial Size**</span></span>  
 <span data-ttu-id="3ac9b-133">输入或修改文件的初始大小 (MB)。</span><span class="sxs-lookup"><span data-stu-id="3ac9b-133">Enter or modify the initial size for the file in megabytes.</span></span> <span data-ttu-id="3ac9b-134">默认情况下，这是 **model** 数据库的值。</span><span class="sxs-lookup"><span data-stu-id="3ac9b-134">By default, this is the value of the **model** database.</span></span>  
  
 <span data-ttu-id="3ac9b-135">此字段对于 FILESTREAM 文件无效。</span><span class="sxs-lookup"><span data-stu-id="3ac9b-135">This field is not valid for FILESTREAM files.</span></span>  
  
 <span data-ttu-id="3ac9b-136">对于内存优化文件组中的文件，此字段不能修改。</span><span class="sxs-lookup"><span data-stu-id="3ac9b-136">For files in memory-optimized filegroups, this field cannot be modified.</span></span>  
  
 <span data-ttu-id="3ac9b-137">**自动增长**</span><span class="sxs-lookup"><span data-stu-id="3ac9b-137">**Autogrowth**</span></span>  
 <span data-ttu-id="3ac9b-138">选择或显示文件的自动增长属性。</span><span class="sxs-lookup"><span data-stu-id="3ac9b-138">Select or display the autogrowth properties for the file.</span></span> <span data-ttu-id="3ac9b-139">这些属性控制在达到文件的最大文件大小时文件的扩展方式。</span><span class="sxs-lookup"><span data-stu-id="3ac9b-139">These properties control how the file expands when its maximum file size is reached.</span></span> <span data-ttu-id="3ac9b-140">若要编辑自动增长值，请单击所需文件的自动增长属性旁的编辑按钮，然后更改 **“更改自动增长设置”** 对话框中的值。</span><span class="sxs-lookup"><span data-stu-id="3ac9b-140">To edit autogrowth values, click the edit button next to the autogrowth properties for the file that you want, and change the values in the **Change Autogrowth** dialog box.</span></span> <span data-ttu-id="3ac9b-141">默认情况下，它们是 **model** 数据库的值。</span><span class="sxs-lookup"><span data-stu-id="3ac9b-141">By default, these are the values of the **model** database.</span></span>  
  
 <span data-ttu-id="3ac9b-142">此字段对于 FILESTREAM 文件无效。</span><span class="sxs-lookup"><span data-stu-id="3ac9b-142">This field is not valid for FILESTREAM files.</span></span>  
  
 <span data-ttu-id="3ac9b-143">对于内存优化文件组中的文件，此字段应该是 **无限制**。</span><span class="sxs-lookup"><span data-stu-id="3ac9b-143">For files in memory-optimized filegroups, this field should be **Unlimited**.</span></span>  
  
 <span data-ttu-id="3ac9b-144">**路径**</span><span class="sxs-lookup"><span data-stu-id="3ac9b-144">**Path**</span></span>  
 <span data-ttu-id="3ac9b-145">显示所选文件的路径。</span><span class="sxs-lookup"><span data-stu-id="3ac9b-145">Displays the path of the selected file.</span></span> <span data-ttu-id="3ac9b-146">若要指定新文件的路径，请单击文件路径旁的编辑按钮，再导航到目标文件夹。</span><span class="sxs-lookup"><span data-stu-id="3ac9b-146">To specify a path for a new file, click the edit button next to the path for the file, and navigate to the destination folder.</span></span> <span data-ttu-id="3ac9b-147">您无法修改现有文件的路径。</span><span class="sxs-lookup"><span data-stu-id="3ac9b-147">You cannot modify the path of an existing file.</span></span>  
  
 <span data-ttu-id="3ac9b-148">对于 FILESTREAM 文件，该路径是一个文件夹。</span><span class="sxs-lookup"><span data-stu-id="3ac9b-148">For FILESTREAM files, the path is a folder.</span></span> <span data-ttu-id="3ac9b-149">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 将在此文件夹中创建基础文件。</span><span class="sxs-lookup"><span data-stu-id="3ac9b-149">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] will create the underlying files in this folder.</span></span>  
  
 <span data-ttu-id="3ac9b-150">**文件名**</span><span class="sxs-lookup"><span data-stu-id="3ac9b-150">**File Name**</span></span>  
 <span data-ttu-id="3ac9b-151">显示文件的名称。</span><span class="sxs-lookup"><span data-stu-id="3ac9b-151">Displays the name of the file.</span></span>  
  
 <span data-ttu-id="3ac9b-152">此字段对于 FILESTREAM 文件（包括内存优化文件组中的文件）无效。</span><span class="sxs-lookup"><span data-stu-id="3ac9b-152">This field is not valid for FILESTREAM files, including files in memory-optimized filegroups.</span></span>  
  
 <span data-ttu-id="3ac9b-153">**添加**</span><span class="sxs-lookup"><span data-stu-id="3ac9b-153">**Add**</span></span>  
 <span data-ttu-id="3ac9b-154">将新文件添加到数据库。</span><span class="sxs-lookup"><span data-stu-id="3ac9b-154">Add a new file to the database.</span></span>  
  
 <span data-ttu-id="3ac9b-155">**删除**</span><span class="sxs-lookup"><span data-stu-id="3ac9b-155">**Remove**</span></span>  
 <span data-ttu-id="3ac9b-156">从数据库中删除所选文件。</span><span class="sxs-lookup"><span data-stu-id="3ac9b-156">Delete the selected file from the database.</span></span> <span data-ttu-id="3ac9b-157">除非文件为空，否则无法移除文件。</span><span class="sxs-lookup"><span data-stu-id="3ac9b-157">A file cannot be removed unless it is empty.</span></span> <span data-ttu-id="3ac9b-158">无法移除主数据文件和日志文件。</span><span class="sxs-lookup"><span data-stu-id="3ac9b-158">The primary data file and log file cannot be removed.</span></span>  
  
 <span data-ttu-id="3ac9b-159">有关文件的信息，请参阅 [Database Files and Filegroups](database-files-and-filegroups.md)。</span><span class="sxs-lookup"><span data-stu-id="3ac9b-159">For information about files, see [Database Files and Filegroups](database-files-and-filegroups.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ac9b-160">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3ac9b-160">See Also</span></span>  
 <span data-ttu-id="3ac9b-161">[ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3ac9b-161">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 [<span data-ttu-id="3ac9b-162">sys.databases (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="3ac9b-162">sys.databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
