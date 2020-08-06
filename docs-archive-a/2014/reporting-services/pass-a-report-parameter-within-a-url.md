---
title: 在 URL 内传递报表参数 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- URL access [Reporting Services], passing parameters
- passing parameters [Reporting Services]
ms.assetid: f93a94cc-27b5-435a-aa85-69e6ec6459ad
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cf41ed82728d5d7c840276e135937b08f83fb131
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87692784"
---
# <a name="pass-a-report-parameter-within-a-url"></a><span data-ttu-id="c3ac1-102">Pass a Report Parameter Within a URL</span><span class="sxs-lookup"><span data-stu-id="c3ac1-102">Pass a Report Parameter Within a URL</span></span>
  <span data-ttu-id="c3ac1-103">您可以通过在报表 URL 中包含报表参数，将它们传递到报表。</span><span class="sxs-lookup"><span data-stu-id="c3ac1-103">You can pass report parameters to a report by including them in a report URL.</span></span> <span data-ttu-id="c3ac1-104">这些 URL 参数不带前缀，因为它们被直接传递到报表处理引擎。</span><span class="sxs-lookup"><span data-stu-id="c3ac1-104">These URL parameters are not prefixed because they are passed directly to the report processing engine.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c3ac1-105">非常重要的一点是，URL 包括用于通过 SharePoint 和 `_vti_bin` HTTP 代理路由请求的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 代理语法。</span><span class="sxs-lookup"><span data-stu-id="c3ac1-105">It is important the URL include the `_vti_bin` proxy syntax to route the request through SharePoint and the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] HTTP proxy.</span></span> <span data-ttu-id="c3ac1-106">该代理会向 HTTP 请求中添加某一上下文，该上下文是确保为 SharePoint 模式报表服务器正确执行报表所需要的。</span><span class="sxs-lookup"><span data-stu-id="c3ac1-106">The proxy adds some context to the HTTP request, context that is required to ensure proper execution of the report for SharePoint mode report servers.</span></span>  
