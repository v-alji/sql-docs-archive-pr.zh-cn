---
title: SqlXmlAdapter 对象 (SQLXML 托管类) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- void Update(DataSet ds) method
- SqlXmlAdapter object
- void Fill(DataSet ds) method
- SQLXML Managed Classes, SqlXmlAdapter object
- Managed Classes [SQLXML], SqlXmlAdapter object
ms.assetid: 0a16eddf-fc26-4d92-82d4-359b5fb905d5
author: rothja
ms.author: jroth
ms.openlocfilehash: 1357ab7d070c7c2e451e31bccfda22c58eac42d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87577492"
---
# <a name="sqlxmladapter-object-sqlxml-managed-classes"></a><span data-ttu-id="421e8-102">SqlXmlAdapter 对象（SQLXML 托管类）</span><span class="sxs-lookup"><span data-stu-id="421e8-102">SqlXmlAdapter Object (SQLXML Managed Classes)</span></span>
  <span data-ttu-id="421e8-103">此对象提供用于促进与 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework 中的数据集进行交互的方法。</span><span class="sxs-lookup"><span data-stu-id="421e8-103">This object provides methods that facilitate interaction with the dataset in the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework.</span></span> <span data-ttu-id="421e8-104">有关工作示例，请参阅[在 .Net 环境中访问 SQLXML 功能](accessing-sqlxml-functionality-in-the-net-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="421e8-104">For a working sample, see [Accessing SQLXML Functionality in the .NET Environment](accessing-sqlxml-functionality-in-the-net-environment.md).</span></span>  
  
 <span data-ttu-id="421e8-105">SqlXmlAdapter 对象支持以下方法：</span><span class="sxs-lookup"><span data-stu-id="421e8-105">The SqlXmlAdapter object supports these methods:</span></span>  
  
 <span data-ttu-id="421e8-106">void Fill (DataSet ds) </span><span class="sxs-lookup"><span data-stu-id="421e8-106">void Fill(DataSet ds)</span></span>  
 <span data-ttu-id="421e8-107">用从 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 检索的 XML 数据填充 .NET Framework 中的数据集。</span><span class="sxs-lookup"><span data-stu-id="421e8-107">Fills the dataset in the .NET Framework with the XML data retrieved from [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="421e8-108">void 更新 (DataSet ds) </span><span class="sxs-lookup"><span data-stu-id="421e8-108">void Update(DataSet ds)</span></span>  
 <span data-ttu-id="421e8-109">用数据集中的数据更新 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中的记录。</span><span class="sxs-lookup"><span data-stu-id="421e8-109">Applies updates to records in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] from the data in the dataset.</span></span>  
  
 <span data-ttu-id="421e8-110">SqlXmlAdapter 对象支持以下构造函数：</span><span class="sxs-lookup"><span data-stu-id="421e8-110">The SqlXmlAdapter object supports these constructors:</span></span>  
  
```  
public SqlXmlAdapter(SqlXmlCommand  cmd)   
  
public SqlXmlAdapter(  
                     string commandText,   
                     SqlXmlCommandType cmdType,   
                     string connectionString  
                      )   
  
public SqlXmlAdapter(  
                     Stream commandStream,   
                     SqlXmlCommandType cmdType,   
                     string connectionString  
                     )   
```  
  
## <a name="see-also"></a><span data-ttu-id="421e8-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="421e8-111">See Also</span></span>  
 <span data-ttu-id="421e8-112">[SQLXML 托管类 &#40;的 SqlXmlCommand 对象&#41;](sqlxml-4-0-net-framework-support-managed-classes.md) </span><span class="sxs-lookup"><span data-stu-id="421e8-112">[SqlXmlCommand Object &#40;SQLXML Managed Classes&#41;](sqlxml-4-0-net-framework-support-managed-classes.md) </span></span>  
 [<span data-ttu-id="421e8-113">SQLXML 托管类 &#40;的 SqlXmlParameter 对象&#41;</span><span class="sxs-lookup"><span data-stu-id="421e8-113">SqlXmlParameter Object &#40;SQLXML Managed Classes&#41;</span></span>](sqlxml-managed-classes-sqlxmlparameter-object.md)  
  
  
