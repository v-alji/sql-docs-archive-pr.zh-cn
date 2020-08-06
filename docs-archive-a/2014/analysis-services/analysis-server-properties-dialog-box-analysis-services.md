---
title: Analysis Server 属性 "对话框中 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- SQL12.ASVS.SSMSIMBI.SERVERPROPERTIES.F1
- SQL12.ASVS.SQLSERVERSTUDIO.SERVERPROPERTIES.F1
helpviewer_keywords:
- Analysis Server Properties dialog box
ms.assetid: b01ec658-c191-49c9-a6cb-549b21a368ab
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6daef467782917d52fa00c6d236ce2d9305ab9e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87579410"
---
# <a name="analysis-server-properties-dialog-box-analysis-services"></a><span data-ttu-id="9e96a-102">“分析服务器属性”对话框 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="9e96a-102">Analysis Server Properties Dialog Box (Analysis Services)</span></span>
  <span data-ttu-id="9e96a-103">可以使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中的“分析服务器属性”\*\*\*\* 对话框，为 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例设置常规、语言/排序规则和安全设置。</span><span class="sxs-lookup"><span data-stu-id="9e96a-103">Use the **Analysis Server Properties** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to set the general, language/collation, and security settings for an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="9e96a-104">通过在“对象资源管理器”中右键单击某个 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例，再从上下文菜单中选择“属性”，可以显示“分析服务器属性”\*\*\*\*\*\*\*\*\*\*\*\* 对话框。</span><span class="sxs-lookup"><span data-stu-id="9e96a-104">You can display the **Analysis Server Properties** dialog box by right-clicking an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance in **Object Explorer** and selecting **Properties** from the context menu.</span></span> <span data-ttu-id="9e96a-105">**“分析服务器属性”** 对话框包含下列属性。</span><span class="sxs-lookup"><span data-stu-id="9e96a-105">The **Analysis Server Properties** dialog box contains the following properties.</span></span>  
  
## <a name="information-properties"></a><span data-ttu-id="9e96a-106">信息属性</span><span class="sxs-lookup"><span data-stu-id="9e96a-106">Information Properties</span></span>  
 <span data-ttu-id="9e96a-107">使用此页可查看服务器模式、版本和兼容性级别。</span><span class="sxs-lookup"><span data-stu-id="9e96a-107">Use this page to view server mode, version, and compatibility level.</span></span> <span data-ttu-id="9e96a-108">每个实例均在表格或多维服务器模式下进行安装，且能够加载表格或多维模型。</span><span class="sxs-lookup"><span data-stu-id="9e96a-108">Each instance is installed in either Tabular or Multidimensional server mode, with the ability to load tabular or multidimensional models.</span></span> <span data-ttu-id="9e96a-109">如果您需要支持这两种模式，则必须安装两个实例。</span><span class="sxs-lookup"><span data-stu-id="9e96a-109">If you need to support both modes, you must install two instances.</span></span>  
  
 <span data-ttu-id="9e96a-110">**支持的兼容级别**等效于 `DefaultCompatibilityLevel` AMO 中的属性。</span><span class="sxs-lookup"><span data-stu-id="9e96a-110">**Supported Compatibility Level** is equivalent to the `DefaultCompatibilityLevel` property in AMO.</span></span> <span data-ttu-id="9e96a-111">它是只读的，且基于安装期间指定的服务器部署模式。</span><span class="sxs-lookup"><span data-stu-id="9e96a-111">It is read-only, based on the server deployment mode specified during installation.</span></span> <span data-ttu-id="9e96a-112">服务器在执行因服务器模式或版本而异的操作（如将表格数据库的备份还原到表格服务器实例上）时会检查此属性。</span><span class="sxs-lookup"><span data-stu-id="9e96a-112">The server checks this property when performing operations that vary by server mode or version, such as restoring a backup of a tabular database onto a tabular server instance.</span></span> <span data-ttu-id="9e96a-113">请不要将其与表格模型或多维模型的数据库兼容模式混淆，它们具有类似的名称和值。</span><span class="sxs-lookup"><span data-stu-id="9e96a-113">Do not confuse it with the database compatibility mode of tabular or multidimensional models, which have a similar names and values.</span></span> <span data-ttu-id="9e96a-114">此服务器属性的有效值包括：</span><span class="sxs-lookup"><span data-stu-id="9e96a-114">Valid values for this server property include:</span></span>  
  
-   <span data-ttu-id="9e96a-115">对于多维模式和数据挖掘模式，**1100** 是部署模式 0 的默认兼容级别。</span><span class="sxs-lookup"><span data-stu-id="9e96a-115">**1100** is the default compatibility level for a deployment mode of 0, for multidimensional and data mining mode.</span></span>  
  
