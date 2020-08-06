---
title: ProtocolOrder 属性 (ClientNetworkProtocol 类) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- ProtocolOrder Property (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- ProtocolOrder property
ms.assetid: aa09b8ab-37db-4406-8973-acf503855fd2
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8bccb7109972dea4697e9e289081cbf47d2f9492
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87591194"
---
# <a name="protocolorder-property-clientnetworkprotocol-class"></a><span data-ttu-id="12b50-102">ProtocolOrder 属性（ClientNetworkProtocol 类）</span><span class="sxs-lookup"><span data-stu-id="12b50-102">ProtocolOrder Property (ClientNetworkProtocol Class)</span></span>
  <span data-ttu-id="12b50-103">获取[SetOrderValue 方法 (ClientNetworkProtocol 类) ](clientnetworkprotocol-class.md)方法指定的当前引用的客户端网络协议的序号。</span><span class="sxs-lookup"><span data-stu-id="12b50-103">Gets the order number of the currently referenced client network protocol as specified by the [SetOrderValue Method (ClientNetworkProtocol Class)](clientnetworkprotocol-class.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12b50-104">语法</span><span class="sxs-lookup"><span data-stu-id="12b50-104">Syntax</span></span>  
  
```  
  
object  
.ProtocolOrder [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="12b50-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="12b50-105">Parts</span></span>  
 <span data-ttu-id="12b50-106">对象</span><span class="sxs-lookup"><span data-stu-id="12b50-106">*object*</span></span>  
 <span data-ttu-id="12b50-107">一个表示客户端使用的网络协议的[ClientNetworkProtocol 类](clientnetworkprotocol-class.md)对象 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="12b50-107">A [ClientNetworkProtocol Class](clientnetworkprotocol-class.md) object that represents the network protocol used by the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="12b50-108">属性值/返回值</span><span class="sxs-lookup"><span data-stu-id="12b50-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="12b50-109">一个 `uint32` 值，用于指定按照 `OrderValue` 方法设置的当前所引用的客户端网络协议的序号。</span><span class="sxs-lookup"><span data-stu-id="12b50-109">A `uint32` value that specifies the order number of the currently referenced client network protocol as set by the `OrderValue` method.</span></span> <span data-ttu-id="12b50-110">如果客户端网络协议为禁用状态，则此值将为零。</span><span class="sxs-lookup"><span data-stu-id="12b50-110">If the client network protocol is disabled, this value will be zero.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12b50-111">备注</span><span class="sxs-lookup"><span data-stu-id="12b50-111">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12b50-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="12b50-112">See Also</span></span>  
 <span data-ttu-id="12b50-113">[配置客户端协议](https://technet.microsoft.com/library/ms181035.aspx) </span><span class="sxs-lookup"><span data-stu-id="12b50-113">[Configure Client Protocols](https://technet.microsoft.com/library/ms181035.aspx) </span></span>  
 [<span data-ttu-id="12b50-114">配置客户端网络协议和网络库</span><span class="sxs-lookup"><span data-stu-id="12b50-114">Configuring Client Network Protocols and Net-Libraries</span></span>](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
