---
title: 群集磁盘选择 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- cluster disk selection
ms.assetid: 0d6b863d-5972-4a20-9990-64ee8016fea6
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0f53d6d3f623254d2b17996be7fd5b8235dca223
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586204"
---
# <a name="cluster-disk-selection"></a><span data-ttu-id="87676-102">群集磁盘选择</span><span class="sxs-lookup"><span data-stu-id="87676-102">Cluster Disk Selection</span></span>
  <span data-ttu-id="87676-103">使用 **安装向导的** “群集磁盘选择” [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 页为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 故障转移群集选择共享群集磁盘资源。</span><span class="sxs-lookup"><span data-stu-id="87676-103">Use the **Cluster Disk Selection** page of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard to select the shared cluster disk resource for your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster.</span></span> <span data-ttu-id="87676-104">群集磁盘用于存放 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据。</span><span class="sxs-lookup"><span data-stu-id="87676-104">The cluster disk is where the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data will be placed.</span></span>  
  
 <span data-ttu-id="87676-105">共享群集磁盘不是群集安装所必需的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="87676-105">A shared cluster disk is not a requirement for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../../includes/ssde-md.md)] cluster installations.</span></span> <span data-ttu-id="87676-106">SMB 文件服务器是一种受支持的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 故障转移群集安装存储，可以在完成安装之前使用 "**数据库引擎-数据目录**" 页指定。</span><span class="sxs-lookup"><span data-stu-id="87676-106">An SMB file server is a supported storage for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../../includes/ssde-md.md)] failover cluster installations, and can be specified by using the **Database Engine - Data Directories** page before completing the installation.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="87676-107">如果选择了要安装 Analysis Services，您必须指定共享群集磁盘。</span><span class="sxs-lookup"><span data-stu-id="87676-107">If you have selected Analysis Services to be installed, you must specify a shared cluster disk.</span></span>  
>   
>  <span data-ttu-id="87676-108">如果您计划在此 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 故障转移群集实例上启用 FILESTREAM，必须指定共享群集磁盘。</span><span class="sxs-lookup"><span data-stu-id="87676-108">If you plan to enable FILESTREAM on this [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster instance, you must specify a shared cluster disk.</span></span>  
  
## <a name="options"></a><span data-ttu-id="87676-109">选项</span><span class="sxs-lookup"><span data-stu-id="87676-109">Options</span></span>  
 <span data-ttu-id="87676-110">**共享磁盘**</span><span class="sxs-lookup"><span data-stu-id="87676-110">**Shared Disks**</span></span>  
 <span data-ttu-id="87676-111">从列表中选择一个磁盘。</span><span class="sxs-lookup"><span data-stu-id="87676-111">Select a single disk from the list.</span></span> <span data-ttu-id="87676-112">群集磁盘用于存放 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据。</span><span class="sxs-lookup"><span data-stu-id="87676-112">The cluster disk is where the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data will be placed.</span></span>  
  
 <span data-ttu-id="87676-113">只能指定一个磁盘。</span><span class="sxs-lookup"><span data-stu-id="87676-113">Only one disk can be specified.</span></span> <span data-ttu-id="87676-114">如果选择包含群集仲裁资源的组，将显示警告。</span><span class="sxs-lookup"><span data-stu-id="87676-114">If you select the group containing the cluster quorum resource, a warning will be displayed.</span></span> <span data-ttu-id="87676-115">建议不要安装到群集仲裁资源。</span><span class="sxs-lookup"><span data-stu-id="87676-115">We recommend that you do not install to the cluster quorum resource.</span></span>  
  
 <span data-ttu-id="87676-116">**可用共享磁盘**</span><span class="sxs-lookup"><span data-stu-id="87676-116">**Available Shared Disks**</span></span>  
 <span data-ttu-id="87676-117">显示可用磁盘的列表，对于列表中的每个磁盘，均会显示是否可用作共享磁盘以及磁盘资源的说明。</span><span class="sxs-lookup"><span data-stu-id="87676-117">Displays a list of available disks, whether each is qualified as a shared disk, and a description of each disk resource.</span></span>  
  
  
