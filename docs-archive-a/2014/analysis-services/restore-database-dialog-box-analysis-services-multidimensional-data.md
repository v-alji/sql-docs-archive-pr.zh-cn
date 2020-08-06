---
title: "\"还原数据库\" 对话框 (Analysis Services 多维数据) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.Restore.f1
ms.assetid: a3990d47-55e2-424e-8eac-87edc937e806
author: minewiskan
ms.author: owend
ms.openlocfilehash: f45a41eb10e81e1cfe1100045cc4d00353cb11fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694601"
---
# <a name="restore-database-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="4ec01-102">“还原数据库”对话框（Analysis Services - 多维数据）</span><span class="sxs-lookup"><span data-stu-id="4ec01-102">Restore Database Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="4ec01-103">可使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中的“还原数据库”\*\*\*\* 对话框，以 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 备份文件 (.abf) 格式从备份文件中还原 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库。</span><span class="sxs-lookup"><span data-stu-id="4ec01-103">Use the **Restore Database** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to restore an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database from a backup file using the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Backup File (.abf) format.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4ec01-104">对于每个备份文件，运行还原命令的用户必须对每个文件的指定备份位置具有读取权限。</span><span class="sxs-lookup"><span data-stu-id="4ec01-104">For each backup file, the user who runs the restore command must have permission to read from the backup location specified for each file.</span></span> <span data-ttu-id="4ec01-105">若要还原未在服务器上安装的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库，用户还必须是此 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例的服务器角色成员。</span><span class="sxs-lookup"><span data-stu-id="4ec01-105">To restore an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database that is not installed on the server, the user must also be a member of the server role for that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="4ec01-106">若要覆盖 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 数据库，用户必须具有以下角色之一： [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例的服务器角色成员，或对要还原的数据库拥有完全控制（管理员）权限的数据库角色成员。</span><span class="sxs-lookup"><span data-stu-id="4ec01-106">To overwrite an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, the user must have one of the following roles: a member of the server role for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance, or a member of a database role with Full Control (Administrator) permissions on the database to be restored.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4ec01-107">还原现有数据库之后，还原了此数据库的用户可能会失去对还原后的数据库的访问权限。</span><span class="sxs-lookup"><span data-stu-id="4ec01-107">After restoring an existing database, the user who restored the database might lose access to the restored database.</span></span> <span data-ttu-id="4ec01-108">如果在执行备份时用户不是服务器角色成员或者不是拥有完全控制（管理员）权限的数据库角色成员，则会出现这种失去访问权限的情形。</span><span class="sxs-lookup"><span data-stu-id="4ec01-108">This loss of access can occur if, at the time that the backup was performed, the user was not a member of the server role or was not a member of the database role with Full Control (Administrator) permissions.</span></span>  
  
 <span data-ttu-id="4ec01-109">**显示“还原数据库”对话框**</span><span class="sxs-lookup"><span data-stu-id="4ec01-109">**To display the Restore Database dialog box**</span></span>  
  
-   <span data-ttu-id="4ec01-110">在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中，右键单击 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例的“数据库”\*\*\*\* 文件夹或“对象资源管理器”\*\*\*\* 中的数据库，然后单击“还原”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4ec01-110">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], right-click either the **Databases** folder of an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance or a database in **Object Explorer**, and then click **Restore**.</span></span>  
  
 <span data-ttu-id="4ec01-111">**“还原数据库”** 对话框包含以下页。</span><span class="sxs-lookup"><span data-stu-id="4ec01-111">The **Restore Database** dialog box contains the following pages.</span></span>  
  
## <a name="pages"></a><span data-ttu-id="4ec01-112">页数</span><span class="sxs-lookup"><span data-stu-id="4ec01-112">Pages</span></span>  
 <span data-ttu-id="4ec01-113">**常规**</span><span class="sxs-lookup"><span data-stu-id="4ec01-113">**General**</span></span>  
 <span data-ttu-id="4ec01-114">使用此页可以选择要还原的数据库、从中还原数据库的备份文件以及还原数据库时使用的常规选项和密码。</span><span class="sxs-lookup"><span data-stu-id="4ec01-114">Use this page to select the database to restore, the backup file from which to restore the database, as well as the general options and password to use while restoring the database.</span></span> <span data-ttu-id="4ec01-115">有关该页的详细信息，请参阅[常规（“还原数据库”对话框）（Analysis Services - 多维数据）](general-restore-database-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="4ec01-115">For more information about this page, see [General &#40;Restore Database Dialog Box&#41; &#40;Analysis Services - Multidimensional Data&#41;](general-restore-database-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="4ec01-116">**分区**</span><span class="sxs-lookup"><span data-stu-id="4ec01-116">**Partitions**</span></span>  
 <span data-ttu-id="4ec01-117">使用此页可以将本地分区还原到指定的位置，以及从远程备份文件还原远程分区。</span><span class="sxs-lookup"><span data-stu-id="4ec01-117">Use this page to restore local partitions to specified locations, and to restore remote partitions from remote backup files.</span></span> <span data-ttu-id="4ec01-118">有关该页的详细信息，请参阅[分区（“还原数据库”对话框）（Analysis Services - 多维数据）](partitions-restore-database-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="4ec01-118">For more information about this page, see [Partitions &#40;Restore Database Dialog Box&#41; &#40;Analysis Services - Multidimensional Data&#41;](partitions-restore-database-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ec01-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4ec01-119">See Also</span></span>  
 <span data-ttu-id="4ec01-120">[&#40;多维数据的 Analysis Services 设计器和对话框&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="4ec01-120">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="4ec01-121">备份和还原 Analysis Services 数据库</span><span class="sxs-lookup"><span data-stu-id="4ec01-121">Backup and Restore of Analysis Services Databases</span></span>](multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  
