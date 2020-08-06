---
title: 使用 URL 访问报表服务器项 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- referencing URL items for report server access
- URL access [Reporting Services], report servers
ms.assetid: a58b4ca6-129d-45e9-95c7-e9169fe5bba4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6693419490c1b3770ccb41b2645cbdba8996630a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87588366"
---
# <a name="access-report-server-items-using-url-access"></a><span data-ttu-id="22d1f-102">使用 URL 访问报表服务器项</span><span class="sxs-lookup"><span data-stu-id="22d1f-102">Access Report Server Items Using URL Access</span></span>
  <span data-ttu-id="22d1f-103">本主题介绍如何使用 rs:Command=Value 访问报表服务器数据库或 SharePoint 站点中不同类型的目录项。</span><span class="sxs-lookup"><span data-stu-id="22d1f-103">This topic describes how to access catalog items of different types in a report server data base or in a SharePoint site using *rs:Command*=*Value*.</span></span>  
  
 <span data-ttu-id="22d1f-104">不必添加此参数字符串。</span><span class="sxs-lookup"><span data-stu-id="22d1f-104">It is not necessary to add this parameter string.</span></span> <span data-ttu-id="22d1f-105">如果您省略此字符串，报表服务器将会计算项类型，并且自动选择适当的参数值。</span><span class="sxs-lookup"><span data-stu-id="22d1f-105">If you omit it, the report server evaluates the item type and selects the appropriate parameter value automatically.</span></span> <span data-ttu-id="22d1f-106">但是，在 URL 中使用 rs:Command=Value 字符串可改进报表服务器的性能。</span><span class="sxs-lookup"><span data-stu-id="22d1f-106">However, using the *rs:Command*=*Value* string in the URL improves the performance of the report server.</span></span>  
  
 <span data-ttu-id="22d1f-107">请注意下面示例中的 `_vti_bin` 代理语法。</span><span class="sxs-lookup"><span data-stu-id="22d1f-107">Note the `_vti_bin` proxy syntax in the examples below.</span></span> <span data-ttu-id="22d1f-108">有关使用代理语法的详细信息，请参阅 [URL Access Parameter Reference](url-access-parameter-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="22d1f-108">For more information about using the proxy syntax, see [URL Access Parameter Reference](url-access-parameter-reference.md).</span></span>  
  
## <a name="access-a-report"></a><span data-ttu-id="22d1f-109">访问报表</span><span class="sxs-lookup"><span data-stu-id="22d1f-109">Access a Report</span></span>  
 <span data-ttu-id="22d1f-110">若要在浏览器中查看报表，请使用*rs： Command* = *Render*参数。</span><span class="sxs-lookup"><span data-stu-id="22d1f-110">To view a report in the browser, use the *rs:Command*=*Render* parameter.</span></span> <span data-ttu-id="22d1f-111">例如：</span><span class="sxs-lookup"><span data-stu-id="22d1f-111">For example:</span></span>  
  
 <span data-ttu-id="22d1f-112">`Native` `http://myrshost/reportserver?/Sales/YearlySalesByCategory&rs:Command=Render`</span><span class="sxs-lookup"><span data-stu-id="22d1f-112">`Native` `http://myrshost/reportserver?/Sales/YearlySalesByCategory&rs:Command=Render`</span></span>  
  
 <span data-ttu-id="22d1f-113">`SharePoint` `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/YearlySalesByCategory&rs:Command=Render`</span><span class="sxs-lookup"><span data-stu-id="22d1f-113">`SharePoint` `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/YearlySalesByCategory&rs:Command=Render`</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="22d1f-114">非常重要的一点是，URL 包括用于通过 SharePoint 和 `_vti_bin` HTTP 代理路由请求的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 代理语法。</span><span class="sxs-lookup"><span data-stu-id="22d1f-114">It is important the URL include the `_vti_bin` proxy syntax to route the request through SharePoint and the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] HTTP proxy.</span></span> <span data-ttu-id="22d1f-115">该代理会向 HTTP 请求中添加某一上下文，该上下文是确保为 SharePoint 模式报表服务器正确执行报表所需要的。</span><span class="sxs-lookup"><span data-stu-id="22d1f-115">The proxy adds some context to the HTTP request, context that is required to ensure proper execution of the report for SharePoint mode report servers.</span></span>  
  
## <a name="access-a-resource"></a><span data-ttu-id="22d1f-116">访问资源</span><span class="sxs-lookup"><span data-stu-id="22d1f-116">Access a Resource</span></span>  
 <span data-ttu-id="22d1f-117">若要访问资源，请使用*rs： Command* = *GetResourceContents*参数。如果资源与浏览器（如图像）兼容，则会在浏览器中打开该资源。</span><span class="sxs-lookup"><span data-stu-id="22d1f-117">To access a resource, use the *rs:Command*=*GetResourceContents* parameter.If the resource is compatible with the browser, such as an image, it is opened in the browser.</span></span> <span data-ttu-id="22d1f-118">否则，系统会提示您打开文件或资源或将其保存到磁盘。</span><span class="sxs-lookup"><span data-stu-id="22d1f-118">Otherwise, you are prompted to open or save the file or resource to disk.</span></span>  
  
 <span data-ttu-id="22d1f-119">`Native` `http://myrshost/reportserver?/Sales/StorePicture&rs:Command=GetResourceContents`</span><span class="sxs-lookup"><span data-stu-id="22d1f-119">`Native` `http://myrshost/reportserver?/Sales/StorePicture&rs:Command=GetResourceContents`</span></span>  
  
 <span data-ttu-id="22d1f-120">`SharePoint` `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/StorePicture.jpg&rs:Command=GetResourceContents`</span><span class="sxs-lookup"><span data-stu-id="22d1f-120">`SharePoint` `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/StorePicture.jpg&rs:Command=GetResourceContents`</span></span>  
  
