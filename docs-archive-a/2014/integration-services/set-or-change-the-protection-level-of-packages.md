---
title: 设置或更改包的保护级别 |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- passwords [Integration Services]
- packages [Integration Services],security
- security [Integration Services],protection levels
- protection level for packages [Integration Services]
ms.assetid: 904a5580-82ba-4a26-b0c5-d1c989975f61
author: chugugrace
ms.author: chugu
ms.openlocfilehash: da8e63028498097b4321e4ef1383fbc8aa5845b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693401"
---
# <a name="set-or-change-the-protection-level-of-packages"></a><span data-ttu-id="239c9-102">设置或更改包的保护级别</span><span class="sxs-lookup"><span data-stu-id="239c9-102">Set or Change the Protection Level of Packages</span></span>
  <span data-ttu-id="239c9-103">若要控制对包内容以及其中包含的敏感值（如密码）的访问，请设置 `ProtectionLevel` 属性的值。</span><span class="sxs-lookup"><span data-stu-id="239c9-103">To control access to the contents of packages and to the sensitive values that they contain, such as passwords, set the value of the `ProtectionLevel` property.</span></span> <span data-ttu-id="239c9-104">项目中所含的包需要具有与项目相同的保护级别才能生成项目。</span><span class="sxs-lookup"><span data-stu-id="239c9-104">The packages contained in a project need to have the same protection level as the project, to build the project.</span></span> <span data-ttu-id="239c9-105">如果更改项目的 `ProtectionLevel` 属性设置，需要为包手动更新该属性设置。</span><span class="sxs-lookup"><span data-stu-id="239c9-105">If you change the `ProtectionLevel` property setting on the project, you need to manually update the property setting for the packages.</span></span>  
  
 <span data-ttu-id="239c9-106">有关如何在 `ProtectionLevel` 包生命周期中的不同阶段确定适用于你的包的设置的信息，请参阅[对包中敏感数据的访问控制](security/access-control-for-sensitive-data-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="239c9-106">For information about how to determine the `ProtectionLevel` settings that are appropriate for your packages at different stages in the package life cycle, see [Access Control for Sensitive Data in Packages](security/access-control-for-sensitive-data-in-packages.md).</span></span> <span data-ttu-id="239c9-107">有关 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 中安全功能的概述，请参阅[安全性概述 (Integration Services)](security/security-overview-integration-services.md)。</span><span class="sxs-lookup"><span data-stu-id="239c9-107">For an overview of security features in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], see [Security Overview &#40;Integration Services&#41;](security/security-overview-integration-services.md).</span></span>  
  
 <span data-ttu-id="239c9-108">本主题中的过程介绍如何使用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 或 dtutil 命令提示实用工具来更改 `ProtectionLevel` 属性。</span><span class="sxs-lookup"><span data-stu-id="239c9-108">The procedures in this topic describe how to use either [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] or the dtutil command prompt utility to change the `ProtectionLevel` property.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="239c9-109">除了本主题中的过程外，当导入或导出包时，您通常可以设置或更改包的 `ProtectionLevel` 属性。</span><span class="sxs-lookup"><span data-stu-id="239c9-109">In addition to the procedures in this topic, you can typically set or change the `ProtectionLevel` property of a package when you import or export the package.</span></span> <span data-ttu-id="239c9-110">当使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 导入和导出向导保存包时，您也可以更改包的 `ProtectionLevel` 属性。</span><span class="sxs-lookup"><span data-stu-id="239c9-110">You can also change the `ProtectionLevel` property of a package when you use the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Import and Export Wizard to save a package.</span></span>  
  
### <a name="to-set-or-change-the-protection-level-of-a-package-in-sql-server-data-tools"></a><span data-ttu-id="239c9-111">在 SQL Server Data Tools 中设置或更改包的保护级别</span><span class="sxs-lookup"><span data-stu-id="239c9-111">To set or change the protection level of a package in SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="239c9-112">`ProtectionLevel`在主题中查看属性的可用值，[设置包的保护级别](security/access-control-for-sensitive-data-in-packages.md)，并确定包的适当值。</span><span class="sxs-lookup"><span data-stu-id="239c9-112">Review the available values for the `ProtectionLevel` property in the topic, [Setting the Protection Level of Packages](security/access-control-for-sensitive-data-in-packages.md), and determine the appropriate value for your package.</span></span>  
  
2.  <span data-ttu-id="239c9-113">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，打开包含该包的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 项目。</span><span class="sxs-lookup"><span data-stu-id="239c9-113">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package.</span></span>  
  
3.  <span data-ttu-id="239c9-114">在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器中打开包。</span><span class="sxs-lookup"><span data-stu-id="239c9-114">Open the package in the [!INCLUDE[ssIS](../includes/ssis-md.md)] designer.</span></span>  
  
4.  <span data-ttu-id="239c9-115">如果“属性”窗口未显示包的属性，请单击设计图面。</span><span class="sxs-lookup"><span data-stu-id="239c9-115">If the Properties window does not show the properties of the package, click the design surface.</span></span>  
  
5.  <span data-ttu-id="239c9-116">在属性窗口的 "**安全**" 组中，为属性选择适当的值 `ProtectionLevel` 。</span><span class="sxs-lookup"><span data-stu-id="239c9-116">In the Properties window, in the **Security** group, select the appropriate value for the `ProtectionLevel` property.</span></span>  
  
     <span data-ttu-id="239c9-117">如果选择的保护级别需要密码，请输入密码作为 **PackagePassword** 属性的值。</span><span class="sxs-lookup"><span data-stu-id="239c9-117">If you select a protection level that requires a password, enter the password as the value of the **PackagePassword** property.</span></span>  
  
6.  <span data-ttu-id="239c9-118">在 **“文件”** 菜单上，选择 **“保存选定项”** 以保存修改的包。</span><span class="sxs-lookup"><span data-stu-id="239c9-118">On the **File** menu, select **Save Selected Items** to save the modified package.</span></span>  
  
### <a name="to-set-or-change-the-protection-level-of-packages-at-the-command-prompt"></a><span data-ttu-id="239c9-119">在命令提示符下设置或更改包的保护级别</span><span class="sxs-lookup"><span data-stu-id="239c9-119">To set or change the protection level of packages at the command prompt</span></span>  
  
1.  <span data-ttu-id="239c9-120">`ProtectionLevel`在主题中查看属性的可用值，[设置包的保护级别](security/access-control-for-sensitive-data-in-packages.md)，并确定包的适当值。</span><span class="sxs-lookup"><span data-stu-id="239c9-120">Review the available values for the `ProtectionLevel` property in the topic, [Setting the Protection Level of Packages](security/access-control-for-sensitive-data-in-packages.md), and determine the appropriate value for your package.</span></span>  
  
2.  <span data-ttu-id="239c9-121">`Encrypt`在主题[dtutil 实用工具](dtutil-utility.md)中查看选项的映射，然后确定要用作所选属性的值的相应整数 `ProtectionLevel` 。</span><span class="sxs-lookup"><span data-stu-id="239c9-121">Review the mappings for the `Encrypt` option in the topic, [dtutil Utility](dtutil-utility.md), and determine the appropriate integer to use as the value of the selected `ProtectionLevel` property.</span></span>  
  
3.  <span data-ttu-id="239c9-122">打开命令提示符窗口。</span><span class="sxs-lookup"><span data-stu-id="239c9-122">Open a Command Prompt window.</span></span>  
  
4.  <span data-ttu-id="239c9-123">在命令提示符下，导航到您要为其设置 `ProtectionLevel` 属性的包所在的文件夹。</span><span class="sxs-lookup"><span data-stu-id="239c9-123">At the command prompt, navigate to the folder that contains the package or packages for which you want to set the `ProtectionLevel` property.</span></span>  
  
     <span data-ttu-id="239c9-124">下面步骤中所示的语法示例假设此文件夹是当前文件夹。</span><span class="sxs-lookup"><span data-stu-id="239c9-124">The syntax examples shown in the following step assume that this folder is the current folder.</span></span>  
  
5.  <span data-ttu-id="239c9-125">使用与下列示例之一相类似的命令，设置或更改包的保护级别。</span><span class="sxs-lookup"><span data-stu-id="239c9-125">Set or change the protection level of the package or packages by using a command similar to the one of the following examples:</span></span>  
  
    -   <span data-ttu-id="239c9-126">下面的命令将文件系统中的单个包的 `ProtectionLevel` 属性设置为级别 2“使用密码加密敏感数据”，密码为“strongpassword”：</span><span class="sxs-lookup"><span data-stu-id="239c9-126">The following command sets the `ProtectionLevel` property of an individual package in the file system to level 2, "Encrypt sensitive with password", with the password, "strongpassword":</span></span>  
  
         `dtutil.exe /file "C:\Package.dtsx" /encrypt file;"C:\Package.dtsx";2;strongpassword`  
  
    -   <span data-ttu-id="239c9-127">下面的命令将文件系统中特定文件夹内所有包的 `ProtectionLevel` 属性设置为级别 2“使用密码加密敏感数据”，密码为“strongpassword”：</span><span class="sxs-lookup"><span data-stu-id="239c9-127">The following command sets the `ProtectionLevel` property of all packages in a particular folder in the file system to level 2, "Encrypt sensitive with password", with the password, "strongpassword":</span></span>  
  
         `for %f in (*.dtsx) do dtutil.exe /file %f /encrypt file;%f;2;strongpassword`  
  
         <span data-ttu-id="239c9-128">如果您在批文件中使用类似的命令，则请输入文件占位符“%f”作为批文件中的“%%f”。</span><span class="sxs-lookup"><span data-stu-id="239c9-128">If you use a similar command in a batch file, enter the file placeholder, "%f", as "%%f" in the batch file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="239c9-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="239c9-129">See Also</span></span>  
 [<span data-ttu-id="239c9-130">dtutil 实用工具</span><span class="sxs-lookup"><span data-stu-id="239c9-130">dtutil Utility</span></span>](dtutil-utility.md)  
  
  
