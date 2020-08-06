---
title: 选择备份设备 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.selectbackupdevice.f1
ms.assetid: 7887c9fd-15ce-4cc8-b069-845c1d09088c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8a848f9188eec0ebb09931bca460b0389b9570ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691752"
---
# <a name="select-backup-device"></a><span data-ttu-id="48c93-102">选择备份设备</span><span class="sxs-lookup"><span data-stu-id="48c93-102">Select Backup Device</span></span>
  <span data-ttu-id="48c93-103">使用 **“选择备份设备”** 对话框可以选择还原操作使用的逻辑备份设备。</span><span class="sxs-lookup"><span data-stu-id="48c93-103">Use the **Select Backup Device** dialog box to select a logical backup device for the restore operation.</span></span>  
  
 <span data-ttu-id="48c93-104">逻辑备份设备是与物理设备对应的用户定义的逻辑设备，它是操作系统提供的磁带机或磁盘驱动器。</span><span class="sxs-lookup"><span data-stu-id="48c93-104">A logical backup device is a user-defined logical device that corresponds to a physical device, either a tape drive or a disk drive, that is provided by the operating system.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="48c93-105">如果备份使用多个备份设备，这些设备必须与单一类型的设备相对应。</span><span class="sxs-lookup"><span data-stu-id="48c93-105">If a backup uses multiple backup devices, they all must correspond to a single type of device.</span></span>  
  
 <span data-ttu-id="48c93-106">**使用 SQL Server Management Studio 查看备份设备的内容**</span><span class="sxs-lookup"><span data-stu-id="48c93-106">**To use SQL Server Management Studio to view the contents of a backup device**</span></span>  
  
-   [<span data-ttu-id="48c93-107">查看备份磁带或文件的内容 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="48c93-107">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [<span data-ttu-id="48c93-108">查看逻辑备份设备的属性和内容 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="48c93-108">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
## <a name="options"></a><span data-ttu-id="48c93-109">选项</span><span class="sxs-lookup"><span data-stu-id="48c93-109">Options</span></span>  
 <span data-ttu-id="48c93-110">**备份设备**</span><span class="sxs-lookup"><span data-stu-id="48c93-110">**Backup device**</span></span>  
 <span data-ttu-id="48c93-111">在该列表框中，选择要从中进行还原的逻辑备份设备的名称。</span><span class="sxs-lookup"><span data-stu-id="48c93-111">In the list box, select the name of a logical backup device from which you want to restore.</span></span>  
  
 <span data-ttu-id="48c93-112">有关如何查看备份设备内容的信息，请参阅 [查看逻辑备份设备的属性和内容 (SQL Server)](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="48c93-112">For information about how to view the contents of a backup device, see [View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48c93-113">备注</span><span class="sxs-lookup"><span data-stu-id="48c93-113">Remarks</span></span>  
 <span data-ttu-id="48c93-114">如果您在列表中看不到包含所查找备份的逻辑备份设备，则备份可能已直接写入一个或多个文件或磁带机中。</span><span class="sxs-lookup"><span data-stu-id="48c93-114">If you do not see a logical backup device that contains the backup you are seeking on the list, the backup might have been written directly to one or more files or tape drives.</span></span> <span data-ttu-id="48c93-115">在此情况下，请取消 **“选择备份设备”** 对话框；并在 **“指定备份”** 对话框中的 **“备份介质”** 列表框中选择 **“文件”** 或 **“磁带”** 。</span><span class="sxs-lookup"><span data-stu-id="48c93-115">If this is the case, cancel the **Select Backup Device** dialog box; and in the **Specify Backup** dialog box, select **File** or **Tape** in the **Backup media** list box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48c93-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="48c93-116">See Also</span></span>  
 [<span data-ttu-id="48c93-117">备份设备 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="48c93-117">Backup Devices &#40;SQL Server&#41;</span></span>](backup-devices-sql-server.md)  
  
  
