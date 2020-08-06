---
title: CDC 实例部署脚本 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 8fa82822-ac99-48ef-a18d-f4f3a77105b4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6deea884168c2329e312eeaa2be16c28a955cca3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693437"
---
# <a name="cdc-instance-deployment-script"></a><span data-ttu-id="8b07e-102">CDC 实例部署脚本</span><span class="sxs-lookup"><span data-stu-id="8b07e-102">CDC Instance Deployment Script</span></span>
  <span data-ttu-id="8b07e-103">显示 CDC 实例部署脚本的“CDC 实例部署脚本”对话框。</span><span class="sxs-lookup"><span data-stu-id="8b07e-103">The CDC Instance Deployment Script dialog box that displays the CDC instance deployment script.</span></span> <span data-ttu-id="8b07e-104">此脚本可用于使用其在不同 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例上的所有项目重新创建 CDC 数据库。</span><span class="sxs-lookup"><span data-stu-id="8b07e-104">This script can be used to re-create the CDC database with all of its artifacts on a different [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="8b07e-105">在部署脚本完成后，您应该确保以下几个方面：</span><span class="sxs-lookup"><span data-stu-id="8b07e-105">At the completion of the deployment script, you should make sure of the following:</span></span>  
  
-   <span data-ttu-id="8b07e-106">部署脚本假定已通过使用 Oracle CDC 服务配置控制台或通过使用程序创建的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] “准备脚本” **为 Oracle CDC 准备了目标** 实例。</span><span class="sxs-lookup"><span data-stu-id="8b07e-106">The deployment script assumes that the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance was prepared for Oracle CDC, by using the Oracle CDC Service Configuration Console or by using **prepare script** that program creates.</span></span>  
  
-   <span data-ttu-id="8b07e-107">用于启用 CDC 数据库的脚本部分需要由 `sysadmin`运行。</span><span class="sxs-lookup"><span data-stu-id="8b07e-107">The part of the script that is used to enable the database for CDC needs to be run by a `sysadmin`.</span></span>  
  
-   <span data-ttu-id="8b07e-108">该脚本不会保留 Oracle 日志挖掘密码。</span><span class="sxs-lookup"><span data-stu-id="8b07e-108">The script does not preserve the Oracle log-mining password.</span></span> <span data-ttu-id="8b07e-109">该密码需要在脚本已运行并且 Oracle CDC 服务已启动后手动设置。</span><span class="sxs-lookup"><span data-stu-id="8b07e-109">This needs to be set manually after the script is run and the Oracle CDC Service is started.</span></span>  
  
 <span data-ttu-id="8b07e-110">在 **“CDC 实例部署脚本”** 对话框中选择以下选项。</span><span class="sxs-lookup"><span data-stu-id="8b07e-110">Select the following options in the **CDC Instance Deployment Script** dialog box.</span></span>  
  
 <span data-ttu-id="8b07e-111">**另存为**</span><span class="sxs-lookup"><span data-stu-id="8b07e-111">**Save As**</span></span>  
 <span data-ttu-id="8b07e-112">将脚本保存在一个文本文件中，您可以将该文本文件保存在所需的任何位置。</span><span class="sxs-lookup"><span data-stu-id="8b07e-112">Saves the script in a text file that you can save in any location you want.</span></span> <span data-ttu-id="8b07e-113">您可以将包含该脚本的文件复制到任何其他服务器以便在那里运行脚本。</span><span class="sxs-lookup"><span data-stu-id="8b07e-113">You can copy the file with the script to any other server to run it there.</span></span>  
  
 <span data-ttu-id="8b07e-114">**Copy**</span><span class="sxs-lookup"><span data-stu-id="8b07e-114">**Copy**</span></span>  
 <span data-ttu-id="8b07e-115">将脚本复制到剪贴板。</span><span class="sxs-lookup"><span data-stu-id="8b07e-115">Copies the script to the clipboard.</span></span> <span data-ttu-id="8b07e-116">然后，您可以将脚本粘贴到 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或任何文本编辑器，以便以后运行脚本。</span><span class="sxs-lookup"><span data-stu-id="8b07e-116">You can then paste the script into the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or any text editor to run the scripts later.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b07e-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8b07e-117">See Also</span></span>  
 [<span data-ttu-id="8b07e-118">为 CDC 准备 SQL Server</span><span class="sxs-lookup"><span data-stu-id="8b07e-118">Prepare SQL Server for CDC</span></span>](prepare-sql-server-for-cdc.md)  
  
  
