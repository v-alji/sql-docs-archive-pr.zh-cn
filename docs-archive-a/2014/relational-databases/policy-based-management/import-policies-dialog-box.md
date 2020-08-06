---
title: “导入策略”对话框 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.dmf.importpolicy.f1
ms.assetid: 78ab5f6e-2f13-4788-937e-8892ef4e2345
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2601c21ea08d00bf77e9b97a5186f2d6d1200a10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578175"
---
# <a name="import-policies-dialog-box"></a><span data-ttu-id="70ca2-102">“导入策略”对话框</span><span class="sxs-lookup"><span data-stu-id="70ca2-102">Import Policies Dialog Box</span></span>
  <span data-ttu-id="70ca2-103">使用此对话框可以将保存为 XML 文件的一个或多个策略（及其引用的条件）导入当前 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="70ca2-103">Use this dialog box to import one or more policies (and their referenced condition) that are saved as XML files, into the current [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] instance.</span></span>  
  
## <a name="options"></a><span data-ttu-id="70ca2-104">选项</span><span class="sxs-lookup"><span data-stu-id="70ca2-104">Options</span></span>  
 <span data-ttu-id="70ca2-105">**要导入的文件**</span><span class="sxs-lookup"><span data-stu-id="70ca2-105">**Files to import**</span></span>  
 <span data-ttu-id="70ca2-106">若要从 XML 文件导入策略，请键入该文件的路径和名称或者使用“浏览”( **...** ) 按钮。</span><span class="sxs-lookup"><span data-stu-id="70ca2-106">To import a policy from an XML file, type the path and name of the file or use the Browse (**...**) button.</span></span>  
  
 <span data-ttu-id="70ca2-107">**用导入的项替换重复项**</span><span class="sxs-lookup"><span data-stu-id="70ca2-107">**Replace duplicates with items imported**</span></span>  
 <span data-ttu-id="70ca2-108">如果选择此选项，当相同名称的任何现有策略或条件在此 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例上已存在时，则会覆盖这些内容。</span><span class="sxs-lookup"><span data-stu-id="70ca2-108">Select to overwrite any existing policy or condition of the same name if it already exists on this [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance.</span></span> <span data-ttu-id="70ca2-109">无法覆盖具有依赖策略的条件，除非也覆盖该依赖策略。</span><span class="sxs-lookup"><span data-stu-id="70ca2-109">A condition with a dependent policy cannot be overwritten unless the dependent policy is also being overwritten.</span></span> <span data-ttu-id="70ca2-110">如果未选择此选项，使用相同条件表达式的现有条件不会导致错误。</span><span class="sxs-lookup"><span data-stu-id="70ca2-110">If this option is not selected, an existing condition that is using the same condition expression will not cause an error.</span></span>  
  
 <span data-ttu-id="70ca2-111">**策略状态**</span><span class="sxs-lookup"><span data-stu-id="70ca2-111">**Policy state**</span></span>  
 <span data-ttu-id="70ca2-112">为导入的策略选择所需的状态：</span><span class="sxs-lookup"><span data-stu-id="70ca2-112">Select the state that you want for the imported policy:</span></span>  
  
-   <span data-ttu-id="70ca2-113">**保留导入时的策略状态**</span><span class="sxs-lookup"><span data-stu-id="70ca2-113">**Preserve policy state on import**</span></span>  
  
-   <span data-ttu-id="70ca2-114">**启用关于导入的所有策略**</span><span class="sxs-lookup"><span data-stu-id="70ca2-114">**Enable all policies on import**</span></span>  
  
-   <span data-ttu-id="70ca2-115">**禁用关于导入的所有策略**</span><span class="sxs-lookup"><span data-stu-id="70ca2-115">**Disable all policies on import**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70ca2-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="70ca2-116">See Also</span></span>  
 <span data-ttu-id="70ca2-117">[使用基于策略的管理来管理服务器](administer-servers-by-using-policy-based-management.md) </span><span class="sxs-lookup"><span data-stu-id="70ca2-117">[Administer Servers by Using Policy-Based Management](administer-servers-by-using-policy-based-management.md) </span></span>  
 <span data-ttu-id="70ca2-118">[导入基于策略的管理策略](import-a-policy-based-management-policy.md) </span><span class="sxs-lookup"><span data-stu-id="70ca2-118">[Import a Policy-Based Management Policy](import-a-policy-based-management-policy.md) </span></span>  
 [<span data-ttu-id="70ca2-119">导出基于策略的管理策略</span><span class="sxs-lookup"><span data-stu-id="70ca2-119">Export a Policy-Based Management Policy</span></span>](export-a-policy-based-management-policy.md)  
  
  
