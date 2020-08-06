---
title: 删除包 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 85b7d512-0ea7-47f5-8937-b1af6592b5b5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5c7a61d8c65c1934eb72101bf91ac3b73be60f94
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694534"
---
# <a name="delete-packages"></a><span data-ttu-id="1f427-102">删除包</span><span class="sxs-lookup"><span data-stu-id="1f427-102">Delete Packages</span></span>
  <span data-ttu-id="1f427-103">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，可以删除已保存到文件系统的包。</span><span class="sxs-lookup"><span data-stu-id="1f427-103">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], you can delete packages saved to the file system.</span></span> <span data-ttu-id="1f427-104">如果删除某个包，则该包将被永久删除并且无法还原到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="1f427-104">If you delete a package, it is deleted permanently and it cannot be restored to an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1f427-105">如果要从 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目中删除包，但要在其他项目中使用这些包，则应使用“从项目中排除”选项，而不是“删除”选项   。</span><span class="sxs-lookup"><span data-stu-id="1f427-105">If you want to remove packages from an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, but use them in other projects, then you should use the **Exclude From Project** option instead of the **Delete** option.</span></span>  
  
### <a name="to-delete-a-package-in-business-intelligence"></a><span data-ttu-id="1f427-106">在 Business Intelligence 中删除包</span><span class="sxs-lookup"><span data-stu-id="1f427-106">To delete a package in Business Intelligence</span></span>  
  
1.  <span data-ttu-id="1f427-107">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开包含要删除的包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="1f427-107">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want to delete.</span></span>  
  
2.  <span data-ttu-id="1f427-108">在解决方案资源管理器中，右键单击该包，然后单击“删除”  。</span><span class="sxs-lookup"><span data-stu-id="1f427-108">In Solution Explorer, right-click the package, and then click **Delete**.</span></span>  
  
3.  <span data-ttu-id="1f427-109">单击 **“确定”** 以确认删除，或单击 **“取消”** 以保留该包。</span><span class="sxs-lookup"><span data-stu-id="1f427-109">Click **OK** to confirm the deletion or click **Cancel** to keep the package.</span></span>  
  
  
