---
title: Integration Services 参数 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Integration Services, parameters
ms.assetid: b1bb3ea3-8097-4e76-b9c2-78a0f46a23bc
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 76a5ebe7018fdc58f02a4d2454d40f172c752c4e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693201"
---
# <a name="integration-services-parameters"></a><span data-ttu-id="26e9f-102">Integration Services 参数</span><span class="sxs-lookup"><span data-stu-id="26e9f-102">Integration Services Parameters</span></span>
  <span data-ttu-id="26e9f-103">对于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ，你可以决定分析 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 计算机上的包或 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 文件系统中的包文件。</span><span class="sxs-lookup"><span data-stu-id="26e9f-103">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], you can decide to analyze [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages on the computer, or [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package files in the file system.</span></span> <span data-ttu-id="26e9f-104">如果分析文件系统中的文件，则需要提供包含 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包的文件夹的路径。</span><span class="sxs-lookup"><span data-stu-id="26e9f-104">If you analyze files in the file system, provide a path to the folder that contains the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span>  
  
## <a name="options"></a><span data-ttu-id="26e9f-105">选项</span><span class="sxs-lookup"><span data-stu-id="26e9f-105">Options</span></span>  
 <span data-ttu-id="26e9f-106">**分析计算机上的 SSIS 包**</span><span class="sxs-lookup"><span data-stu-id="26e9f-106">**Analyze SSIS packages on Computer**</span></span>  
 <span data-ttu-id="26e9f-107">选择此选项可分析计算机上 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="26e9f-107">Select this option to analyze [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages on the computer.</span></span> <span data-ttu-id="26e9f-108">默认情况下选择此选项。</span><span class="sxs-lookup"><span data-stu-id="26e9f-108">By default, this option is selected.</span></span>  
  
 <span data-ttu-id="26e9f-109">**分析 SSIS 包文件**</span><span class="sxs-lookup"><span data-stu-id="26e9f-109">**Analyze SSIS package files**</span></span>  
 <span data-ttu-id="26e9f-110">选择此选项可分析文件系统中的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包。</span><span class="sxs-lookup"><span data-stu-id="26e9f-110">Select this option to analyze [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages in the file system.</span></span>  
  
 <span data-ttu-id="26e9f-111">**SSIS 包的路径**</span><span class="sxs-lookup"><span data-stu-id="26e9f-111">**Path to SSIS packages**</span></span>  
 <span data-ttu-id="26e9f-112">找到包含 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包的 UNC 或本地路径。</span><span class="sxs-lookup"><span data-stu-id="26e9f-112">Locate a UNC or local path that holds your [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span> <span data-ttu-id="26e9f-113">不必包含文件名。</span><span class="sxs-lookup"><span data-stu-id="26e9f-113">You do not have to include file names.</span></span> <span data-ttu-id="26e9f-114">如果你输入的路径无法访问，则无法单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="26e9f-114">If the path you have entered cannot be accessed, you cannot click **Next**.</span></span> <span data-ttu-id="26e9f-115">默认情况下，此路径为空。</span><span class="sxs-lookup"><span data-stu-id="26e9f-115">By default, the path is blank.</span></span> <span data-ttu-id="26e9f-116">仅当选择 "**分析 SSIS 包文件**" 时，才会启用此字段。</span><span class="sxs-lookup"><span data-stu-id="26e9f-116">This field is enabled only when you select **Analyze SSIS package files**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26e9f-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="26e9f-117">See Also</span></span>  
 <span data-ttu-id="26e9f-118">[使用升级顾问](../../../2014/sql-server/install/working-with-upgrade-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="26e9f-118">[Working with Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md) </span></span>  
 [<span data-ttu-id="26e9f-119">升级顾问用户界面参考</span><span class="sxs-lookup"><span data-stu-id="26e9f-119">Upgrade Advisor User Interface Reference</span></span>](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)  
  
  
