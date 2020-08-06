---
title: 更改用于美国英语和英国英语的断字符 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
ms.assetid: 6b5d2177-db98-47f5-b32e-4b80a2f74ffe
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3b759b90ec834dcb666f7862bfba3857f2fea0d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87587318"
---
# <a name="change-the-word-breaker-used-for-us-english-and-uk-english"></a><span data-ttu-id="b10b5-102">Change the Word Breaker Used for US English and UK English</span><span class="sxs-lookup"><span data-stu-id="b10b5-102">Change the Word Breaker Used for US English and UK English</span></span>
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="b10b5-103">针对英语安装断字符和词干分析器的新版本（版本 14.0.4999.1038），以替换这些组件的以前版本（版本 12.0.6828.0）。</span><span class="sxs-lookup"><span data-stu-id="b10b5-103">installs a new version (version 14.0.4999.1038) of the word breaker and stemmer for the English language, replacing the previous version of these components (version 12.0.6828.0).</span></span> <span data-ttu-id="b10b5-104">有关新组件的更改的行为的信息，请参阅 [全文搜索的行为更改](full-text-search.md)。</span><span class="sxs-lookup"><span data-stu-id="b10b5-104">For information about the changed behavior of the new components, see [Behavior Changes to Full-Text Search](full-text-search.md).</span></span> <span data-ttu-id="b10b5-105">本主题说明如何在这些组件的新版本和以前的版本间切换。</span><span class="sxs-lookup"><span data-stu-id="b10b5-105">This topic describes how to switch from the new version of these components to the previous version, or to switch back from the previous version to the new version.</span></span> <span data-ttu-id="b10b5-106">对于群集安装，应对所有主节点和被动节点进行这些更改。</span><span class="sxs-lookup"><span data-stu-id="b10b5-106">For cluster installations, these changes should be made on all the primary and passive nodes.</span></span>  
  
 <span data-ttu-id="b10b5-107">以前版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用不同 CLSID 所表示的不同断字符，这些 CLSID 分别用于美国英语 (LCID 1033) 和英国英语 (LCID 2057)。</span><span class="sxs-lookup"><span data-stu-id="b10b5-107">Previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] used different word breakers represented by different CLSIDs for US English (LCID 1033) and UK English (LCID 2057).</span></span> <span data-ttu-id="b10b5-108">在此发行版中，这两个 LCID 使用具有相同 CLSID 的相同组件，如下表中所示：</span><span class="sxs-lookup"><span data-stu-id="b10b5-108">In this release, both LCIDs use the same components with the same CLSIDs, as shown in the following table:</span></span>  
  
