---
title: 通过设置注册表值实现签名策略 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- signing policies [Integration Services]
ms.assetid: 64f6966f-2292-401f-acb1-2ccb5aee484a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1e844b65df5b45f212554f7583f4e4b327b740e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87578316"
---
# <a name="implement-a-signing-policy-by-setting-a-registry-value"></a><span data-ttu-id="6c90e-102">通过设置注册表值实现签名策略</span><span class="sxs-lookup"><span data-stu-id="6c90e-102">Implement a Signing Policy by Setting a Registry Value</span></span>
  <span data-ttu-id="6c90e-103">使用可选的注册表值可以管理组织用于加载签名包和未签名包的策略。</span><span class="sxs-lookup"><span data-stu-id="6c90e-103">You can use an optional registry value to manage an organization's policy for loading signed or unsigned packages.</span></span> <span data-ttu-id="6c90e-104">如果使用此注册表值，则必须在将运行 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包以及将强制实施该策略的每台计算机上创建此注册表值。</span><span class="sxs-lookup"><span data-stu-id="6c90e-104">If you use this registry value, you must create this registry value on each computer on which [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages will run and on which you want to enforce the policy.</span></span> <span data-ttu-id="6c90e-105">设置该注册表值后， [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 将在加载包之前检查或验证签名。</span><span class="sxs-lookup"><span data-stu-id="6c90e-105">After the registry value has been set, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] will check or verify the signatures before loading packages.</span></span>  
  
 <span data-ttu-id="6c90e-106">本主题中的此过程将介绍如何将可选的 `BlockedSignatureStates` DWORD 值添加到 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\SSIS 注册表项中。</span><span class="sxs-lookup"><span data-stu-id="6c90e-106">This procedure in this topic describes how to add the optional `BlockedSignatureStates` DWORD value to the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\SSIS registry key.</span></span> <span data-ttu-id="6c90e-107">`BlockedSignatureStates` 中的数据值决定当包具有不可信签名、具有无效签名或未签名时是否阻止该包。</span><span class="sxs-lookup"><span data-stu-id="6c90e-107">The data value in `BlockedSignatureStates` determines whether a package should be blocked if it has an untrusted signature, has an invalid signature, or is unsigned.</span></span> <span data-ttu-id="6c90e-108">对于用来进行包签名的签名的状态，`BlockedSignatureStates` 注册表值使用下列定义：</span><span class="sxs-lookup"><span data-stu-id="6c90e-108">With regard to the status of signatures used to sign packages, the `BlockedSignatureStates` registry value uses the following definitions:</span></span>  
  
-   <span data-ttu-id="6c90e-109">“有效签名” \*\* 是一个可以成功读取的签名。</span><span class="sxs-lookup"><span data-stu-id="6c90e-109">A *valid signature* is one that can be read successfully.</span></span>  
  
