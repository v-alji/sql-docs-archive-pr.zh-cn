---
title: SecureConnectionLevel 属性 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- SecureConnectionLevel
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SecureConnectionLevel property
ms.assetid: fd5549e7-b874-41e2-866e-2f58caf6f733
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5d1b3bccc8a7fee3899fa21208d83a718a33f5fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692156"
---
# <a name="secureconnectionlevel-property-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="b72d3-102">SecureConnectionLevel 属性 (WMI MSReportServer_ConfigurationSetting)</span><span class="sxs-lookup"><span data-stu-id="b72d3-102">SecureConnectionLevel Property (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="b72d3-103">返回 RSReportServer.config 文件中指定的安全连接级别。</span><span class="sxs-lookup"><span data-stu-id="b72d3-103">Returns the secure connection level specified in the RSReportServer.config file.</span></span> <span data-ttu-id="b72d3-104">只读。</span><span class="sxs-lookup"><span data-stu-id="b72d3-104">Read-only.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b72d3-105">语法</span><span class="sxs-lookup"><span data-stu-id="b72d3-105">Syntax</span></span>  
  
```vb  
Public Dim SecureConnectionLevel As Integer  
```  
  
```csharp  
public Integer SecureConnectionLevel;  
```  
  
## <a name="property-values"></a><span data-ttu-id="b72d3-106">属性值</span><span class="sxs-lookup"><span data-stu-id="b72d3-106">Property Values</span></span>  
 <span data-ttu-id="b72d3-107">一个 `Integer` 值，该值表示安全连接级别。</span><span class="sxs-lookup"><span data-stu-id="b72d3-107">An `Integer` value that represents the secure connection level.</span></span> <span data-ttu-id="b72d3-108">返回值表示是否配置 SSL。</span><span class="sxs-lookup"><span data-stu-id="b72d3-108">The return values indicate that the SSL is either configured or not.</span></span> <span data-ttu-id="b72d3-109">值大于或等于 1 表示打开了 SSL。</span><span class="sxs-lookup"><span data-stu-id="b72d3-109">A value of greater than or equal to 1 indicates that SSL is turned on.</span></span> <span data-ttu-id="b72d3-110">值为 0 表示关闭了 SSL。</span><span class="sxs-lookup"><span data-stu-id="b72d3-110">A value of 0 indicates that SSL is turned off.</span></span>  
  
## <a name="example-code"></a><span data-ttu-id="b72d3-111">示例代码</span><span class="sxs-lookup"><span data-stu-id="b72d3-111">Example Code</span></span>  
 [<span data-ttu-id="b72d3-112">MSReportServer_ConfigurationSetting 类</span><span class="sxs-lookup"><span data-stu-id="b72d3-112">MSReportServer_ConfigurationSetting Class</span></span>](msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a><span data-ttu-id="b72d3-113">要求</span><span class="sxs-lookup"><span data-stu-id="b72d3-113">Requirements</span></span>  
 <span data-ttu-id="b72d3-114">**命名空间：** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b72d3-114">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b72d3-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b72d3-115">See Also</span></span>  
 [<span data-ttu-id="b72d3-116">MSReportServer_ConfigurationSetting 成员</span><span class="sxs-lookup"><span data-stu-id="b72d3-116">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  