|<span data-ttu-id="b10b5-109">LCID</span><span class="sxs-lookup"><span data-stu-id="b10b5-109">LCID</span></span>|<span data-ttu-id="b10b5-110">以前版本安装的断字符</span><span class="sxs-lookup"><span data-stu-id="b10b5-110">Word breaker installed by previous versions</span></span><br /><br /> <span data-ttu-id="b10b5-111">版本 12.0.6828.0</span><span class="sxs-lookup"><span data-stu-id="b10b5-111">version 12.0.6828.0</span></span>|<span data-ttu-id="b10b5-112">以前版本安装的词干分析器</span><span class="sxs-lookup"><span data-stu-id="b10b5-112">Stemmer installed by previous versions</span></span>|<span data-ttu-id="b10b5-113">此版本安装的断字符</span><span class="sxs-lookup"><span data-stu-id="b10b5-113">Word breaker installed by this version</span></span><br /><br /> <span data-ttu-id="b10b5-114">版本 14.0.4999.1038</span><span class="sxs-lookup"><span data-stu-id="b10b5-114">version 14.0.4999.1038</span></span>|<span data-ttu-id="b10b5-115">此版本安装的词干分析器</span><span class="sxs-lookup"><span data-stu-id="b10b5-115">Stemmer installed by this version</span></span>|  
|----------|-------------------------------------------------------------------------|--------------------------------------------|-----------------------------------------------------------------------|---------------------------------------|  
|<span data-ttu-id="b10b5-116">2052</span><span class="sxs-lookup"><span data-stu-id="b10b5-116">1033</span></span><br /><span data-ttu-id="b10b5-117">（美国英语）</span><span class="sxs-lookup"><span data-stu-id="b10b5-117">(US English)</span></span>|<span data-ttu-id="b10b5-118">188D6CC5-CB03-4C01-912E-47D21295D77E</span><span class="sxs-lookup"><span data-stu-id="b10b5-118">188D6CC5-CB03-4C01-912E-47D21295D77E</span></span>|<span data-ttu-id="b10b5-119">EEED4C20-7F1B-11CE-BE57-00AA0051FE20</span><span class="sxs-lookup"><span data-stu-id="b10b5-119">EEED4C20-7F1B-11CE-BE57-00AA0051FE20</span></span>|<span data-ttu-id="b10b5-120">9faed859-0b30-4434-ae65-412e14a16fb8</span><span class="sxs-lookup"><span data-stu-id="b10b5-120">9faed859-0b30-4434-ae65-412e14a16fb8</span></span>|<span data-ttu-id="b10b5-121">e1e5ef84-c4a6-4e50-8188-99aef3de2659</span><span class="sxs-lookup"><span data-stu-id="b10b5-121">e1e5ef84-c4a6-4e50-8188-99aef3de2659</span></span>|  
|<span data-ttu-id="b10b5-122">2057</span><span class="sxs-lookup"><span data-stu-id="b10b5-122">2057</span></span><br /><span data-ttu-id="b10b5-123">（英国英语）</span><span class="sxs-lookup"><span data-stu-id="b10b5-123">(UK English)</span></span>|<span data-ttu-id="b10b5-124">173C97E2-AEBE-437C-9445-01B237ABF2F6</span><span class="sxs-lookup"><span data-stu-id="b10b5-124">173C97E2-AEBE-437C-9445-01B237ABF2F6</span></span>|<span data-ttu-id="b10b5-125">D99F7670-7F1A-11CE-BE57-00AA0051FE20</span><span class="sxs-lookup"><span data-stu-id="b10b5-125">D99F7670-7F1A-11CE-BE57-00AA0051FE20</span></span>|<span data-ttu-id="b10b5-126">9faed859-0b30-4434-ae65-412e14a16fb8</span><span class="sxs-lookup"><span data-stu-id="b10b5-126">9faed859-0b30-4434-ae65-412e14a16fb8</span></span>|<span data-ttu-id="b10b5-127">e1e5ef84-c4a6-4e50-8188-99aef3de2659</span><span class="sxs-lookup"><span data-stu-id="b10b5-127">e1e5ef84-c4a6-4e50-8188-99aef3de2659</span></span>|  
  
 <span data-ttu-id="b10b5-128">本主题中所述的组件是在 `MSSQL\Binn` 实例的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 文件夹中安装的 DLL 文件。</span><span class="sxs-lookup"><span data-stu-id="b10b5-128">The components described in this topic are DLL files that are installed in the `MSSQL\Binn` folder for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="b10b5-129">完整路径通常是 `C:\Program Files\Microsoft SQL Server\<instance>\MSSQL\Binn`。</span><span class="sxs-lookup"><span data-stu-id="b10b5-129">The full path is typically `C:\Program Files\Microsoft SQL Server\<instance>\MSSQL\Binn`.</span></span>  
  
 <span data-ttu-id="b10b5-130">有关断字符和词干分析器的详细信息，请参阅 [配置和管理断字符和词干分析器以便搜索](configure-and-manage-word-breakers-and-stemmers-for-search.md)。</span><span class="sxs-lookup"><span data-stu-id="b10b5-130">For more information about word breakers and stemmers, see [Configure and Manage Word Breakers and Stemmers for Search](configure-and-manage-word-breakers-and-stemmers-for-search.md).</span></span>  
  
## <a name="switching-from-the-current-english-word-breaker-to-the-previous-english-word-breakers"></a><span data-ttu-id="b10b5-131">从当前的英语断字符切换到以前的英语断字符</span><span class="sxs-lookup"><span data-stu-id="b10b5-131">Switching from the current English word breaker to the previous English word breakers</span></span>  
  
#### <a name="to-switch-from-the-current-version-of-the-us-english-word-breaker-to-the-previous-version"></a><span data-ttu-id="b10b5-132">从当前版本的美国英语断字符切换到以前的版本</span><span class="sxs-lookup"><span data-stu-id="b10b5-132">To switch from the current version of the US English word breaker to the previous version</span></span>  
  
1.  <span data-ttu-id="b10b5-133">在注册表中，导航到以下节点：**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\CLSID**。</span><span class="sxs-lookup"><span data-stu-id="b10b5-133">In the registry, navigate to the following node: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\CLSID**.</span></span>  
  
