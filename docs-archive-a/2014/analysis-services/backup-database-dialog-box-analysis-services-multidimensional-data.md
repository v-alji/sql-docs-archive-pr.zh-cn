---
title: "\"备份数据库\" 对话框 (Analysis Services 多维数据) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.Backup.f1
ms.assetid: 7811ce7d-6c37-4189-bfa6-ef36fb4932db
author: minewiskan
ms.author: owend
ms.openlocfilehash: 48cf094353c53213864dae656af94ae791442105
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579352"
---
# <a name="backup-database-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="d99de-102">“备份数据库”对话框（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="d99de-102">Backup Database Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="d99de-103">可以使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中的\*\*\*\*“备份数据库”对话框，使用 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 备份文件 (.abf) 格式将 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库备份到备份文件中。</span><span class="sxs-lookup"><span data-stu-id="d99de-103">Use the **Backup Database** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to back up an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database to a backup file using the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Backup File (.abf) format.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d99de-104">对于每个备份文件，运行备份命令的用户必须对每个文件的指定备份位置拥有写入权限。</span><span class="sxs-lookup"><span data-stu-id="d99de-104">For each backup file, the user who runs the backup command must have permission to write to the backup location specified for each file.</span></span> <span data-ttu-id="d99de-105">此外，用户必须具有以下角色之一：针对 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例的服务器角色成员，或对要备份的数据库拥有完全控制（管理员）权限的数据库角色成员。</span><span class="sxs-lookup"><span data-stu-id="d99de-105">Also, the user must have one of the following roles: a member of a server role for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance, or a member of a database role with Full Control (Administrator) permissions on the database to be backed up.</span></span>  
  
 <span data-ttu-id="d99de-106">**显示“备份数据库”对话框**</span><span class="sxs-lookup"><span data-stu-id="d99de-106">**To display the Backup Database dialog box**</span></span>  
  
-   <span data-ttu-id="d99de-107">在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中，右键单击 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例的“数据库”文件夹或“对象资源管理器”中的数据库，然后单击“备份”。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="d99de-107">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], right-click either the **Databases** folder of an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance or a database in **Object Explorer**, and then click **Backup**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d99de-108">选项</span><span class="sxs-lookup"><span data-stu-id="d99de-108">Options</span></span>  
 <span data-ttu-id="d99de-109">**脚本**</span><span class="sxs-lookup"><span data-stu-id="d99de-109">**Script**</span></span>  
 <span data-ttu-id="d99de-110">创建备份脚本，该脚本基于在对话框中选定的选项。</span><span class="sxs-lookup"><span data-stu-id="d99de-110">Creates a backup script that is based on the options selected in the dialog box.</span></span> <span data-ttu-id="d99de-111">还原脚本是用 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 脚本语言 (ASSL) 编写的。</span><span class="sxs-lookup"><span data-stu-id="d99de-111">The restore script is written in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Scripting Language (ASSL).</span></span>  
  
 <span data-ttu-id="d99de-112">默认情况下，单击 **“脚本”** 图标会将备份脚本发送到新的查询窗口。</span><span class="sxs-lookup"><span data-stu-id="d99de-112">Clicking the **Script** icon sends the backup script into a new query window, by default.</span></span>  
  
 <span data-ttu-id="d99de-113">单击 **“脚本”** 箭头将显示一个菜单，您可以使用此菜单选择将备份脚本发送到的位置：</span><span class="sxs-lookup"><span data-stu-id="d99de-113">Clicking the **Script** arrow displays a menu that allows you to choose where to send the backup script:</span></span>  
  
-   <span data-ttu-id="d99de-114">发送到新查询窗口（默认值）。</span><span class="sxs-lookup"><span data-stu-id="d99de-114">To a new query window (default).</span></span>  
  
-   <span data-ttu-id="d99de-115">发送到文件。</span><span class="sxs-lookup"><span data-stu-id="d99de-115">To a file.</span></span>  
  
-   <span data-ttu-id="d99de-116">发送到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="d99de-116">To the clipboard.</span></span>  
  
