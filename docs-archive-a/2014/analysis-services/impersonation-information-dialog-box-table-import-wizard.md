---
title: "\"模拟信息\" 对话框 (表导入向导) |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.impersonationinfo.f1
ms.assetid: bee7eee5-0650-41f1-a372-5076ae97a58c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5300f8b6106a7f29f51018b4e039c2a8c28aa729
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687328"
---
# <a name="impersonation-information-dialog-box-table-import-wizard"></a><span data-ttu-id="90031-102">“模拟信息”对话框（表导入向导）</span><span class="sxs-lookup"><span data-stu-id="90031-102">Impersonation Information Dialog Box (Table Import Wizard)</span></span>
  <span data-ttu-id="90031-103">使用 **“模拟信息”** 页可以指定 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 将用于连接到数据源的凭据。</span><span class="sxs-lookup"><span data-stu-id="90031-103">Use the **Impersonation Information** page to specify the credentials that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] will use to connect to the data source.</span></span> <span data-ttu-id="90031-104">有关凭据模拟的详细信息，请参阅[模拟 &#40;SSAS 表格&#41;](tabular-models/impersonation-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="90031-104">For more information about credentials impersonation, see [Impersonation &#40;SSAS Tabular&#41;](tabular-models/impersonation-ssas-tabular.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="90031-105">选项</span><span class="sxs-lookup"><span data-stu-id="90031-105">Options</span></span>  
 <span data-ttu-id="90031-106">**特定的 Windows 用户名和密码**</span><span class="sxs-lookup"><span data-stu-id="90031-106">**Specific Windows user name and password**</span></span>  
 <span data-ttu-id="90031-107">选择此选项将使表格模型使用指定的 Windows 用户帐户的安全凭据。</span><span class="sxs-lookup"><span data-stu-id="90031-107">Select this option to have the tabular model use the security credentials of a specified Windows user account.</span></span>  
  
 <span data-ttu-id="90031-108">**用户名**</span><span class="sxs-lookup"><span data-stu-id="90031-108">**User name**</span></span>  
 <span data-ttu-id="90031-109">键入要使用的用户帐户的域和名称。</span><span class="sxs-lookup"><span data-stu-id="90031-109">Type the domain and name of the user account to be used.</span></span> <span data-ttu-id="90031-110">使用以下格式：</span><span class="sxs-lookup"><span data-stu-id="90031-110">Use the following format:</span></span>  
  
 <span data-ttu-id="90031-111">*\<Domain name>* **\\** *\<User account name>*</span><span class="sxs-lookup"><span data-stu-id="90031-111">*\<Domain name>* **\\** *\<User account name>*</span></span>  
  
 <span data-ttu-id="90031-112">只有选定了 **“使用特定名称和密码”** ，才启用此选项。</span><span class="sxs-lookup"><span data-stu-id="90031-112">This option is enabled only if **Use a specific name and password** is selected.</span></span>  
  
 <span data-ttu-id="90031-113">**密码**</span><span class="sxs-lookup"><span data-stu-id="90031-113">**Password**</span></span>  
 <span data-ttu-id="90031-114">键入表格模型将使用的用户帐户的密码。</span><span class="sxs-lookup"><span data-stu-id="90031-114">Type the password of the user account to be used by the Tabular model.</span></span>  
  
 <span data-ttu-id="90031-115">只有选定了 **“使用特定名称和密码”** ，才启用此选项。</span><span class="sxs-lookup"><span data-stu-id="90031-115">This option is enabled only if **Use a specific name and password** is selected.</span></span>  
  
 <span data-ttu-id="90031-116">**服务帐户**</span><span class="sxs-lookup"><span data-stu-id="90031-116">**Service account**</span></span>  
 <span data-ttu-id="90031-117">选择此选项将使用与管理该模型的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 服务相关联的安全凭据。</span><span class="sxs-lookup"><span data-stu-id="90031-117">Select this option to use the security credentials associated with the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] service that manages the model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90031-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="90031-118">See Also</span></span>  
 [<span data-ttu-id="90031-119">模拟（SSAS 表格）</span><span class="sxs-lookup"><span data-stu-id="90031-119">Impersonation &#40;SSAS Tabular&#41;</span></span>](tabular-models/impersonation-ssas-tabular.md)  
  
  
