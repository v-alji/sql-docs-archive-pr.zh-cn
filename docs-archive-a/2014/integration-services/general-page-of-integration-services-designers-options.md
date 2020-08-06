---
title: 常规页 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Business_Intelligence_Designers.Data_Transformation_Designers.General
ms.assetid: d695690a-923b-4036-945e-7621e8651deb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 59073ac29f95f1e64bd0a9382366e9539ce1408a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578328"
---
# <a name="general-page"></a><span data-ttu-id="d039e-102">“常规”页</span><span class="sxs-lookup"><span data-stu-id="d039e-102">General Page</span></span>
  <span data-ttu-id="d039e-103">使用 **“选项”** 对话框中 **“Integration Services 设计器”** 页的 **“常规”** 页，可以指定用于加载、显示和升级包的选项。</span><span class="sxs-lookup"><span data-stu-id="d039e-103">Use the **General** page of the **Integration Services Designers** page in the **Options** dialog box to specify the options for loading, displaying, and upgrading packages.</span></span>  
  
 <span data-ttu-id="d039e-104">若要打开 **“常规”** 页，请在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，单击 **“工具”** 菜单上的 **“选项”** ，展开 **“商业智能设计器”** ，然后选择 **“Integration Services 设计器”** 。</span><span class="sxs-lookup"><span data-stu-id="d039e-104">To open the **General** page, in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], on the **Tools** menu, click **Options**, expand **Business Intelligence Designers**, and select **Integration Services Designers**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d039e-105">选项</span><span class="sxs-lookup"><span data-stu-id="d039e-105">Options</span></span>  
 <span data-ttu-id="d039e-106">**加载包时检查数字签名**</span><span class="sxs-lookup"><span data-stu-id="d039e-106">**Check digital signature when loading a package**</span></span>  
 <span data-ttu-id="d039e-107">选择让 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 在加载包时检查数字签名。</span><span class="sxs-lookup"><span data-stu-id="d039e-107">Select to have [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] check the digital signature when loading a package.</span></span> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="d039e-108">仅会检查数字签名是否存在、是否有效，并且是否来自可靠来源。</span><span class="sxs-lookup"><span data-stu-id="d039e-108">will only check whether the digital signature is present, is valid, and is from a trusted source.</span></span> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="d039e-109">不会检查包经过签名后是否发生过更改。</span><span class="sxs-lookup"><span data-stu-id="d039e-109">will not check whether the package has been changed since the package was signed.</span></span>  
  
 <span data-ttu-id="d039e-110">如果你设置 **BlockedSignatureStates** 注册表值，则此注册表值会替代“加载包时检查数字签名”  选项。</span><span class="sxs-lookup"><span data-stu-id="d039e-110">If you set the **BlockedSignatureStates** registry value, this registry value overrides the **Check digital signature when loading a package** option.</span></span> <span data-ttu-id="d039e-111">有关详细信息，请参阅 [通过设置注册表值实现签名策略](implement-a-signing-policy-by-setting-a-registry-value.md)。</span><span class="sxs-lookup"><span data-stu-id="d039e-111">For more information, see [Implement a Signing Policy by Setting a Registry Value](implement-a-signing-policy-by-setting-a-registry-value.md).</span></span>  
  
 <span data-ttu-id="d039e-112">有关数字证书和包的详细信息，请参阅 [使用数字签名标识包的源](security/identify-the-source-of-packages-with-digital-signatures.md)。</span><span class="sxs-lookup"><span data-stu-id="d039e-112">For more information about digital certificates and packages, see [Identify the Source of Packages with Digital Signatures](security/identify-the-source-of-packages-with-digital-signatures.md).</span></span>  
  
 <span data-ttu-id="d039e-113">**如果包未经签名则显示警告**</span><span class="sxs-lookup"><span data-stu-id="d039e-113">**Show warning if package is unsigned**</span></span>  
 <span data-ttu-id="d039e-114">选择此项将在加载未经签名的包时显示警告。</span><span class="sxs-lookup"><span data-stu-id="d039e-114">Select to display a warning when loading a package that is not signed.</span></span>  
  
 <span data-ttu-id="d039e-115">**显示优先约束标签**</span><span class="sxs-lookup"><span data-stu-id="d039e-115">**Show precedence constraint labels**</span></span>  
 <span data-ttu-id="d039e-116">选择在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中查看包时，显示哪种优先约束标签（“成功”、“失败”或“完成”）。</span><span class="sxs-lookup"><span data-stu-id="d039e-116">Select which label-Success, Failure, or Completion-to display on precedence constraints when viewing packages in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="d039e-117">**脚本语言**</span><span class="sxs-lookup"><span data-stu-id="d039e-117">**Scripting language**</span></span>  
 <span data-ttu-id="d039e-118">选择新脚本任务和脚本组件的默认脚本语言。</span><span class="sxs-lookup"><span data-stu-id="d039e-118">Select the default scripting language for new Script tasks and Script components.</span></span>  
  
 <span data-ttu-id="d039e-119">**更新连接字符串以使用新的提供程序名称**</span><span class="sxs-lookup"><span data-stu-id="d039e-119">**Update connection strings to use new provider names**</span></span>  
 <span data-ttu-id="d039e-120">对于当前版本的 [!INCLUDE[ssISversion2005](../includes/ssisversion2005-md.md)] ，打开或升级 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]包时，请将连接字符串更新为使用下列提供程序的名称：</span><span class="sxs-lookup"><span data-stu-id="d039e-120">When opening or upgrading [!INCLUDE[ssISversion2005](../includes/ssisversion2005-md.md)] packages, update connection strings to use the names for the following providers, for the current release of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]:</span></span>  
  
