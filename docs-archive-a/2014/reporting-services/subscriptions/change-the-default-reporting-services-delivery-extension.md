---
title: 更改默认 Reporting Services 传递扩展插件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Report Manager [Reporting Services], default delivery extension
ms.assetid: 5f6fee72-01bf-4f6c-85d2-7863c46c136b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cc1b3af2a4fe3038b761d0b48030062da06d354e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691034"
---
# <a name="change-the-default-reporting-services-delivery-extension"></a><span data-ttu-id="71364-102">更改默认 Reporting Services 传递扩展插件</span><span class="sxs-lookup"><span data-stu-id="71364-102">Change the Default Reporting Services Delivery Extension</span></span>
  <span data-ttu-id="71364-103">你可以通过修改 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 配置设置，来更改显示在订阅定义页的“传递方式”  列表中的默认传递扩展插件。</span><span class="sxs-lookup"><span data-stu-id="71364-103">You can modify [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] configuration settings to change the default delivery extension that appears in the **Delivered by** list of a subscription definition page.</span></span> <span data-ttu-id="71364-104">例如，你可以修改该配置，以便在用户创建新订阅时，文件共享传递（而非电子邮件传递）默认处于选中状态。</span><span class="sxs-lookup"><span data-stu-id="71364-104">For example you can modify the configuration so that when users create a new subscription, file share delivery is selected by default instead of e-mail delivery.</span></span> <span data-ttu-id="71364-105">你还可以更改传递扩展插件在用户界面中的排列顺序。</span><span class="sxs-lookup"><span data-stu-id="71364-105">You can also change the order the delivery extensions are listed in the user interface.</span></span>

 <span data-ttu-id="71364-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 本机模式 | [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="71364-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Native mode | [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint mode</span></span>

 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="71364-107">同时包含“电子邮件”和“Windows 文件共享”这两种传递扩展插件。</span><span class="sxs-lookup"><span data-stu-id="71364-107">includes E-mail and Windows File Share delivery are extensions.</span></span> <span data-ttu-id="71364-108">如果您部署了自定义扩展插件或第三方扩展插件来支持自定义传递，则报表服务器可能具有其他传递扩展插件。</span><span class="sxs-lookup"><span data-stu-id="71364-108">Your report server might have additional delivery extensions if you have deployed custom or third-party extensions to support custom delivery.</span></span> <span data-ttu-id="71364-109">传递扩展插件的可用性取决于它是否在报表服务器上进行了部署。</span><span class="sxs-lookup"><span data-stu-id="71364-109">The availability of a delivery extension depends on whether it is deployed on a report server.</span></span>

## <a name="default-native-mode-report-server-configuration"></a><span data-ttu-id="71364-110">默认的本机模式报表服务器配置</span><span class="sxs-lookup"><span data-stu-id="71364-110">Default Native mode report server configuration</span></span>
 <span data-ttu-id="71364-111">报表管理器的“传递方式”  列表中传递扩展插件的显示顺序取决于 **RSReportServer.config** 文件中传递扩展插件项的顺序。</span><span class="sxs-lookup"><span data-stu-id="71364-111">The order of a delivery extension appears in Report Manager in the **Delivered by** list is based on the order of the delivery extension entries in the **RSReportServer.config** file.</span></span> <span data-ttu-id="71364-112">例如，下图显示列表中最先显示的是“电子邮件”，并且它默认处于选中状态。</span><span class="sxs-lookup"><span data-stu-id="71364-112">For example the following image shows e-mail first in the list and it is selected by default.</span></span>

 <span data-ttu-id="71364-113">![传递扩展插件的默认列表](../media/ssrs-default-delivery.png "传递扩展插件的默认列表")</span><span class="sxs-lookup"><span data-stu-id="71364-113">![default list of delivery extensions](../media/ssrs-default-delivery.png "default list of delivery extensions")</span></span>

 <span data-ttu-id="71364-114">以下是 **RSReportServer.config** 的默认部分，用于控制默认传递扩展插件及其在报表管理器中的显示顺序。</span><span class="sxs-lookup"><span data-stu-id="71364-114">The following is the default section of **RSReportServer.config** that controls the default delivery extension and the order they are displayed in Report Manager.</span></span> <span data-ttu-id="71364-115">请注意，“电子邮件”最先显示在该文件中，并且已设置为默认项。</span><span class="sxs-lookup"><span data-stu-id="71364-115">Note that email appears first in the file and it is set as the default.</span></span>

```xml
<DeliveryUI>
     <Extension Name="Report Server Email" Type="Microsoft.ReportingServices.EmailDeliveryProvider.EmailDeliveryProviderControl,ReportingServicesEmailDeliveryProvider">
          <DefaultDeliveryExtension>True</DefaultDeliveryExtension>
               <Configuration>
               <RSEmailDPConfiguration>
                    <DefaultRenderingExtension>MHTML</DefaultRenderingExtension>
               </RSEmailDPConfiguration>
               </Configuration>
     </Extension>
     <Extension Name="Report Server FileShare" Type="Microsoft.ReportingServices.FileShareDeliveryProvider.FileShareUIControl,ReportingServicesFileShareDeliveryProvider"/>
</DeliveryUI>
```

#### <a name="configure-file-share-delivery-as-the-default-delivery-extension-in-report-manager"></a><span data-ttu-id="71364-116">将“文件共享传递”配置为报表管理器中的默认传递扩展插件</span><span class="sxs-lookup"><span data-stu-id="71364-116">Configure File Share Delivery as the default delivery extension in Report Manager</span></span>

1.  <span data-ttu-id="71364-117">此过程中的步骤可用于修改该配置，以便“文件共享传递”可作为第一个选项列在 UI 中，并默认处于选中状态。</span><span class="sxs-lookup"><span data-stu-id="71364-117">The steps in this procedure modify the configuration so that file share delivery is listed as the first option in the UI and it is the default selection.</span></span>

     <span data-ttu-id="71364-118">在文本编辑器中打开 RSReportServer.config 文件。</span><span class="sxs-lookup"><span data-stu-id="71364-118">Open the RSReportServer.config file in a text editor.</span></span> <span data-ttu-id="71364-119">有关配置文件的详细信息，请参阅 [RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md)。</span><span class="sxs-lookup"><span data-stu-id="71364-119">For more information on the configuration file, see [RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md).</span></span> <span data-ttu-id="71364-120">更改该配置后，UI 的外观将类似于下图：</span><span class="sxs-lookup"><span data-stu-id="71364-120">After the configuration changes, the UI will look like the following image:</span></span>

     <span data-ttu-id="71364-121">![修改后的传递扩展插件的列表](../media/ssrs-modified-delivery.png "修改后的传递扩展插件的列表")</span><span class="sxs-lookup"><span data-stu-id="71364-121">![modified list of delivery extensions](../media/ssrs-modified-delivery.png "modified list of delivery extensions")</span></span>

2.  <span data-ttu-id="71364-122">将 DeliveryUI 部分修改为如以下示例所示，并注意关键更改：</span><span class="sxs-lookup"><span data-stu-id="71364-122">Modify the DeliveryUI section to look like the following sample and note the key changes of:</span></span>

    1.  <span data-ttu-id="71364-123">文件共享扩展插件位于电子邮件扩展插件之前。</span><span class="sxs-lookup"><span data-stu-id="71364-123">The FileShare extension is before the email extension.</span></span> <span data-ttu-id="71364-124">这将更改这两种扩展插件在报表管理器中的排列顺序。</span><span class="sxs-lookup"><span data-stu-id="71364-124">This will change the order the extensions are listed in Report Manager.</span></span>

    2.  <span data-ttu-id="71364-125">文件共享扩展插件包含 DefaultExtension 标记 `<DefaultDeliveryExtension>True</DefaultDeliveryExtension>` ，以及已添加 `</Extension>`的扩展插件结束标记。</span><span class="sxs-lookup"><span data-stu-id="71364-125">The File share extension contains DefaultExtension tag `<DefaultDeliveryExtension>True</DefaultDeliveryExtension>` and the extension end tag was added `</Extension>`.</span></span>

    3.  <span data-ttu-id="71364-126">电子邮件扩展插件不再配置为默认设置。</span><span class="sxs-lookup"><span data-stu-id="71364-126">The email extension is no longer configured as the default.</span></span> `<DefaultDeliveryExtension>False</DefaultDeliveryExtension>`

    ```
    <DeliveryUI>
         <Extension Name="Report Server FileShare" Type="Microsoft.ReportingServices.FileShareDeliveryProvider.FileShareUIControl,ReportingServicesFileShareDeliveryProvider">
              <DefaultDeliveryExtension>True</DefaultDeliveryExtension>
         </Extension>
         <Extension Name="Report Server Email" Type="Microsoft.ReportingServices.EmailDeliveryProvider.EmailDeliveryProviderControl,ReportingServicesEmailDeliveryProvider">
         <DefaultDeliveryExtension>False</DefaultDeliveryExtension>
         <Configuration>
              <RSEmailDPConfiguration>
                   <DefaultRenderingExtension>MHTML</DefaultRenderingExtension>
              </RSEmailDPConfiguration>
         </Configuration>
         </Extension>
    </DeliveryUI>
    ```

3.  <span data-ttu-id="71364-127">保存此配置文件。</span><span class="sxs-lookup"><span data-stu-id="71364-127">Save the configuration file.</span></span>

4.  <span data-ttu-id="71364-128">报表服务器将在几分钟内重新加载该配置文件，随后新设置将生效。</span><span class="sxs-lookup"><span data-stu-id="71364-128">Within a few minutes the report server will reload the configuration file and the new settings will take effect.</span></span> <span data-ttu-id="71364-129">你可以重新启动报表服务器服务，以强制加载配置文件。</span><span class="sxs-lookup"><span data-stu-id="71364-129">You can restart the report server service to force the loading of the configuration file.</span></span>

     <span data-ttu-id="71364-130">读取配置文件时，以下事件将被写入 Windows 事件日志中。</span><span class="sxs-lookup"><span data-stu-id="71364-130">The following event is written to the windows event log when the configuration is read.</span></span>

     <span data-ttu-id="71364-131">**事件 ID：** 109</span><span class="sxs-lookup"><span data-stu-id="71364-131">**Event ID:** 109</span></span>

     <span data-ttu-id="71364-132">**源：** 报表服务器 Windows 服务（实例名称）</span><span class="sxs-lookup"><span data-stu-id="71364-132">**Source:** Report Server Windows Service (instance name)</span></span>

     <span data-ttu-id="71364-133">已修改 RSReportServer.config 文件</span><span class="sxs-lookup"><span data-stu-id="71364-133">The RSReportServer.config file has been modified</span></span>

## <a name="sharepoint-mode-report-servers"></a><span data-ttu-id="71364-134">SharePoint 模式报表服务器</span><span class="sxs-lookup"><span data-stu-id="71364-134">SharePoint mode report servers</span></span>
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="71364-135">SharePoint 模式会将扩展插件信息存储在 SharePoint 服务应用程序数据库中，而非 RsrReportServer.config 文件中。</span><span class="sxs-lookup"><span data-stu-id="71364-135">SharePoint mode stores extensions information in the SharePoint service application databases and not in the RsrReportServer.config file.</span></span> <span data-ttu-id="71364-136">在 SharePoint 模式下，传递扩展插件配置将使用 PowerShell 进行修改。</span><span class="sxs-lookup"><span data-stu-id="71364-136">In SharePoint mode, delivery extension configuration is modified using PowerShell.</span></span>

#### <a name="configure-the-default-delivery-extension"></a><span data-ttu-id="71364-137">配置默认传递扩展插件</span><span class="sxs-lookup"><span data-stu-id="71364-137">Configure the default delivery extension</span></span>

1.  <span data-ttu-id="71364-138">打开“SharePoint Management Shell”  。</span><span class="sxs-lookup"><span data-stu-id="71364-138">Open the **SharePoint Management Shell**.</span></span>

2.  <span data-ttu-id="71364-139">如果你已经知道 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 服务应用程序的名称，则可以跳过此步骤。</span><span class="sxs-lookup"><span data-stu-id="71364-139">You can skip this step if you already know the name of your [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] service application.</span></span> <span data-ttu-id="71364-140">使用以下 PowerShell，将 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 服务应用程序列在 SharePoint 场中。</span><span class="sxs-lookup"><span data-stu-id="71364-140">Use the following PowerShell to list the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] service applications in your SharePoint farm.</span></span>

    ```powershell
    Get-SPRSServiceApplication | Format-List *
    ```

