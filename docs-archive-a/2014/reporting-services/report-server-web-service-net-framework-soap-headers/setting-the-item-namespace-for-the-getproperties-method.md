---
title: 为 GetProperties 方法设置项命名空间 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- item properties [Reporting Services]
- ItemNamespaceHeader SOAP header
- GetProperties method
ms.assetid: b0a08639-3101-40a2-abe2-3a41753826d1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 14e8147a9a7639dd357077b5d881e2d4ed87fcc7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87690354"
---
# <a name="setting-the-item-namespace-for-the-getproperties-method"></a><span data-ttu-id="36777-102">为 GetProperties 方法设置项命名空间</span><span class="sxs-lookup"><span data-stu-id="36777-102">Setting the Item Namespace for the GetProperties Method</span></span>
  <span data-ttu-id="36777-103">可以根据两个不同的项标识符在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中使用 <xref:ReportService2010.ItemNamespaceHeader> SOAP 标头：项的完整路径或项的 ID。</span><span class="sxs-lookup"><span data-stu-id="36777-103">You can use the <xref:ReportService2010.ItemNamespaceHeader> SOAP header in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] to retrieve item properties based on two different item identifiers: the full path of the item or the ID of the item.</span></span>  
  
 <span data-ttu-id="36777-104">当您调用 <xref:ReportService2010.ReportingService2010.GetProperties%2A> 方法时，通常将要检索其属性的项的完整路径作为参数传递。</span><span class="sxs-lookup"><span data-stu-id="36777-104">When you make a call to the <xref:ReportService2010.ReportingService2010.GetProperties%2A> method, you normally pass as an argument the full path of the item for which you want to retrieve properties.</span></span> <span data-ttu-id="36777-105">使用 <xref:ReportService2010.ItemNamespaceHeader>，您可以为方法调用设置 SOAP 标头，以便通过将项的 ID 作为标识符传递来使用 <xref:ReportService2010.ReportingService2010.GetProperties%2A>。</span><span class="sxs-lookup"><span data-stu-id="36777-105">By using <xref:ReportService2010.ItemNamespaceHeader>, you can set the SOAP header for your method call to enable you to use <xref:ReportService2010.ReportingService2010.GetProperties%2A> by passing the ID of the item as an identifier.</span></span>  
  
 <span data-ttu-id="36777-106">以下代码示例根据项的 ID 检索项属性的值。</span><span class="sxs-lookup"><span data-stu-id="36777-106">The following code sample retrieves the values for item properties based on the ID of the item.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="36777-107">默认情况下，如果您将完整路径名称作为项标识符传递到 <xref:ReportService2010.ItemNamespaceHeader> 方法，则不需要为 <xref:ReportService2010.ReportingService2010.GetProperties%2A> 设置值。</span><span class="sxs-lookup"><span data-stu-id="36777-107">By default, you do not need to set a value for the <xref:ReportService2010.ItemNamespaceHeader> if you pass to the <xref:ReportService2010.ReportingService2010.GetProperties%2A> method the full path name as the item identifier.</span></span>  
  
```vb  
Imports System  
Imports System.Collections  
  
Class Sample  
   Sub Main()  
      Dim rs As New ReportingService2010()  
      rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
      rs.Url = "http://<Server Name>/reportserver/ReportService2010.asmx"  
  
      Dim items() As CatalogItem  
  
      Try  
         ' Need the ID property of items. Normally, you would already have   
         ' this stored somewhere.  
         items = rs.ListChildren("/AdventureWorks Sample Reports", False)  
  
         ' Set the item namespace header to be GUID-based  
         rs.ItemNamespaceHeaderValue = New ItemNamespaceHeader()  
         rs.ItemNamespaceHeaderValue.ItemNamespace = ItemNamespaceEnum.GUIDBased  
  
         ' Call GetProperties with item ID.  
         If Not (items Is Nothing) Then  
            Dim item As CatalogItem  
            For Each item In  items  
               Dim properties As [Property]() = rs.GetProperties(item.ID, Nothing)  
               Dim property As [Property]  
               For Each property In  properties  
                  Console.WriteLine(([property].Name + ": " + [property].Value))  
               Next property  
               Console.WriteLine()  
            Next item  
         End If  
  
      Catch e As Exception  
         Console.WriteLine((e.Message + ": " + e.StackTrace))  
      End Try  
   End Sub 'Main  
End Class 'Sample  
```  
  
```csharp  
using System;  
using System.Collections;  
  
class Sample  
{  
   static void Main()  
   {  
   ReportingService2010 rs = new ReportingService2010();  
      rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
      rs.Url = "http://<Server Name>/reportserver/ReportService2010.asmx";  
  
      CatalogItem[] items;  
  
      try  
      {  
         // Need the ID property of items. Normally, you would already have   
         // this stored somewhere.  
         items = rs.ListChildren("/AdventureWorks Sample Reports", false);  
  
         // Set the item namespace header to be GUID-based  
         rs.ItemNamespaceHeaderValue = new ItemNamespaceHeader();  
         rs.ItemNamespaceHeaderValue.ItemNamespace = ItemNamespaceEnum.GUIDBased;  
  
         // Call GetProperties with item ID.  
         if (items != null)  
         {  
            foreach( CatalogItem item in items)  
            {  
               Property[] properties = rs.GetProperties(item.ID, null);  
               foreach (Property property in properties)  
               {  
                  Console.WriteLine(property.Name + ": " + property.Value);  
               }  
               Console.WriteLine();  
            }  
         }  
      }  
  
      catch (Exception e)  
      {  
         Console.WriteLine(e.Message);  
      }  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="36777-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="36777-108">See Also</span></span>  
 <span data-ttu-id="36777-109">[SSRS&#41;&#40;技术参考](../technical-reference-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="36777-109">[Technical Reference &#40;SSRS&#41;](../technical-reference-ssrs.md) </span></span>  
 [<span data-ttu-id="36777-110">使用 Reporting Services SOAP 标头</span><span class="sxs-lookup"><span data-stu-id="36777-110">Using Reporting Services SOAP Headers</span></span>](using-reporting-services-soap-headers.md)  
  
  
