---
title: 在 Windows 应用程序中使用 URL 访问 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Windows applications [Reporting Services]
- Web Browser controls [Reporting Services]
- Windows Forms [Reporting Services]
- browser controls [Reporting Services]
- URL access [Reporting Services], Windows applications
ms.assetid: a4b222e5-0cbd-409c-92c4-046a674db8ac
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8f8b901481b1d6fcc3cdd8626b43cd3a69174c1a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87691138"
---
# <a name="using-url-access-in-a-windows-application"></a><span data-ttu-id="0610f-102">在 Windows 应用程序中使用 URL 访问</span><span class="sxs-lookup"><span data-stu-id="0610f-102">Using URL Access in a Windows Application</span></span>
  <span data-ttu-id="0610f-103">尽管可以针对 Web 环境优化对报表服务器的 URL 访问，但也可以使用 URL 访问将 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 报表嵌入到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 应用程序中。</span><span class="sxs-lookup"><span data-stu-id="0610f-103">Although URL access to a report server is optimized for a Web environment, you can also use URL access to embed [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] reports into a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows application.</span></span> <span data-ttu-id="0610f-104">不过，涉及 Windows 窗体的 URL 访问仍然要求您使用 Web 浏览器技术。</span><span class="sxs-lookup"><span data-stu-id="0610f-104">However, URL access that involves Windows Forms still requires that you use Web browser technology.</span></span> <span data-ttu-id="0610f-105">您可以将以下集成方案用于 URL 访问和 Windows 窗体：</span><span class="sxs-lookup"><span data-stu-id="0610f-105">You can use the following integration scenarios with URL access and Windows Forms:</span></span>  
  
-   <span data-ttu-id="0610f-106">通过以编程方式启动 Web 浏览器，从 Windows 窗体应用程序显示报表。</span><span class="sxs-lookup"><span data-stu-id="0610f-106">Display a report from a Windows Form application by starting a Web browser programmatically.</span></span>  
  
-   <span data-ttu-id="0610f-107">使用 Windows 窗体上的 <xref:System.Windows.Forms.WebBrowser> 控件显示报表。</span><span class="sxs-lookup"><span data-stu-id="0610f-107">Use the <xref:System.Windows.Forms.WebBrowser> control on a Windows Form to display a report.</span></span>  
  
## <a name="starting-internet-explorer-from-a-windows-form"></a><span data-ttu-id="0610f-108">从 Windows 窗体启动 Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="0610f-108">Starting Internet Explorer from a Windows Form</span></span>  
 <span data-ttu-id="0610f-109">可以使用 <xref:System.Diagnostics.Process> 类访问正在计算机上运行的进程。</span><span class="sxs-lookup"><span data-stu-id="0610f-109">You can use the <xref:System.Diagnostics.Process> class to access a process that is running on a computer.</span></span> <span data-ttu-id="0610f-110"><xref:System.Diagnostics.Process>类是 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 用于启动、停止、控制和监视应用程序的有用构造。</span><span class="sxs-lookup"><span data-stu-id="0610f-110">The <xref:System.Diagnostics.Process> class is a useful [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] construct for starting, stopping, controlling, and monitoring applications.</span></span> <span data-ttu-id="0610f-111">若要查看报表服务器数据库中的特定报表，可以启动 IExplore 进程，同时将 URL 传递给报表\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0610f-111">To view a specific report in your report server database, you can start the **IExplore** process, passing in the URL to the report.</span></span> <span data-ttu-id="0610f-112">以下代码示例可用于在用户单击 Windows 窗体上的某个按钮时，启动 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer 并传递特定的报表 URL。</span><span class="sxs-lookup"><span data-stu-id="0610f-112">The following code example can be used to start [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer and pass a specific report URL when the user clicks a button on a Windows Form.</span></span>  
  
```vb  
Private Sub viewReportButton_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles viewReportButton.Click  
   ' Build the URL access string based on values supplied by a user  
   Dim url As String = serverUrlTextBox.Text + "?" & reportPathTextBox.Text & _  
   "&rs:Command=Render" & "&rs:Format=HTML4.0"  
  
   ' If the user does not select the toolbar check box,  
   ' turn the toolbar off in the HTML Viewer  
   If toolbarCheckBox.Checked = False Then  
      url += "&rc:Toolbar=False"  
   End If  
   ' load report in the Web browser  
   Try  
      System.Diagnostics.Process.Start("IExplore", url)  
   Catch  
      MessageBox.Show("The system could not start the specified report using Internet Explorer.", _  
      "An error has occurred", MessageBoxButtons.OK, MessageBoxIcon.Error)  
   End Try  
End Sub 'viewReportButton_Click  
```  
  
```csharp  
// Sample click event for a Button control on a Windows Form  
private void viewReportButton_Click(object sender, System.EventArgs e)  
{  
   // Build the URL access string based on values supplied by a user  
   string url = serverUrlTextBox.Text + "?" + reportPathTextBox.Text +  
      "&rs:Command=Render" + "&rs:Format=HTML4.0";  
  
   // If the user does not check the toolbar check box,  
   // turn the toolbar off in the HTML Viewer  
   if (toolbarCheckBox.Checked == false)  
      url += "&rc:Toolbar=False";  
  
   // load report in the Web browser  
   try  
   {  
      System.Diagnostics.Process.Start("IExplore", url);  
   }  
  
   catch (Exception)  
   {  
      MessageBox.Show(  
         "The system could not open the specified report using Internet Explorer.",   
         "An error has occurred", MessageBoxButtons.OK, MessageBoxIcon.Error);  
   }  
}  
```  
  
