---
title: 删除数据处理扩展插件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- deleting data processing extensions
- data processing extensions [Reporting Services], removing
- removing data processing extensions
ms.assetid: 1d89e32b-0631-44f6-8178-a57fb791d26d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9f5dfd3a6a7615fa3fd91c917bba6dbf0808f0f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693630"
---
# <a name="removing-a-data-processing-extension"></a><span data-ttu-id="04750-102">删除数据处理扩展插件</span><span class="sxs-lookup"><span data-stu-id="04750-102">Removing a Data Processing Extension</span></span>
  <span data-ttu-id="04750-103">要删除数据处理扩展插件，只需从配置文件中删除数据处理扩展插件的 Extension 元素\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="04750-103">To remove a data processing extension, simply remove the **Extension** element for your data processing extension from the configuration file.</span></span> <span data-ttu-id="04750-104">如果为报表服务器以及报表设计器生成了条目，则从 RSReportServer.config 文件和 RSReportDesigner.config 文件中删除 Extension 元素\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="04750-104">If you made entries for a report server as well as Report Designer, remove the **Extension** element from both the RSReportServer.config and RSReportDesigner.config files.</span></span> <span data-ttu-id="04750-105">在删除配置信息之后，该数据处理扩展插件对于该组件将不再可用。</span><span class="sxs-lookup"><span data-stu-id="04750-105">After the configuration information is removed, the data processing extension is no longer available to the component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04750-106">另请参阅</span><span class="sxs-lookup"><span data-stu-id="04750-106">See Also</span></span>  
 <span data-ttu-id="04750-107">[Reporting Services 扩展](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="04750-107">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="04750-108">[实现数据处理扩展插件](implementing-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="04750-108">[Implementing a Data Processing Extension](implementing-a-data-processing-extension.md) </span></span>  
 [<span data-ttu-id="04750-109">Reporting Services 扩展插件库</span><span class="sxs-lookup"><span data-stu-id="04750-109">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
