---
title: 启用和禁用 Reporting Services 的客户端打印 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 0e709c96-7517-4547-8ef6-5632f8118524
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 031a7cd9b5da07b03b76b6bf49db63572a8fe546
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588277"
---
# <a name="enable-and-disable-client-side-printing-for-reporting-services"></a><span data-ttu-id="80051-102">启用和禁用 Reporting Services 的客户端打印</span><span class="sxs-lookup"><span data-stu-id="80051-102">Enable and Disable Client-Side Printing for Reporting Services</span></span>
  <span data-ttu-id="80051-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)]ActiveX 控件**RSClientPrint**为在浏览器中查看的报表提供客户端打印。</span><span class="sxs-lookup"><span data-stu-id="80051-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX control, **RSClientPrint**, provides client-side printing for reports viewed in a browser.</span></span> <span data-ttu-id="80051-104">该控件显示一个自定义打印对话框，它支持其他打印对话框常见的功能。</span><span class="sxs-lookup"><span data-stu-id="80051-104">The control displays a custom print dialog box that supports features common to other print dialog boxes.</span></span> <span data-ttu-id="80051-105">这些功能包括打印预览、指定特定页和范围的页面选择、页边距和打印方向等功能。</span><span class="sxs-lookup"><span data-stu-id="80051-105">The features include print preview, page selections for specifying specific pages and ranges, page margins, and orientation.</span></span> <span data-ttu-id="80051-106">虽然默认情况下将启用客户端打印功能，但是您也可以将其禁用，以禁止使用该功能。</span><span class="sxs-lookup"><span data-stu-id="80051-106">Although client-side printing is enabled by default, you can disable the feature to prevent it from being used.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="80051-107">下载 ActiveX 控件需要管理员权限。</span><span class="sxs-lookup"><span data-stu-id="80051-107">Downloading ActiveX controls requires administrator permissions.</span></span>  
  
