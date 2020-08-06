---
title: DatabaseQueryTimeout 属性 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- DatabaseQueryTimeout Property
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DatabaseQueryTimeout property
ms.assetid: 96faed97-9799-4bbf-a66f-fdd532d3eace
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2e92e3e0f6752ea99fe89c962ebe96e343c0195b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692165"
---
# <a name="databasequerytimeout-property-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="d478b-102">DatabaseQueryTimeout 属性 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="d478b-102">DatabaseQueryTimeout Property (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="d478b-103">指定必须经过多少秒后报表服务器才能假设命令失败或命令执行的时间过长。</span><span class="sxs-lookup"><span data-stu-id="d478b-103">Specifies the number of seconds that must elapse before the report server assumes the command failed or took too much time to perform.</span></span> <span data-ttu-id="d478b-104">报表服务器会根据 SQL 目录对查询进行计时，而不会根据报表的数据源计时。</span><span class="sxs-lookup"><span data-stu-id="d478b-104">The report server is timing the querying against the SQL catalog, not a data source for the report.</span></span> <span data-ttu-id="d478b-105">读/写。</span><span class="sxs-lookup"><span data-stu-id="d478b-105">Read/write.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d478b-106">语法</span><span class="sxs-lookup"><span data-stu-id="d478b-106">Syntax</span></span>  
  
```vb  
Public Dim DatabaseQueryTimeout As UInt32  
```  
  
```csharp  
public UInt32 DatabaseQueryTimeout;  
```  
  
## <a name="property-values"></a><span data-ttu-id="d478b-107">属性值</span><span class="sxs-lookup"><span data-stu-id="d478b-107">Property Values</span></span>  
 <span data-ttu-id="d478b-108">32 位的无符号 `integer` 对象，表示允许查询运行的秒数。</span><span class="sxs-lookup"><span data-stu-id="d478b-108">A 32-bit unsigned `integer` object that represents the number of seconds that the query is allowed to run.</span></span>  
  
## <a name="example-code"></a><span data-ttu-id="d478b-109">示例代码</span><span class="sxs-lookup"><span data-stu-id="d478b-109">Example Code</span></span>  
 [<span data-ttu-id="d478b-110">MSReportServer_ConfigurationSetting 类</span><span class="sxs-lookup"><span data-stu-id="d478b-110">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a><span data-ttu-id="d478b-111">要求</span><span class="sxs-lookup"><span data-stu-id="d478b-111">Requirements</span></span>  
 <span data-ttu-id="d478b-112">**命名空间：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d478b-112">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d478b-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d478b-113">See Also</span></span>  
 [<span data-ttu-id="d478b-114">MSReportServer_ConfigurationSetting 成员</span><span class="sxs-lookup"><span data-stu-id="d478b-114">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