-   <span data-ttu-id="9e96a-116">对于支持表格模式或**的安装，** 1103 [!INCLUDE[ssGeminiShort](../includes/ssgeminishort-md.md)]是部署模式 1 或 2 的默认兼容级别。</span><span class="sxs-lookup"><span data-stu-id="9e96a-116">**1103** is the default compatibility level for deployment modes 1 or 2, for installations supporting Tabular mode or [!INCLUDE[ssGeminiShort](../includes/ssgeminishort-md.md)].</span></span>  
  
 <span data-ttu-id="9e96a-117">在支持命名空间的客户端请求 DISCOVER_XML_METADATA 时，服务器将返回此值。</span><span class="sxs-lookup"><span data-stu-id="9e96a-117">The server returns this value when a client supporting the namespace requests DISCOVER_XML_METADATA.</span></span> <span data-ttu-id="9e96a-118">有关详细信息，请参阅 [DISCOVER_XML_METADATA 行集](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-xml-metadata-rowset) 。</span><span class="sxs-lookup"><span data-stu-id="9e96a-118">See [DISCOVER_XML_METADATA Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-xml-metadata-rowset) for more details.</span></span>  
  
## <a name="general-properties"></a><span data-ttu-id="9e96a-119">常规属性</span><span class="sxs-lookup"><span data-stu-id="9e96a-119">General Properties</span></span>  
 <span data-ttu-id="9e96a-120">使用此页可设置 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例的基本和高级的常规属性，如文件夹位置和网络设置。</span><span class="sxs-lookup"><span data-stu-id="9e96a-120">Use this page to set the basic and advanced general properties, such as folder locations and network settings, for an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="9e96a-121">服务器属性页仅显示管理员更有可能更改的属性，如用于针对特定配置优化服务器的内存和线程池属性。</span><span class="sxs-lookup"><span data-stu-id="9e96a-121">The server properties page shows only those properties an administrator is more likely to change, such as memory and thread pool properties used to tune the server for certain configurations.</span></span> <span data-ttu-id="9e96a-122">下面的列表提供了指向主属性组的链接：</span><span class="sxs-lookup"><span data-stu-id="9e96a-122">The following list provides links to the main property groups:</span></span>  
  
-   [<span data-ttu-id="9e96a-123">常规属性</span><span class="sxs-lookup"><span data-stu-id="9e96a-123">General Properties</span></span>](server-properties/general-properties.md)  
  
-   [<span data-ttu-id="9e96a-124">数据挖掘属性</span><span class="sxs-lookup"><span data-stu-id="9e96a-124">Data Mining Properties</span></span>](server-properties/data-mining-properties.md)  
  
-   [<span data-ttu-id="9e96a-125">Feature 属性</span><span class="sxs-lookup"><span data-stu-id="9e96a-125">Feature Properties</span></span>](server-properties/feature-properties.md)  
  
-   [<span data-ttu-id="9e96a-126">每个属性</span><span class="sxs-lookup"><span data-stu-id="9e96a-126">Filestore Properties</span></span>](server-properties/filestore-properties.md)  
  
-   [<span data-ttu-id="9e96a-127">锁管理器属性</span><span class="sxs-lookup"><span data-stu-id="9e96a-127">Lock Manager Properties</span></span>](server-properties/lock-manager-properties.md)  
  
-   [<span data-ttu-id="9e96a-128">日志属性</span><span class="sxs-lookup"><span data-stu-id="9e96a-128">Log Properties</span></span>](server-properties/log-properties.md)  
  
-   [<span data-ttu-id="9e96a-129">内存属性</span><span class="sxs-lookup"><span data-stu-id="9e96a-129">Memory Properties</span></span>](server-properties/memory-properties.md)  
  
-   [<span data-ttu-id="9e96a-130">网络属性</span><span class="sxs-lookup"><span data-stu-id="9e96a-130">Network Properties</span></span>](server-properties/network-properties.md)  
  
-   [<span data-ttu-id="9e96a-131">OLAP 属性</span><span class="sxs-lookup"><span data-stu-id="9e96a-131">OLAP Properties</span></span>](server-properties/olap-properties.md)  
  
-   [<span data-ttu-id="9e96a-132">安全属性</span><span class="sxs-lookup"><span data-stu-id="9e96a-132">Security Properties</span></span>](server-properties/security-properties.md)  
  
-   [<span data-ttu-id="9e96a-133">线程池属性</span><span class="sxs-lookup"><span data-stu-id="9e96a-133">Thread Pool Properties</span></span>](server-properties/thread-pool-properties.md)  
  