2.  <span data-ttu-id="b10b5-134">使用以下步骤添加 COM ClassID 的新键，用于 LCID 1033 的以前美国英语的断字符和词干分析器接口：</span><span class="sxs-lookup"><span data-stu-id="b10b5-134">Use the following steps to add new keyS for the COM ClassIDs for the previous US English word breaker and stemmer interfaces for LCID 1033:</span></span>  
  
    1.  <span data-ttu-id="b10b5-135">为以前的断字符添加值为 **{188D6CC5-CB03-4C01-912E-47D21295D77E}** 的新键。</span><span class="sxs-lookup"><span data-stu-id="b10b5-135">Add a new key with the value **{188D6CC5-CB03-4C01-912E-47D21295D77E}** for the previous word breaker.</span></span>  
  
    2.  <span data-ttu-id="b10b5-136">将该键值的（默认）数据更新为 **langwrbk.dll**。</span><span class="sxs-lookup"><span data-stu-id="b10b5-136">Update the (Default) data of that key value to **langwrbk.dll**.</span></span>  
  
    3.  <span data-ttu-id="b10b5-137">为以前的词干分析器添加值为 **{EEED4C20-7F1B-11CE-BE57-00AA0051FE20}** 的新键。</span><span class="sxs-lookup"><span data-stu-id="b10b5-137">Add a new key with the value **{EEED4C20-7F1B-11CE-BE57-00AA0051FE20}** for the previous stemmer.</span></span>  
  
    4.  <span data-ttu-id="b10b5-138">将该键值的（默认）数据更新为 **infosoft.dll**。</span><span class="sxs-lookup"><span data-stu-id="b10b5-138">Update the (Default) data of that key value to **infosoft.dll**.</span></span>  
  
3.  <span data-ttu-id="b10b5-139">在注册表中，导航到以下节点：**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\Language\enu**。</span><span class="sxs-lookup"><span data-stu-id="b10b5-139">In the registry, navigate to the following node: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\Language\enu**.</span></span>  
  
4.  <span data-ttu-id="b10b5-140">将 **WBreakerClass** 键值更新为 **{188D6CC5-CB03-4C01-912E-47D21295D77E}** 。</span><span class="sxs-lookup"><span data-stu-id="b10b5-140">Update the **WBreakerClass** key value to **{188D6CC5-CB03-4C01-912E-47D21295D77E}**.</span></span>  
  
5.  <span data-ttu-id="b10b5-141">将 **StemmerClass** 键值更新为 **{EEED4C20-7F1B-11CE-BE57-00AA0051FE20}** 。</span><span class="sxs-lookup"><span data-stu-id="b10b5-141">Update the **StemmerClass** key value to **{EEED4C20-7F1B-11CE-BE57-00AA0051FE20}**.</span></span>  
  
6.  <span data-ttu-id="b10b5-142">重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b10b5-142">Restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
#### <a name="to-switch-from-the-current-version-of-the-uk-english-word-breaker-to-the-previous-version"></a><span data-ttu-id="b10b5-143">从当前版本的英国英语断字符切换到以前的版本</span><span class="sxs-lookup"><span data-stu-id="b10b5-143">To switch from the current version of the UK English word breaker to the previous version</span></span>  
  
1.  <span data-ttu-id="b10b5-144">在注册表中，导航到以下节点：**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\CLSID**。</span><span class="sxs-lookup"><span data-stu-id="b10b5-144">In the registry, navigate to the following node: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\CLSID**.</span></span>  
  
2.  <span data-ttu-id="b10b5-145">使用以下步骤添加 COM ClassID 的新键，用于 LCID 2057 的以前英国英语的断字符和词干分析器接口：</span><span class="sxs-lookup"><span data-stu-id="b10b5-145">Use the following steps to add a new key for the COM ClassIDs for the previous UK English word breaker and stemmer interfaces for LCID 2057:</span></span>  
  
    1.  <span data-ttu-id="b10b5-146">为以前的断字符添加值为 **{173C97E2-AEBE-437C-9445-01B237ABF2F6}** 的新键。</span><span class="sxs-lookup"><span data-stu-id="b10b5-146">Add a new key with the value **{173C97E2-AEBE-437C-9445-01B237ABF2F6}** for the previous word breaker.</span></span>  
  
    2.  <span data-ttu-id="b10b5-147">将该键值的（默认）数据更新为 **langwrbk.dll**。</span><span class="sxs-lookup"><span data-stu-id="b10b5-147">Update the (Default) data of that key value to **langwrbk.dll**.</span></span>  
  
    3.  <span data-ttu-id="b10b5-148">为以前的词干分析器添加值为 **{D99F7670-7F1A-11CE-BE57-00AA0051FE20}** 的新键。</span><span class="sxs-lookup"><span data-stu-id="b10b5-148">Add a new key with the value **{D99F7670-7F1A-11CE-BE57-00AA0051FE20}** for the previous stemmer.</span></span>  
  
    4.  <span data-ttu-id="b10b5-149">将该键值的（默认）数据更新为 **infosoft.dll**。</span><span class="sxs-lookup"><span data-stu-id="b10b5-149">Update the (Default) data of that key value to **infosoft.dll**.</span></span>  
  
