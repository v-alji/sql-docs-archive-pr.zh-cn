---
title: 使用脚本任务处理图像 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- graphics [Integration Services]
- Script task [Integration Services], images
- Drawing namespace
- images [Integration Services]
- SSIS Script task, images
- Script task [Integration Services], examples
- thumbnails [Integration Services]
- System.Drawing namespace
- JPEG format [Integration Services]
- .jpeg files
ms.assetid: 74aeb7ab-51b2-4b9f-84ee-0b46a7908ab9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 75a5b72f87a4463d7270dc9f28529a81525860cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87586904"
---
# <a name="working-with-images-with-the-script-task"></a><span data-ttu-id="e2a85-102">使用脚本任务处理图像</span><span class="sxs-lookup"><span data-stu-id="e2a85-102">Working with Images with the Script Task</span></span>
  <span data-ttu-id="e2a85-103">除文本和数值数据外，产品数据库或用户数据库还经常包含图像。</span><span class="sxs-lookup"><span data-stu-id="e2a85-103">A database of products or users frequently includes images in addition to text and numeric data.</span></span> <span data-ttu-id="e2a85-104">Microsoft .NET Framework 中的 `System.Drawing` 命名空间提供用于操作图像的类。</span><span class="sxs-lookup"><span data-stu-id="e2a85-104">The `System.Drawing` namespace in the Microsoft .NET Framework provides classes for manipulating images.</span></span>  
  
 [<span data-ttu-id="e2a85-105">示例 1：将图像转换为 JPEG 格式</span><span class="sxs-lookup"><span data-stu-id="e2a85-105">Example 1: Convert Images to JPEG Format</span></span>](#example1)  
  
 [<span data-ttu-id="e2a85-106">示例 2：创建并保存缩略图图像</span><span class="sxs-lookup"><span data-stu-id="e2a85-106">Example 2: Create and Save Thumbnail Images</span></span>](#example2)  
  
> [!NOTE]  
>  <span data-ttu-id="e2a85-107">如果希望创建可更方便地重用于多个包的任务，请考虑以此脚本任务示例中的代码为基础，创建自定义任务。</span><span class="sxs-lookup"><span data-stu-id="e2a85-107">If you want to create a task that you can more easily reuse across multiple packages, consider using the code in this Script task sample as the starting point for a custom task.</span></span> <span data-ttu-id="e2a85-108">有关详细信息，请参阅 [开发自定义任务](../extending-packages-custom-objects/task/developing-a-custom-task.md)。</span><span class="sxs-lookup"><span data-stu-id="e2a85-108">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>  
  
##  <a name="example-1-description-convert-images-to-jpeg-format"></a><a name="example1"></a><span data-ttu-id="e2a85-109">示例 1 说明：将图像转换为 JPEG 格式</span><span class="sxs-lookup"><span data-stu-id="e2a85-109">Example 1 Description: Convert Images to JPEG Format</span></span>  
 <span data-ttu-id="e2a85-110">下面的示例打开一个由变量指定的图像文件，并使用编码器将其保存为压缩后的 JPEG 文件。</span><span class="sxs-lookup"><span data-stu-id="e2a85-110">The following example opens an image file specified by a variable and saves it as a compressed JPEG file by using an encoder.</span></span> <span data-ttu-id="e2a85-111">检索编码器信息的代码封装在一个私有函数中。</span><span class="sxs-lookup"><span data-stu-id="e2a85-111">The code to retrieve encoder information is encapsulated in a private function.</span></span>  
  
#### <a name="to-configure-this-script-task-example-for-use-with-a-single-image-file"></a><span data-ttu-id="e2a85-112">将此脚本任务示例配置为用于单个图像文件</span><span class="sxs-lookup"><span data-stu-id="e2a85-112">To configure this Script Task example for use with a single image file</span></span>  
  
1.  <span data-ttu-id="e2a85-113">创建一个名为 `CurrentImageFile` 的字符串变量，并将其值设置为一个现有图像文件的路径和名称。</span><span class="sxs-lookup"><span data-stu-id="e2a85-113">Create a string variable named `CurrentImageFile` and set its value to the path and file name of an existing image file.</span></span>  
  
2.  <span data-ttu-id="e2a85-114">在 "**脚本任务编辑器**" 的 "**脚本**" 页中，将 `CurrentImageFile` 变量添加到属性中 `ReadOnlyVariables` 。</span><span class="sxs-lookup"><span data-stu-id="e2a85-114">On the **Script** page of the **Script Task Editor**, add the `CurrentImageFile` variable to the `ReadOnlyVariables` property.</span></span>  
  
3.  <span data-ttu-id="e2a85-115">在脚本项目中，设置一个对 `System.Drawing` 命名空间的引用。</span><span class="sxs-lookup"><span data-stu-id="e2a85-115">In the script project, set a reference to the `System.Drawing` namespace.</span></span>  
  
4.  <span data-ttu-id="e2a85-116">在您的代码中，使用 `Imports` 语句导入 `System.Drawing` 和 `System.IO` 命名空间。</span><span class="sxs-lookup"><span data-stu-id="e2a85-116">In your code, use `Imports` statements to import the `System.Drawing` and `System.IO` namespaces.</span></span>  
  
#### <a name="to-configure-this-script-task-example-for-use-with-multiple-image-files"></a><span data-ttu-id="e2a85-117">将此脚本任务示例配置为用于多个图像文件</span><span class="sxs-lookup"><span data-stu-id="e2a85-117">To configure this Script Task example for use with multiple image files</span></span>  
  
1.  <span data-ttu-id="e2a85-118">将脚本任务放入 Foreach 循环容器。</span><span class="sxs-lookup"><span data-stu-id="e2a85-118">Place the Script task within a Foreach Loop container.</span></span>  
  
2.  <span data-ttu-id="e2a85-119">在“Foreach 循环编辑器”的“集合”页中，选择“Foreach 文件枚举器”作为枚举器，并指定源文件的路径和文件掩码，如“\*.bmp”    。</span><span class="sxs-lookup"><span data-stu-id="e2a85-119">On the **Collection** page of the **Foreach Loop Editor**, select the **Foreach File Enumerator** as the enumerator, and specify the path and file mask of the source files, such as "\*.bmp."</span></span>  
  
3.  <span data-ttu-id="e2a85-120">在“变量映射”页中，将 `CurrentImageFile` 变量映射到索引 0。</span><span class="sxs-lookup"><span data-stu-id="e2a85-120">On the **Variable Mappings** page, map the `CurrentImageFile` variable to Index 0.</span></span> <span data-ttu-id="e2a85-121">此变量在枚举器的每次迭代中将当前文件名传递给脚本任务。</span><span class="sxs-lookup"><span data-stu-id="e2a85-121">This variable passes the current file name to the Script task on each iteration of the enumerator.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e2a85-122">这些步骤是在执行用于单个图像文件配置过程中列出的步骤之外还要执行的步骤。</span><span class="sxs-lookup"><span data-stu-id="e2a85-122">These steps are in addition to the steps listed in the procedure for use with a single image file.</span></span>  
  
### <a name="example-1-code"></a><span data-ttu-id="e2a85-123">示例 1 代码</span><span class="sxs-lookup"><span data-stu-id="e2a85-123">Example 1 Code</span></span>  
  
```vb  
Public Sub Main()  
  
    'Create and initialize variables.  
    Dim currentFile As String  
    Dim newFile As String  
    Dim bmp As Bitmap  
    Dim eps As New Imaging.EncoderParameters(1)  
    Dim ici As Imaging.ImageCodecInfo  
    Dim supportedExtensions() As String = _  
        {".BMP", ".GIF", ".JPG", ".JPEG", ".EXIF", ".PNG", _  
        ".TIFF", ".TIF", ".ICO", ".ICON"}  
  
    Try  
        'Store the variable in a string for local manipulation.  
        currentFile = Dts.Variables("CurrentImageFile").Value.ToString  
        'Check the extension of the file against a list of  
        'files that the Bitmap class supports.  
        If Array.IndexOf(supportedExtensions, _  
            Path.GetExtension(currentFile).ToUpper) > -1 Then  
  
            'Load the file.  
            bmp = New Bitmap(currentFile)  
  
            'Calculate the new name for the compressed image.  
            'Note: This will overwrite existing JPEGs.  
            newFile = Path.Combine( _  
                Path.GetDirectoryName(currentFile), _  
                String.Concat(Path.GetFileNameWithoutExtension(currentFile), _  
                ".jpg"))  
  
            'Specify the compression ratio (0=worst quality, 100=best quality).  
            eps.Param(0) = New Imaging.EncoderParameter( _  
                Imaging.Encoder.Quality, 75)  
  
            'Retrieve the ImageCodecInfo associated with the jpeg format.  
            ici = GetEncoderInfo("image/jpeg")  
  
            'Save the file, compressing it into the jpeg encoding.  
            bmp.Save(newFile, ici, eps)  
        Else  
            'The file is not supported by the Bitmap class.  
            Dts.Events.FireWarning(0, "Image Resampling Sample", _  
                "File " & currentFile & " is not a supported format.", _  
                "", 0)  
         End If  
        Dts.TaskResult = ScriptResults.Success  
    Catch ex As Exception  
        'An error occurred.  
        Dts.Events.FireError(0, "Image Resampling Sample", _  
            ex.Message & ControlChars.CrLf & ex.StackTrace, _  
            String.Empty, 0)  
        Dts.TaskResult = ScriptResults.Failure  
    End Try  
  
End Sub  
  
Private Function GetEncoderInfo(ByVal mimeType As String) As Imaging.ImageCodecInfo  
  
    'The available image codecs are returned as an array,  
    'which requires code to iterate until the specified codec is found.  
  
    Dim count As Integer  
    Dim encoders() As Imaging.ImageCodecInfo  
  
    encoders = Imaging.ImageCodecInfo.GetImageEncoders()  
  
    For count = 0 To encoders.Length  
        If encoders(count).MimeType = mimeType Then  
            Return encoders(count)  
        End If  
    Next  
  
    'This point is only reached if a codec is not found.  
    Err.Raise(513, "Image Resampling Sample", String.Format( _  
        "The {0} codec is not available. Unable to compress file.", _  
            mimeType))  
    Return Nothing  
  
End Function  
  
```  
  
##  <a name="example-2-description-create-and-save-thumbnail-images"></a><a name="example2"></a><span data-ttu-id="e2a85-124">示例 2 说明：创建并保存缩略图图像</span><span class="sxs-lookup"><span data-stu-id="e2a85-124">Example 2 Description: Create and Save Thumbnail Images</span></span>  
 <span data-ttu-id="e2a85-125">下面的示例打开一个由变量指定的图像文件，在保持宽高比不变的情况下创建一个该图像的缩略图，并将此缩略图以修改后的名称保存。</span><span class="sxs-lookup"><span data-stu-id="e2a85-125">The following example opens an image file specified by a variable, creates a thumbnail of the image while maintaining a constant aspect ratio, and saves the thumbnail with a modified file name.</span></span> <span data-ttu-id="e2a85-126">在保持宽高比不变的情况下计算缩略图的高度和宽度的代码封装在一个私有子例程中。</span><span class="sxs-lookup"><span data-stu-id="e2a85-126">The code that calculates the height and width of the thumbnail while maintaining a constant aspect ratio is encapsulated in a private subroutine.</span></span>  
  
#### <a name="to-configure-this-script-task-example-for-use-with-a-single-image-file"></a><span data-ttu-id="e2a85-127">将此脚本任务示例配置为用于单个图像文件</span><span class="sxs-lookup"><span data-stu-id="e2a85-127">To configure this Script Task example for use with a single image file</span></span>  
  
1.  <span data-ttu-id="e2a85-128">创建一个名为 `CurrentImageFile` 的字符串变量，并将其值设置为一个现有图像文件的路径和名称。</span><span class="sxs-lookup"><span data-stu-id="e2a85-128">Create a string variable named `CurrentImageFile` and set its value to the path and file name of an existing image file.</span></span>  
  
2.  <span data-ttu-id="e2a85-129">再创建整数变量 `MaxThumbSize`，并赋值（单位为像素），例如 100。</span><span class="sxs-lookup"><span data-stu-id="e2a85-129">Also create the `MaxThumbSize` integer variable and assign a value in pixels, such as 100.</span></span>  
  
3.  <span data-ttu-id="e2a85-130">在 "**脚本任务编辑器**" 的 "**脚本**" 页上，将两个变量添加到 `ReadOnlyVariables` 属性中。</span><span class="sxs-lookup"><span data-stu-id="e2a85-130">On the **Script** page of the **Script Task Editor**, add both variables to the `ReadOnlyVariables` property.</span></span>  
  
4.  <span data-ttu-id="e2a85-131">在脚本项目中，设置一个对 `System.Drawing` 命名空间的引用。</span><span class="sxs-lookup"><span data-stu-id="e2a85-131">In the script project, set a reference to the `System.Drawing` namespace.</span></span>  
  
5.  <span data-ttu-id="e2a85-132">在您的代码中，使用 `Imports` 语句导入 `System.Drawing` 和 `System.IO` 命名空间。</span><span class="sxs-lookup"><span data-stu-id="e2a85-132">In your code, use `Imports` statements to import the `System.Drawing` and `System.IO` namespaces.</span></span>  
  
#### <a name="to-configure-this-script-task-example-for-use-with-multiple-image-files"></a><span data-ttu-id="e2a85-133">将此脚本任务示例配置为用于多个图像文件</span><span class="sxs-lookup"><span data-stu-id="e2a85-133">To configure this Script Task example for use with multiple image files</span></span>  
  
1.  <span data-ttu-id="e2a85-134">将脚本任务放入 Foreach 循环容器。</span><span class="sxs-lookup"><span data-stu-id="e2a85-134">Place the Script task within a Foreach Loop container.</span></span>  
  
2.  <span data-ttu-id="e2a85-135">在“Foreach 循环编辑器”的“集合”页中，选择“Foreach 文件枚举器”作为“枚举器”，并指定源文件的路径和文件掩码，如“\*.jpg”     。</span><span class="sxs-lookup"><span data-stu-id="e2a85-135">On the **Collection** page of the **Foreach Loop Editor**, select the **Foreach File Enumerator** as the **Enumerator**, and specify the path and file mask of the source files, such as "\*.jpg."</span></span>  
  
3.  <span data-ttu-id="e2a85-136">在“变量映射”页中，将 `CurrentImageFile` 变量映射到索引 0。</span><span class="sxs-lookup"><span data-stu-id="e2a85-136">On the **Variable Mappings** page, map the `CurrentImageFile` variable to Index 0.</span></span> <span data-ttu-id="e2a85-137">此变量在枚举器的每次迭代中将当前文件名传递给脚本任务。</span><span class="sxs-lookup"><span data-stu-id="e2a85-137">This variable passes the current file name to the Script task on each iteration of the enumerator.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e2a85-138">这些步骤是在执行用于单个图像文件配置过程中列出的步骤之外还要执行的步骤。</span><span class="sxs-lookup"><span data-stu-id="e2a85-138">These steps are in addition to the steps listed in the procedure for use with a single image file.</span></span>  
  
### <a name="example-2-code"></a><span data-ttu-id="e2a85-139">示例 2 代码</span><span class="sxs-lookup"><span data-stu-id="e2a85-139">Example 2 Code</span></span>  
  
```vb  
Public Sub Main()  
  
    Dim currentImageFile As String  
    Dim currentImage As Image  
    Dim maxThumbSize As Integer  
    Dim thumbnailImage As Image  
    Dim thumbnailFile As String  
    Dim thumbnailHeight As Integer  
    Dim thumbnailWidth As Integer  
  
    currentImageFile = Dts.Variables("CurrentImageFile").Value.ToString  
    thumbnailFile = Path.Combine( _  
        Path.GetDirectoryName(currentImageFile), _  
        String.Concat(Path.GetFileNameWithoutExtension(currentImageFile), _  
        "_thumbnail.jpg"))  
  
    Try  
        currentImage = Image.FromFile(currentImageFile)  
  
        maxThumbSize = CType(Dts.Variables("MaxThumbSize").Value, Integer)  
        CalculateThumbnailSize( _  
            maxThumbSize, currentImage, thumbnailWidth, thumbnailHeight)  
  
        thumbnailImage = currentImage.GetThumbnailImage( _  
           thumbnailWidth, thumbnailHeight, Nothing, Nothing)  
        thumbnailImage.Save(thumbnailFile)  
        Dts.TaskResult = ScriptResults.Success  
    Catch ex As Exception  
        Dts.Events.FireError(0, "Script Task Example", _  
        ex.Message & ControlChars.CrLf & ex.StackTrace, _  
        String.Empty, 0)  
        Dts.TaskResult = ScriptResults.Failure  
    End Try  
  
End Sub  
  
Private Sub CalculateThumbnailSize( _  
    ByVal maxSize As Integer, ByVal sourceImage As Image, _  
    ByRef thumbWidth As Integer, ByRef thumbHeight As Integer)  
  
    If sourceImage.Width > sourceImage.Height Then  
        thumbWidth = maxSize  
        thumbHeight = CInt((maxSize / sourceImage.Width) * sourceImage.Height)  
    Else  
        thumbHeight = maxSize  
        thumbWidth = CInt((maxSize / sourceImage.Height) * sourceImage.Width)  
    End If  
  
End Sub  
```  
  
```csharp  
bool ThumbnailCallback()  
        {  
            return false;  
        }  
        public void Main()  
        {  
  
            string currentImageFile;  
            Image currentImage;  
            int maxThumbSize;  
            Image thumbnailImage;  
            string thumbnailFile;  
            int thumbnailHeight = 0;  
            int thumbnailWidth = 0;  
  
            currentImageFile = Dts.Variables["CurrentImageFile"].Value.ToString();  
            thumbnailFile = Path.Combine(Path.GetDirectoryName(currentImageFile), String.Concat(Path.GetFileNameWithoutExtension(currentImageFile), "_thumbnail.jpg"));  
  
            try  
            {  
  
                currentImage = Image.FromFile(currentImageFile);  
  
                maxThumbSize = (int)Dts.Variables["MaxThumbSize"].Value;  
                CalculateThumbnailSize(maxThumbSize, currentImage, ref thumbnailWidth, ref thumbnailHeight);  
  
                Image.GetThumbnailImageAbort myCallback = new Image.GetThumbnailImageAbort(ThumbnailCallback);  
  
                thumbnailImage = currentImage.GetThumbnailImage(thumbnailWidth, thumbnailHeight, ThumbnailCallback, IntPtr.Zero);  
                thumbnailImage.Save(thumbnailFile);  
                Dts.TaskResult = (int)ScriptResults.Success;  
            }  
            catch (Exception ex)  
            {  
                Dts.Events.FireError(0, "Script Task Example", ex.Message + "\r" + ex.StackTrace, String.Empty, 0);  
                Dts.TaskResult = (int)ScriptResults.Failure;  
            }  
  
        }  
  
        private void CalculateThumbnailSize(int maxSize, Image sourceImage, ref int thumbWidth, ref int thumbHeight)  
        {  
  
            if (sourceImage.Width > sourceImage.Height)  
            {  
                thumbWidth = maxSize;  
                thumbHeight = (int)(sourceImage.Height * maxSize / sourceImage.Width);  
            }  
            else  
            {  
                thumbHeight = maxSize;  
                thumbWidth = (int)(sourceImage.Width * maxSize / sourceImage.Height);  
  
            }  
  
        }  
  
```  
  
<span data-ttu-id="e2a85-140">![Integration Services 图标 (小型) ](../media/dts-16.gif "集成服务图标（小）")  **随时保持最新 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="e2a85-140">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="e2a85-141">若要从 Microsoft 获得最新的下载内容、文章、示例和视频，以及从社区获得所选解决方案，请访问 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 页：</span><span class="sxs-lookup"><span data-stu-id="e2a85-141">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="e2a85-142">访问 MSDN 上的 Integration Services 页</span><span class="sxs-lookup"><span data-stu-id="e2a85-142">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="e2a85-143">若要获得有关这些更新的自动通知，请订阅该页上提供的 RSS 源。</span><span class="sxs-lookup"><span data-stu-id="e2a85-143">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