-   [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] <span data-ttu-id="d039e-121">OLE DB 访问接口</span><span class="sxs-lookup"><span data-stu-id="d039e-121">OLE DB provider</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="d039e-122">Native Client{2}</span><span class="sxs-lookup"><span data-stu-id="d039e-122">Native Client</span></span>  
  
 <span data-ttu-id="d039e-123">[!INCLUDE[ssIS](../includes/ssis-md.md)] 包升级向导仅更新存储在连接管理器中的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="d039e-123">The [!INCLUDE[ssIS](../includes/ssis-md.md)] Package Upgrade Wizard updates only connection strings that are stored in connection managers.</span></span> <span data-ttu-id="d039e-124">向导不会更新通过使用 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 表达式语言或在脚本任务中使用代码动态构造的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="d039e-124">The wizard does not update connection strings that are constructed dynamically by using the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] expression language, or by using code in a Script task.</span></span>  
  
 <span data-ttu-id="d039e-125">**创建新的包 ID**</span><span class="sxs-lookup"><span data-stu-id="d039e-125">**Create new package ID**</span></span>  
 <span data-ttu-id="d039e-126">升级 [!INCLUDE[ssISversion2005](../includes/ssisversion2005-md.md)] 包时，为包的升级版本创建新的包 ID。</span><span class="sxs-lookup"><span data-stu-id="d039e-126">When upgrading [!INCLUDE[ssISversion2005](../includes/ssisversion2005-md.md)] packages, create new package IDs for the upgraded versions of the packages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d039e-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d039e-127">See Also</span></span>  
 <span data-ttu-id="d039e-128">[安全性概述 (Integration Services)](security/security-overview-integration-services.md) </span><span class="sxs-lookup"><span data-stu-id="d039e-128">[Security Overview &#40;Integration Services&#41;](security/security-overview-integration-services.md) </span></span>  
 [<span data-ttu-id="d039e-129">用脚本扩展包</span><span class="sxs-lookup"><span data-stu-id="d039e-129">Extending Packages with Scripting</span></span>](extending-packages-scripting/extending-packages-with-scripting.md)  
  
  