-   <span data-ttu-id="d99de-117">发送到作业。</span><span class="sxs-lookup"><span data-stu-id="d99de-117">To a job.</span></span>  
  
 <span data-ttu-id="d99de-118">**Database**</span><span class="sxs-lookup"><span data-stu-id="d99de-118">**Database**</span></span>  
 <span data-ttu-id="d99de-119">显示当前所选 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="d99de-119">Displays the name of the currently selected [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="d99de-120">**“备份文件”**</span><span class="sxs-lookup"><span data-stu-id="d99de-120">**Backup file**</span></span>  
 <span data-ttu-id="d99de-121">键入要使用的备份文件的完整路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="d99de-121">Type the full path and file name of the backup file to use.</span></span>  
  
 <span data-ttu-id="d99de-122">**“浏览”**</span><span class="sxs-lookup"><span data-stu-id="d99de-122">**Browse**</span></span>  
 <span data-ttu-id="d99de-123">单击可显示“文件另存为”对话框，并选择要使用的备份文件的路径和文件名。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="d99de-123">Click to display the **Save File As** dialog box and select the path and file name of the backup file to use.</span></span> <span data-ttu-id="d99de-124">有关“文件另存为”\*\*\*\* 对话框的详细信息，请参阅[“文件另存为”对话框（Analysis Services - 多维数据）](save-file-as-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="d99de-124">For more information about the **Save File As** dialog box, see [Save File As Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](save-file-as-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="d99de-125">**允许覆盖文件**</span><span class="sxs-lookup"><span data-stu-id="d99de-125">**Allow file overwrite**</span></span>  
 <span data-ttu-id="d99de-126">选择此选项可覆盖现有备份文件或远程备份文件（如果存在）。</span><span class="sxs-lookup"><span data-stu-id="d99de-126">Select to overwrite an existing backup file or remote backup file, if one exists.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d99de-127"> 如果未选择此选项，并且 **“备份文件”** 中指定的备份文件或 **“远程备份文件”** 中指定的远程备份文件存在，则会出现错误。</span><span class="sxs-lookup"><span data-stu-id="d99de-127">If this option is not selected and the backup file specified in **Backup file** or a remote backup file specified in **Remote backup file** exists, an error occurs.</span></span>  
  
 <span data-ttu-id="d99de-128">**应用压缩**</span><span class="sxs-lookup"><span data-stu-id="d99de-128">**Apply compression**</span></span>  
 <span data-ttu-id="d99de-129">选择此选项可压缩备份文件和远程备份文件（如果指定）的内容。</span><span class="sxs-lookup"><span data-stu-id="d99de-129">Select to compress the contents of the backup file and, if specified, remote backup files.</span></span>  
  
 <span data-ttu-id="d99de-130">**加密备份文件**</span><span class="sxs-lookup"><span data-stu-id="d99de-130">**Encrypt backup file**</span></span>  
 <span data-ttu-id="d99de-131">选择此选项可使用“密码”中所提供密码加密备份文件。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="d99de-131">Select to encrypt the backup file using the password supplied in **Password**.</span></span>  
  
 <span data-ttu-id="d99de-132">**密码**</span><span class="sxs-lookup"><span data-stu-id="d99de-132">**Password**</span></span>  
 <span data-ttu-id="d99de-133">键入加密备份文件和远程备份文件（如果指定）时所使用的密码。</span><span class="sxs-lookup"><span data-stu-id="d99de-133">Type the password to use when encrypting the backup file and, if specified, remote backup files.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d99de-134"> 只有在选择 **“加密备份文件”** 时，才会启用此选项。</span><span class="sxs-lookup"><span data-stu-id="d99de-134">This option is enabled only if **Encrypt backup file** is selected.</span></span>  
  
 <span data-ttu-id="d99de-135">**确认密码**</span><span class="sxs-lookup"><span data-stu-id="d99de-135">**Confirm Password**</span></span>  
 <span data-ttu-id="d99de-136">键入在“密码”中所输入的密码，以确认备份文件和远程备份文件（如果指定）的密码。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="d99de-136">Type the password entered in **Password** to confirm the password for the backup file and, if specified, remote backup files.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d99de-137"> 只有在选择 **“加密备份文件”** 时，才会启用此选项。</span><span class="sxs-lookup"><span data-stu-id="d99de-137">This option is enabled only if **Encrypt backup file** is selected.</span></span>  
  
 <span data-ttu-id="d99de-138">**备份远程分区**</span><span class="sxs-lookup"><span data-stu-id="d99de-138">**Backup remote partition(s)**</span></span>  
 <span data-ttu-id="d99de-139">选择此选项可将远程分区的位置信息和数据包含在备份文件中。</span><span class="sxs-lookup"><span data-stu-id="d99de-139">Select to include location information and data for remote partitions in the backup file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d99de-140">只有当前所选 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库使用远程分区时，才会启用此选项。</span><span class="sxs-lookup"><span data-stu-id="d99de-140">This option is enabled only if the currently selected [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database uses remote partitions.</span></span>  
  
 <span data-ttu-id="d99de-141">**远程分区备份位置**</span><span class="sxs-lookup"><span data-stu-id="d99de-141">**Remote partition backup location**</span></span>  
 <span data-ttu-id="d99de-142">显示与所选数据库关联的远程分区的位置，以及用于备份远程分区的数据和元数据的远程备份文件。</span><span class="sxs-lookup"><span data-stu-id="d99de-142">Displays the location of remote partitions associated with the selected database, as well as the remote backup file used to back up the data and metadata for the remote partitions.</span></span> <span data-ttu-id="d99de-143">可用的列包括：</span><span class="sxs-lookup"><span data-stu-id="d99de-143">The following columns are available:</span></span>  
  
|<span data-ttu-id="d99de-144">列</span><span class="sxs-lookup"><span data-stu-id="d99de-144">Column</span></span>|<span data-ttu-id="d99de-145">说明</span><span class="sxs-lookup"><span data-stu-id="d99de-145">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="d99de-146">**Server**</span><span class="sxs-lookup"><span data-stu-id="d99de-146">**Server**</span></span>|<span data-ttu-id="d99de-147">显示管理远程分区的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="d99de-147">Displays the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance that manages the remote partitions.</span></span>|  
|<span data-ttu-id="d99de-148">**Database**</span><span class="sxs-lookup"><span data-stu-id="d99de-148">**Database**</span></span>|<span data-ttu-id="d99de-149">显示包含远程分区的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="d99de-149">Displays the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database that contains the remote partitions.</span></span>|  
|<span data-ttu-id="d99de-150">**分区列表**</span><span class="sxs-lookup"><span data-stu-id="d99de-150">**Partition List**</span></span>|<span data-ttu-id="d99de-151">显示 **“数据库”** 中显示的数据库所包含的远程分区列表。</span><span class="sxs-lookup"><span data-stu-id="d99de-151">Displays the list of remote partitions contained by the database displayed in **Database**.</span></span>|  
|<span data-ttu-id="d99de-152">**“远程备份文件”**</span><span class="sxs-lookup"><span data-stu-id="d99de-152">**Remote backup file**</span></span>|<span data-ttu-id="d99de-153">键入要使用的远程备份文件的完整路径和文件名，或单击省略号按钮 (**...**) 以显示“文件另存为”对话框，再选择要使用的远程备份文件的路径和文件名。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="d99de-153">Type the full path and file name of the remote backup file to use, or click the ellipsis button (**...**) to display the **Save File As** dialog box and select the path and file name of the remote backup file to use.</span></span> <span data-ttu-id="d99de-154">有关“文件另存为”\*\*\*\* 对话框的详细信息，请参阅[“文件另存为”对话框（Analysis Services - 多维数据）](save-file-as-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="d99de-154">For more information about the **Save File As** dialog box, see [Save File As Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](save-file-as-dialog-box-analysis-services-multidimensional-data.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d99de-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d99de-155">See Also</span></span>  
 <span data-ttu-id="d99de-156">[&#40;多维数据的 Analysis Services 设计器和对话框&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="d99de-156">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="d99de-157">备份和还原 Analysis Services 数据库</span><span class="sxs-lookup"><span data-stu-id="d99de-157">Backup and Restore of Analysis Services Databases</span></span>](multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  
