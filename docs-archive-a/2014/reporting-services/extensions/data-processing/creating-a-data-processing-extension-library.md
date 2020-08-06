---
title: 创建数据处理扩展插件库 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], namespace assignments
- library [Reporting Services]
- assigning namespaces to extensions
ms.assetid: 82f4b71b-dd39-467d-8d8c-6771eb2b12de
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a3c14ed699e94c7d8ed0f6f3d727e9ba6e355b7e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87694353"
---
# <a name="creating-a-data-processing-extension-library"></a><span data-ttu-id="9d4e6-102">创建数据处理扩展插件库</span><span class="sxs-lookup"><span data-stu-id="9d4e6-102">Creating a Data Processing Extension Library</span></span>
  <span data-ttu-id="9d4e6-103">您创建的每个 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 数据处理扩展插件都应分配到唯一的命名空间并被内置到某个库或程序集文件中。</span><span class="sxs-lookup"><span data-stu-id="9d4e6-103">Each [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension you create should be assigned to a unique namespace and built into a library or assembly file.</span></span> <span data-ttu-id="9d4e6-104">命名空间的确切名称并不重要，但命名空间必须是唯一的且不能与任何其他扩展插件共享。</span><span class="sxs-lookup"><span data-stu-id="9d4e6-104">The exact name of the namespace is not important, but it must be unique and not shared with any other extension.</span></span> [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="9d4e6-105">可以将命名空间 <xref:Microsoft.ReportingServices.DataProcessing> 用于 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 提供的数据处理扩展插件。</span><span class="sxs-lookup"><span data-stu-id="9d4e6-105">uses the namespace <xref:Microsoft.ReportingServices.DataProcessing> for the data processing extensions that ship with [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="9d4e6-106">您应该为公司的数据处理扩展插件创建您自己的唯一命名空间。</span><span class="sxs-lookup"><span data-stu-id="9d4e6-106">You should create your own unique namespaces for your company's data processing extensions.</span></span>  
  
 <span data-ttu-id="9d4e6-107">以下示例说明开始某个 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 数据处理扩展插件的代码，此扩展插件使用包含数据处理接口和任何实用工具类的命名空间。</span><span class="sxs-lookup"><span data-stu-id="9d4e6-107">The following example shows the code to begin a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension, which uses the namespaces that contain the data processing interfaces and any utility classes.</span></span>  
  
```vb  
Imports System  
Imports Microsoft.ReportingServices.DataProcessing  
Imports Microsoft.ReportingServices.Interfaces  
  
Namespace CompanyName.ExtensionName  
   ...  
```  
  
```csharp  
using System;  
using Microsoft.ReportingServices.DataProcessing;  
using Microsoft.ReportingServices.Interfaces;  
  
namespace CompanyName.ExtensionName  
{  
   ...  
```  
  
 <span data-ttu-id="9d4e6-108">当编译 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 数据处理扩展插件时，因为此处包含数据处理扩展插件接口，所以您必须向编译器提供对于 Microsoft.ReportingServices.Interfaces.dll 的引用。</span><span class="sxs-lookup"><span data-stu-id="9d4e6-108">When compiling a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension, you must supply to the compiler a reference to Microsoft.ReportingServices.Interfaces.dll, because the data processing extension interfaces are contained there.</span></span> <span data-ttu-id="9d4e6-109">实现数据处理扩展插件接口需要 <xref:Microsoft.ReportingServices.DataProcessing> 命名空间，而实现 <xref:Microsoft.ReportingServices.Interfaces> 接口需要 <xref:Microsoft.ReportingServices.Interfaces.IExtension> 命名空间。</span><span class="sxs-lookup"><span data-stu-id="9d4e6-109">The <xref:Microsoft.ReportingServices.DataProcessing> namespace is needed to implement the data processing extension interfaces, and the <xref:Microsoft.ReportingServices.Interfaces> namespace is needed to implement the <xref:Microsoft.ReportingServices.Interfaces.IExtension> interface.</span></span> <span data-ttu-id="9d4e6-110">例如，如果扩展名为 .cs 的所有文件（其中包含实现以 C# 编写的 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 数据处理扩展插件的代码）都位于单个目录中，则将从该目录发出以下命令，以编译存储在 CompanyName.ExtensionName.dll 中的文件。</span><span class="sxs-lookup"><span data-stu-id="9d4e6-110">For example, if all the files containing the code to implement a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extension written in C# were in a single directory with the extension .cs, the following command would be issued from that directory to compile the files stored in CompanyName.ExtensionName.dll.</span></span>  
  
```csharp  
csc /t:library /out:CompanyName.ExtensionName.dll *.cs /r:System.dll /r:Microsoft.ReportingServices.Interfaces.dll  
```  
  
 <span data-ttu-id="9d4e6-111">下面的代码示例展示了可用于扩展名为 .vb 的 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 文件的命令。</span><span class="sxs-lookup"><span data-stu-id="9d4e6-111">The following code example shows the command that would be used for [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] files with the extension .vb.</span></span>  
  
```vb  
vbc /t:library /out:CompanyName.ExtensionName.dll *.vb /r:System.dll /r:Microsoft.ReportingServices.Interfaces.dll  
```  
  
> [!NOTE]  
>  <span data-ttu-id="9d4e6-112">还可以使用 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 设计、开发和生成数据处理扩展插件。</span><span class="sxs-lookup"><span data-stu-id="9d4e6-112">You can also design, develop, and build your data processing extension using [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="9d4e6-113">有关在 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 中开发程序集的详细信息，请参阅 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 文档。</span><span class="sxs-lookup"><span data-stu-id="9d4e6-113">For more information about developing assemblies in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], see your [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d4e6-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9d4e6-114">See Also</span></span>  
 <span data-ttu-id="9d4e6-115">[Reporting Services 扩展插件](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="9d4e6-115">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="9d4e6-116">[实现数据处理扩展插件](implementing-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="9d4e6-116">[Implementing a Data Processing Extension](implementing-a-data-processing-extension.md) </span></span>  
 [<span data-ttu-id="9d4e6-117">Reporting Services 扩展插件库</span><span class="sxs-lookup"><span data-stu-id="9d4e6-117">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