## <a name="language-collation-properties"></a><span data-ttu-id="9e96a-134">语言排序规则属性</span><span class="sxs-lookup"><span data-stu-id="9e96a-134">Language Collation Properties</span></span>  
 <span data-ttu-id="9e96a-135">使用此页可设置 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]的默认语言和排序规则选项。</span><span class="sxs-lookup"><span data-stu-id="9e96a-135">Use this page to set the default language and collation options for an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="9e96a-136">下面的列表包含每个选项的简短说明。</span><span class="sxs-lookup"><span data-stu-id="9e96a-136">The following list contains short descriptions of each option.</span></span> <span data-ttu-id="9e96a-137">有关详细信息，请参阅 [Languages and Collations &#40;Analysis Services&#41;](languages-and-collations-analysis-services.md) 。</span><span class="sxs-lookup"><span data-stu-id="9e96a-137">See [Languages and Collations &#40;Analysis Services&#41;](languages-and-collations-analysis-services.md) for more detailed descriptions.</span></span>  
  
-   <span data-ttu-id="9e96a-138">**“二进制”** 用于根据为每个字符定义的位模式对数据进行排序和比较。</span><span class="sxs-lookup"><span data-stu-id="9e96a-138">**Binary** is used to sort and compare data based on the bit patterns defined for each character.</span></span> <span data-ttu-id="9e96a-139">二进制排序顺序区分大小写，即先小写字母后大写字母，并区分重音。</span><span class="sxs-lookup"><span data-stu-id="9e96a-139">Binary sort order is case-sensitive, that is, lowercase precedes uppercase, and accent-sensitive.</span></span> <span data-ttu-id="9e96a-140">这是最快的排序顺序。</span><span class="sxs-lookup"><span data-stu-id="9e96a-140">This is the fastest sorting order.</span></span>  
  
     <span data-ttu-id="9e96a-141">如果未选择此选项，则 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 将遵循字典中定义的相关语言或字母表的排序和比较规则。</span><span class="sxs-lookup"><span data-stu-id="9e96a-141">If this option is not selected, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] follows sorting and comparison rules as defined in dictionaries for the associated language or alphabet.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9e96a-142">如果选择此选项，将会禁用“区分大小写”、“区分重音”、“区分假名”和“区分全半角”选项\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9e96a-142">If this option is selected, the **Case-Sensitive**, **Accent-Sensitive**, **Kana-Sensitive**, and **Width-Sensitive** options are disabled.</span></span>  
  
-   <span data-ttu-id="9e96a-143">**“二进制 2”** 用于根据为每个字符定义的位模式对 Unicode 数据进行排序和比较。</span><span class="sxs-lookup"><span data-stu-id="9e96a-143">**Binary 2** is used to sort and compare Unicode data based on the bit patterns defined for each character.</span></span> <span data-ttu-id="9e96a-144">二进制排序顺序区分大小写，即先小写字母后大写字母，并区分重音。</span><span class="sxs-lookup"><span data-stu-id="9e96a-144">Binary sort order is case-sensitive, that is, lowercase precedes uppercase, and accent-sensitive.</span></span> <span data-ttu-id="9e96a-145">这是最快的排序顺序。</span><span class="sxs-lookup"><span data-stu-id="9e96a-145">This is the fastest sorting order.</span></span>  
  
-   <span data-ttu-id="9e96a-146">“区分大小写”\*\*\*\* 用于根据为相关语言或字母表提供的字典规则对数据进行排序和比较，并区分大小写字母。</span><span class="sxs-lookup"><span data-stu-id="9e96a-146">**Case-Sensitive** is used to sort and compare data based on the dictionary rules provided for the associated language or alphabet, and to distinguish between uppercase and lowercase letters.</span></span>  
  
     <span data-ttu-id="9e96a-147">如果未选择此选项， [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 将认为大写字母和小写字母是一样的。</span><span class="sxs-lookup"><span data-stu-id="9e96a-147">If this option is not selected, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] considers the uppercase and lowercase versions of letters to be equal.</span></span> [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]<span data-ttu-id="9e96a-148">如果未选择 "**区分大小写**"，则不会定义小写字母是否根据大写字母进行排序。</span><span class="sxs-lookup"><span data-stu-id="9e96a-148">does not define whether lowercase letters sort lower or higher in relation to uppercase letters when **Case-sensitive** is not selected.</span></span>  
  
-   <span data-ttu-id="9e96a-149">“区分重音”\*\*\*\* 用于根据为相关语言或字母表提供的字典规则对数据进行排序和比较，并区分重音和非重音字符。</span><span class="sxs-lookup"><span data-stu-id="9e96a-149">**Accent-Sensitive** is used to sort and compare data based on the dictionary rules provided for the associated language or alphabet, and to distinguish between accented and unaccented characters.</span></span> <span data-ttu-id="9e96a-150">例如，“a”和“á”将被视为不同的字符。</span><span class="sxs-lookup"><span data-stu-id="9e96a-150">For example, 'a' is not equal to 'á'.</span></span>  
  
     <span data-ttu-id="9e96a-151">如果未选择此选项，则 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 会将字母的重音形式和非重音形式视为相同。</span><span class="sxs-lookup"><span data-stu-id="9e96a-151">If this option is not selected, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] considers the accented and unaccented versions of letters to be equal.</span></span>  
  