3.  <span data-ttu-id="b10b5-150">在注册表中，导航到以下节点：**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\Language\eng**。</span><span class="sxs-lookup"><span data-stu-id="b10b5-150">In the registry, navigate to the following node: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\Language\eng**.</span></span>  
  
4.  <span data-ttu-id="b10b5-151">将 **WBreakerClass** 键值更新为 **{173C97E2-AEBE-437C-9445-01B237ABF2F6}** 。</span><span class="sxs-lookup"><span data-stu-id="b10b5-151">Update the **WBreakerClass** key value to **{173C97E2-AEBE-437C-9445-01B237ABF2F6}**.</span></span>  
  
5.  <span data-ttu-id="b10b5-152">将 **StemmerClass** 键值更新 **{D99F7670-7F1A-11CE-BE57-00AA0051FE20}** 。</span><span class="sxs-lookup"><span data-stu-id="b10b5-152">Update the **StemmerClass** key value to **{D99F7670-7F1A-11CE-BE57-00AA0051FE20}**.</span></span>  
  
6.  <span data-ttu-id="b10b5-153">重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b10b5-153">Restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="switching-back-from-the-previous-english-word-breakers-to-the-current-english-word-breaker"></a><span data-ttu-id="b10b5-154">从以前的英语断字符切换回当前的英语断字符</span><span class="sxs-lookup"><span data-stu-id="b10b5-154">Switching back from the previous English word breakers to the current English word breaker</span></span>  
  
#### <a name="to-switch-back-from-the-previous-version-of-the-us-english-word-breaker-to-the-current-version"></a><span data-ttu-id="b10b5-155">从以前版本的美国英语断字符切换回当前版本</span><span class="sxs-lookup"><span data-stu-id="b10b5-155">To switch back from the previous version of the US English word breaker to the current version</span></span>  
  
1.  <span data-ttu-id="b10b5-156">在注册表中，导航到以下节点：**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\CLSID**。</span><span class="sxs-lookup"><span data-stu-id="b10b5-156">In the registry, navigate to the following node: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\CLSID**.</span></span>  
  
2.  <span data-ttu-id="b10b5-157">如果以下键不存在，则使用以下步骤添加 COM ClassID 的新键，用于 LCID 1033 的当前美国英语的断字符和词干分析器接口：</span><span class="sxs-lookup"><span data-stu-id="b10b5-157">If the following keys do not exist, then use the following steps to add a new key for the COM ClassIDs for the current US English word breaker and stemmer interfaces for LCID 1033:</span></span>  
  
    1.  <span data-ttu-id="b10b5-158">添加值为 **{9faed859-0b30-4434-ae65-412e14a16fb8}** 的新键用于当前断字符。</span><span class="sxs-lookup"><span data-stu-id="b10b5-158">Add a new key with the value **{9faed859-0b30-4434-ae65-412e14a16fb8}** for the current word breaker.</span></span>  
  
    2.  <span data-ttu-id="b10b5-159">将该键值的（默认）数据更新为 **MsWb7.dll**。</span><span class="sxs-lookup"><span data-stu-id="b10b5-159">Update the (Default) data of that key value to **MsWb7.dll**.</span></span>  
  
    3.  <span data-ttu-id="b10b5-160">添加值为 **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}** 的新键用于当前词干分析器。</span><span class="sxs-lookup"><span data-stu-id="b10b5-160">Add a new key with the value **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}** for the current stemmer.</span></span>  
  
    4.  <span data-ttu-id="b10b5-161">将该键值的（默认）数据更新为 **MsWb7.dll**。</span><span class="sxs-lookup"><span data-stu-id="b10b5-161">Update the (Default) data of that key value to **MsWb7.dll**.</span></span>  
  
3.  <span data-ttu-id="b10b5-162">在注册表中，导航到以下节点：**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\Language\eng**。</span><span class="sxs-lookup"><span data-stu-id="b10b5-162">In the registry, navigate to the following node: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\Language\eng**.</span></span>  
  
4.  <span data-ttu-id="b10b5-163">将 **WBreakerClass** 键值更新为 **{9faed859-0b30-4434-ae65-412e14a16fb8}** 。</span><span class="sxs-lookup"><span data-stu-id="b10b5-163">Update the **WBreakerClass** key value to **{9faed859-0b30-4434-ae65-412e14a16fb8}**.</span></span>  
  