## <a name="embedding-a-browser-control-on-a-windows-form"></a><span data-ttu-id="0610f-113">在 Windows 窗体中嵌入浏览器控件</span><span class="sxs-lookup"><span data-stu-id="0610f-113">Embedding a Browser Control on a Windows Form</span></span>  
 <span data-ttu-id="0610f-114">如果您不想在外部 Web 浏览器中查看报表，可以使用 <xref:System.Windows.Forms.WebBrowser> 控件将 Web 浏览器作为 Windows 窗体的一部分无缝嵌入。</span><span class="sxs-lookup"><span data-stu-id="0610f-114">If you do not want to view your report in an external Web browser, you can embed a Web browser seamlessly as part of your Windows Form using the <xref:System.Windows.Forms.WebBrowser> control.</span></span>  
  
###### <a name="to-add-the-webbrowser-control-to-your-windows-form"></a><span data-ttu-id="0610f-115">将 WebBrowser 控件添加到 Windows 窗体</span><span class="sxs-lookup"><span data-stu-id="0610f-115">To add the WebBrowser control to your Windows Form</span></span>  
  
1.  <span data-ttu-id="0610f-116">在或中创建新的 Windows 应用程序 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="0610f-116">Create a new Windows application in either [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] or [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)].</span></span>  
  
2.  <span data-ttu-id="0610f-117">找到“工具箱”对话框中的 <xref:System.Windows.Forms.WebBrowser> 控件\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0610f-117">Locate the <xref:System.Windows.Forms.WebBrowser> control in the **Toolbox** Dialog Box.</span></span>  
  
     <span data-ttu-id="0610f-118">如果不显示“工具箱”，可以通过单击“视图”菜单项并选择“工具箱”来访问它\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0610f-118">If the **Toolbox** is not visible you can access it by clicking the **View** menu item and selecting **Toolbox**.</span></span>  
  
3.  <span data-ttu-id="0610f-119">将 <xref:System.Windows.Forms.WebBrowser> 控件拖到 Windows 窗体的设计图面上。</span><span class="sxs-lookup"><span data-stu-id="0610f-119">Drag the <xref:System.Windows.Forms.WebBrowser>control onto the design surface of your Windows Form.</span></span>  
  
     <span data-ttu-id="0610f-120">名为 webBrowser1 的 <xref:System.Windows.Forms.WebBrowser> 控件被添加到窗体中</span><span class="sxs-lookup"><span data-stu-id="0610f-120">The <xref:System.Windows.Forms.WebBrowser>control named webBrowser1 is added to the Form</span></span>  
  
 <span data-ttu-id="0610f-121">可以通过调用其 Navigate 方法将 <xref:System.Windows.Forms.WebBrowser> 控件定向到 URL\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0610f-121">You direct the <xref:System.Windows.Forms.WebBrowser> control to a URL by calling its **Navigate** method.</span></span> <span data-ttu-id="0610f-122">可以在运行时将特定的 URL 访问字符串分配给 <xref:System.Windows.Forms.WebBrowser> 控件，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="0610f-122">You can assign a specific URL access string to your <xref:System.Windows.Forms.WebBrowser> control at run time as shown in the following example.</span></span>  
  
```vb  
Dim url As String = "http://localhost/reportserver?/" & _  
                    "AdventureWorks2012 Sample Reports/" & _  
                    "Company Sales&rs:Command=Render"  
WebBrowser1.Navigate(url)  
```  
  
```csharp  
string url = "http://localhost/reportserver?/" +  
             "AdventureWorks2012 Sample Reports/" +  
             "Company Sales&rs:Command=Render";  
webBrowser1.Navigate(url);  
```  
  
## <a name="see-also"></a><span data-ttu-id="0610f-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0610f-123">See Also</span></span>  
 <span data-ttu-id="0610f-124">[将 Reporting Services 集成到应用程序中](../application-integration/integrating-reporting-services-into-applications.md) </span><span class="sxs-lookup"><span data-stu-id="0610f-124">[Integrating Reporting Services into Applications](../application-integration/integrating-reporting-services-into-applications.md) </span></span>  
 <span data-ttu-id="0610f-125">[使用 URL 访问集成 Reporting Services](integrating-reporting-services-using-url-access.md) </span><span class="sxs-lookup"><span data-stu-id="0610f-125">[Integrating Reporting Services Using URL Access](integrating-reporting-services-using-url-access.md) </span></span>  
 <span data-ttu-id="0610f-126">[使用 SOAP 集成 Reporting Services](integrating-reporting-services-using-soap.md) </span><span class="sxs-lookup"><span data-stu-id="0610f-126">[Integrating Reporting Services Using SOAP](integrating-reporting-services-using-soap.md) </span></span>  
 <span data-ttu-id="0610f-127">[使用 ReportViewer 控件集成 Reporting Services](integrating-reporting-services-using-reportviewer-controls.md) </span><span class="sxs-lookup"><span data-stu-id="0610f-127">[Integrating Reporting Services Using the ReportViewer Controls](integrating-reporting-services-using-reportviewer-controls.md) </span></span>  
 [<span data-ttu-id="0610f-128">URL 访问 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="0610f-128">URL Access &#40;SSRS&#41;</span></span>](../url-access-ssrs.md)  
  
  