-   <span data-ttu-id="9e96a-152">“区分假名”\*\*\*\* 用于根据为相关语言或字母表提供的字典规则对数据进行排序和比较，并区分日语中的两种假名字符类型：平假名和片假名。</span><span class="sxs-lookup"><span data-stu-id="9e96a-152">**Kana-Sensitive** is used to and compare data based on the dictionary rules provided for the associated language or alphabet, and to distinguish between the two types of Japanese kana characters: Hiragana and Katakana.</span></span>  
  
     <span data-ttu-id="9e96a-153">如果未选择此选项，则 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 会将平假名字符和片假名字符视为相同。</span><span class="sxs-lookup"><span data-stu-id="9e96a-153">If this option is not selected, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] considers Hiragana and Katakana characters to be equal.</span></span>  
  
-   <span data-ttu-id="9e96a-154">“区分全半角”\*\*\*\* 用于根据为相关语言或字母表提供的字典规则对数据进行排序和比较，并区分以单字节字符（半角）和双字节字符（全角）表示的相同字符。</span><span class="sxs-lookup"><span data-stu-id="9e96a-154">**Width-Sensitive** is used to sort and compare data based on the dictionary rules provided for the associated language or alphabet, and to distinguish between a single-byte character (half-width) and the same character when represented as a double-byte character (full-width).</span></span>  
  
     <span data-ttu-id="9e96a-155">如果未选择此选项，则 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 会将同一字符的单字节形式和双字节形式视为相同。</span><span class="sxs-lookup"><span data-stu-id="9e96a-155">If this option is not selected, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] considers the single-byte and double-byte representation of the same character to be equal.</span></span>  
  
## <a name="security-properties"></a><span data-ttu-id="9e96a-156">安全属性</span><span class="sxs-lookup"><span data-stu-id="9e96a-156">Security Properties</span></span>  
 <span data-ttu-id="9e96a-157">使用此页可为 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 实例指定属于服务器管理员角色的 Windows 用户帐户和组帐户。</span><span class="sxs-lookup"><span data-stu-id="9e96a-157">Use this page to specify the Windows user and group accounts belonging to the server administrator role for an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="9e96a-158">此角色中的成员身份传达执行服务器范围内任务（如创建或处理数据库、修改服务器属性、添加或删除此角色的其他成员或启动跟踪）的权限。</span><span class="sxs-lookup"><span data-stu-id="9e96a-158">Membership in this role conveys permission to perform server-wide tasks, such as creating or processing a database, modifying server properties, adding or removing other members of this role, or launching a trace.</span></span> <span data-ttu-id="9e96a-159">有关详细信息，请参阅[授予服务器管理员权限 &#40;Analysis Services&#41;](instances/grant-server-admin-rights-to-an-analysis-services-instance.md) 。</span><span class="sxs-lookup"><span data-stu-id="9e96a-159">See [Grant Server Administrator Permissions &#40;Analysis Services&#41;](instances/grant-server-admin-rights-to-an-analysis-services-instance.md) for details.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e96a-160">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9e96a-160">See Also</span></span>  
 <span data-ttu-id="9e96a-161">[确定 Analysis Services 实例的服务器模式](instances/determine-the-server-mode-of-an-analysis-services-instance.md) </span><span class="sxs-lookup"><span data-stu-id="9e96a-161">[Determine the Server Mode of an Analysis Services Instance](instances/determine-the-server-mode-of-an-analysis-services-instance.md) </span></span>  
 <span data-ttu-id="9e96a-162">[在 Analysis Services 中配置服务器属性](server-properties/server-properties-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="9e96a-162">[Configure Server Properties in Analysis Services](server-properties/server-properties-in-analysis-services.md) </span></span>  
 <span data-ttu-id="9e96a-163">[Analysis Services 支持的身份验证方法](instances/authentication-methodologies-supported-by-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="9e96a-163">[Authentication methodologies supported by Analysis Services](instances/authentication-methodologies-supported-by-analysis-services.md) </span></span>  
 <span data-ttu-id="9e96a-164">[角色和权限 &#40;Analysis Services&#41;](multidimensional-models/roles-and-permissions-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="9e96a-164">[Roles and Permissions &#40;Analysis Services&#41;](multidimensional-models/roles-and-permissions-analysis-services.md) </span></span>  
 [<span data-ttu-id="9e96a-165">语言和排序规则 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="9e96a-165">Languages and Collations &#40;Analysis Services&#41;</span></span>](languages-and-collations-analysis-services.md)  
  
  