5.  <span data-ttu-id="b10b5-164">将 **StemmerClass** 键值更新为 **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}** 。</span><span class="sxs-lookup"><span data-stu-id="b10b5-164">Update the **StemmerClass** key value to **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}**.</span></span>  
  
6.  <span data-ttu-id="b10b5-165">重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b10b5-165">Restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
#### <a name="to-switch-back-from-the-previous-version-of-the-uk-english-word-breaker-to-the-current-version"></a><span data-ttu-id="b10b5-166">从以前版本的英国英语断字符切换回当前版本</span><span class="sxs-lookup"><span data-stu-id="b10b5-166">To switch back from the previous version of the UK English word breaker to the current version</span></span>  
  
1.  <span data-ttu-id="b10b5-167">在注册表中，导航到以下节点：**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\CLSID**。</span><span class="sxs-lookup"><span data-stu-id="b10b5-167">In the registry, navigate to the following node: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\CLSID**.</span></span>  
  
2.  <span data-ttu-id="b10b5-168">如果以下键不存在，则使用以下步骤添加 COM ClassID 的新键，用于 LCID 2057 的当前英国英语的断字符和词干分析器接口：</span><span class="sxs-lookup"><span data-stu-id="b10b5-168">If the following keys do not exist, then use the following steps to add a new key for the COM ClassIDs for the current UK English word breaker and stemmer interfaces for LCID 2057:</span></span>  
  
    1.  <span data-ttu-id="b10b5-169">添加值为 **{9faed859-0b30-4434-ae65-412e14a16fb8}** 的新键用于当前断字符。</span><span class="sxs-lookup"><span data-stu-id="b10b5-169">Add a new key with the value **{9faed859-0b30-4434-ae65-412e14a16fb8}** for the current word breaker.</span></span>  
  
    2.  <span data-ttu-id="b10b5-170">将该键值的（默认）数据更新为 **MsWb7.dll**。</span><span class="sxs-lookup"><span data-stu-id="b10b5-170">Update the (Default) data of that key value to **MsWb7.dll**.</span></span>  
  
    3.  <span data-ttu-id="b10b5-171">添加值为 **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}** 的新键用于当前词干分析器。</span><span class="sxs-lookup"><span data-stu-id="b10b5-171">Add a new key with the value **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}** for the current stemmer.</span></span>  
  
    4.  <span data-ttu-id="b10b5-172">将该键值的（默认）数据更新为 **MsWb7.dll**。</span><span class="sxs-lookup"><span data-stu-id="b10b5-172">Update the (Default) data of that key value to **MsWb7.dll**.</span></span>  
  
3.  <span data-ttu-id="b10b5-173">在注册表中，导航到以下节点：**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\Language\eng**。</span><span class="sxs-lookup"><span data-stu-id="b10b5-173">In the registry, navigate to the following node: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<InstanceRoot\>\MSSearch\Language\eng**.</span></span>  
  
4.  <span data-ttu-id="b10b5-174">将 **WBreakerClass** 键值更新为 **{9faed859-0b30-4434-ae65-412e14a16fb8}** 。</span><span class="sxs-lookup"><span data-stu-id="b10b5-174">Update the **WBreakerClass** key value to **{9faed859-0b30-4434-ae65-412e14a16fb8}**.</span></span>  
  
5.  <span data-ttu-id="b10b5-175">将 **StemmerClass** 键值更新为 **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}** 。</span><span class="sxs-lookup"><span data-stu-id="b10b5-175">Update the **StemmerClass** key value to **{e1e5ef84-c4a6-4e50-8188-99aef3de2659}**.</span></span>  
  
6.  <span data-ttu-id="b10b5-176">重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b10b5-176">Restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b10b5-177">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b10b5-177">See Also</span></span>  
 <span data-ttu-id="b10b5-178">[将搜索功能所使用的断字符还原到以前的版本](revert-the-word-breakers-used-by-search-to-the-previous-version.md) </span><span class="sxs-lookup"><span data-stu-id="b10b5-178">[Revert the Word Breakers Used by Search to the Previous Version](revert-the-word-breakers-used-by-search-to-the-previous-version.md) </span></span>  
 [<span data-ttu-id="b10b5-179">对全文搜索的行为更改</span><span class="sxs-lookup"><span data-stu-id="b10b5-179">Behavior Changes to Full-Text Search</span></span>](full-text-search.md)  
  
  