3.  <span data-ttu-id="71364-141">运行以下 PowerShell，验证 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 服务应用程序“ssrsapp”的当前默认传递扩展插件。</span><span class="sxs-lookup"><span data-stu-id="71364-141">Run the following PowerShell to verify the current default delivery extension for the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] service application "ssrsapp".</span></span>

    ```powershell
    $app = Get-SPRSServiceApplication | Where {$_.name -Like "ssrsapp*"};
    Get-SPRSExtension -Identity $app | Where {$_.ServerDirectivesXML -Like "<DefaultDelivery*"} | Format-List *
    ```

## <a name="see-also"></a><span data-ttu-id="71364-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="71364-142">See Also</span></span>
 <span data-ttu-id="71364-143">[Rsreportserver.config 配置文件](../report-server/rsreportserver-config-configuration-file.md) [rsreportserver.config 配置文件](../report-server/rsreportserver-config-configuration-file.md) [Reporting Services](file-share-delivery-in-reporting-services.md)中的[电子邮件传递 Reporting Services](e-mail-delivery-in-reporting-services.md)配置[报表服务器以进行电子邮件传递 &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)</span><span class="sxs-lookup"><span data-stu-id="71364-143">[RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md) [RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md) [File Share Delivery in Reporting Services](file-share-delivery-in-reporting-services.md) [E-Mail Delivery in Reporting Services](e-mail-delivery-in-reporting-services.md) [Configure a Report Server for E-Mail Delivery &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)</span></span>
