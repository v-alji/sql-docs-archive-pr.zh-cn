---
title: 常规 (还原数据库 "对话框)  (Analysis Services 多维数据) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.restoredbdialog.f1
ms.assetid: 319e7ef5-c9c7-4e50-8690-02a90aed006f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 25a49e17227fc2ed6b7b18d2e0964cd8812cbdcb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590980"
---
# <a name="general-restore-database-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="c17b6-102">常规（“还原数据库”对话框）（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="c17b6-102">General (Restore Database Dialog Box) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="c17b6-103">在 **中，可以使用** “还原数据库” **对话框的** “常规” [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 页指定在还原 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库时使用的备份文件和常规设置。</span><span class="sxs-lookup"><span data-stu-id="c17b6-103">Use the **General** page of the **Restore Database** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to specify the backup file and general settings to use when restoring an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c17b6-104">对于每个备份文件，运行还原命令的用户必须对每个文件的指定备份位置具有读取权限。</span><span class="sxs-lookup"><span data-stu-id="c17b6-104">For each backup file, the user who runs the restore command must have permission to read from the backup location specified for each file.</span></span> <span data-ttu-id="c17b6-105">若要还原未在服务器上安装的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库，用户还必须是此 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例的服务器角色成员。</span><span class="sxs-lookup"><span data-stu-id="c17b6-105">To restore an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database that is not installed on the server, the user must also be a member of the server role for that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="c17b6-106">若要覆盖 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库，用户必须具有以下角色之一： [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例的服务器角色成员，或对要还原的数据库拥有完全控制（管理员）权限的数据库角色成员。</span><span class="sxs-lookup"><span data-stu-id="c17b6-106">To overwrite an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, the user must have one of the following roles: a member of the server role for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance, or a member of a database role with Full Control (Administrator) permissions on the database to be restored.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c17b6-107">还原现有数据库之后，还原了此数据库的用户可能会失去对还原后的数据库的访问权限。</span><span class="sxs-lookup"><span data-stu-id="c17b6-107">After restoring an existing database, the user who restored the database might lose access to the restored database.</span></span> <span data-ttu-id="c17b6-108">如果在执行备份时用户不是服务器角色成员或者不是拥有完全控制（管理员）权限的数据库角色成员，则会出现这种失去访问权限的情形。</span><span class="sxs-lookup"><span data-stu-id="c17b6-108">This loss of access can occur if, at the time that the backup was performed, the user was not a member of the server role or was not a member of the database role with Full Control (Administrator) permissions.</span></span>  
  
 <span data-ttu-id="c17b6-109">**通过“还原数据库”对话框显示“常规”页**</span><span class="sxs-lookup"><span data-stu-id="c17b6-109">**To display the General page in the Restore Database dialog box**</span></span>  
  
-   <span data-ttu-id="c17b6-110">在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中，右键单击 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例的“数据库”\*\*\*\* 文件夹，或“对象资源管理器”\*\*\*\* 中的数据库，单击“还原”\*\*\*\*，然后在“选择页”\*\*\*\* 下单击“常规”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c17b6-110">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], right-click either the **Databases** folder of an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance or a database in **Object Explorer**, click **Restore**, and then under **Select a page**, click **General**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c17b6-111">选项</span><span class="sxs-lookup"><span data-stu-id="c17b6-111">Options</span></span>  
 <span data-ttu-id="c17b6-112">**脚本**</span><span class="sxs-lookup"><span data-stu-id="c17b6-112">**Script**</span></span>  
 <span data-ttu-id="c17b6-113">创建还原脚本，该脚本基于在对话框中选定的选项。</span><span class="sxs-lookup"><span data-stu-id="c17b6-113">Creates a restore script that is based on the options selected in the dialog box.</span></span> <span data-ttu-id="c17b6-114">还原脚本是用 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 脚本语言 (ASSL) 编写的。</span><span class="sxs-lookup"><span data-stu-id="c17b6-114">The restore script is written in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Scripting Language (ASSL).</span></span>  
  
 <span data-ttu-id="c17b6-115">默认情况下，单击 **“脚本”** 图标会将还原脚本发送到新的查询窗口。</span><span class="sxs-lookup"><span data-stu-id="c17b6-115">Clicking the **Script** icon sends the restore script into a new query window, by default.</span></span>  
  
 <span data-ttu-id="c17b6-116">单击 **“脚本”** 箭头将显示一个菜单，您可以使用此菜单选择将还原脚本发送到的位置：</span><span class="sxs-lookup"><span data-stu-id="c17b6-116">Clicking the **Script** arrow displays a menu that allows you to choose where to send the restore script:</span></span>  
  
-   <span data-ttu-id="c17b6-117">发送到新查询窗口（默认值）。</span><span class="sxs-lookup"><span data-stu-id="c17b6-117">To a new query window (default).</span></span>  
  
-   <span data-ttu-id="c17b6-118">发送到文件。</span><span class="sxs-lookup"><span data-stu-id="c17b6-118">To a file.</span></span>  
  
-   <span data-ttu-id="c17b6-119">发送到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="c17b6-119">To the clipboard.</span></span>  
  
-   <span data-ttu-id="c17b6-120">发送到作业。</span><span class="sxs-lookup"><span data-stu-id="c17b6-120">To a job.</span></span>  
  
 <span data-ttu-id="c17b6-121">**还原数据库**</span><span class="sxs-lookup"><span data-stu-id="c17b6-121">**Restore database**</span></span>  
 <span data-ttu-id="c17b6-122">选择要还原的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="c17b6-122">Select the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database to restore.</span></span>  
  
 <span data-ttu-id="c17b6-123">**从备份文件**</span><span class="sxs-lookup"><span data-stu-id="c17b6-123">**From backup file**</span></span>  
 <span data-ttu-id="c17b6-124">选择从中还原所选 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库的备份文件。</span><span class="sxs-lookup"><span data-stu-id="c17b6-124">Select the backup file from which to restore the selected [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="c17b6-125">**“浏览”**</span><span class="sxs-lookup"><span data-stu-id="c17b6-125">**Browse**</span></span>  
 <span data-ttu-id="c17b6-126">单击可显示“定位数据库文件”\*\*\*\* 对话框，并选择要使用的备份文件的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="c17b6-126">Click to display the **Locate Database Files** dialog box and select the path and file name of the backup file to use.</span></span> <span data-ttu-id="c17b6-127">有关“定位数据库文件”\*\*\*\* 对话框的详细信息，请参阅[“定位数据库文件”对话框（Analysis Services - 多维数据）](locate-database-files-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="c17b6-127">For more information about the **Locate Database Files** dialog box, see [Locate Database Files Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](locate-database-files-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="c17b6-128">**允许覆盖数据库**</span><span class="sxs-lookup"><span data-stu-id="c17b6-128">**Allow database overwrite**</span></span>  
 <span data-ttu-id="c17b6-129">选择此选项允许 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 还原所选备份文件的内容来覆盖所选 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库中的现有对象。</span><span class="sxs-lookup"><span data-stu-id="c17b6-129">Select to allow [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] to restore the contents of the selected backup file over any existing objects in the selected [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="c17b6-130">**包括安全信息**</span><span class="sxs-lookup"><span data-stu-id="c17b6-130">**Include security information**</span></span>  
 <span data-ttu-id="c17b6-131">选择此选项可以将备份文件中存储的所有安全信息复制到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="c17b6-131">Select to copy any security information stored in the backup file to the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="c17b6-132">如果选择此选项，则可以从通过选择此选项启用的下拉列表中选择安全信息。</span><span class="sxs-lookup"><span data-stu-id="c17b6-132">If this option is selected, you can choose the amount of security information from the drop-down list enabled by selecting this option.</span></span> <span data-ttu-id="c17b6-133">提供了以下选项：</span><span class="sxs-lookup"><span data-stu-id="c17b6-133">The following options are available:</span></span>  
  
|<span data-ttu-id="c17b6-134">选项</span><span class="sxs-lookup"><span data-stu-id="c17b6-134">Option</span></span>|<span data-ttu-id="c17b6-135">说明</span><span class="sxs-lookup"><span data-stu-id="c17b6-135">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="c17b6-136">**全部复制**</span><span class="sxs-lookup"><span data-stu-id="c17b6-136">**Copy All**</span></span>|<span data-ttu-id="c17b6-137">还原备份文件中包含的数据库角色以及与这些角色关联的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="c17b6-137">Restores the database roles contained in the backup file, as well as the user accounts associated with the roles.</span></span>|  
|<span data-ttu-id="c17b6-138">**跳过成员身份**</span><span class="sxs-lookup"><span data-stu-id="c17b6-138">**Skip Membership**</span></span>|<span data-ttu-id="c17b6-139">还原备份文件中包含的数据库角色，但不还原与这些角色关联的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="c17b6-139">Restores the database roles contained in the backup file, but does not restore the user accounts associated with the roles.</span></span>|  
  
 <span data-ttu-id="c17b6-140">**密码**</span><span class="sxs-lookup"><span data-stu-id="c17b6-140">**Password**</span></span>  
 <span data-ttu-id="c17b6-141">如果对备份文件进行了加密，请键入用于加密备份文件的密码。</span><span class="sxs-lookup"><span data-stu-id="c17b6-141">If the backup file is encrypted, type the password used to encrypt the backup file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c17b6-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c17b6-142">See Also</span></span>  
 <span data-ttu-id="c17b6-143">["还原数据库" 对话框 &#40;Analysis Services 多维数据&#41;](restore-database-dialog-box-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="c17b6-143">[Restore Database Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](restore-database-dialog-box-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="c17b6-144">[分区 &#40;还原数据库 "对话框&#41; &#40;Analysis Services 多维数据&#41;](partitions-restore-database-dialog-box-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="c17b6-144">[Partitions &#40;Restore Database Dialog Box&#41; &#40;Analysis Services - Multidimensional Data&#41;](partitions-restore-database-dialog-box-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="c17b6-145">备份和还原 Analysis Services 数据库</span><span class="sxs-lookup"><span data-stu-id="c17b6-145">Backup and Restore of Analysis Services Databases</span></span>](multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  
