---
title: " (Upgrade Advisor) Report Server 上检测到自定义扩展插件 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- rendering extensions [Reporting Services], custom extensions
- security extensions [Reporting Services]
- custom extensions [Reporting Services]
- data processing extensions [Reporting Services], custom extensions
- delivery extensions [Reporting Services]
ms.assetid: fa184bd7-11d6-4ea3-9249-bc1b13db49e5
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: e4be596ff0f110515155f2aa14dc00aceaf85efd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579964"
---
# <a name="custom-extensions-were-detected-on-the-report-server-upgrade-advisor"></a><span data-ttu-id="f555d-102">在报表服务器上检测到自定义扩展插件（升级顾问）</span><span class="sxs-lookup"><span data-stu-id="f555d-102">Custom extensions were detected on the report server (Upgrade Advisor)</span></span>
  <span data-ttu-id="f555d-103">升级顾问在配置文件中检测到自定义扩展插件设置，这说明您的安装包括一个或多个用于进行数据处理、传递、呈现、安全或身份验证的自定义扩展插件。</span><span class="sxs-lookup"><span data-stu-id="f555d-103">Upgrade Advisor detected custom extension settings in the configuration files, indicating that your installation includes one or more custom extensions for data processing, delivery, rendering, security, or authentication.</span></span> <span data-ttu-id="f555d-104">升级操作将移动被升级的报表服务器上的扩展插件配置设置。</span><span class="sxs-lookup"><span data-stu-id="f555d-104">Upgrade will move the extension configuration settings with the upgraded report server.</span></span> <span data-ttu-id="f555d-105">但是，如果在现有报表服务器安装文件夹中安装了自定义扩展插件，则这些自定义扩展插件的程序集文件不会在升级过程期间移动到新安装文件夹。</span><span class="sxs-lookup"><span data-stu-id="f555d-105">However, if the custom extensions are installed in the existing report server installation folder, the assembly files for those custom extensions will not be moved to the new installation folder during the upgrade process.</span></span> <span data-ttu-id="f555d-106">在升级完成之后，必须将程序集文件移动到新的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安装文件夹。</span><span class="sxs-lookup"><span data-stu-id="f555d-106">After upgrade completes, you must move the assembly files to the new [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation folder.</span></span>  
  
||  
|-|  
|<span data-ttu-id="f555d-107">**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 本机模式 &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式。</span><span class="sxs-lookup"><span data-stu-id="f555d-107">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="f555d-108">组件</span><span class="sxs-lookup"><span data-stu-id="f555d-108">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="f555d-109">说明</span><span class="sxs-lookup"><span data-stu-id="f555d-109">Description</span></span>  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<span data-ttu-id="f555d-110">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]提供了一种可扩展的体系结构，使开发人员可以创建自定义扩展插件，用于数据处理、传递、呈现、安全和身份验证。</span><span class="sxs-lookup"><span data-stu-id="f555d-110">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] provides an extensible architecture that allows developers to create custom extensions for data processing, delivery, rendering, security, and authentication.</span></span>  
  
 <span data-ttu-id="f555d-111">如果在您的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安装中使用自定义扩展插件或程序集，则可以使用安装程序执行升级，但可能需要在升级完成之后将扩展插件移动到新的安装位置，否则可能需要在升级之前执行相应步骤。</span><span class="sxs-lookup"><span data-stu-id="f555d-111">If custom extensions or assemblies are used in your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation, you can use Setup to perform an upgrade, but you may need to move extensions to the new installation location after upgrade completes, or you may need to perform steps prior to upgrade.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f555d-112">升级顾问未检测到是否配置了用于在报表中计算项值、样式和格式的自定义代码程序集。</span><span class="sxs-lookup"><span data-stu-id="f555d-112">Upgrade Advisor does not detect whether custom code assemblies are configured for use in reports to calculate item values, styles, and formatting.</span></span> <span data-ttu-id="f555d-113">有关详细信息，请参阅[其他 Reporting Services 升级问题](../../../2014/sql-server/install/other-reporting-services-upgrade-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="f555d-113">For more information, see [Other Reporting Services Upgrade Issues](../../../2014/sql-server/install/other-reporting-services-upgrade-issues.md).</span></span>  
  
 <span data-ttu-id="f555d-114">如果购买了某个软件供应商的自定义扩展插件，请向供应商索取有关升级自定义功能的其他信息。</span><span class="sxs-lookup"><span data-stu-id="f555d-114">If you purchased custom extensions from a software vendor, check with the vendor for additional information about upgrading your custom functionality.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="f555d-115">纠正措施</span><span class="sxs-lookup"><span data-stu-id="f555d-115">Corrective Action</span></span>  
 <span data-ttu-id="f555d-116">使用以下几节可以确定除了执行 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的升级以外或在执行该操作之前要执行的步骤：</span><span class="sxs-lookup"><span data-stu-id="f555d-116">Use the following sections to determine steps to perform in addition to or prior to performing an upgrade of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]:</span></span>  
  
 [<span data-ttu-id="f555d-117">自定义数据处理或传递扩展插件</span><span class="sxs-lookup"><span data-stu-id="f555d-117">Custom data processing or delivery extensions</span></span>](#dataprocdeliver)  
  
 [<span data-ttu-id="f555d-118">自定义呈现扩展插件</span><span class="sxs-lookup"><span data-stu-id="f555d-118">Custom rendering extensions</span></span>](#render)  
  
 [<span data-ttu-id="f555d-119">SQL Server 2000 Report Server 上的自定义安全或身份验证扩展插件</span><span class="sxs-lookup"><span data-stu-id="f555d-119">Custom security or authentication extensions on a SQL Server 2000 report server</span></span>](#secauth2000)  
  
 [<span data-ttu-id="f555d-120">在 SQL Server 2005 报表服务器上自定义安全或身份验证扩展插件</span><span class="sxs-lookup"><span data-stu-id="f555d-120">Custom security or authentication extensions on a SQL Server 2005 report server</span></span>](#secauth2005)  
  
 <span data-ttu-id="f555d-121">在升级完成之后，请将扩展程序集移动到新安装文件夹，然后验证自定义扩展插件是否可按期望工作。</span><span class="sxs-lookup"><span data-stu-id="f555d-121">After upgrade completes, move the extension assemblies to the new installation folder and then verify that the custom extensions work as expected.</span></span> <span data-ttu-id="f555d-122">如果扩展插件不工作，则可能必须重新编译它。</span><span class="sxs-lookup"><span data-stu-id="f555d-122">If your extension does not work, you might have to recompile it.</span></span>  
  
#### <a name="to-recompile-an-extension"></a><span data-ttu-id="f555d-123">重新编译扩展插件</span><span class="sxs-lookup"><span data-stu-id="f555d-123">To recompile an extension</span></span>  
  
1.  <span data-ttu-id="f555d-124">将 Microsoft.ReportingServices.Interfaces.dll 文件复制到包含源代码的文件夹中。</span><span class="sxs-lookup"><span data-stu-id="f555d-124">Copy the Microsoft.ReportingServices.Interfaces.dll file to the folder that contains your source code.</span></span>  
  
2.  <span data-ttu-id="f555d-125">打开包含源文件的项目，并添加对 Microsoft.ReportingServices.Interfaces.dll 文件的引用。</span><span class="sxs-lookup"><span data-stu-id="f555d-125">Open the project that contains your source files and add a reference to the Microsoft.ReportingServices.Interfaces.dll file.</span></span>  
  
3.  <span data-ttu-id="f555d-126">重新生成解决方案以绑定扩展插件。</span><span class="sxs-lookup"><span data-stu-id="f555d-126">Rebuild the solution to bind the extension.</span></span>  
  
 <span data-ttu-id="f555d-127">如果决定不继续升级，则可能决定转而迁移 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f555d-127">If you decide not to continue with upgrade, you might decide to migrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instead.</span></span> <span data-ttu-id="f555d-128">有关迁移自定义扩展插件的步骤，请参阅本主题中的[迁移自定义扩展](#migrcustext)插件。</span><span class="sxs-lookup"><span data-stu-id="f555d-128">For steps on migrating custom extensions, see [Migrating custom extensions](#migrcustext) in this topic.</span></span>  
  
###  <a name="custom-data-processing-or-delivery-extensions"></a><a name="dataprocdeliver"></a><span data-ttu-id="f555d-129">自定义数据处理或传递扩展插件</span><span class="sxs-lookup"><span data-stu-id="f555d-129">Custom data processing or delivery extensions</span></span>  
 <span data-ttu-id="f555d-130">如果升级顾问检测到自定义数据处理或传递扩展插件，则不阻塞升级过程。</span><span class="sxs-lookup"><span data-stu-id="f555d-130">If Upgrade Advisor detects custom data processing or delivery extensions, the upgrade process is not blocked.</span></span> <span data-ttu-id="f555d-131">但是，在升级完成之后，可能需要先执行其他步骤，然后这些扩展插件提供的自定义功能才能工作。</span><span class="sxs-lookup"><span data-stu-id="f555d-131">However, after upgrade completes, you might need to perform additional steps before the custom functionality provided by these extensions will work.</span></span> <span data-ttu-id="f555d-132">例如，在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安装文件夹中安装自定义扩展插件文件时，必须执行其他步骤。</span><span class="sxs-lookup"><span data-stu-id="f555d-132">For example, you must perform additional steps when the custom extension files are installed in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation folder.</span></span>  
  
##### <a name="post-upgrade-steps-for-custom-data-processing-or-delivery-extensions"></a><span data-ttu-id="f555d-133">自定义数据处理或传递扩展插件的升级后步骤</span><span class="sxs-lookup"><span data-stu-id="f555d-133">Post-upgrade steps for custom data processing or delivery extensions</span></span>  
  
1.  <span data-ttu-id="f555d-134">将扩展插件文件移动到报表服务器的新程序文件夹。</span><span class="sxs-lookup"><span data-stu-id="f555d-134">Move the extension file or files to the new program folder for the report server.</span></span> <span data-ttu-id="f555d-135">默认情况下，Report Server 程序文件夹位于 \Program Files\Microsoft SQL Server \ MSRS10_50 中。 \<*instance_name*>\report 服务器。</span><span class="sxs-lookup"><span data-stu-id="f555d-135">By default, the report server program folder is in \Program Files\Microsoft SQL Server\MSRS10_50.\<*instance_name*>\report server.</span></span>  
  
 <span data-ttu-id="f555d-136">有关详细信息，请参阅 SQL Server 联机丛书中的“部署数据处理扩展插件”和“实现传递扩展插件”。</span><span class="sxs-lookup"><span data-stu-id="f555d-136">For more information, see "Deploying a Data Processing Extension" and "Implementing a Delivery Extension" in SQL Server Books Online.</span></span>  
  
###  <a name="custom-rendering-extensions"></a><a name="render"></a><span data-ttu-id="f555d-137">自定义呈现扩展插件</span><span class="sxs-lookup"><span data-stu-id="f555d-137">Custom rendering extensions</span></span>  
 <span data-ttu-id="f555d-138">如果升级顾问检测到自定义呈现扩展插件，则阻塞升级过程。</span><span class="sxs-lookup"><span data-stu-id="f555d-138">If Upgrade Advisor detects custom rendering extensions, the upgrade process is blocked.</span></span> <span data-ttu-id="f555d-139">通过从配置文件中删除自定义扩展插件配置项，可以继续执行升级过程。</span><span class="sxs-lookup"><span data-stu-id="f555d-139">You can continue with the upgrade process by removing the custom extension configuration entries from the configuration file.</span></span> <span data-ttu-id="f555d-140">但是，这将导致在升级完成之后自定义扩展插件对用户不可用。</span><span class="sxs-lookup"><span data-stu-id="f555d-140">However, this will cause the custom extensions to be unavailable to users after upgrade completes.</span></span> <span data-ttu-id="f555d-141">如果需要在升级之后自定义呈现扩展插件，必须生成更新的呈现扩展插件，或从自定义扩展插件供应商那里获得更新的呈现扩展插件。</span><span class="sxs-lookup"><span data-stu-id="f555d-141">If you need custom rendering extensions after upgrade, you must build updated rendering extensions or obtain updated rendering extensions from a custom extension vendor.</span></span>  
  
 <span data-ttu-id="f555d-142">必须执行相应步骤才能启用升级，否则可能选择迁移 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f555d-142">You must perform steps to enable an upgrade or you may chose to migrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instead.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f555d-143">请在已测试并验证更新的呈现扩展插件可以按期望工作后，才升级或迁移报表服务器。</span><span class="sxs-lookup"><span data-stu-id="f555d-143">Do not upgrade or migrate your report server until you have tested and verified that the updated rendering extension works as expected.</span></span>  
  
##### <a name="to-upgrade-custom-rendering-extensions"></a><span data-ttu-id="f555d-144">升级自定义呈现扩展插件</span><span class="sxs-lookup"><span data-stu-id="f555d-144">To upgrade custom rendering extensions</span></span>  
  
1.  <span data-ttu-id="f555d-145">获得带有最新接口的呈现扩展插件。</span><span class="sxs-lookup"><span data-stu-id="f555d-145">Obtain rendering extensions with the latest interfaces.</span></span>  
  
2.  <span data-ttu-id="f555d-146">从 RSReportServer.config 删除旧的自定义呈现扩展插件项。</span><span class="sxs-lookup"><span data-stu-id="f555d-146">Remove the old custom rendering extension entry or entries from RSReportServer.config.</span></span>  
  
3.  <span data-ttu-id="f555d-147">升级报表服务器。</span><span class="sxs-lookup"><span data-stu-id="f555d-147">Upgrade the report server.</span></span>  
  
4.  <span data-ttu-id="f555d-148">在升级完成之后，请在报表服务器上安装更新的扩展插件。</span><span class="sxs-lookup"><span data-stu-id="f555d-148">After upgrade completes, install the updated extensions on the report server.</span></span>  
  
 <span data-ttu-id="f555d-149">有关详细信息，请参阅 SQL Server 联机丛书中的“实现呈现扩展插件”。</span><span class="sxs-lookup"><span data-stu-id="f555d-149">For more information, see "Implementing a Rendering Extension" in SQL Server Books Online.</span></span>  
  
###  <a name="custom-security-or-authentication-extensions-on-a-sql-server-2000-report-server"></a><a name="secauth2000"></a><span data-ttu-id="f555d-150">SQL Server 2000 Report Server 上的自定义安全或身份验证扩展插件</span><span class="sxs-lookup"><span data-stu-id="f555d-150">Custom security or authentication extensions on a SQL Server 2000 report server</span></span>  
 <span data-ttu-id="f555d-151">如果升级顾问在 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 报表服务器上检测到自定义安全或身份验证扩展插件，则阻塞升级过程。</span><span class="sxs-lookup"><span data-stu-id="f555d-151">If Upgrade Advisor detects custom security or authentication extensions on a [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] report server, the upgrade process is blocked.</span></span> <span data-ttu-id="f555d-152">必须执行相应步骤才能启用升级，否则可能选择迁移 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f555d-152">You must perform steps to enable an upgrade or you may chose to migrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instead.</span></span> <span data-ttu-id="f555d-153">在两种情况下，都必须用 Microsoft.ReportingServices.Interfaces.dll 中的最新接口以更新和重新编译扩展插件，因为此接口已在 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 和 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 之间发生更改。</span><span class="sxs-lookup"><span data-stu-id="f555d-153">In either case, you must update and recompile the extensions with the latest interfaces in Microsoft.ReportingServices.Interfaces.dll, because the interfaces have changed between [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] and [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f555d-154">请在已测试并验证更新的安全或身份验证扩展插件可以按期望工作之后，才升级或迁移报表服务器。</span><span class="sxs-lookup"><span data-stu-id="f555d-154">Do not upgrade or migrate your report server until you have tested and verified that the updated security or authentication extension works as expected.</span></span>  
  
 <span data-ttu-id="f555d-155">如果使用的是为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2000 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 创建的自定义身份验证扩展插件，则必须修改源代码以支持为模型驱动报表引入的新的类和成员。</span><span class="sxs-lookup"><span data-stu-id="f555d-155">If you are using a custom authentication extension that you created for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2000 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you must modify the source code to support new classes and members introduced for model-driven reporting.</span></span>  
  
##### <a name="to-upgrade-custom-security-or-authentication-extensions-from-a-sql-server-2000-report-server"></a><span data-ttu-id="f555d-156">从 SQL Server 2000 Report Server 升级自定义安全或身份验证扩展插件</span><span class="sxs-lookup"><span data-stu-id="f555d-156">To upgrade custom security or authentication extensions from a SQL Server 2000 report server</span></span>  
  
1.  <span data-ttu-id="f555d-157">用最新接口更新并重新编译任何安全或身份验证扩展插件。</span><span class="sxs-lookup"><span data-stu-id="f555d-157">Update and recompile any security or authentication extensions with the latest interfaces.</span></span>  
  
2.  <span data-ttu-id="f555d-158">从 RSReportServer.config 删除安全或身份验证扩展插件项。</span><span class="sxs-lookup"><span data-stu-id="f555d-158">Remove the security or authentication extension entry or entries from RSReportServer.config.</span></span>  
  
3.  <span data-ttu-id="f555d-159">升级报表服务器。</span><span class="sxs-lookup"><span data-stu-id="f555d-159">Upgrade the report server.</span></span>  
  
4.  <span data-ttu-id="f555d-160">在升级完成之后，请在报表服务器上安装更新的扩展插件。</span><span class="sxs-lookup"><span data-stu-id="f555d-160">After upgrade completes, install the updated extensions on the report server.</span></span>  
  
 <span data-ttu-id="f555d-161">有关详细信息，请参阅 SQL Server 联机丛书中的“实现安全扩展插件”。</span><span class="sxs-lookup"><span data-stu-id="f555d-161">For more information, see "Implementing a Security Extension" in SQL Server Books Online.</span></span>  
  
###  <a name="custom-security-or-authentication-extensions-on-a-sql-server-2005-report-server"></a><a name="secauth2005"></a><span data-ttu-id="f555d-162">SQL Server 2005 Report Server 上的自定义安全或身份验证扩展插件</span><span class="sxs-lookup"><span data-stu-id="f555d-162">Custom security or authentication extensions on a SQL Server 2005 report server</span></span>  
 <span data-ttu-id="f555d-163">如果升级顾问在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 报表服务器上检测到自定义安全或身份验证扩展插件，则阻塞升级过程。</span><span class="sxs-lookup"><span data-stu-id="f555d-163">If Upgrade Advisor detects custom security or authentication extensions on a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] report server, the upgrade process is blocked.</span></span> <span data-ttu-id="f555d-164">必须执行相应步骤才能启用升级，否则可能选择迁移 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f555d-164">You must perform steps to enable an upgrade or you may chose to migrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instead.</span></span>  
  
##### <a name="to-upgrade-custom-security-or-authentication-extensions-from-a-sql-server-2005-report-server"></a><span data-ttu-id="f555d-165">从 SQL Server 2005 报表服务器升级自定义安全或身份验证扩展插件</span><span class="sxs-lookup"><span data-stu-id="f555d-165">To upgrade custom security or authentication extensions from a SQL Server 2005 report server</span></span>  
  
1.  <span data-ttu-id="f555d-166">从 RSReportServer.config 删除安全或身份验证扩展插件配置项。</span><span class="sxs-lookup"><span data-stu-id="f555d-166">Remove the security or authentication extension configuration entries from RSReportServer.config.</span></span>  
  
2.  <span data-ttu-id="f555d-167">升级报表服务器。</span><span class="sxs-lookup"><span data-stu-id="f555d-167">Upgrade the report server.</span></span>  
  
3.  <span data-ttu-id="f555d-168">升级完成之后，请在 RSReportServer.config 中添加配置项。</span><span class="sxs-lookup"><span data-stu-id="f555d-168">After upgrade completes, add the configuration entries back in RSReportServer.config.</span></span>  
  
4.  <span data-ttu-id="f555d-169">如果将扩展程序集安装在旧的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安装文件夹中，请将它们移动到新安装文件夹。</span><span class="sxs-lookup"><span data-stu-id="f555d-169">If the extension assemblies were installed in the old [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation folder, move then to the new installation folder.</span></span>  
  
 <span data-ttu-id="f555d-170">有关详细信息，请参阅 SQL Server 联机丛书中的“实现安全扩展插件”。</span><span class="sxs-lookup"><span data-stu-id="f555d-170">For more information, see "Implementing a Security Extension" in SQL Server Books Online.</span></span>  
  
###  <a name="migrating-custom-extensions"></a><a name="migrcustext"></a><span data-ttu-id="f555d-171">迁移自定义扩展插件</span><span class="sxs-lookup"><span data-stu-id="f555d-171">Migrating custom extensions</span></span>  
 <span data-ttu-id="f555d-172">如果决定迁移 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 而不执行升级，请执行相应步骤将自定义扩展插件迁移到新 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 实例。</span><span class="sxs-lookup"><span data-stu-id="f555d-172">If you decide to migrate [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instead performing an upgrade, use the steps to migrate custom extensions to the new [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance.</span></span>  
  
##### <a name="to-migrate-custom-extensions-to-a-new-reporting-services-instance"></a><span data-ttu-id="f555d-173">将自定义扩展插件迁移到新报表服务实例</span><span class="sxs-lookup"><span data-stu-id="f555d-173">To migrate custom extensions to a new Reporting Services instance</span></span>  
  
1.  <span data-ttu-id="f555d-174">生成或获得带有最新 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 接口的更新的扩展插件。</span><span class="sxs-lookup"><span data-stu-id="f555d-174">Build or obtain updated extensions with the latest [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] interfaces.</span></span>  
  
2.  <span data-ttu-id="f555d-175">将报表服务器迁移到新实例。</span><span class="sxs-lookup"><span data-stu-id="f555d-175">Migrate the report server to a new instance.</span></span>  
  
3.  <span data-ttu-id="f555d-176">在新实例上配置扩展插件。</span><span class="sxs-lookup"><span data-stu-id="f555d-176">Configure the extensions on the new instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f555d-177">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f555d-177">See Also</span></span>  
 [<span data-ttu-id="f555d-178">升级顾问 &#40;Reporting Services 升级问题&#41;</span><span class="sxs-lookup"><span data-stu-id="f555d-178">Reporting Services Upgrade Issues &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
