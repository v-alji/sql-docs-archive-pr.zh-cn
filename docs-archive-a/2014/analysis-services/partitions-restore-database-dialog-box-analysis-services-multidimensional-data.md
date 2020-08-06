---
title: 分区 (还原数据库 "对话框)  (Analysis Services 多维数据) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.restoredbdialog.partitions.f1
ms.assetid: 1ad4dde5-4651-4069-875c-7ab73cd8b4f4
author: minewiskan
ms.author: owend
ms.openlocfilehash: b54ac204cd09651a933f1c53c7780fc96ae1bfb6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87589923"
---
# <a name="partitions-restore-database-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="e40c7-102">分区（“还原数据库”对话框）（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="e40c7-102">Partitions (Restore Database Dialog Box) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="e40c7-103">可以使用 **中的** “还原数据库” **对话框上的** “分区” [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 页，指定还原本地分区的位置、是否还原远程分区以及在还原远程分区时使用的远程备份文件。</span><span class="sxs-lookup"><span data-stu-id="e40c7-103">Use the **Partitions** page of the **Restore Database** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to specify the location to restore local partitions, and to specify whether to restore remote partitions and the remote backup files to use when restoring remote partitions.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e40c7-104">对于每个备份文件，运行还原命令的用户必须对每个文件的指定备份位置具有读取权限。</span><span class="sxs-lookup"><span data-stu-id="e40c7-104">For each backup file, the user who runs the restore command must have permission to read from the backup location specified for each file.</span></span> <span data-ttu-id="e40c7-105">若要还原未在服务器上安装的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库，用户还必须是此 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例的服务器角色成员。</span><span class="sxs-lookup"><span data-stu-id="e40c7-105">To restore an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database that is not installed on the server, the user must also be a member of the server role for that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="e40c7-106">若要覆盖 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库，用户必须具有以下角色之一： [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例的服务器角色成员，或对要还原的数据库拥有完全控制（管理员）权限的数据库角色成员。</span><span class="sxs-lookup"><span data-stu-id="e40c7-106">To overwrite an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, the user must have one of the following roles: a member of the server role for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance, or a member of a database role with Full Control (Administrator) permissions on the database to be restored.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e40c7-107">还原现有数据库之后，还原了此数据库的用户可能会失去对还原后的数据库的访问权限。</span><span class="sxs-lookup"><span data-stu-id="e40c7-107">After restoring an existing database, the user who restored the database might lose access to the restored database.</span></span> <span data-ttu-id="e40c7-108">如果在执行备份时用户不是服务器角色成员或者不是拥有完全控制（管理员）权限的数据库角色成员，则会出现这种失去访问权限的情形。</span><span class="sxs-lookup"><span data-stu-id="e40c7-108">This loss of access can occur if, at the time that the backup was performed, the user was not a member of the server role or was not a member of the database role with Full Control (Administrator) permissions.</span></span>  
  
 <span data-ttu-id="e40c7-109">**显示 "还原数据库" 对话框中的 "分区" 页**</span><span class="sxs-lookup"><span data-stu-id="e40c7-109">**To display the Partitions page in the Restore Database dialog box**</span></span>  
  
-   <span data-ttu-id="e40c7-110">在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中，右键单击 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例的“数据库”\*\*\*\* 文件夹或**对象资源管理器**中的数据库，单击“还原”\*\*\*\*，然后在“选择页”\*\*\*\* 下单击“分区”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e40c7-110">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], right-click either the **Databases** folder of an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance or a database in **Object Explorer**, click **Restore**, and then under **Select a page**, click **Partitions**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e40c7-111">选项</span><span class="sxs-lookup"><span data-stu-id="e40c7-111">Options</span></span>  
 <span data-ttu-id="e40c7-112">**脚本**</span><span class="sxs-lookup"><span data-stu-id="e40c7-112">**Script**</span></span>  
 <span data-ttu-id="e40c7-113">创建还原脚本，该脚本基于在对话框中选定的选项。</span><span class="sxs-lookup"><span data-stu-id="e40c7-113">Creates a restore script that is based on the options selected in the dialog box.</span></span> <span data-ttu-id="e40c7-114">还原脚本是用 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 脚本语言 (ASSL) 编写的。</span><span class="sxs-lookup"><span data-stu-id="e40c7-114">The restore script is written in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Scripting Language (ASSL).</span></span>  
  
 <span data-ttu-id="e40c7-115">默认情况下，单击 **“脚本”** 图标会将还原脚本发送到新的查询窗口。</span><span class="sxs-lookup"><span data-stu-id="e40c7-115">Clicking the **Script** icon sends the restore script into a new query window, by default.</span></span>  
  
 <span data-ttu-id="e40c7-116">单击 **“脚本”** 箭头将显示一个菜单，您可以使用此菜单选择将还原脚本发送到的位置：</span><span class="sxs-lookup"><span data-stu-id="e40c7-116">Clicking the **Script** arrow displays a menu that allows you to choose where to send the restore script:</span></span>  
  
-   <span data-ttu-id="e40c7-117">发送到新查询窗口（默认值）。</span><span class="sxs-lookup"><span data-stu-id="e40c7-117">To a new query window (default).</span></span>  
  
-   <span data-ttu-id="e40c7-118">发送到文件。</span><span class="sxs-lookup"><span data-stu-id="e40c7-118">To a file.</span></span>  
  
-   <span data-ttu-id="e40c7-119">发送到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="e40c7-119">To the clipboard.</span></span>  
  
-   <span data-ttu-id="e40c7-120">发送到作业。</span><span class="sxs-lookup"><span data-stu-id="e40c7-120">To a job.</span></span>  
  
 <span data-ttu-id="e40c7-121">**还原到原位置**</span><span class="sxs-lookup"><span data-stu-id="e40c7-121">**Restore to original locations**</span></span>  
 <span data-ttu-id="e40c7-122">选择此选项可以将备份文件中包含的本地分区还原到其原位置。</span><span class="sxs-lookup"><span data-stu-id="e40c7-122">Select to restore local partitions contained in the backup file to their original locations.</span></span>  
  
 <span data-ttu-id="e40c7-123">**选择其他位置**</span><span class="sxs-lookup"><span data-stu-id="e40c7-123">**Select different locations**</span></span>  
 <span data-ttu-id="e40c7-124">选择此选项可以指定要还原本地分区的其他位置。</span><span class="sxs-lookup"><span data-stu-id="e40c7-124">Select to specify different locations in which to restore local partitions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e40c7-125">只有在多维数据集中为本地分区指定了默认位置之外的位置时，才可以更改本地分区的还原文件夹。</span><span class="sxs-lookup"><span data-stu-id="e40c7-125">You can only change the restoration folder of a local partition if a location other than the default location was specified for that partition in the cube.</span></span>  
  
 <span data-ttu-id="e40c7-126">下面的网格（选择此选项后启用）用于指定每个本地分区的还原文件夹：</span><span class="sxs-lookup"><span data-stu-id="e40c7-126">The following grid, enabled when this option is selected, is used to specify a restoration folder for each local partition:</span></span>  
  
|<span data-ttu-id="e40c7-127">列</span><span class="sxs-lookup"><span data-stu-id="e40c7-127">Column</span></span>|<span data-ttu-id="e40c7-128">说明</span><span class="sxs-lookup"><span data-stu-id="e40c7-128">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="e40c7-129">**Cube**</span><span class="sxs-lookup"><span data-stu-id="e40c7-129">**Cube**</span></span>|<span data-ttu-id="e40c7-130">显示包含本地分区的多维数据集的名称。</span><span class="sxs-lookup"><span data-stu-id="e40c7-130">Displays the name of the cube that contains the local partition.</span></span>|  
|<span data-ttu-id="e40c7-131">**MeasureGroup**</span><span class="sxs-lookup"><span data-stu-id="e40c7-131">**MeasureGroup**</span></span>|<span data-ttu-id="e40c7-132">显示包含本地分区的度量值组的名称。</span><span class="sxs-lookup"><span data-stu-id="e40c7-132">Displays the name of the measure group that contains the local partition.</span></span>|  
|<span data-ttu-id="e40c7-133">分区</span><span class="sxs-lookup"><span data-stu-id="e40c7-133">**Partition**</span></span>|<span data-ttu-id="e40c7-134">显示本地分区的名称。</span><span class="sxs-lookup"><span data-stu-id="e40c7-134">Displays the name of the local partition.</span></span>|  
|<span data-ttu-id="e40c7-135">**大小(MB)**</span><span class="sxs-lookup"><span data-stu-id="e40c7-135">**Size (MB)**</span></span>|<span data-ttu-id="e40c7-136">显示本地分区的大小 (MB)。</span><span class="sxs-lookup"><span data-stu-id="e40c7-136">Displays the size, in megabytes, of the local partition.</span></span>|  
|<span data-ttu-id="e40c7-137">**原始文件夹**</span><span class="sxs-lookup"><span data-stu-id="e40c7-137">**Original Folder**</span></span>|<span data-ttu-id="e40c7-138">显示存储本地分区的原始文件夹的名称。</span><span class="sxs-lookup"><span data-stu-id="e40c7-138">Displays the name of the original folder in which the local partition was stored.</span></span>|  
|<span data-ttu-id="e40c7-139">**还原文件夹**</span><span class="sxs-lookup"><span data-stu-id="e40c7-139">**Restoration Folder**</span></span>|<span data-ttu-id="e40c7-140">键入本地分区的还原文件夹的名称，或单击省略号按钮 (**...**) 以显示“查找远程文件夹”\*\*\*\* 对话框，再选择要使用的文件夹的路径。</span><span class="sxs-lookup"><span data-stu-id="e40c7-140">Type the name of the restoration folder for the local partition, or click the ellipsis button (**...**) to display the **Browse for Remote Folder** dialog box and select the path of the folder to use.</span></span> <span data-ttu-id="e40c7-141">有关“查找远程文件夹”\*\*\*\* 对话框的详细信息，请参阅[“查找远程文件夹”对话框（Analysis Services - 多维数据）](browse-for-remote-folder-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="e40c7-141">For more information about the **Browse for Remote Folder** dialog box, see [Browse for Remote Folder Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](browse-for-remote-folder-dialog-box-analysis-services-multidimensional-data.md).</span></span>|  
  
 <span data-ttu-id="e40c7-142">**还原远程分区**</span><span class="sxs-lookup"><span data-stu-id="e40c7-142">**Restore remote partitions**</span></span>  
 <span data-ttu-id="e40c7-143">选择此选项可以还原在远程备份文件中存储的远程分区。</span><span class="sxs-lookup"><span data-stu-id="e40c7-143">Select to restore remote partitions stored in remote backup files.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e40c7-144">只有备份文件中包含对远程分区的引用时，才会启用此选项。</span><span class="sxs-lookup"><span data-stu-id="e40c7-144">This option is enabled only if the backup file contains references to remote partitions.</span></span>  
  
 <span data-ttu-id="e40c7-145">下面的网格（选择此选项后启用）用于指定每个本地分区的还原文件夹：</span><span class="sxs-lookup"><span data-stu-id="e40c7-145">The following grid, enabled when this option is selected, is used to specify a restoration folder for each local partition:</span></span>  
  
|<span data-ttu-id="e40c7-146">列</span><span class="sxs-lookup"><span data-stu-id="e40c7-146">Column</span></span>|<span data-ttu-id="e40c7-147">说明</span><span class="sxs-lookup"><span data-stu-id="e40c7-147">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="e40c7-148">**Server**</span><span class="sxs-lookup"><span data-stu-id="e40c7-148">**Server**</span></span>|<span data-ttu-id="e40c7-149">显示管理远程分区的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例的名称。</span><span class="sxs-lookup"><span data-stu-id="e40c7-149">Displays the name of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance that manages the remote partition.</span></span>|  
|<span data-ttu-id="e40c7-150">**数据源**</span><span class="sxs-lookup"><span data-stu-id="e40c7-150">**Data Source**</span></span>|<span data-ttu-id="e40c7-151">显示备份文件中数据源的名称，该数据源代表包含远程分区的数据库。</span><span class="sxs-lookup"><span data-stu-id="e40c7-151">Displays the name of the data source in the backup file that represents the database that contains the remote partition.</span></span>|  
|<span data-ttu-id="e40c7-152">**备份文件**</span><span class="sxs-lookup"><span data-stu-id="e40c7-152">**Backup File**</span></span>|<span data-ttu-id="e40c7-153">键入要使用的远程备份文件的完整路径和文件名，或单击省略号按钮 (**...**) 以显示“定位数据库文件”\*\*\*\* 对话框，再选择要使用的远程备份文件的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="e40c7-153">Type the full path and file name of the remote backup file to use, or click the ellipsis button (**...**) to display the **Locate Database Files** dialog box and select the path and file name of the remote backup file to use.</span></span> <span data-ttu-id="e40c7-154">有关“定位数据库文件”\*\*\*\* 对话框的详细信息，请参阅[“定位数据库文件”对话框（Analysis Services - 多维数据）](locate-database-files-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="e40c7-154">For more information about the **Locate Database Files** dialog box, see [Locate Database Files Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](locate-database-files-dialog-box-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="e40c7-155">**...**</span><span class="sxs-lookup"><span data-stu-id="e40c7-155">**...**</span></span>|<span data-ttu-id="e40c7-156">单击此按钮可以显示“远程分区 - 高级设置”\*\*\*\* 对话框，以便修改用于还原远程分区的高级选项，例如数据源的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="e40c7-156">Click to display the **Remote Partitions - Advanced Settings** dialog box and modify advanced options, such as the connection string for the data source, for restoring the remote partition.</span></span> <span data-ttu-id="e40c7-157">有关“远程分区 - 高级设置”\*\*\*\* 对话框的详细信息，请参阅[对话框（Analysis Services - 多维数据）](remote-partitions-advanced-settings-dialog-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="e40c7-157">For more information about the **Remote Partitions - Advanced Settings** dialog box, see [Remote Partitions - Advanced Settings Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](remote-partitions-advanced-settings-dialog-analysis-services-multidimensional-data.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e40c7-158">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e40c7-158">See Also</span></span>  
 <span data-ttu-id="e40c7-159">["还原数据库" 对话框 &#40;Analysis Services 多维数据&#41;](restore-database-dialog-box-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="e40c7-159">[Restore Database Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](restore-database-dialog-box-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="e40c7-160">[常规 &#40;还原数据库 "对话框&#41; &#40;Analysis Services 多维数据&#41;](general-restore-database-dialog-box-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="e40c7-160">[General &#40;Restore Database Dialog Box&#41; &#40;Analysis Services - Multidimensional Data&#41;](general-restore-database-dialog-box-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="e40c7-161">备份和还原 Analysis Services 数据库</span><span class="sxs-lookup"><span data-stu-id="e40c7-161">Backup and Restore of Analysis Services Databases</span></span>](multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  