## <a name="downloading-the-activex-control"></a><span data-ttu-id="80051-108">下载 ActiveX 控件</span><span class="sxs-lookup"><span data-stu-id="80051-108">Downloading the ActiveX Control</span></span>  
 <span data-ttu-id="80051-109">对于希望使用打印功能的每个用户来说，都必须下载并安装提供客户端打印功能的 ActiveX 控件。</span><span class="sxs-lookup"><span data-stu-id="80051-109">Each user who wants to use the print feature must download and install the ActiveX control that provides client print functionality.</span></span> <span data-ttu-id="80051-110">用户首次单击报表工具栏上的**打印机**图标时，Microsoft ActiveX 控件将下载到计算机。</span><span class="sxs-lookup"><span data-stu-id="80051-110">The first time a user clicks the **Printer** icon on the report toolbar, the Microsoft ActiveX control is downloaded to the computer.</span></span> <span data-ttu-id="80051-111">在下载该控件后，每当用户单击**打印机**图标时，都会显示 "**打印**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="80051-111">After the control is downloaded, the **Print** dialog box displays whenever the user clicks the **Printer** icon.</span></span>  
  
 <span data-ttu-id="80051-112">根据浏览器设置的不同，系统可能会提示用户安装控件，阻止用户安装控件，或者在后台透明地安装控件。</span><span class="sxs-lookup"><span data-stu-id="80051-112">Depending on browser settings, the user may be prompted to install the control, be prevented from installing the control, or have the control install transparently in the background.</span></span>  
  
 <span data-ttu-id="80051-113">对于 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer，可通过 Web 内容区域的 "**安全设置**" 页中的 " **ActiveX 控件和插件**" 节点来指定影响 ActiveX 控件下载和安装的设置。</span><span class="sxs-lookup"><span data-stu-id="80051-113">For [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer, settings that affect ActiveX control download and installation are specified through the **ActiveX controls and plug-ins** node in the **Security Settings** page for the Web content zone.</span></span> <span data-ttu-id="80051-114">以下设置基于 Web 区域安全首选项，确定用户是否可以下载和运行打印控件：</span><span class="sxs-lookup"><span data-stu-id="80051-114">The following settings determine whether users can download and run the print control, based on Web zone security preferences:</span></span>  
  
-   <span data-ttu-id="80051-115">下载已签名的 ActiveX 控件。</span><span class="sxs-lookup"><span data-stu-id="80051-115">Download signed ActiveX controls.</span></span>  
  
-   <span data-ttu-id="80051-116">对标记为可安全执行脚本的 ActiveX 控件执行脚本。</span><span class="sxs-lookup"><span data-stu-id="80051-116">Script ActiveX controls marked safe for scripting.</span></span>  
  
-   <span data-ttu-id="80051-117">运行 ActiveX 控件和插件。</span><span class="sxs-lookup"><span data-stu-id="80051-117">Run ActiveX controls and plug-ins.</span></span>  
  
 <span data-ttu-id="80051-118">希望使用**RSClientPrint**执行客户端打印的用户必须启用以下各项：</span><span class="sxs-lookup"><span data-stu-id="80051-118">Users who want to use **RSClientPrint** to perform client-side printing must enable the following:</span></span>  
  
-   <span data-ttu-id="80051-119">**下载已签名的 activex 控件**和**脚本 activex 控件**，并将其标记为安全，以便进行安装。</span><span class="sxs-lookup"><span data-stu-id="80051-119">**Download signed ActiveX controls** and **Script ActiveX control marked safe for scripting** for installation purposes.</span></span>  
  
-   <span data-ttu-id="80051-120">为正在进行的打印操作**运行 ActiveX 控件和插件**。</span><span class="sxs-lookup"><span data-stu-id="80051-120">**Run ActiveX controls and plug-ins** for ongoing print operations.</span></span>  
  
 <span data-ttu-id="80051-121">**RSClientPrint** ActiveX 控件已签名，这意味着它包含中的有效数字证书 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="80051-121">The **RSClientPrint** ActiveX control is signed, meaning it contains a valid digital certificate from [!INCLUDE[msCoName](../../includes/msconame-md.md)].</span></span>  
  
## <a name="enabling-and-disabling-client-side-printing"></a><span data-ttu-id="80051-122">启用和禁用客户端打印功能</span><span class="sxs-lookup"><span data-stu-id="80051-122">Enabling and Disabling Client-Side Printing</span></span>  
 <span data-ttu-id="80051-123">报表服务器管理员可以通过将 Report Server 系统属性**EnableClientPrinting**设置为来禁用打印功能 `false` 。</span><span class="sxs-lookup"><span data-stu-id="80051-123">Report server administrators have the option of disabling the print feature by setting the report server system property **EnableClientPrinting** to `false`.</span></span> <span data-ttu-id="80051-124">这将对该服务器管理的所有报表禁用客户端打印功能。</span><span class="sxs-lookup"><span data-stu-id="80051-124">This will disable client-side printing for all reports managed by that server.</span></span> <span data-ttu-id="80051-125">默认情况下， **EnableClientPrinting**设置为 `true` 。</span><span class="sxs-lookup"><span data-stu-id="80051-125">By default, **EnableClientPrinting** is set to `true`.</span></span> <span data-ttu-id="80051-126">您可以通过下列方式禁用客户端打印功能：</span><span class="sxs-lookup"><span data-stu-id="80051-126">You can disable client-side printing in the following ways:</span></span>  
  
-   <span data-ttu-id="80051-127">对于本机模式下的报表服务器 \*\*\*\*：</span><span class="sxs-lookup"><span data-stu-id="80051-127">For a **Native mode report server**:</span></span>  
  
    1.  <span data-ttu-id="80051-128">使用管理权限启动 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="80051-128">Start [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] with administrative privileges.</span></span>  
  
    2.  <span data-ttu-id="80051-129">连接到 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中的报表服务器实例。</span><span class="sxs-lookup"><span data-stu-id="80051-129">Connect to a report server instance in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
    3.  <span data-ttu-id="80051-130">右键单击报表服务器节点，然后单击“属性”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="80051-130">Right-click the report server node, and then click **Properties**.</span></span> <span data-ttu-id="80051-131">如果 **“属性”** 选项被禁用，请确认您是在使用管理权限启动 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="80051-131">If the **Properties** option is disabled, verify you started [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] with administrative privileges.</span></span>  
  
    4.  <span data-ttu-id="80051-132">选择 **"启用 ActiveX 客户端打印控件的下载"**。</span><span class="sxs-lookup"><span data-stu-id="80051-132">Select **Enable download for the ActiveX client print control**.</span></span>  
  
    5.  <span data-ttu-id="80051-133">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="80051-133">Click **OK**.</span></span>  
  
-   <span data-ttu-id="80051-134">对于 SharePoint 模式报表服务器 \*\*\*\*：</span><span class="sxs-lookup"><span data-stu-id="80051-134">For a **SharePoint mode report server**:</span></span>  
  
    1.  <span data-ttu-id="80051-135">在 SharePoint 管理中心中，单击 **“应用程序管理”**。</span><span class="sxs-lookup"><span data-stu-id="80051-135">In SharePoint Central Administration, click **Application Management**.</span></span>  
  
    2.  <span data-ttu-id="80051-136">单击 **“管理服务应用程序”**。</span><span class="sxs-lookup"><span data-stu-id="80051-136">Click **Manage service applications**.</span></span>  
  
    3.  <span data-ttu-id="80051-137">单击 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服务应用程序的名称，然后在 SharePoint 功能区中单击 "**管理**"。</span><span class="sxs-lookup"><span data-stu-id="80051-137">Click the name of your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application, and then click **Manage** in the SharePoint ribbon.</span></span>  
  
    4.  <span data-ttu-id="80051-138">单击 **“系统设置”**。</span><span class="sxs-lookup"><span data-stu-id="80051-138">Click **System Settings**.</span></span>  
  
    5.  <span data-ttu-id="80051-139">选择 **“启用客户端打印”**。</span><span class="sxs-lookup"><span data-stu-id="80051-139">Select **Enable Client Printing**.</span></span> <span data-ttu-id="80051-140">**“启用客户端打印”** 选项位于页面的底部附近。</span><span class="sxs-lookup"><span data-stu-id="80051-140">The **Enable Client Printing** option is near the bottom of the page.</span></span>  
  
    6.  <span data-ttu-id="80051-141">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="80051-141">Click **OK**.</span></span>  
  
-   <span data-ttu-id="80051-142">编写脚本或代码，以将 Report Server 系统属性**EnableClientPrinting**设置为`false.`</span><span class="sxs-lookup"><span data-stu-id="80051-142">Write script or code to set the report server system property **EnableClientPrinting** to `false.`</span></span>  
  
 <span data-ttu-id="80051-143">下面的示例脚本说明了一种禁用客户端打印功能的方法。</span><span class="sxs-lookup"><span data-stu-id="80051-143">The following sample script illustrates one approach for disabling client-side printing.</span></span> <span data-ttu-id="80051-144">编译并运行以下 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 代码，将 EnableClientPrinting\*\*\*\* 属性设置为 False\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="80051-144">Compile and then run the following [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] code to set the **EnableClientPrinting** property to **False**.</span></span> <span data-ttu-id="80051-145">在运行代码后，请重新启动 IIS。</span><span class="sxs-lookup"><span data-stu-id="80051-145">After you run the code, restart IIS.</span></span>  
  
### <a name="sample-script"></a><span data-ttu-id="80051-146">示例脚本</span><span class="sxs-lookup"><span data-stu-id="80051-146">Sample Script</span></span>  
  
```  
Imports System  
Imports System.Web.Services.Protocols  
Class Sample  
   Public Shared Sub Main()  
Dim rs As New ReportingService()  
      rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
        Dim props(0) As [Property]  
        Dim setProp As New [Property]  
        setProp.Name = "EnableClientPrinting"  
        setProp.Value = "False"   
        props(0) = setProp  
        Try  
            rs.SetSystemProperties(props)  
        Catch ex As System.Web.Services.Protocols.SoapException  
            Console.Write(ex.Detail.InnerXml)  
        Catch e as Exception  
            Console.Write(e.Message)  
        End Try  
    End Sub 'Main  
End Class 'Sample  
```  
  
  
