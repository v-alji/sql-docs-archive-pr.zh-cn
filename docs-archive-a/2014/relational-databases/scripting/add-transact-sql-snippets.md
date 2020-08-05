---
title: 添加 Transact-SQL 代码段
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 901c7995-8eb5-4d12-8bb0-de0a922b48f8
author: rothja
ms.author: jroth
ms.openlocfilehash: 5b5886f8f36ae3753fcb7c89dd3aeff9c69eeba5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87580661"
---
# <a name="add-transact-sql-snippets"></a><span data-ttu-id="af012-102">添加 Transact-SQL 代码段</span><span class="sxs-lookup"><span data-stu-id="af012-102">Add Transact-SQL Snippets</span></span>
  <span data-ttu-id="af012-103">您可以将自己的 Transact-SQL 代码段添加到在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中包括的一组预定义的代码段中。</span><span class="sxs-lookup"><span data-stu-id="af012-103">You can add your own Transact-SQL code snippets to the set of pre-defined snippets included in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="creating-a-transact-sql-snippet-file"></a><span data-ttu-id="af012-104">创建 Transact-SQL 代码段文件</span><span class="sxs-lookup"><span data-stu-id="af012-104">Creating a Transact-SQL Snippet File</span></span>  
 <span data-ttu-id="af012-105">创建 [!INCLUDE[tsql](../../includes/tsql-md.md)] 代码段的第一步是创建具有您的代码段文本的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="af012-105">The first part of creating a [!INCLUDE[tsql](../../includes/tsql-md.md)] code snippet is to create an XML file with the text of your code snippet.</span></span> <span data-ttu-id="af012-106">该文件必须具有 .snippet 文件扩展名，并且必须满足 [代码段架构](https://go.microsoft.com/fwlink/?LinkId=207504)的要求。</span><span class="sxs-lookup"><span data-stu-id="af012-106">The file must have a .snippet file extension, and meet the requirements of the [Code Snippets Schema](https://go.microsoft.com/fwlink/?LinkId=207504).</span></span> <span data-ttu-id="af012-107">将代码段语言设置为 SQL。</span><span class="sxs-lookup"><span data-stu-id="af012-107">Set the snippet language to SQL.</span></span>  
  
 <span data-ttu-id="af012-108">您可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 随附的预定义代码段作为示例。</span><span class="sxs-lookup"><span data-stu-id="af012-108">You can use the pre-defined snippets that ship with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as examples.</span></span> <span data-ttu-id="af012-109">若要找到预定义的代码段，请打开 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]，选择“工具”  菜单，然后单击“代码段管理器”  。</span><span class="sxs-lookup"><span data-stu-id="af012-109">To find the pre-defined snippets, open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], select the **Tools** menu, and click **Code Snippet Manager**.</span></span> <span data-ttu-id="af012-110">在 **“语言”** 列表框中选择 **SQL** ，指向 [!INCLUDE[tsql](../../includes/tsql-md.md)] 代码段的路径将显示在 **“位置”** 框中。</span><span class="sxs-lookup"><span data-stu-id="af012-110">Select **SQL** in the **Language** list box, the path to the [!INCLUDE[tsql](../../includes/tsql-md.md)] snippets is displayed in the **Location** box.</span></span>  
  
