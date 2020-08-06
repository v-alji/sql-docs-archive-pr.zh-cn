---
title: SQLConnect |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLConnect function
ms.assetid: 6da74e3a-4388-4907-81cb-987389bae467
author: rothja
ms.author: jroth
ms.openlocfilehash: 43b37ae16638e461e37edaead83cd9ceedc1c86d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586660"
---
# <a name="sqlconnect"></a><span data-ttu-id="c9232-102">SQLConnect</span><span class="sxs-lookup"><span data-stu-id="c9232-102">SQLConnect</span></span>
  <span data-ttu-id="c9232-103">当打开连接时，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 将 SQL_COPT_SS_MUTUALLY_AUTHENTICATED 和 SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD 设置为用于打开此连接的身份验证方法。</span><span class="sxs-lookup"><span data-stu-id="c9232-103">When a connection is opened, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client sets SQL_COPT_SS_MUTUALLY_AUTHENTICATED and SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD to the authentication method used to open the connection.</span></span> <span data-ttu-id="c9232-104">有关 Spn 的详细信息，请参阅[&#40;ODBC&#41;的客户端连接中的服务主体名称 &#40;spn&#41; ](../native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="c9232-104">For more information about SPNs, see [Service Principal Names &#40;SPNs&#41; in Client Connections &#40;ODBC&#41;](../native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md).</span></span>  
  
## <a name="sqlconnect-support-for-high-availability-disaster-recovery"></a><span data-ttu-id="c9232-105">对高可用性、灾难恢复的 SQLConnect 支持</span><span class="sxs-lookup"><span data-stu-id="c9232-105">SQLConnect Support for High Availability, Disaster Recovery</span></span>  
 <span data-ttu-id="c9232-106">有关使用**SQLConnect**连接到群集的详细信息 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] ，请参阅[高可用性和灾难恢复的 SQL Server Native Client 支持](../native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)。</span><span class="sxs-lookup"><span data-stu-id="c9232-106">For more information on using **SQLConnect** to connect to a [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] cluster, see [SQL Server Native Client Support for High Availability, Disaster Recovery](../native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9232-107">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c9232-107">See Also</span></span>  
 <span data-ttu-id="c9232-108">[SQLConnect 函数](https://go.microsoft.com/fwlink/?LinkId=101541) </span><span class="sxs-lookup"><span data-stu-id="c9232-108">[SQLConnect Function](https://go.microsoft.com/fwlink/?LinkId=101541) </span></span>  
 [<span data-ttu-id="c9232-109">ODBC API 实现细节</span><span class="sxs-lookup"><span data-stu-id="c9232-109">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
