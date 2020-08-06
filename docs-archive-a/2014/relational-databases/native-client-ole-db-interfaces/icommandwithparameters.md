---
title: ICommandWithParameters | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 66644c70-def7-46d8-8c47-b883292a0288
author: rothja
ms.author: jroth
ms.openlocfilehash: df3103181b3cad772e7d1c73068b8864bf591b73
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590191"
---
# <a name="icommandwithparameters"></a><span data-ttu-id="9c8e1-102">ICommandWithParameters</span><span class="sxs-lookup"><span data-stu-id="9c8e1-102">ICommandWithParameters</span></span>
  <span data-ttu-id="9c8e1-103">从 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 开始，数据库引擎中的改进功能允许 ICommandWithParameters::GetParameterInfo 获取关于预期结果的更准确描述。</span><span class="sxs-lookup"><span data-stu-id="9c8e1-103">Improvements in the database engine beginning with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] allow ICommandWithParameters::GetParameterInfo to obtain more accurate descriptions of the expected results.</span></span> <span data-ttu-id="9c8e1-104">这些更准确的结果可能与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以前版本中的 CommandWithParameters::GetParameterInfo 所返回的值有所不同。</span><span class="sxs-lookup"><span data-stu-id="9c8e1-104">These more accurate results may differ from the values returned by CommandWithParameters::GetParameterInfo in previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9c8e1-105">有关详细信息，请参阅[元数据发现](../native-client/features/metadata-discovery.md)。</span><span class="sxs-lookup"><span data-stu-id="9c8e1-105">For more information, see [Metadata Discovery](../native-client/features/metadata-discovery.md).</span></span>  
  
 <span data-ttu-id="9c8e1-106">同样从 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 开始，在调用 ICommandWithParameters::SetParameterInfo 时，传递给 pwszName 参数的值必须是有效的标识符\*\*。</span><span class="sxs-lookup"><span data-stu-id="9c8e1-106">Also beginning in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], when calling ICommandWithParameters::SetParameterInfo, the value passed to the *pwszName* parameter must be a valid identifier.</span></span> <span data-ttu-id="9c8e1-107">有关详细信息，请参阅 [Database Identifiers](../databases/database-identifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="9c8e1-107">For more information, see [Database Identifiers](../databases/database-identifiers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c8e1-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9c8e1-108">See Also</span></span>  
 [<span data-ttu-id="9c8e1-109">接口 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="9c8e1-109">Interfaces &#40;OLE DB&#41;</span></span>](../../database-engine/dev-guide/interfaces-ole-db.md)  
  
  
