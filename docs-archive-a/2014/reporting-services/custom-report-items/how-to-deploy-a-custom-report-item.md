---
title: 如何：部署自定义报表项 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom report items, deploying
ms.assetid: 80e97b0d-e355-4240-aebd-08cbc84089ed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 66519610526478caadeb41b48c9823414e88d5d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693654"
---
# <a name="how-to-deploy-a-custom-report-item"></a><span data-ttu-id="827ee-102">如何：部署自定义报表项</span><span class="sxs-lookup"><span data-stu-id="827ee-102">How to: Deploy a Custom Report Item</span></span>
  <span data-ttu-id="827ee-103">若要在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中部署自定义报表项，必须修改报表服务器配置文件，并将设计时和运行时组件程序集复制到报表设计器和报表服务器的相应应用程序文件夹中。</span><span class="sxs-lookup"><span data-stu-id="827ee-103">To deploy a custom report item in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you must modify the report server configuration files and copy the design-time and run-time component assemblies into the appropriate application folders for both Report Designer and the report server.</span></span>  
  
### <a name="to-deploy-a-custom-report-item"></a><span data-ttu-id="827ee-104">部署自定义报表项</span><span class="sxs-lookup"><span data-stu-id="827ee-104">To deploy a custom report item</span></span>  
  
1.  <span data-ttu-id="827ee-105">编辑 Rsreportdesigner.config 文件，以配置供在相应设计器中使用的自定义报表项运行时组件和设计时组件。</span><span class="sxs-lookup"><span data-stu-id="827ee-105">Edit the Rsreportdesigner.config file to configure the custom report item run-time and design-time components for use in the designer.</span></span> <span data-ttu-id="827ee-106">请注意，`ReportItemName` 条目必须与 `CustomReportItemAttribute` 类中使用的 `CustomReportItemDesigner` 属性匹配。</span><span class="sxs-lookup"><span data-stu-id="827ee-106">Note that the `ReportItemName` entry must match the `CustomReportItemAttribute` attribute used in your `CustomReportItemDesigner` class.</span></span> <span data-ttu-id="827ee-107">例如：</span><span class="sxs-lookup"><span data-stu-id="827ee-107">For example:</span></span>  
  
    ```  
    <ReportItems>  
       <ReportItem Name="Polygons" Type="PolygonsCRI.PolygonsCRI,PolygonsCRI"/>  
    </ReportItems>  
    <ReportItemDesigner>  
       <ReportItem Name="Polygons" Type="PolygonsCRI.PolygonsDesigner, PolygonsDesigner" />  
    </ReportItemDesigner>  
    <ReportItemConverter>  
       <Converter Source="Chart" Target="Polygons" Type="PolygonsCRI.PolygonsConverter, PolygonsDesigner" />  
    </ReportItemConverter>  
    ```  
  
2.  <span data-ttu-id="827ee-108">编辑 Rsreportserver.config 文件以注册自定义报表项运行时组件。</span><span class="sxs-lookup"><span data-stu-id="827ee-108">Edit the Rsreportserver.config file to register the custom report item run-time component.</span></span> <span data-ttu-id="827ee-109">例如：</span><span class="sxs-lookup"><span data-stu-id="827ee-109">For example:</span></span>  
  
    ```  
    <ReportItems>  
       <ReportItem Name="Polygons" Type="PolygonsCRI.PolygonsCRI,PolygonsCRI"/>  
    </ReportItems>  
    ```  
  
3.  <span data-ttu-id="827ee-110">编辑 Rsssrvpolicy.config 文件以添加用于为相应自定义报表项授予合适权限的 `CodeGroup`。</span><span class="sxs-lookup"><span data-stu-id="827ee-110">Edit the Rsssrvpolicy.config file to add a `CodeGroup` that grants the proper permissions to the custom report item.</span></span> <span data-ttu-id="827ee-111">例如：</span><span class="sxs-lookup"><span data-stu-id="827ee-111">For example:</span></span>  
  
    ```  
    <CodeGroup   
       class="UnionCodeGroup"   
       version="1"   
       PermissionSetName="FullTrust"  
       Description="This code group grants MyCustomReportItem.dll FullTrust permission. ">  
       <IMembershipCondition   
          class="UrlMembershipCondition"  
          version="1"  
       Url="C:\Program Files\Microsoft SQL Server\ MSRS10_50.SQLSERVER\Reporting Services\ReportServer\bin\MyCustomReportItem.dll" />  
    </CodeGroup>  
    ```  
  
4.  <span data-ttu-id="827ee-112">将相应自定义报表项运行时组件 DLL 复制到 %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies 和 \Program Files\Microsoft SQL Server\MSRS10_50.SQLSERVER\Reporting Services\ReportServer\bin 目录下。</span><span class="sxs-lookup"><span data-stu-id="827ee-112">Copy the custom report item run-time component DLL to the %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies and \Program Files\Microsoft SQL Server\MSRS10_50.SQLSERVER\Reporting Services\ReportServer\bin directories.</span></span>  
  
5.  <span data-ttu-id="827ee-113">将相应自定义报表项设计时组件 DLL 复制到 %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies 目录下。</span><span class="sxs-lookup"><span data-stu-id="827ee-113">Copy the custom report item design-time component DLL to the %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="827ee-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="827ee-114">See Also</span></span>  
 <span data-ttu-id="827ee-115">[Reporting Services 配置文件](../report-server/reporting-services-configuration-files.md) </span><span class="sxs-lookup"><span data-stu-id="827ee-115">[Reporting Services Configuration Files](../report-server/reporting-services-configuration-files.md) </span></span>  
 [<span data-ttu-id="827ee-116">自定义报表项类库</span><span class="sxs-lookup"><span data-stu-id="827ee-116">Custom Report Item Class Libraries</span></span>](custom-report-item-class-libraries.md)  
  
  
