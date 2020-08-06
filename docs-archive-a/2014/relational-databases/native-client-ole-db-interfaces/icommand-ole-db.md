---
title: ICommand (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ICommand [SQL Server Native Client]
ms.assetid: 5e24b3a0-0658-44fc-b653-f4c52f9eb328
author: rothja
ms.author: jroth
ms.openlocfilehash: 03bdccc83a04078210f2283d0b330f237ed02979
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87590193"
---
# <a name="icommand-ole-db"></a><span data-ttu-id="c7141-102">ICommand (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="c7141-102">ICommand (OLE DB)</span></span>
  <span data-ttu-id="c7141-103">本主题讨论特定于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 的 OLE DB 行为。</span><span class="sxs-lookup"><span data-stu-id="c7141-103">This topic discusses OLE DB behavior that is specific to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
## <a name="icommandexecute"></a><span data-ttu-id="c7141-104">ICommand::Execute</span><span class="sxs-lookup"><span data-stu-id="c7141-104">ICommand::Execute</span></span>  
 <span data-ttu-id="c7141-105">如果插入的数据大于列的大小，通常会导致错误。</span><span class="sxs-lookup"><span data-stu-id="c7141-105">Inserting data that is greater than the size of a column typically results in an error.</span></span> <span data-ttu-id="c7141-106">但是，可能会出现将返回 S_OK、但 dwStatus 将设置为 DBSTATUS_S_TRUNCATED 的情况\*\*。</span><span class="sxs-lookup"><span data-stu-id="c7141-106">However, there are situations where S_OK will be returned but the *dwStatus* will be set to DBSTATUS_S_TRUNCATED.</span></span> <span data-ttu-id="c7141-107">当用参数插入数据时，通常会发生这种情况，列的大小不足以容纳数据，并且尚未 `ICommandWithParameters::SetParameterInfo` 调用。</span><span class="sxs-lookup"><span data-stu-id="c7141-107">This generally occurs when inserting data with parameters, where the column is not large enough to hold the data, and `ICommandWithParameters::SetParameterInfo` has not been called.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7141-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c7141-108">See Also</span></span>  
 [<span data-ttu-id="c7141-109">接口 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="c7141-109">Interfaces &#40;OLE DB&#41;</span></span>](../../database-engine/dev-guide/interfaces-ole-db.md)  
  
  
