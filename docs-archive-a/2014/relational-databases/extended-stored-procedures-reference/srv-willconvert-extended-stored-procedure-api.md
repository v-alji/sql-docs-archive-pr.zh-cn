---
title: srv_willconvert（扩展存储过程 API）| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_willconvert
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_willconvert
ms.assetid: 6f4db5fd-215a-461c-95e4-17697852733e
author: rothja
ms.author: jroth
ms.openlocfilehash: 0b9adfbd2a73b30cbfc0229b7942f79d3ddc1a82
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693894"
---
# <a name="srv_willconvert-extended-stored-procedure-api"></a><span data-ttu-id="8b169-102">srv_willconvert（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="8b169-102">srv_willconvert (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="8b169-103">请改用 CLR 集成。</span><span class="sxs-lookup"><span data-stu-id="8b169-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="8b169-104">确定特定数据类型转换在 ODS 库中是否可用。</span><span class="sxs-lookup"><span data-stu-id="8b169-104">Determines whether a specific data type conversion is available within the ODS Library.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b169-105">语法</span><span class="sxs-lookup"><span data-stu-id="8b169-105">Syntax</span></span>  
  
```  
  
BOOL srv_willconvert (  
int  
srctype  
,  
int  
desttype   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="8b169-106">参数</span><span class="sxs-lookup"><span data-stu-id="8b169-106">Arguments</span></span>  
 <span data-ttu-id="8b169-107">srctype\*\*</span><span class="sxs-lookup"><span data-stu-id="8b169-107">*srctype*</span></span>  
 <span data-ttu-id="8b169-108">指示要转换的数据的数据类型。</span><span class="sxs-lookup"><span data-stu-id="8b169-108">Indicates the data type of the data to be converted.</span></span> <span data-ttu-id="8b169-109">该参数可以为任意一种扩展存储过程 API 数据类型。</span><span class="sxs-lookup"><span data-stu-id="8b169-109">This parameter can be any of the Extended Stored Procedure API data types.</span></span>  
  
 <span data-ttu-id="8b169-110">desttype\*\*</span><span class="sxs-lookup"><span data-stu-id="8b169-110">*desttype*</span></span>  
 <span data-ttu-id="8b169-111">指示源数据要转换成的目标数据类型。</span><span class="sxs-lookup"><span data-stu-id="8b169-111">Indicates the data type to which the source data is converted.</span></span> <span data-ttu-id="8b169-112">该参数可以为任意一种扩展存储过程 API 数据类型。</span><span class="sxs-lookup"><span data-stu-id="8b169-112">This parameter can be any of the Extended Stored Procedure API data types.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="8b169-113">返回</span><span class="sxs-lookup"><span data-stu-id="8b169-113">Returns</span></span>  
 <span data-ttu-id="8b169-114">如果支持数据类型转换，则为 TRUE；否则为 FALSE。</span><span class="sxs-lookup"><span data-stu-id="8b169-114">TRUE if the data type conversion is supported; FALSE if the data type conversion is not supported.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b169-115">备注</span><span class="sxs-lookup"><span data-stu-id="8b169-115">Remarks</span></span>  
 <span data-ttu-id="8b169-116">有关每种数据类型的说明，请参阅[数据类型（扩展存储过程 API）](data-types-extended-stored-procedure-api.md)。</span><span class="sxs-lookup"><span data-stu-id="8b169-116">For a description of each data type, see [Data Types &#40;Extended Stored Procedure API&#41;](data-types-extended-stored-procedure-api.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8b169-117">应全面检查扩展存储过程的源代码，并在生产服务器中安装编译的 DLL 之前，对这些 DLL 进行测试。</span><span class="sxs-lookup"><span data-stu-id="8b169-117">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="8b169-118">有关安全检查和测试的信息，请访问此 [Microsoft 网站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="8b169-118">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b169-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8b169-119">See Also</span></span>  
 [<span data-ttu-id="8b169-120">srv_convert（扩展存储过程 API）</span><span class="sxs-lookup"><span data-stu-id="8b169-120">srv_convert &#40;Extended Stored Procedure API&#41;</span></span>](srv-convert-extended-stored-procedure-api.md)  
  
  
