---
title: SQL Server 中的本地语言版本 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 20b99363-0490-4aa3-9a3d-262f827d81e8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 646ffaed1e4b709c2c26030379f0a7f223f221e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688439"
---
# <a name="local-language-versions-in-sql-server"></a><span data-ttu-id="f281e-102">SQL Server 中的本地语言版本</span><span class="sxs-lookup"><span data-stu-id="f281e-102">Local Language Versions in SQL Server</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f281e-103">支持 Windows 操作系统所支持的所有语言。</span><span class="sxs-lookup"><span data-stu-id="f281e-103">supports all languages that are supported by Windows operating systems.</span></span>  
  
## <a name="cross-language-support"></a><span data-ttu-id="f281e-104">跨语言支持</span><span class="sxs-lookup"><span data-stu-id="f281e-104">Cross-Language Support</span></span>  
  
-   <span data-ttu-id="f281e-105">所有操作系统的本地化版本均支持 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 英文版。</span><span class="sxs-lookup"><span data-stu-id="f281e-105">The English-language version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is supported on all localized versions of operating systems.</span></span>  
  
-   <span data-ttu-id="f281e-106">通过使用 Windows 多语言用户界面包 (MUI) 设置，具有相应语言的已本地化的操作系统或者支持的操作系统的英文版本支持 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的本地化版本。</span><span class="sxs-lookup"><span data-stu-id="f281e-106">Localized versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are supported on localized operating systems with the corresponding language or on English-language versions of supported operating systems by using the Windows Multilingual User Interface Pack (MUI) settings.</span></span> <span data-ttu-id="f281e-107">有关详细信息，请参阅 [Configure Operating System to Support Localized Versions](../../../2014/sql-server/install/local-language-versions-in-sql-server.md#BK_ConfigureOS)。</span><span class="sxs-lookup"><span data-stu-id="f281e-107">For more information, see [Configure Operating System to Support Localized Versions](../../../2014/sql-server/install/local-language-versions-in-sql-server.md#BK_ConfigureOS).</span></span>  
  
-   <span data-ttu-id="f281e-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的本地化版本只能升级到同一语言的本地化版本，并且不能升级到英文版本。</span><span class="sxs-lookup"><span data-stu-id="f281e-108">Localized versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can only be upgraded to localized versions of the same language, and cannot be upgraded to the English-language version.</span></span>  
  
-   <span data-ttu-id="f281e-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的本地化版本也可以与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的英文实例并行安装。</span><span class="sxs-lookup"><span data-stu-id="f281e-109">Localized versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can also be installed side by side with English-language instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
##  <a name="configure-operating-system-to-support-localized-versions"></a><a name="BK_ConfigureOS"></a> <span data-ttu-id="f281e-110">Configure Operating System to Support Localized Versions</span><span class="sxs-lookup"><span data-stu-id="f281e-110">Configure Operating System to Support Localized Versions</span></span>  
 <span data-ttu-id="f281e-111">在支持的操作系统的英文版上，通过使用 Windows 多语言用户界面包 (MUI) 设置，支持使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的本地化版本。</span><span class="sxs-lookup"><span data-stu-id="f281e-111">Localized versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are supported on English-language versions of supported operating systems through the use of Windows Multilingual User Interface Pack (MUI) settings.</span></span>  
  
 <span data-ttu-id="f281e-112">不过，在运行英语版操作系统（具有非英文 MUI 设置）的服务器上安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的本地化版本之前，必须先验证某些操作系统设置。</span><span class="sxs-lookup"><span data-stu-id="f281e-112">However, you must verify certain operating system settings before installing a localized version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on a server that is running an English-language operating system with a non-English MUI setting.</span></span> <span data-ttu-id="f281e-113">需要验证下列操作系统设置是否匹配要安装的本地化 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的语言：</span><span class="sxs-lookup"><span data-stu-id="f281e-113">You need to verify that the following operating system settings match the language of the localized [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to be installed:</span></span>  
  
-   <span data-ttu-id="f281e-114">操作系统用户界面设置</span><span class="sxs-lookup"><span data-stu-id="f281e-114">The operating system user interface setting</span></span>  
  
-   <span data-ttu-id="f281e-115">操作系统用户区域设置</span><span class="sxs-lookup"><span data-stu-id="f281e-115">The operating system user locale setting</span></span>  
  
-   <span data-ttu-id="f281e-116">系统区域设置</span><span class="sxs-lookup"><span data-stu-id="f281e-116">The system locale setting</span></span>  
  
 <span data-ttu-id="f281e-117">如果这些设置与要安装的本地化 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的语言不匹配，请使用下列过程正确设置这些操作系统设置。</span><span class="sxs-lookup"><span data-stu-id="f281e-117">If the settings do not match the language of the localized [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to be installed, then use the following procedures to correctly set these operating system settings.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="f281e-118">不支持在同一台计算机上安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的不同语言版本。</span><span class="sxs-lookup"><span data-stu-id="f281e-118">Installations of different language versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances on the same computer are not supported.</span></span>  
  
#### <a name="to-change-the-operating-system-user-interface-setting"></a><span data-ttu-id="f281e-119">更改操作系统用户界面设置</span><span class="sxs-lookup"><span data-stu-id="f281e-119">To change the operating system user interface setting</span></span>  
  
1.  <span data-ttu-id="f281e-120">安装与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的本地化版本匹配的操作系统 MUI（如果尚未安装）。</span><span class="sxs-lookup"><span data-stu-id="f281e-120">If not already installed, install the operating system MUI that matches your localized version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="f281e-121">在 Control Panel 中，打开 **Regional and Language Options**。</span><span class="sxs-lookup"><span data-stu-id="f281e-121">In Control Panel, open **Regional and Language Options**.</span></span>  
  
3.  <span data-ttu-id="f281e-122">在 **Languages** 选项卡上，从列表中为 **Language used in menus and dialogs**选择一个值。</span><span class="sxs-lookup"><span data-stu-id="f281e-122">On the **Languages** tab, for **Language used in menus and dialogs**, select a value from the list.</span></span>  
  
     <span data-ttu-id="f281e-123">此设置将影响 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的用户界面语言，所以它必须与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的本地化版本匹配。</span><span class="sxs-lookup"><span data-stu-id="f281e-123">This setting will affect the user interface language of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], so it must match your localized version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
4.  <span data-ttu-id="f281e-124">单击 **Apply** 确认更改，然后单击 **OK** 关闭窗口。</span><span class="sxs-lookup"><span data-stu-id="f281e-124">Click **Apply** to confirm the change, and **OK** to close the window.</span></span>  
  
#### <a name="to-change-the-operating-system-user-locale-setting"></a><span data-ttu-id="f281e-125">更改操作系统用户区域设置</span><span class="sxs-lookup"><span data-stu-id="f281e-125">To change the operating system user locale setting</span></span>  
  
1.  <span data-ttu-id="f281e-126">安装与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的本地化版本匹配的操作系统 MUI（如果尚未安装）。</span><span class="sxs-lookup"><span data-stu-id="f281e-126">If not already installed, install the operating system MUI that matches your localized version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="f281e-127">在 Control Panel 中，打开 **Regional and Language Options**。</span><span class="sxs-lookup"><span data-stu-id="f281e-127">In Control Panel, open **Regional and Language Options**.</span></span>  
  
3.  <span data-ttu-id="f281e-128">在 **Regional Options** 选项卡上，从列表中为 **Select an item to match its preferences**选择一个值。</span><span class="sxs-lookup"><span data-stu-id="f281e-128">On the **Regional Options** tab, for **Select an item to match its preferences**, select a value from the list.</span></span>  
  
     <span data-ttu-id="f281e-129">此设置将影响特定于区域性的数据格式。</span><span class="sxs-lookup"><span data-stu-id="f281e-129">This setting will affect culture-specific data formatting.</span></span>  
  
4.  <span data-ttu-id="f281e-130">单击 **Apply** 确认更改，然后单击 **OK** 关闭窗口。</span><span class="sxs-lookup"><span data-stu-id="f281e-130">Click **Apply** to confirm the change, and **OK** to close the window.</span></span>  
  
#### <a name="to-change-the-system-locale-setting"></a><span data-ttu-id="f281e-131">更改系统区域设置</span><span class="sxs-lookup"><span data-stu-id="f281e-131">To change the system locale setting</span></span>  
  
1.  <span data-ttu-id="f281e-132">安装与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的本地化版本匹配的操作系统 MUI（如果尚未安装）。</span><span class="sxs-lookup"><span data-stu-id="f281e-132">If not already installed, install the operating system MUI that matches your localized version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="f281e-133">在 Control Panel 中，打开 **Regional and Language Options**。</span><span class="sxs-lookup"><span data-stu-id="f281e-133">In Control Panel, open **Regional and Language Options**.</span></span>  
  
3.  <span data-ttu-id="f281e-134">在“高级”  选项卡上，从列表中为“选择一种语言来匹配要使用的非 Unicode 程序的语言版本”  选择一个值。</span><span class="sxs-lookup"><span data-stu-id="f281e-134">On the **Advanced** tab, for **Select a language to match the language version of the non-Unicode programs you want to use**, select a value from the list.</span></span>  
  
     <span data-ttu-id="f281e-135">此设置将使 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装程序可以为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装选择最佳默认排序规则。</span><span class="sxs-lookup"><span data-stu-id="f281e-135">This setting will allow [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup to choose the best default collation for your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation.</span></span>  
  
4.  <span data-ttu-id="f281e-136">单击 **Apply** 确认更改，然后单击 **OK** 关闭窗口。</span><span class="sxs-lookup"><span data-stu-id="f281e-136">Click **Apply** to confirm the change, and **OK** to close the window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f281e-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f281e-137">See Also</span></span>  
 <span data-ttu-id="f281e-138">[安装 SQL Server 2014 的硬件和软件要求](hardware-and-software-requirements-for-installing-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f281e-138">[Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md) </span></span>  
 [<span data-ttu-id="f281e-139">安装 SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="f281e-139">Install SQL Server 2014</span></span>](../../database-engine/install-windows/install-sql-server.md)  
  
  
