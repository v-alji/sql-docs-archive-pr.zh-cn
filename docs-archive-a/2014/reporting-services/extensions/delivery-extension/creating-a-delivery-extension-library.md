---
title: 创建传递扩展插件库 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], namespace assignments
- library [Reporting Services]
- assigning namespaces to extensions
ms.assetid: 63b32f93-4bab-4b07-bd72-39a47aca1cda
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c9891c2b0c1bb9c7d495b3ab1f8f2267ce04b79f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693623"
---
# <a name="creating-a-delivery-extension-library"></a><span data-ttu-id="a2272-102">创建传递扩展插件库</span><span class="sxs-lookup"><span data-stu-id="a2272-102">Creating a Delivery Extension Library</span></span>
  <span data-ttu-id="a2272-103">您创建的每个 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 传递扩展插件都应分配到唯一的命名空间并被内置到某个库或程序集文件中。</span><span class="sxs-lookup"><span data-stu-id="a2272-103">Each [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] delivery extension you create should be assigned to a unique namespace and built into a library or assembly file.</span></span> <span data-ttu-id="a2272-104">命名空间的确切名称并不重要，但命名空间必须是唯一的且不能与任何其他扩展插件共享。</span><span class="sxs-lookup"><span data-stu-id="a2272-104">The exact name of the namespace is not important, but it must be unique and not shared with any other extension.</span></span> <span data-ttu-id="a2272-105">您应该为公司的传递扩展插件创建您自己的唯一命名空间。</span><span class="sxs-lookup"><span data-stu-id="a2272-105">You should create your own unique namespaces for your company's delivery extensions.</span></span>  
  
 <span data-ttu-id="a2272-106">以下示例说明开始某个 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 传递扩展插件的代码，此扩展插件使用包含传递接口和任何实用工具类的命名空间。</span><span class="sxs-lookup"><span data-stu-id="a2272-106">The following example shows the code to begin a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] delivery extension, which uses the namespaces that contain the delivery interfaces and any utility classes.</span></span>  
  
```vb  
Imports System  
Imports Microsoft.ReportingServices.Interfaces  
  
Namespace CompanyName.ExtensionName  
   ...  
```  
  
```csharp  
using System;  
using Microsoft.ReportingServices.Interfaces;  
  
namespace CompanyName.ExtensionName  
{  
   ...  
```  
  
 <span data-ttu-id="a2272-107">当编译 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 传递扩展插件时，因为此处包含传递扩展插件接口和类，所以您必须向编译器提供对于 Microsoft.ReportingServices.Interfaces.dll 的引用。</span><span class="sxs-lookup"><span data-stu-id="a2272-107">When compiling a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] delivery extension, you must supply to the compiler a reference to Microsoft.ReportingServices.Interfaces.dll, because the delivery extension interfaces and classes are contained there.</span></span> <span data-ttu-id="a2272-108"><xref:Microsoft.ReportingServices.Interfaces> 命名空间是实现 <xref:Microsoft.ReportingServices.Interfaces.IExtension> 接口、<xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> 接口等所需的。</span><span class="sxs-lookup"><span data-stu-id="a2272-108">The <xref:Microsoft.ReportingServices.Interfaces> namespace is needed to implement the <xref:Microsoft.ReportingServices.Interfaces.IExtension> interface, the <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> interface, and more.</span></span> <span data-ttu-id="a2272-109">例如，如果所有文件（其中包含实现以 C# 编写的 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 传递扩展插件的代码）都位于扩展名为 .cs 的单个目录中，则将从该目录发出以下命令，以编译存储在 CompanyName.ExtensionName.dll 中的文件。</span><span class="sxs-lookup"><span data-stu-id="a2272-109">For example, if all the files containing the code to implement a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] delivery extension written in C# were in a single directory with the extension .cs, the following command would be issued from that directory to compile the files stored in CompanyName.ExtensionName.dll.</span></span>  
  
```csharp  
csc /t:library /out:CompanyName.ExtensionName.dll *.cs /r:System.dll   
/r:Microsoft.ReportingServices.Interfaces.dll  
```  
  
 <span data-ttu-id="a2272-110">下面的代码示例展示了可用于扩展名为 .vb 的 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 文件的命令。</span><span class="sxs-lookup"><span data-stu-id="a2272-110">The following code example shows the command that would be used for [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] files with the extension .vb.</span></span>  
  
```vb  
vbc /t:library /out:CompanyName.ExtensionName.dll *.vb /r:System.dll   
/r:Microsoft.ReportingServices.Interfaces.dll  
```  
  
> [!NOTE]  
>  <span data-ttu-id="a2272-111">还可以使用 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 设计、开发和生成传递扩展插件。</span><span class="sxs-lookup"><span data-stu-id="a2272-111">You can also design, develop, and build your delivery extension using [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="a2272-112">有关在 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 中开发程序集的详细信息，请参阅 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 文档。</span><span class="sxs-lookup"><span data-stu-id="a2272-112">For more information about developing assemblies in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], see your [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2272-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a2272-113">See Also</span></span>  
 <span data-ttu-id="a2272-114">[Reporting Services 扩展插件](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="a2272-114">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="a2272-115">[实现传递扩展插件](implementing-a-delivery-extension.md) </span><span class="sxs-lookup"><span data-stu-id="a2272-115">[Implementing a Delivery Extension](implementing-a-delivery-extension.md) </span></span>  
 [<span data-ttu-id="a2272-116">Reporting Services 扩展插件库</span><span class="sxs-lookup"><span data-stu-id="a2272-116">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