>   
>  <span data-ttu-id="c3ac1-107">如果不包含代理语法，则需要为参数添加*rp：* 前缀。</span><span class="sxs-lookup"><span data-stu-id="c3ac1-107">If you don't include the proxy syntax, then you need to prefix the parameter with *rp:*.</span></span>  
  
 <span data-ttu-id="c3ac1-108">所有查询参数都可具有对应的报表参数。</span><span class="sxs-lookup"><span data-stu-id="c3ac1-108">All query parameters can have corresponding report parameters.</span></span> <span data-ttu-id="c3ac1-109">通过传递相应报表参数将查询参数传递给报表。</span><span class="sxs-lookup"><span data-stu-id="c3ac1-109">You pass a query parameter to a report by passing the corresponding report parameter.</span></span> <span data-ttu-id="c3ac1-110">有关详细信息，请参阅[在关系查询设计器中生成查询（报表生成器和 SSRS）](report-data/build-a-query-in-the-relational-query-designer-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="c3ac1-110">For more information, see [Build a Query in the Relational Query Designer &#40;Report Builder and SSRS&#41;](report-data/build-a-query-in-the-relational-query-designer-report-builder-and-ssrs.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c3ac1-111">报表参数区分大小写。</span><span class="sxs-lookup"><span data-stu-id="c3ac1-111">Report parameters are case-sensitive.</span></span>  
> 
> [!NOTE]
>  <span data-ttu-id="c3ac1-112">报表参数区分大小写并使用以下特殊字符：</span><span class="sxs-lookup"><span data-stu-id="c3ac1-112">Report parameters are case-sensitive and utilize the following special characters:</span></span>  
> 
>  -   <span data-ttu-id="c3ac1-113">URL 字符串中的任何空格字符将根据 URL 编码标准被字符“%20”替换。</span><span class="sxs-lookup"><span data-stu-id="c3ac1-113">Any space characters in the URL string are replaced with the characters "%20," according to URL encoding standards.</span></span>  
> -   <span data-ttu-id="c3ac1-114">URL 的参数部分中的空格字符将被加号字符 (+) 替换。</span><span class="sxs-lookup"><span data-stu-id="c3ac1-114">A space character in the parameter portion of the URL is replaced with a plus character (+).</span></span>  
> -   <span data-ttu-id="c3ac1-115">字符串任何部分中的分号将被字符“%3A”替换。</span><span class="sxs-lookup"><span data-stu-id="c3ac1-115">A semicolon in any portion of the string is replaced with the characters "%3A."</span></span>  
> -   <span data-ttu-id="c3ac1-116">浏览器应自动执行正确的 URL 编码。</span><span class="sxs-lookup"><span data-stu-id="c3ac1-116">Browsers should automatically perform the proper URL encoding.</span></span> <span data-ttu-id="c3ac1-117">您不必手动对任何字符进行编码。</span><span class="sxs-lookup"><span data-stu-id="c3ac1-117">You do not have to encode any of the characters manually.</span></span>  
  
 <span data-ttu-id="c3ac1-118">若要设置 URL 内的报表参数，请使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="c3ac1-118">To set a report parameter within a URL, use the following syntax:</span></span>  
  
```  
  
parameter=value  
```  
  
 <span data-ttu-id="c3ac1-119">例如，若要指定在报表中定义的两个参数“ReportMonth”和“ReportYear”，请将以下 URL 用于本机模式报表服务器：</span><span class="sxs-lookup"><span data-stu-id="c3ac1-119">For example, to specify two parameters, "ReportMonth" and "ReportYear", defined in a report, use the following URL for a native mode report server:</span></span>  
  
```  
http://myrshost/ReportServer?/AdventureWorks 2008R2/Employee_Sales_Summary_2008R2&ReportMonth=3&ReportYear=2008  
```  
  
 <span data-ttu-id="c3ac1-120">例如，若要指定在报表中定义的两个相同参数，请将以下 URL 用于 SharePoint 集成模式的报表服务器。</span><span class="sxs-lookup"><span data-stu-id="c3ac1-120">For example, to specify the same two parameters defined in a report, use the following URL for a SharePoint integrated mode report server.</span></span> <span data-ttu-id="c3ac1-121">注意 `/_vti_bin`：</span><span class="sxs-lookup"><span data-stu-id="c3ac1-121">Note the `/_vti_bin`:</span></span>  
  
```  
http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/AdventureWorks 2008R2/Employee_Sales_Summary_2008R2.rdl&ReportMonth=3&ReportYear=2008  
```  
  
 <span data-ttu-id="c3ac1-122">若要为参数传递 Null 值，请使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="c3ac1-122">To pass a null value for a parameter, use the following syntax:</span></span>  
  
```  
  
parameter  
:isnull=true  
  
```  
  
 <span data-ttu-id="c3ac1-123">例如，应用于对象的</span><span class="sxs-lookup"><span data-stu-id="c3ac1-123">For example,</span></span>  
  
```  
SalesOrderNumber:isnull=true  
```  
  
 <span data-ttu-id="c3ac1-124">要传递`Boolean`值，请使用 0 表示 False，使用 1 表示 True。</span><span class="sxs-lookup"><span data-stu-id="c3ac1-124">To pass a `Boolean` value, use 0 for false and 1 for true.</span></span> <span data-ttu-id="c3ac1-125">要传递`Float`值，请包含服务器区域设置的小数分隔符。</span><span class="sxs-lookup"><span data-stu-id="c3ac1-125">To pass a `Float` value, include the decimal separator of the server locale</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c3ac1-126">如果报表包含的某个报表参数具有默认值，并且 `Prompt` 属性的值为 `false`（也即，在报表管理器中未选择 Prompt User 属性），则您无法在 URL 中为该报表参数传递值。</span><span class="sxs-lookup"><span data-stu-id="c3ac1-126">If your report contains a report parameter that has a default value and the value of the `Prompt` property is `false` (that is, the Prompt User property is not selected in Report Manager), then you cannot pass a value for that report parameter within a URL.</span></span> <span data-ttu-id="c3ac1-127">这向管理员提供了一个选项，以防止最终用户添加或修改某些报表参数的值。</span><span class="sxs-lookup"><span data-stu-id="c3ac1-127">This provides administrators an option for preventing end users from adding or modifying the values of certain report parameters.</span></span>  
  
##  <a name="additional-examples"></a><a name="bkmk_examples"></a> <span data-ttu-id="c3ac1-128">其他示例</span><span class="sxs-lookup"><span data-stu-id="c3ac1-128">Additional Examples</span></span>  
 <span data-ttu-id="c3ac1-129">以下 URL 示例包含空格和多个参数</span><span class="sxs-lookup"><span data-stu-id="c3ac1-129">The following URL example includes spaces and multiple parameters</span></span>  
  
-   <span data-ttu-id="c3ac1-130">文件夹名称“SQL Server User Education Team”包含空格，因此“+”将替换每个空格。</span><span class="sxs-lookup"><span data-stu-id="c3ac1-130">Folder name of "SQL Server User Education Team" includes spaces and therefore the "+" replaces each space.</span></span>  
  
-   <span data-ttu-id="c3ac1-131">报表名称“team project report”包含空格，因此“+”将替换每个空格。</span><span class="sxs-lookup"><span data-stu-id="c3ac1-131">Report name of "team project report" includes spaces and therefore the "+" replaces each space.</span></span>  
  
-   <span data-ttu-id="c3ac1-132">传递值分别为“xgroup”和“ygroup”的两个参数“teamgrouping2”和“teamgrouping1”。</span><span class="sxs-lookup"><span data-stu-id="c3ac1-132">Passes two parameters of "teamgrouping2" with a value of "xgroup" and "teamgrouping1" with a value of "ygroup".</span></span>  
  
```  
https://myserver/Reportserver?/SQL+Server+User+Education+Team/_ContentTeams/folder123/team+project+report&teamgrouping2=xgroup&teamgrouping1=ygroup  
```  
  
 <span data-ttu-id="c3ac1-133">以下 URL 示例包含一个多值参数“OrderID”。</span><span class="sxs-lookup"><span data-stu-id="c3ac1-133">The following URL example includes a multi-value parameter "OrderID.</span></span> <span data-ttu-id="c3ac1-134">多值参数的格式是每个值都有重复的参数名称。</span><span class="sxs-lookup"><span data-stu-id="c3ac1-134">The format for a Multi-Value parameter is to repeat the parameter name for each value.</span></span>  
  
```  
https://myserver/Reportserver?/SQL+Server+User+Education+Team/_ContentTeams/folder123/team+project+report&teamgrouping2=xgroup&teamgrouping1=ygroup&OrderID=747&OrderID=787&OrderID=12  
```  
  
 <span data-ttu-id="c3ac1-135">以下 URL 示例为本机模式 Report Server 传递值为 "7/1/2005" 的*SellStartDate*的单个参数。</span><span class="sxs-lookup"><span data-stu-id="c3ac1-135">The following URL example passes a single parameter of *SellStartDate* with a value of "7/1/2005", for a native mode report server.</span></span>  
  
```  
http://myserver/ReportServer/Pages/ReportViewer.aspx?%2fProduct_and_Sales_Report_AdventureWorks&SellStartDate=7/1/2005  
```  
  
## <a name="see-also"></a><span data-ttu-id="c3ac1-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c3ac1-136">See Also</span></span>  
 <span data-ttu-id="c3ac1-137">[&#40;SSRS&#41;的 URL 访问](url-access-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c3ac1-137">[URL Access &#40;SSRS&#41;](url-access-ssrs.md) </span></span>  
 [<span data-ttu-id="c3ac1-138">URL 访问参数引用</span><span class="sxs-lookup"><span data-stu-id="c3ac1-138">URL Access Parameter Reference</span></span>](url-access-parameter-reference.md)  
  
  