-   <span data-ttu-id="6c90e-110">“无效签名”\*\* 是一个解密的校验和（由私钥加密的包代码的单向哈希）与在加载 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 包的过程中计算的解密校验和不相符的签名。</span><span class="sxs-lookup"><span data-stu-id="6c90e-110">An *invalid signature* is one for which the decrypted checksum (the one-way hash of the package code encrypted by a private key) does not match the decrypted checksum that is calculated as part of the process of loading [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span>  
  
-   <span data-ttu-id="6c90e-111">“可信签名” \*\* 是一个使用由受信任的根证书颁发机构签名的数字证书创建的签名。</span><span class="sxs-lookup"><span data-stu-id="6c90e-111">A *trusted signature* is one that is created by using a digital certificate signed by a Trusted Root Certification Authority.</span></span> <span data-ttu-id="6c90e-112">该设置不要求签名者出现在可信发布服务器的用户列表中。</span><span class="sxs-lookup"><span data-stu-id="6c90e-112">This setting does not require the signer to be found in the user's list of Trusted Publishers.</span></span>  
  
-   <span data-ttu-id="6c90e-113">“不可信签名 \*\* ”是一个不能验证为由受信任的根证书颁发机构颁发的签名，或不是最新版本的签名。</span><span class="sxs-lookup"><span data-stu-id="6c90e-113">An *untrusted signature* is one that cannot be verified as issued by a Trusted Root Certification Authority, or a signature that is not current.</span></span>  
  
 <span data-ttu-id="6c90e-114">下表列出了 DWORD 数据的有效值及其相关策略。</span><span class="sxs-lookup"><span data-stu-id="6c90e-114">The following table lists the valid values of the DWORD data and their associated policy.</span></span>  
  
|<span data-ttu-id="6c90e-115">值</span><span class="sxs-lookup"><span data-stu-id="6c90e-115">Value</span></span>|<span data-ttu-id="6c90e-116">说明</span><span class="sxs-lookup"><span data-stu-id="6c90e-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6c90e-117">0</span><span class="sxs-lookup"><span data-stu-id="6c90e-117">0</span></span>|<span data-ttu-id="6c90e-118">无管理限制。</span><span class="sxs-lookup"><span data-stu-id="6c90e-118">No administrative restriction.</span></span>|  
|<span data-ttu-id="6c90e-119">1</span><span class="sxs-lookup"><span data-stu-id="6c90e-119">1</span></span>|<span data-ttu-id="6c90e-120">阻止无效签名。</span><span class="sxs-lookup"><span data-stu-id="6c90e-120">Block invalid signatures.</span></span><br /><br /> <span data-ttu-id="6c90e-121">该设置不阻止未签名的包。</span><span class="sxs-lookup"><span data-stu-id="6c90e-121">This setting does not block unsigned packages.</span></span>|  
|<span data-ttu-id="6c90e-122">2</span><span class="sxs-lookup"><span data-stu-id="6c90e-122">2</span></span>|<span data-ttu-id="6c90e-123">阻止无效签名和不可信签名。</span><span class="sxs-lookup"><span data-stu-id="6c90e-123">Block invalid and untrusted signatures.</span></span><br /><br /> <span data-ttu-id="6c90e-124">该设置不阻止未签名的包，但会阻止自我生成的签名。</span><span class="sxs-lookup"><span data-stu-id="6c90e-124">This setting does not block unsigned packages, but blocks self-generated signatures.</span></span>|  
|<span data-ttu-id="6c90e-125">3</span><span class="sxs-lookup"><span data-stu-id="6c90e-125">3</span></span>|<span data-ttu-id="6c90e-126">阻止无效签名、不可信签名以及未签名的包</span><span class="sxs-lookup"><span data-stu-id="6c90e-126">Block invalid and untrusted signatures and unsigned packages</span></span><br /><br /> <span data-ttu-id="6c90e-127">该设置也阻止自我生成的签名。</span><span class="sxs-lookup"><span data-stu-id="6c90e-127">This setting also blocks self-generated signatures.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="6c90e-128">`BlockedSignatureStates` 的建议设置为 3。</span><span class="sxs-lookup"><span data-stu-id="6c90e-128">The recommended setting for `BlockedSignatureStates` is 3.</span></span> <span data-ttu-id="6c90e-129">该设置提供针对未签名包或者无效或不可信签名的最强保护功能。</span><span class="sxs-lookup"><span data-stu-id="6c90e-129">This setting provides the greatest protection against unsigned packages or signatures that are either not valid or untrusted.</span></span> <span data-ttu-id="6c90e-130">不过，建议的设置并非适用于所有情况。</span><span class="sxs-lookup"><span data-stu-id="6c90e-130">However, the recommended setting may not be appropriate in all circumstances.</span></span> <span data-ttu-id="6c90e-131">有关如何进行数字资产签名的详细信息，请参阅 MSDN Library 中的主题“[Introduction to Code Signing](https://go.microsoft.com/fwlink/?LinkId=51414)（代码签名简介）”。</span><span class="sxs-lookup"><span data-stu-id="6c90e-131">For more information about signing digital assets, see the topic, "[Introduction to Code Signing](https://go.microsoft.com/fwlink/?LinkId=51414)," in the MSDN Library.</span></span>  
  
### <a name="to-implement-a-signing-policy-for-packages"></a><span data-ttu-id="6c90e-132">实现包的签名策略</span><span class="sxs-lookup"><span data-stu-id="6c90e-132">To implement a signing policy for packages</span></span>  
  
1.  <span data-ttu-id="6c90e-133">在 **“开始”** 菜单上，单击 **“运行”** 。</span><span class="sxs-lookup"><span data-stu-id="6c90e-133">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="6c90e-134">在 "运行" 对话框中，键入 `Regedit` ，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="6c90e-134">In the Run dialog box, type `Regedit`, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="6c90e-135">找到注册表项 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\SSIS。</span><span class="sxs-lookup"><span data-stu-id="6c90e-135">Locate the registry key, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\SSIS.</span></span>  
  
4.  <span data-ttu-id="6c90e-136">右键单击“MSDTS”\*\*\*\*，指向“新建”\*\*\*\*，然后单击“DWORD 值”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6c90e-136">Right-click **MSDTS**, point to **New**, and then click **DWORD Value**.</span></span>  
  
5.  <span data-ttu-id="6c90e-137">将新值的名称更新为 `BlockedSignatureStates`。</span><span class="sxs-lookup"><span data-stu-id="6c90e-137">Update the name of the new value to `BlockedSignatureStates`.</span></span>  
  
6.  <span data-ttu-id="6c90e-138">右键单击 `BlockedSignatureStates` ，然后单击 "**修改**"。</span><span class="sxs-lookup"><span data-stu-id="6c90e-138">Right-click `BlockedSignatureStates` and click **Modify**.</span></span>  
  
7.  <span data-ttu-id="6c90e-139">在 **“编辑 DWORD 值”** 对话框中，键入值 0、1、2 或 3。</span><span class="sxs-lookup"><span data-stu-id="6c90e-139">In the **Edit DWORD Value** dialog box, type the value 0, 1, 2, or 3.</span></span>  
  
8.  <span data-ttu-id="6c90e-140">单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="6c90e-140">Click **OK**.</span></span>  
  
9. <span data-ttu-id="6c90e-141">在 **“文件”** 菜单中，单击 **“退出”** 。</span><span class="sxs-lookup"><span data-stu-id="6c90e-141">On the **File** menu, click **Exit**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c90e-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6c90e-142">See Also</span></span>  
 <span data-ttu-id="6c90e-143">[安全概述 &#40;Integration Services&#41;](security/security-overview-integration-services.md) </span><span class="sxs-lookup"><span data-stu-id="6c90e-143">[Security Overview &#40;Integration Services&#41;](security/security-overview-integration-services.md) </span></span>  
 [<span data-ttu-id="6c90e-144">使用数字签名标识包的源</span><span class="sxs-lookup"><span data-stu-id="6c90e-144">Identify the Source of Packages with Digital Signatures</span></span>](security/identify-the-source-of-packages-with-digital-signatures.md)  
  
  
