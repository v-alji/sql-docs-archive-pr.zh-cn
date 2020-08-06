---
title: 编辑签入文件 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- modifying checked-in files
- checking in files
ms.assetid: 560cd19f-ab22-4273-b00c-149993a630e6
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: e2dbe1aad203dfdc83e438d5b7f4ed19c15038c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690053"
---
# <a name="edit-checked-in-files"></a><span data-ttu-id="9e860-102">编辑签入文件</span><span class="sxs-lookup"><span data-stu-id="9e860-102">Edit Checked-In Files</span></span>
  <span data-ttu-id="9e860-103">通常，必须先将源代码管理的文件签出，才能对其进行编辑。</span><span class="sxs-lookup"><span data-stu-id="9e860-103">You typically must check out source-controlled files before you can edit them.</span></span> <span data-ttu-id="9e860-104">不过，您可以对进行配置， [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 以便修改未签出的文件。执行此操作时，所做的更改将保留在内存中，直到你保存文件。</span><span class="sxs-lookup"><span data-stu-id="9e860-104">However, you can configure [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] so that you can modify files you have not checked out. When doing so, your changes are held in memory until you save the files.</span></span> <span data-ttu-id="9e860-105">然后会提示您从源代码管理中签出文件。</span><span class="sxs-lookup"><span data-stu-id="9e860-105">You will then be prompted to check out the file from source control.</span></span>  
  
 <span data-ttu-id="9e860-106">如果您在小组中工作，除非您的源代码管理提供程序同时支持本地版本和服务器版本签出，否则不推荐您使用允许编辑签入文件的功能。</span><span class="sxs-lookup"><span data-stu-id="9e860-106">If you work on a team, allowing checked-in files to be edited is not recommended unless your source control provider supports both local version and server version checkouts.</span></span> <span data-ttu-id="9e860-107">大多数提供程序都不支持本地版本签出。</span><span class="sxs-lookup"><span data-stu-id="9e860-107">Most providers do not support local version checkouts.</span></span> <span data-ttu-id="9e860-108">如果您的提供程序不支持本地版本签出并且您需要编辑签入文件，则必须手动合并内存中版本和服务器版本，才能签入文件。</span><span class="sxs-lookup"><span data-stu-id="9e860-108">If your provider does not support local version checkouts and you edit a checked-in file, you have to merge the in-memory and server versions manually before the file can be checked in.</span></span> <span data-ttu-id="9e860-109">在此情况下，不支持自动合并和由提供程序辅助的合并。</span><span class="sxs-lookup"><span data-stu-id="9e860-109">Automatic and provider-assisted merges are unsupported in this situation.</span></span>  
  
### <a name="to-edit-checked-in-files"></a><span data-ttu-id="9e860-110">编辑签入的文件</span><span class="sxs-lookup"><span data-stu-id="9e860-110">To edit checked-in files</span></span>  
  
1.  <span data-ttu-id="9e860-111">在“工具”  菜单上，单击“选项”  。</span><span class="sxs-lookup"><span data-stu-id="9e860-111">On the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="9e860-112">在 "**选项**" 对话框中，展开 "**源源代码**" 文件夹，然后单击 "**环境**"。</span><span class="sxs-lookup"><span data-stu-id="9e860-112">In the **Options** dialog box, expand the **Source Contro**l folder, and then click **Environment**.</span></span>  
  
3.  <span data-ttu-id="9e860-113">单击 "**允许编辑签入的项**"，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="9e860-113">Click **Allow checked-in items to be edited**, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e860-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9e860-114">See Also</span></span>  
 <span data-ttu-id="9e860-115">[管理签入](../../2014/database-engine/manage-checkins.md) </span><span class="sxs-lookup"><span data-stu-id="9e860-115">[Manage Checkins](../../2014/database-engine/manage-checkins.md) </span></span>  
 [<span data-ttu-id="9e860-116">管理签出</span><span class="sxs-lookup"><span data-stu-id="9e860-116">Manage Checkouts</span></span>](../../2014/database-engine/manage-checkouts.md)  
  
  