## <a name="registering-the-code-snippet"></a><span data-ttu-id="af012-111">注册代码段</span><span class="sxs-lookup"><span data-stu-id="af012-111">Registering the Code Snippet</span></span>  
 <span data-ttu-id="af012-112">在创建代码段文件后，使用代码段管理器向 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]注册该代码段。</span><span class="sxs-lookup"><span data-stu-id="af012-112">After creating the snippet file, use the Code Snippets Manager to register the snippet with [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="af012-113">您可以添加包含多个代码段的文件夹，或者将单独的代码段导入到 **“我的代码段”** 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="af012-113">You can either add a folder containing multiple snippets, or import individual snippets to the **My Code Snippets** folder.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="af012-114">过程</span><span class="sxs-lookup"><span data-stu-id="af012-114">Procedures</span></span>  
  
#### <a name="adding-a-snippet-folder"></a><span data-ttu-id="af012-115">添加代码段文件夹</span><span class="sxs-lookup"><span data-stu-id="af012-115">Adding a Snippet Folder</span></span>  
  
1.  <span data-ttu-id="af012-116">打开 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="af012-116">Open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="af012-117">选择 **“工具”** 菜单，然后单击 **“代码段管理器”** 。</span><span class="sxs-lookup"><span data-stu-id="af012-117">Select the **Tools** menu, and click **Code Snippets Manager**.</span></span>  
  
3.  <span data-ttu-id="af012-118">单击 **“添加”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="af012-118">Click the **Add** button.</span></span>  
  
4.  <span data-ttu-id="af012-119">导航到包含您的代码段的文件夹，然后单击 **“选择文件夹”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="af012-119">Navigate to the folder containing your code snippets, and click the **Select Folder** button.</span></span>  
  
#### <a name="importing-a-snippet"></a><span data-ttu-id="af012-120">导入代码段</span><span class="sxs-lookup"><span data-stu-id="af012-120">Importing a Snippet</span></span>  
  
1.  <span data-ttu-id="af012-121">打开 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="af012-121">Open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="af012-122">选择 **“工具”** 菜单，然后单击 **“代码段管理器”** 。</span><span class="sxs-lookup"><span data-stu-id="af012-122">Select the **Tools** menu, and click **Code Snippets Manager**.</span></span>  
  
3.  <span data-ttu-id="af012-123">单击“导入”按钮。 </span><span class="sxs-lookup"><span data-stu-id="af012-123">Click the **Import** button.</span></span>  
  
4.  <span data-ttu-id="af012-124">导航到包含您的代码段的文件夹，单击 .snippet 文件，然后单击 **“打开”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="af012-124">Navigate to the folder containing your snippet, click on the .snippet file, and click the **Open** button.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="af012-125">示例</span><span class="sxs-lookup"><span data-stu-id="af012-125">Examples</span></span>  
 <span data-ttu-id="af012-126">下面的示例创建一个 `TRY-CATCH` 外侧代码段，然后将其导入到 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中。</span><span class="sxs-lookup"><span data-stu-id="af012-126">The following example creates a `TRY-CATCH` surround-with snippet and imports it to [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
1.  <span data-ttu-id="af012-127">将以下代码粘贴到记事本，然后将其另存为名为 TryCatch.snippet 的文件。</span><span class="sxs-lookup"><span data-stu-id="af012-127">Paste the following code into notepad, then save as a file named TryCatch.snippet.</span></span>  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <CodeSnippets  xmlns="https://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
    <_locDefinition xmlns="urn:locstudio">  
        <_locDefault _loc="locNone" />  
        <_locTag _loc="locData">Title</_locTag>  
        <_locTag _loc="locData">Description</_locTag>  
        <_locTag _loc="locData">Author</_locTag>  
        <_locTag _loc="locData">ToolTip</_locTag>  
       <_locTag _loc="locData">Default</_locTag>  
    </_locDefinition>  
    <CodeSnippet Format="1.0.0">  
    <Header>  
    <Title>TryCatch</Title>  
                            <Shortcut></Shortcut>  
    <Description>Example Snippet for Try-Catch.</Description>  
    <Author>SQL Server Books Online Example</Author>  
    <SnippetTypes>  
                                    <SnippetType>SurroundsWith</SnippetType>  
    </SnippetTypes>  
    </Header>  
    <Snippet>  
    <Declarations>  
                                    <Literal>  
                                    <ID>CatchCode</ID>  
                                    <ToolTip>Code to handle the caught error</ToolTip>  
                                    <Default>CatchCode</Default>  
                                    </Literal>  
    </Declarations>  
    <Code Language="SQL"><![CDATA[  
    BEGIN TRY  
  
    $selected$ $end$  
  
    END TRY  
    BEGIN CATCH  
  
    $CatchCode$  
  
    END CATCH;  
    ]]>  
    </Code>  
    </Snippet>  
    </CodeSnippet>  
    </CodeSnippets>  
    ```  
  
2.  <span data-ttu-id="af012-128">打开 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="af012-128">Open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
3.  <span data-ttu-id="af012-129">选择 **“工具”** 菜单，然后单击 **“代码段管理器”** 。</span><span class="sxs-lookup"><span data-stu-id="af012-129">Select the **Tools** menu, and click **Code Snippets Manager**.</span></span>  
  
4.  <span data-ttu-id="af012-130">单击“导入”按钮。 </span><span class="sxs-lookup"><span data-stu-id="af012-130">Click the **Import** button.</span></span>  
  
5.  <span data-ttu-id="af012-131">导航到包含 TryCatch.snippet 的文件夹，单击该 TryCatch.snippet 文件，然后单击 **“打开”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="af012-131">Navigate to the folder containing TryCatch.snippet, click on the TryCatch.snippet file, and click the **Open** button.</span></span> <span data-ttu-id="af012-132">您不应在 **“我的代码段”** 文件夹中具有 TryCatch 代码段。</span><span class="sxs-lookup"><span data-stu-id="af012-132">You should not have a TryCatch snippet in your **My Code Snippets** folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af012-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="af012-133">See Also</span></span>  
 [<span data-ttu-id="af012-134">插入外侧 Transact-SQL 代码片段</span><span class="sxs-lookup"><span data-stu-id="af012-134">Insert Surround-with Transact-SQL snippets</span></span>](insert-surround-with-transact-sql-snippets.md)  
  
  
