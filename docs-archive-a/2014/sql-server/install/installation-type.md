---
title: 安装类型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 0420c555-7a3b-42b9-8651-0b4f5bcb0008
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: bab1b6c912dce64d1269fd79348a2b0b85f7f670
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688452"
---
# <a name="installation-type"></a><span data-ttu-id="3b068-102">安装类型</span><span class="sxs-lookup"><span data-stu-id="3b068-102">Installation Type</span></span>
  <span data-ttu-id="3b068-103">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装向导的“安装类型”页可以指定是安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的新实例还是向现有实例中添加功能。</span><span class="sxs-lookup"><span data-stu-id="3b068-103">Use the Installation Type page of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard to specify whether to install a new instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or add features to an existing instance.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3b068-104">选项</span><span class="sxs-lookup"><span data-stu-id="3b068-104">Options</span></span>  
 <span data-ttu-id="3b068-105">选择指示您所做选择的单选按钮：</span><span class="sxs-lookup"><span data-stu-id="3b068-105">Select the radio button that specifies your choice:</span></span>  
  
-   <span data-ttu-id="3b068-106">执行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的全新安装</span><span class="sxs-lookup"><span data-stu-id="3b068-106">Perform a new installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
  
-   <span data-ttu-id="3b068-107">向 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的现有实例中添加功能</span><span class="sxs-lookup"><span data-stu-id="3b068-107">Add features to an existing instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
  
     <span data-ttu-id="3b068-108">如果选择与向现有实例中添加功能相对应的选项，则使用下拉列表选择要更新的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="3b068-108">If you select the option to add features to an existing instance, use the drop-down list to select the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to update.</span></span>  
  
 <span data-ttu-id="3b068-109">只能向 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的已准备映像添加 SysPrep 支持的功能 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="3b068-109">You can only add the SysPrep supported features-[!INCLUDE[ssDE](../../includes/ssde-md.md)] and [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-to a prepared image of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="3b068-110">只有在已准备实例完成后，才能添加 SysPrep 不支持的其他功能。</span><span class="sxs-lookup"><span data-stu-id="3b068-110">Other features that are not supported by SysPrep can be added after the prepared instance is completed.</span></span>  
  
 <span data-ttu-id="3b068-111">**注意** 安装故障转移群集实例之后，不能再向其中添加功能。</span><span class="sxs-lookup"><span data-stu-id="3b068-111">**Note** You cannot add features to a failover cluster instance after it is installed.</span></span> <span data-ttu-id="3b068-112">若要向现有故障转移群集中添加 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能，则必须执行全新安装才能安装单独的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例。</span><span class="sxs-lookup"><span data-stu-id="3b068-112">To add [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features to an existing failover cluster, you must perform a new installation to install a separate instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
  