## <a name="access-a-data-source"></a><span data-ttu-id="22d1f-121">访问数据源</span><span class="sxs-lookup"><span data-stu-id="22d1f-121">Access a Data Source</span></span>  
 <span data-ttu-id="22d1f-122">若要访问数据源，请使用*rs： Command* = *GetDataSourceContents*参数。</span><span class="sxs-lookup"><span data-stu-id="22d1f-122">To access a data source, use the *rs:Command*=*GetDataSourceContents* parameter.</span></span> <span data-ttu-id="22d1f-123">如果您的浏览器支持 XML，则当您对于该数据源是具有 `Read Contents` 权限的经过身份验证的用户时，将显示数据源定义。</span><span class="sxs-lookup"><span data-stu-id="22d1f-123">If your browser supports XML, the data source definition is displayed if you are an authenticated user with `Read Contents` permission on the data source.</span></span> <span data-ttu-id="22d1f-124">例如：</span><span class="sxs-lookup"><span data-stu-id="22d1f-124">For example:</span></span>  
  
 <span data-ttu-id="22d1f-125">`Native` `http://myrshost/reportserver?/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents`</span><span class="sxs-lookup"><span data-stu-id="22d1f-125">`Native` `http://myrshost/reportserver?/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents`</span></span>  
  
 <span data-ttu-id="22d1f-126">`SharePoint` `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents`</span><span class="sxs-lookup"><span data-stu-id="22d1f-126">`SharePoint` `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents`</span></span>  
  
 <span data-ttu-id="22d1f-127">XML 结构可能类似于以下示例：</span><span class="sxs-lookup"><span data-stu-id="22d1f-127">The XML structure might look similar to the following example:</span></span>  
  
```  
<DataSourceDefinition>  
   <Extension>SQL</Extension>  
   <ConnectString>Provider=SQLOLEDB.1;Integrated Security=SSPI;Persist Security Info=False;Initial Catalog=AdventureWorks2012;Data Source=MYSERVER1;</ConnectString>  
   <CredentialRetrieval>Integrated</CredentialRetrieval>  
   <WindowsCredentials>False</WindowsCredentials>  
   <ImpersonateUser>False</ImpersonateUser>  
   <Prompt />  
   <Enabled>True</Enabled>  
</DataSourceDefinition>  
```  
  
 <span data-ttu-id="22d1f-128">将根据报表服务器的 **SecureConnectionLevel** 设置返回连接字符串。</span><span class="sxs-lookup"><span data-stu-id="22d1f-128">The connection string is returned based on the **SecureConnectionLevel** setting of the report server.</span></span> <span data-ttu-id="22d1f-129">有关 **SecureConnectionLevel** 设置的详细信息，请参阅 [Using Secure Web Service Methods](report-server-web-service/net-framework/using-secure-web-service-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="22d1f-129">For more information about the **SecureConnectionLevel** setting, see [Using Secure Web Service Methods](report-server-web-service/net-framework/using-secure-web-service-methods.md).</span></span>  
  
## <a name="access-the-contents-of-a-folder"></a><span data-ttu-id="22d1f-130">访问文件夹的内容</span><span class="sxs-lookup"><span data-stu-id="22d1f-130">Access the Contents of a Folder</span></span>  
 <span data-ttu-id="22d1f-131">若要访问文件夹的内容，请使用*rs： Command* = *GetChildren*参数。</span><span class="sxs-lookup"><span data-stu-id="22d1f-131">To access the contents of a folder, use the *rs:Command*=*GetChildren* parameter.</span></span> <span data-ttu-id="22d1f-132">将返回一个一般的文件夹导航页，其中包含指向在所请求文件中包含的子文件夹、报表、数据源和资源的链接。</span><span class="sxs-lookup"><span data-stu-id="22d1f-132">A generic folder-navigation page is returned that contains links to the subfolders, reports, data sources, and resources in the requested folder.</span></span> <span data-ttu-id="22d1f-133">例如：</span><span class="sxs-lookup"><span data-stu-id="22d1f-133">For example:</span></span>  
  
 <span data-ttu-id="22d1f-134">`Native` `http://myrshost/reportserver?/Sales&rs:Command=GetChildren`</span><span class="sxs-lookup"><span data-stu-id="22d1f-134">`Native` `http://myrshost/reportserver?/Sales&rs:Command=GetChildren`</span></span>  
  
 <span data-ttu-id="22d1f-135">`SharePoint` `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales&rs:Command=GetChildren`</span><span class="sxs-lookup"><span data-stu-id="22d1f-135">`SharePoint` `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales&rs:Command=GetChildren`</span></span>  
  
 <span data-ttu-id="22d1f-136">您所看到的用户界面类似于由 [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Information Server (IIS) 使用的目录浏览模式。</span><span class="sxs-lookup"><span data-stu-id="22d1f-136">The user interface you see is similar to the directory browsing mode used by [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Information Server (IIS).</span></span> <span data-ttu-id="22d1f-137">报表服务器的版本号（包括内部版本号）也将显示在文件夹列表之下。</span><span class="sxs-lookup"><span data-stu-id="22d1f-137">The version number, including the build number, of the report server is also displayed below the folder listing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22d1f-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="22d1f-138">See Also</span></span>  
 <span data-ttu-id="22d1f-139">[&#40;SSRS&#41;的 URL 访问](url-access-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="22d1f-139">[URL Access &#40;SSRS&#41;](url-access-ssrs.md) </span></span>  
 [<span data-ttu-id="22d1f-140">URL 访问参数引用</span><span class="sxs-lookup"><span data-stu-id="22d1f-140">URL Access Parameter Reference</span></span>](url-access-parameter-reference.md)  
  
  
