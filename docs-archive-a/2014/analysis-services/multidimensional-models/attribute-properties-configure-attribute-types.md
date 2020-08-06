---
title: 配置属性类型 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- time dimensions [Analysis Services]
- attributes [Analysis Services], types
- slowly changing dimensions
- account dimensions [Analysis Services]
- currency dimensions [Analysis Services]
- Type property
ms.assetid: c2c6a3da-555e-4362-a83f-88da28427520
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3431d26d383ef5348f66a5a54a0f445a1d84872a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87693567"
---
# <a name="configure-attribute-types"></a><span data-ttu-id="8efd1-102">配置属性类型</span><span class="sxs-lookup"><span data-stu-id="8efd1-102">Configure Attribute Types</span></span>
  <span data-ttu-id="8efd1-103">在中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，特性类型可帮助根据业务功能对特性进行分类。</span><span class="sxs-lookup"><span data-stu-id="8efd1-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], attribute types help classify an attribute in terms of business functionality.</span></span> <span data-ttu-id="8efd1-104">特性类型的数目很多，其中的大部分都可由客户端应用程序用来显示或支持特性。</span><span class="sxs-lookup"><span data-stu-id="8efd1-104">There are many attribute types, most of which are used by client applications to display or support an attribute.</span></span> <span data-ttu-id="8efd1-105">但是，某些特性类型对于 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]还有特定的含义。</span><span class="sxs-lookup"><span data-stu-id="8efd1-105">However, some attribute types also have specific meaning to [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="8efd1-106">例如，一些特性类型在时间维度的各种日历中用于标识代表时间段的特性。</span><span class="sxs-lookup"><span data-stu-id="8efd1-106">For example, some attribute types identify attributes that represent time periods in various calendars for time dimensions.</span></span>  
  
##  <a name="setting-attribute-types"></a><a name="setting_attibute_types"></a> <span data-ttu-id="8efd1-107">设置特性类型</span><span class="sxs-lookup"><span data-stu-id="8efd1-107">Setting Attribute Types</span></span>  
 <span data-ttu-id="8efd1-108">特性的 `Type` 属性值将确定该特性的特性类型。</span><span class="sxs-lookup"><span data-stu-id="8efd1-108">The value of the `Type` property for an attribute determines the attribute type for that attribute.</span></span> <span data-ttu-id="8efd1-109">在定义维度或特性时， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中的若干个向导可以对特性类型进行设置。</span><span class="sxs-lookup"><span data-stu-id="8efd1-109">Several wizards in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] set attribute types when defining dimensions or attributes.</span></span> <span data-ttu-id="8efd1-110">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 向导在维度中添加功能时，也会设置特性类型。</span><span class="sxs-lookup"><span data-stu-id="8efd1-110">These [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] wizards also set attribute types when the wizards add functionality to dimensions.</span></span> <span data-ttu-id="8efd1-111">例如，当商业智能向导添加帐户智能时，该向导将几个特性类型应用于维度中的特性，以标识包含维度中的名称、代码、编号和帐户结构的特性。</span><span class="sxs-lookup"><span data-stu-id="8efd1-111">For example, the Business Intelligence Wizard applies several attribute types to attributes in a dimension when the wizard adds account intelligence to identify attributes that contain the names, codes, numbers, and structure of accounts in the dimension.</span></span> <span data-ttu-id="8efd1-112">商业智能向导还可使用属性类型，例如用于货币换算。</span><span class="sxs-lookup"><span data-stu-id="8efd1-112">The Business Intelligence Wizard also consumes attribute types, such as for currency conversion.</span></span> <span data-ttu-id="8efd1-113">有关详细信息，请参阅 [创建货币类型维度](database-dimensions-create-a-currency-type-dimension.md)。</span><span class="sxs-lookup"><span data-stu-id="8efd1-113">For more information, see [Create a Currency type Dimension](database-dimensions-create-a-currency-type-dimension.md).</span></span>  
  
 <span data-ttu-id="8efd1-114">下表列出了 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]中可用的特性类型。</span><span class="sxs-lookup"><span data-stu-id="8efd1-114">The following tables list the attribute types available in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="8efd1-115">这些表将特性类型划分成以下类别：</span><span class="sxs-lookup"><span data-stu-id="8efd1-115">These tables separate attribute types into the following categories:</span></span>  
  
|<span data-ttu-id="8efd1-116">术语</span><span class="sxs-lookup"><span data-stu-id="8efd1-116">Term</span></span>|<span data-ttu-id="8efd1-117">定义</span><span class="sxs-lookup"><span data-stu-id="8efd1-117">Definition</span></span>|  
|----------|----------------|  
|[<span data-ttu-id="8efd1-118">常规特性类型</span><span class="sxs-lookup"><span data-stu-id="8efd1-118">General attribute types</span></span>](#general_attribute_types)|<span data-ttu-id="8efd1-119">这些值可用于所有特性，使用它们只是为了针对客户端应用程序对特性进行归类。</span><span class="sxs-lookup"><span data-stu-id="8efd1-119">These values are available to all attributes, and exist only to enable classification of attributes for client application purposes.</span></span>|  
|[<span data-ttu-id="8efd1-120">帐户维度特性类型</span><span class="sxs-lookup"><span data-stu-id="8efd1-120">Account dimension attribute types</span></span>](#account_dimension_attribute_types)|<span data-ttu-id="8efd1-121">这些值用于标识属于帐户维度的特性。</span><span class="sxs-lookup"><span data-stu-id="8efd1-121">These values identify an attribute that belongs to an account dimension.</span></span> <span data-ttu-id="8efd1-122">有关帐户维度的详细信息，请参阅 [创建父子类型维度的财务帐户](database-dimensions-finance-account-of-parent-child-type.md)。</span><span class="sxs-lookup"><span data-stu-id="8efd1-122">For more information about account dimension, see [Create a Finance Account of parent-child type Dimension](database-dimensions-finance-account-of-parent-child-type.md).</span></span>|  
|[<span data-ttu-id="8efd1-123">货币维度特性类型</span><span class="sxs-lookup"><span data-stu-id="8efd1-123">Currency dimension attribute type</span></span>](#currency_dimension_attribute_types)|<span data-ttu-id="8efd1-124">这些值用于标识属于货币维度的特性。</span><span class="sxs-lookup"><span data-stu-id="8efd1-124">These values identify an attribute that belongs to a currency dimension.</span></span> <span data-ttu-id="8efd1-125">有关货币维度的详细信息，请参阅 [创建货币类型维度](database-dimensions-create-a-currency-type-dimension.md)。</span><span class="sxs-lookup"><span data-stu-id="8efd1-125">For more information about currency dimensions, see [Create a Currency type Dimension](database-dimensions-create-a-currency-type-dimension.md).</span></span>|  
|[<span data-ttu-id="8efd1-126">渐变维度特性</span><span class="sxs-lookup"><span data-stu-id="8efd1-126">Slowly changing dimension attributes</span></span>](#slowly_changing_dimension_attribute_types)|<span data-ttu-id="8efd1-127">这些值用于标识属于渐变维度的特性。</span><span class="sxs-lookup"><span data-stu-id="8efd1-127">These values identify an attribute that belongs to a slowly changing dimension.</span></span>|  
|[<span data-ttu-id="8efd1-128">时间维度特性</span><span class="sxs-lookup"><span data-stu-id="8efd1-128">Time dimension attributes</span></span>](#time_dimension_attribute_types)|<span data-ttu-id="8efd1-129">这些值用于标识属于时间维度的特性。</span><span class="sxs-lookup"><span data-stu-id="8efd1-129">These values identify an attribute that belongs to a time dimension.</span></span> <span data-ttu-id="8efd1-130">有关时间维度的详细信息，请参阅 [创建日期类型维度](database-dimensions-create-a-date-type-dimension.md)。</span><span class="sxs-lookup"><span data-stu-id="8efd1-130">For more information about time dimensions, see [Create a Date type Dimension](database-dimensions-create-a-date-type-dimension.md).</span></span>|  
  
###  <a name="general-attribute-types"></a><a name="general_attribute_types"></a><span data-ttu-id="8efd1-131">常规属性类型</span><span class="sxs-lookup"><span data-stu-id="8efd1-131">General Attribute Types</span></span>  
  
|<span data-ttu-id="8efd1-132">特性类型值</span><span class="sxs-lookup"><span data-stu-id="8efd1-132">Attribute Type Value</span></span>|<span data-ttu-id="8efd1-133">说明</span><span class="sxs-lookup"><span data-stu-id="8efd1-133">Description</span></span>|  
|--------------------------|-----------------|  
|`Address`|<span data-ttu-id="8efd1-134">表示地址。</span><span class="sxs-lookup"><span data-stu-id="8efd1-134">Represents an address.</span></span>|  
|`AddressBuilding`|<span data-ttu-id="8efd1-135">表示地址中的建筑名。</span><span class="sxs-lookup"><span data-stu-id="8efd1-135">Represents a building identifier for an address.</span></span>|  
|`AddressCity`|<span data-ttu-id="8efd1-136">表示地址中的城市。</span><span class="sxs-lookup"><span data-stu-id="8efd1-136">Represents a city for an address.</span></span>|  
|`AddressCountry`|<span data-ttu-id="8efd1-137">表示地址中的国家（地区）。</span><span class="sxs-lookup"><span data-stu-id="8efd1-137">Represents a country or region for an address.</span></span>|  
|`AddressFax`|<span data-ttu-id="8efd1-138">表示传真电话号码。</span><span class="sxs-lookup"><span data-stu-id="8efd1-138">Represents a fax telephone number.</span></span>|  
|`AddressFloor`|<span data-ttu-id="8efd1-139">表示地址中的楼层号。</span><span class="sxs-lookup"><span data-stu-id="8efd1-139">Represents a floor identifier for an address.</span></span>|  
|`AddressHouse`|<span data-ttu-id="8efd1-140">表示地址中的楼牌号。</span><span class="sxs-lookup"><span data-stu-id="8efd1-140">Represents a house number for an address.</span></span>|  
|`AddressPhone`|<span data-ttu-id="8efd1-141">表示电话号码。</span><span class="sxs-lookup"><span data-stu-id="8efd1-141">Represents a telephone number.</span></span>|  
|`AddressQuarter`|<span data-ttu-id="8efd1-142">表示地址中的区。</span><span class="sxs-lookup"><span data-stu-id="8efd1-142">Represents a quarter for an address.</span></span>|  
|`AddressRoom`|<span data-ttu-id="8efd1-143">表示地址中的房间号。</span><span class="sxs-lookup"><span data-stu-id="8efd1-143">Represents a room identifier for an address.</span></span>|  
|`AddressStateOrProvince`|<span data-ttu-id="8efd1-144">表示地址中的省市自治区。</span><span class="sxs-lookup"><span data-stu-id="8efd1-144">Represents a state or province for an address.</span></span>|  
|`AddressStreet`|<span data-ttu-id="8efd1-145">表示地址中的街道名。</span><span class="sxs-lookup"><span data-stu-id="8efd1-145">Represents the street for an address.</span></span>|  
|`AddressZip`|<span data-ttu-id="8efd1-146">表示地址中的邮政编码。</span><span class="sxs-lookup"><span data-stu-id="8efd1-146">Represents a ZIP Code or Postal Code for an address.</span></span>|  
|`BomResource`|<span data-ttu-id="8efd1-147">表示物料清单 (BOM) 的资源。</span><span class="sxs-lookup"><span data-stu-id="8efd1-147">Represents a resource for a bill of materials (BOM).</span></span>|  
|`Caption`|<span data-ttu-id="8efd1-148">表示标题。</span><span class="sxs-lookup"><span data-stu-id="8efd1-148">Represents a caption.</span></span>|  
|`CaptionAbbreviation`|<span data-ttu-id="8efd1-149">表示缩写。</span><span class="sxs-lookup"><span data-stu-id="8efd1-149">Represents an abbreviation.</span></span>|  
|`CaptionDescription`|<span data-ttu-id="8efd1-150">表示说明。</span><span class="sxs-lookup"><span data-stu-id="8efd1-150">Represents a description.</span></span>|  
|`Channel`|<span data-ttu-id="8efd1-151">表示渠道。</span><span class="sxs-lookup"><span data-stu-id="8efd1-151">Represents a channel.</span></span>|  
|`City`|<span data-ttu-id="8efd1-152">表示市县。</span><span class="sxs-lookup"><span data-stu-id="8efd1-152">Represents a city.</span></span>|  
|`Company`|<span data-ttu-id="8efd1-153">表示公司。</span><span class="sxs-lookup"><span data-stu-id="8efd1-153">Represents a company.</span></span>|  
|`Continent`|<span data-ttu-id="8efd1-154">表示洲。</span><span class="sxs-lookup"><span data-stu-id="8efd1-154">Represents a continent.</span></span>|  
|`Country`|<span data-ttu-id="8efd1-155">表示国家（地区）。</span><span class="sxs-lookup"><span data-stu-id="8efd1-155">Represents a country or region.</span></span>|  
|`County`|<span data-ttu-id="8efd1-156">表示市县。</span><span class="sxs-lookup"><span data-stu-id="8efd1-156">Represents a county.</span></span>|  
|`CustomerGroup`|<span data-ttu-id="8efd1-157">表示客户组。</span><span class="sxs-lookup"><span data-stu-id="8efd1-157">Represents a group of customers.</span></span>|  
|`CustomerHousehold`|<span data-ttu-id="8efd1-158">表示全体客户。</span><span class="sxs-lookup"><span data-stu-id="8efd1-158">Represents a household of customers.</span></span>|  
|`Customers`|<span data-ttu-id="8efd1-159">表示客户。</span><span class="sxs-lookup"><span data-stu-id="8efd1-159">Represents a customer.</span></span>|  
|`DateCanceled`|<span data-ttu-id="8efd1-160">表示取消日期。</span><span class="sxs-lookup"><span data-stu-id="8efd1-160">Represents a cancellation date.</span></span>|  
|`DateDuration`|<span data-ttu-id="8efd1-161">表示持续时间。</span><span class="sxs-lookup"><span data-stu-id="8efd1-161">Represents a duration.</span></span>|  
|`DateEnded`|<span data-ttu-id="8efd1-162">表示结束日期。</span><span class="sxs-lookup"><span data-stu-id="8efd1-162">Represents an end date.</span></span>|  
|`DateModified`|<span data-ttu-id="8efd1-163">表示修改日期。</span><span class="sxs-lookup"><span data-stu-id="8efd1-163">Represents a modification date.</span></span>|  
|`DateStart`|<span data-ttu-id="8efd1-164">表示开始日期。</span><span class="sxs-lookup"><span data-stu-id="8efd1-164">Represents a start date.</span></span>|  
|<span data-ttu-id="8efd1-165">**DeletedFlag**</span><span class="sxs-lookup"><span data-stu-id="8efd1-165">**DeletedFlag**</span></span>|<span data-ttu-id="8efd1-166">指示成员是否已删除或应当删除（在业务功能方面）。</span><span class="sxs-lookup"><span data-stu-id="8efd1-166">Indicates whether a member is or should be deleted (in terms of business functionality.)</span></span><br /><br /> <span data-ttu-id="8efd1-167">注意： [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 不用此特性类型来确定是否应删除成员。</span><span class="sxs-lookup"><span data-stu-id="8efd1-167">Note: [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] does not use this attribute type to determine whether a member should be deleted.</span></span> <span data-ttu-id="8efd1-168">此特性类型仅用于客户端应用程序显示。</span><span class="sxs-lookup"><span data-stu-id="8efd1-168">Instead, this attribute type is intended to be used by client applications for display purposes only.</span></span>|  
|`FormattingColor`|<span data-ttu-id="8efd1-169">表示设置格式时使用的颜色。</span><span class="sxs-lookup"><span data-stu-id="8efd1-169">Represents the color used in formatting.</span></span>|  
|`FormattingFont`|<span data-ttu-id="8efd1-170">表示设置格式时使用的字体。</span><span class="sxs-lookup"><span data-stu-id="8efd1-170">Represents the font used in formatting.</span></span>|  
|`FormattingFontEffects`|<span data-ttu-id="8efd1-171">表示设置格式时使用的字体效果。</span><span class="sxs-lookup"><span data-stu-id="8efd1-171">Represents the font effects used in formatting.</span></span>|  
|`FormattingFontSize`|<span data-ttu-id="8efd1-172">表示设置格式时使用的字号。</span><span class="sxs-lookup"><span data-stu-id="8efd1-172">Represents the font size used in formatting.</span></span>|  
|`FormattingOrder`|<span data-ttu-id="8efd1-173">表示设置格式时使用的顺序。</span><span class="sxs-lookup"><span data-stu-id="8efd1-173">Represents the order used in formatting.</span></span>|  
|`FormattingSubtotal`|<span data-ttu-id="8efd1-174">表示小计。</span><span class="sxs-lookup"><span data-stu-id="8efd1-174">Represents a subtotal.</span></span>|  
|`GeoBoundaryBottom`|<span data-ttu-id="8efd1-175">表示地理边界的最底部的值。</span><span class="sxs-lookup"><span data-stu-id="8efd1-175">Represents the bottommost value of a geographic boundary.</span></span>|  
|`GeoBoundaryFront`|<span data-ttu-id="8efd1-176">表示地理边界前面的值。</span><span class="sxs-lookup"><span data-stu-id="8efd1-176">Represents the value at the front of a geographic boundary.</span></span>|  
|`GeoBoundaryLeft`|<span data-ttu-id="8efd1-177">表示地理边界的最左侧的值。</span><span class="sxs-lookup"><span data-stu-id="8efd1-177">Represents the leftmost value of a geographic boundary.</span></span>|  
|`GeoBoundaryPolygon`|<span data-ttu-id="8efd1-178">表示地理边界的多边形定义。</span><span class="sxs-lookup"><span data-stu-id="8efd1-178">Represents the polygon definition of a geographic boundary.</span></span>|  
|`GeoBoundaryRear`|<span data-ttu-id="8efd1-179">表示地理边界的最后面的值。</span><span class="sxs-lookup"><span data-stu-id="8efd1-179">Represents the rearmost value of a geographic boundary.</span></span>|  
|`GeoBoundaryRight`|<span data-ttu-id="8efd1-180">表示地理边界的最右侧的值。</span><span class="sxs-lookup"><span data-stu-id="8efd1-180">Represents the rightmost value of a geographic boundary.</span></span>|  
|`GeoBoundaryTop`|<span data-ttu-id="8efd1-181">表示地理边界的最顶部的值。</span><span class="sxs-lookup"><span data-stu-id="8efd1-181">Represents the topmost value of a geographic boundary.</span></span>|  
|`GeoCentroidX`|<span data-ttu-id="8efd1-182">表示地理区域的 X 轴中点。</span><span class="sxs-lookup"><span data-stu-id="8efd1-182">Represents an X-axis centroid for a geographic region.</span></span>|  
|`GeoCentroidY`|<span data-ttu-id="8efd1-183">表示地理区域的 Y 轴中点。</span><span class="sxs-lookup"><span data-stu-id="8efd1-183">Represents a Y-axis centroid for a geographic region.</span></span>|  
|`GeoCentroidZ`|<span data-ttu-id="8efd1-184">表示地理区域的 Z 轴中点。</span><span class="sxs-lookup"><span data-stu-id="8efd1-184">Represents a Z-axis centroid for a geographic region.</span></span>|  
|`ID`|<span data-ttu-id="8efd1-185">表示标识符 (ID) 或密钥。</span><span class="sxs-lookup"><span data-stu-id="8efd1-185">Represents an identifier (ID) or key.</span></span>|  
|`Image`|<span data-ttu-id="8efd1-186">表示未定义图形格式的图像。</span><span class="sxs-lookup"><span data-stu-id="8efd1-186">Represents an image in an undefined graphic format.</span></span>|  
|`ImageBmp`|<span data-ttu-id="8efd1-187">表示位图图形格式的图像。</span><span class="sxs-lookup"><span data-stu-id="8efd1-187">Represents an image in bitmap graphic format.</span></span>|  
|`ImageGif`|<span data-ttu-id="8efd1-188">表示图形交换格式 (GIF) 图形格式的图像。</span><span class="sxs-lookup"><span data-stu-id="8efd1-188">Represents an image in Graphics Interchange Format (GIF) graphic format.</span></span>|  
|`ImageJpg`|<span data-ttu-id="8efd1-189">表示联合图像专家组 (JPEG) 图形格式的图像。</span><span class="sxs-lookup"><span data-stu-id="8efd1-189">Represents an image in Joint Photographic Experts Group (JPEG) graphic format.</span></span>|  
|`ImagePng`|<span data-ttu-id="8efd1-190">表示可移植网络图形 (PNG) 图形格式的图像。</span><span class="sxs-lookup"><span data-stu-id="8efd1-190">Represents an image in Portable Network Graphics (PNG) graphic format.</span></span>|  
|`ImageTiff`|<span data-ttu-id="8efd1-191">表示标记图像文件格式 (TIFF) 图形格式的图像。</span><span class="sxs-lookup"><span data-stu-id="8efd1-191">Represents an image in Tagged Image File Format (TIFF) graphic format.</span></span>|  
|`OrganizationalUnit`|<span data-ttu-id="8efd1-192">表示部门。</span><span class="sxs-lookup"><span data-stu-id="8efd1-192">Represents an organizational unit.</span></span>|  
|`OrgTitle`|<span data-ttu-id="8efd1-193">表示单位名称。</span><span class="sxs-lookup"><span data-stu-id="8efd1-193">Represents an organizational title.</span></span>|  
|`PercentOwnership`|<span data-ttu-id="8efd1-194">表示所有权百分比。</span><span class="sxs-lookup"><span data-stu-id="8efd1-194">Represents a percent of ownership.</span></span>|  
|`PercentVoteRight`|<span data-ttu-id="8efd1-195">表示投票权百分比。</span><span class="sxs-lookup"><span data-stu-id="8efd1-195">Represents a percent of voting rights.</span></span>|  
|`Person`|<span data-ttu-id="8efd1-196">表示人员。</span><span class="sxs-lookup"><span data-stu-id="8efd1-196">Represents a person.</span></span>|  
|`PersonContact`|<span data-ttu-id="8efd1-197">表示人员的联系信息。</span><span class="sxs-lookup"><span data-stu-id="8efd1-197">Represents contact information for a person.</span></span>|  
|`PersonDemographic`|<span data-ttu-id="8efd1-198">表示人员的人口统计信息。</span><span class="sxs-lookup"><span data-stu-id="8efd1-198">Represents demographic information for a person.</span></span>|  
|`PersonFirstName`|<span data-ttu-id="8efd1-199">表示人员的名字。</span><span class="sxs-lookup"><span data-stu-id="8efd1-199">Represents the first name of a person.</span></span>|  
|`PersonFullName`|<span data-ttu-id="8efd1-200">表示人员的全名。</span><span class="sxs-lookup"><span data-stu-id="8efd1-200">Represents the full name of a person.</span></span>|  
|`PersonLastName`|<span data-ttu-id="8efd1-201">表示人员的姓氏。</span><span class="sxs-lookup"><span data-stu-id="8efd1-201">Represents the surname (last name) of a person.</span></span>|  
|`PersonMiddleName`|<span data-ttu-id="8efd1-202">表示人员的中间名。</span><span class="sxs-lookup"><span data-stu-id="8efd1-202">Represents the middle name of a person.</span></span>|  
|`PhysicalColor`|<span data-ttu-id="8efd1-203">表示颜色。</span><span class="sxs-lookup"><span data-stu-id="8efd1-203">Represents a color.</span></span>|  
|`PhysicalDensity`|<span data-ttu-id="8efd1-204">表示密度。</span><span class="sxs-lookup"><span data-stu-id="8efd1-204">Represents density.</span></span>|  
|`PhysicalDepth`|<span data-ttu-id="8efd1-205">表示深度。</span><span class="sxs-lookup"><span data-stu-id="8efd1-205">Represents depth.</span></span>|  
|`PhysicalHeight`|<span data-ttu-id="8efd1-206">表示高度。</span><span class="sxs-lookup"><span data-stu-id="8efd1-206">Represents height.</span></span>|  
|`PhysicalSize`|<span data-ttu-id="8efd1-207">表示大小。</span><span class="sxs-lookup"><span data-stu-id="8efd1-207">Represents a size.</span></span>|  
|`PhysicalVolume`|<span data-ttu-id="8efd1-208">表示体积。</span><span class="sxs-lookup"><span data-stu-id="8efd1-208">Represents volume.</span></span>|  
|`PhysicalWeight`|<span data-ttu-id="8efd1-209">表示重量。</span><span class="sxs-lookup"><span data-stu-id="8efd1-209">Represents weight.</span></span>|  
|`PhysicalWidth`|<span data-ttu-id="8efd1-210">表示宽度。</span><span class="sxs-lookup"><span data-stu-id="8efd1-210">Represents width.</span></span>|  
|`Point`|<span data-ttu-id="8efd1-211">表示点。</span><span class="sxs-lookup"><span data-stu-id="8efd1-211">Represents a point.</span></span>|  
|`PostalCode`|<span data-ttu-id="8efd1-212">表示邮政代码。</span><span class="sxs-lookup"><span data-stu-id="8efd1-212">Represents a postal code.</span></span>|  
|`Product`|<span data-ttu-id="8efd1-213">表示产品。</span><span class="sxs-lookup"><span data-stu-id="8efd1-213">Represents a product.</span></span>|  
|`ProductBrand`|<span data-ttu-id="8efd1-214">表示产品品牌。</span><span class="sxs-lookup"><span data-stu-id="8efd1-214">Represents a product brand.</span></span>|  
|`ProductCategory`|<span data-ttu-id="8efd1-215">表示产品类别。</span><span class="sxs-lookup"><span data-stu-id="8efd1-215">Represents a product category.</span></span>|  
|`ProductGroup`|<span data-ttu-id="8efd1-216">表示产品组。</span><span class="sxs-lookup"><span data-stu-id="8efd1-216">Represents a product group.</span></span>|  
|`ProductSKU`|<span data-ttu-id="8efd1-217">表示产品的单品 (SKU)。</span><span class="sxs-lookup"><span data-stu-id="8efd1-217">Represents a product stock keeping unit (SKU).</span></span>|  
|`Project`|<span data-ttu-id="8efd1-218">表示项目。</span><span class="sxs-lookup"><span data-stu-id="8efd1-218">Represents a project.</span></span>|  
|`ProjectCode`|<span data-ttu-id="8efd1-219">表示项目代码。</span><span class="sxs-lookup"><span data-stu-id="8efd1-219">Represents a project code.</span></span>|  
|`ProjectCompletion`|<span data-ttu-id="8efd1-220">表示项目的完成状态。</span><span class="sxs-lookup"><span data-stu-id="8efd1-220">Represents the completion status of a project.</span></span>|  
|`ProjectEndDate`|<span data-ttu-id="8efd1-221">表示项目的结束日期。</span><span class="sxs-lookup"><span data-stu-id="8efd1-221">Represents a project end date.</span></span>|  
|`ProjectName`|<span data-ttu-id="8efd1-222">表示项目名称。</span><span class="sxs-lookup"><span data-stu-id="8efd1-222">Represents a project name.</span></span>|  
|`ProjectStartDate`|<span data-ttu-id="8efd1-223">表示项目的开始日期。</span><span class="sxs-lookup"><span data-stu-id="8efd1-223">Represents a project start date.</span></span>|  
|`Promotion`|<span data-ttu-id="8efd1-224">表示促销。</span><span class="sxs-lookup"><span data-stu-id="8efd1-224">Represents a promotion.</span></span>|  
|`QtyRangeHigh`|<span data-ttu-id="8efd1-225">表示数量范围的上限。</span><span class="sxs-lookup"><span data-stu-id="8efd1-225">Represents the highest value of a range of quantities.</span></span>|  
|`QtyRangeLow`|<span data-ttu-id="8efd1-226">表示数量范围的下限。</span><span class="sxs-lookup"><span data-stu-id="8efd1-226">Represents the lowest value of a range of quantities.</span></span>|  
|`Quantitative`|<span data-ttu-id="8efd1-227">表示定量特性。</span><span class="sxs-lookup"><span data-stu-id="8efd1-227">Represents a quantitative attribute.</span></span>|  
|`Rate`|<span data-ttu-id="8efd1-228">表示比率。</span><span class="sxs-lookup"><span data-stu-id="8efd1-228">Represents a rate.</span></span>|  
|`RateType`|<span data-ttu-id="8efd1-229">表示比率类型。</span><span class="sxs-lookup"><span data-stu-id="8efd1-229">Represents a rate type.</span></span>|  
|`Region`|<span data-ttu-id="8efd1-230">表示客户定义地区。</span><span class="sxs-lookup"><span data-stu-id="8efd1-230">Represents a customer-defined region.</span></span>|  
|`Regular`|<span data-ttu-id="8efd1-231">表示常规特性。</span><span class="sxs-lookup"><span data-stu-id="8efd1-231">Represents a regular attribute.</span></span>|  
|`RelationToParent`|<span data-ttu-id="8efd1-232">表示与父级的关系。</span><span class="sxs-lookup"><span data-stu-id="8efd1-232">Represents a relation to a parent.</span></span>|  
|`Representative`|<span data-ttu-id="8efd1-233">表示代表。</span><span class="sxs-lookup"><span data-stu-id="8efd1-233">Represents a representative.</span></span>|  
|`Scenario`|<span data-ttu-id="8efd1-234">表示方案。</span><span class="sxs-lookup"><span data-stu-id="8efd1-234">Represents a scenario.</span></span>|  
|`Sequence`|<span data-ttu-id="8efd1-235">表示序列特性。</span><span class="sxs-lookup"><span data-stu-id="8efd1-235">Represents a sequence attribute.</span></span>|  
|`ShortCaption`|<span data-ttu-id="8efd1-236">表示短标题。</span><span class="sxs-lookup"><span data-stu-id="8efd1-236">Represents a short caption.</span></span>|  
|`StateOrProvince`|<span data-ttu-id="8efd1-237">表示省市自治区。</span><span class="sxs-lookup"><span data-stu-id="8efd1-237">Represents a state or province.</span></span>|  
|`Utility`|<span data-ttu-id="8efd1-238">表示效用。</span><span class="sxs-lookup"><span data-stu-id="8efd1-238">Represents a utility.</span></span>|  
|`Version`|<span data-ttu-id="8efd1-239">表示版本。</span><span class="sxs-lookup"><span data-stu-id="8efd1-239">Represents a version.</span></span>|  
|`WebHtml`|<span data-ttu-id="8efd1-240">表示 HTML 内容。</span><span class="sxs-lookup"><span data-stu-id="8efd1-240">Represents HTML content.</span></span>|  
|`WebMailAlias`|<span data-ttu-id="8efd1-241">表示电子邮件别名。</span><span class="sxs-lookup"><span data-stu-id="8efd1-241">Represents an e-mail alias.</span></span>|  
|`WebUrl`|<span data-ttu-id="8efd1-242">表示 URL 地址。</span><span class="sxs-lookup"><span data-stu-id="8efd1-242">Represents a URL address.</span></span>|  
|`WebXmlOrXsl`|<span data-ttu-id="8efd1-243">表示 XML 或 XSL 内容。</span><span class="sxs-lookup"><span data-stu-id="8efd1-243">Represents XML or XSL content.</span></span>|  
  
###  <a name="account-dimension-attribute-types"></a><a name="account_dimension_attribute_types"></a> <span data-ttu-id="8efd1-244">Account Dimension Attribute Types</span><span class="sxs-lookup"><span data-stu-id="8efd1-244">Account Dimension Attribute Types</span></span>  
  
|<span data-ttu-id="8efd1-245">特性类型值</span><span class="sxs-lookup"><span data-stu-id="8efd1-245">Attribute Type Value</span></span>|<span data-ttu-id="8efd1-246">说明</span><span class="sxs-lookup"><span data-stu-id="8efd1-246">Description</span></span>|  
|--------------------------|-----------------|  
|`Account`|<span data-ttu-id="8efd1-247">表示父级帐户。</span><span class="sxs-lookup"><span data-stu-id="8efd1-247">Represents the parent of an account.</span></span> <span data-ttu-id="8efd1-248">此特性类型通常应用于帐户维度的父级特性。</span><span class="sxs-lookup"><span data-stu-id="8efd1-248">This attribute type is typically applied to the parent attribute of an account dimension.</span></span>|  
|`AccountName`|<span data-ttu-id="8efd1-249">表示帐户的名称。</span><span class="sxs-lookup"><span data-stu-id="8efd1-249">Represents the name of an account.</span></span> <span data-ttu-id="8efd1-250">此特性类型通常应用于帐户维度的键特性。</span><span class="sxs-lookup"><span data-stu-id="8efd1-250">This attribute type is typically applied to the key attributes of an account dimension.</span></span>|  
|`AccountNumber`|<span data-ttu-id="8efd1-251">表示帐户的编号。</span><span class="sxs-lookup"><span data-stu-id="8efd1-251">Represents the number of an account.</span></span>|  
|`AccountType`|<span data-ttu-id="8efd1-252">表示帐户的类型。</span><span class="sxs-lookup"><span data-stu-id="8efd1-252">Represents the type of an account.</span></span> <span data-ttu-id="8efd1-253">此特性类型用于标识 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 数据库的帐户类型维度中的帐户成员的聚合函数。</span><span class="sxs-lookup"><span data-stu-id="8efd1-253">This attribute type identifies the aggregation function of an account member in an account type dimension in the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span>|  
  
###  <a name="currency-dimension-attribute-types"></a><a name="currency_dimension_attribute_types"></a> <span data-ttu-id="8efd1-254">货币维度特性类型</span><span class="sxs-lookup"><span data-stu-id="8efd1-254">Currency Dimension Attribute Types</span></span>  
  
|<span data-ttu-id="8efd1-255">特性类型值</span><span class="sxs-lookup"><span data-stu-id="8efd1-255">Attribute Type Value</span></span>|<span data-ttu-id="8efd1-256">说明</span><span class="sxs-lookup"><span data-stu-id="8efd1-256">Description</span></span>|  
|--------------------------|-----------------|  
|`CurrencyDestination`|<span data-ttu-id="8efd1-257">表示外币兑换的目标货币。</span><span class="sxs-lookup"><span data-stu-id="8efd1-257">Represents the destination currency of a currency exchange.</span></span> <span data-ttu-id="8efd1-258">此特性类型通常应用于报表维度的键特性，在货币换算中使用。</span><span class="sxs-lookup"><span data-stu-id="8efd1-258">This attribute type is typically applied to the key attribute of a reporting dimension, for use in currency conversion.</span></span> <span data-ttu-id="8efd1-259">有关货币换算的详细信息，请参阅[货币换算 (Analysis Services)](../currency-conversions-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="8efd1-259">For more information about currency conversion, see [Currency Conversions &#40;Analysis Services&#41;](../currency-conversions-analysis-services.md).</span></span>|  
|`CurrencyIsoCode`|<span data-ttu-id="8efd1-260">表示货币的国际标准组织 (ISO) 代码。</span><span class="sxs-lookup"><span data-stu-id="8efd1-260">Represents the International Standards Organization (ISO) code of a currency.</span></span> <span data-ttu-id="8efd1-261">有关货币换算的详细信息，请参阅[货币换算 (Analysis Services)](../currency-conversions-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="8efd1-261">For more information about currency conversion, see [Currency Conversions &#40;Analysis Services&#41;](../currency-conversions-analysis-services.md).</span></span>|  
|`CurrencyName`|<span data-ttu-id="8efd1-262">表示货币的名称。</span><span class="sxs-lookup"><span data-stu-id="8efd1-262">Represents the name of a currency.</span></span> <span data-ttu-id="8efd1-263">有关货币换算的详细信息，请参阅[货币换算 (Analysis Services)](../currency-conversions-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="8efd1-263">For more information about currency conversion, see [Currency Conversions &#40;Analysis Services&#41;](../currency-conversions-analysis-services.md).</span></span>|  
|`CurrencySource`|<span data-ttu-id="8efd1-264">表示货币换算的源货币。</span><span class="sxs-lookup"><span data-stu-id="8efd1-264">Represents the source currency of a currency exchange.</span></span> <span data-ttu-id="8efd1-265">此特性类型通常应用于货币维度的键特性，在货币换算中使用。</span><span class="sxs-lookup"><span data-stu-id="8efd1-265">This attribute type is typically applied to the key attribute of a currency dimension, for use in currency conversion.</span></span> <span data-ttu-id="8efd1-266">有关货币换算的详细信息，请参阅[货币换算 (Analysis Services)](../currency-conversions-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="8efd1-266">For more information about currency conversion, see [Currency Conversions &#40;Analysis Services&#41;](../currency-conversions-analysis-services.md).</span></span>|  
  
###  <a name="slowly-changing-dimension-attribute-types"></a><a name="slowly_changing_dimension_attribute_types"></a> <span data-ttu-id="8efd1-267">渐变维度特性类型</span><span class="sxs-lookup"><span data-stu-id="8efd1-267">Slowly Changing Dimension Attribute Types</span></span>  
  
|<span data-ttu-id="8efd1-268">特性类型值</span><span class="sxs-lookup"><span data-stu-id="8efd1-268">Attribute Type Value</span></span>|<span data-ttu-id="8efd1-269">说明</span><span class="sxs-lookup"><span data-stu-id="8efd1-269">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="8efd1-270">**ScdEndDate**</span><span class="sxs-lookup"><span data-stu-id="8efd1-270">**ScdEndDate**</span></span>|<span data-ttu-id="8efd1-271">表示渐变维度中的成员的有效结束日期。</span><span class="sxs-lookup"><span data-stu-id="8efd1-271">Represents the effective end date for a member in a slowly changing dimension.</span></span>|  
|<span data-ttu-id="8efd1-272">**ScdOriginalID**</span><span class="sxs-lookup"><span data-stu-id="8efd1-272">**ScdOriginalID**</span></span>|<span data-ttu-id="8efd1-273">表示渐变维度中的成员的原始标识符。</span><span class="sxs-lookup"><span data-stu-id="8efd1-273">Represents the original identifier for a member in a slowly changing dimension.</span></span>|  
|<span data-ttu-id="8efd1-274">**ScdStartDate**</span><span class="sxs-lookup"><span data-stu-id="8efd1-274">**ScdStartDate**</span></span>|<span data-ttu-id="8efd1-275">表示渐变维度中的成员的有效开始日期。</span><span class="sxs-lookup"><span data-stu-id="8efd1-275">Represents the effective start date for a member in a slowly changing dimension.</span></span>|  
|`ScdStatus`|<span data-ttu-id="8efd1-276">表示渐变维度中的成员的有效状态。</span><span class="sxs-lookup"><span data-stu-id="8efd1-276">Represents the effective status of a member in a slowly changing dimension.</span></span>|  
  
###  <a name="time-dimension-attribute-types"></a><a name="time_dimension_attribute_types"></a> <span data-ttu-id="8efd1-277">时间维度特性类型</span><span class="sxs-lookup"><span data-stu-id="8efd1-277">Time Dimension Attribute Types</span></span>  
  
|<span data-ttu-id="8efd1-278">特性类型值</span><span class="sxs-lookup"><span data-stu-id="8efd1-278">Attribute Type Value</span></span>|<span data-ttu-id="8efd1-279">说明</span><span class="sxs-lookup"><span data-stu-id="8efd1-279">Description</span></span>|  
|--------------------------|-----------------|  
|`Date`|<span data-ttu-id="8efd1-280">表示日期。</span><span class="sxs-lookup"><span data-stu-id="8efd1-280">Represents a date.</span></span> <span data-ttu-id="8efd1-281">此特性类型通常应用于时间维度或服务器时间维度的键特性。</span><span class="sxs-lookup"><span data-stu-id="8efd1-281">This attribute type is typically applied to the key attribute of a time dimension or server time dimension.</span></span>|  
|`DayOfHalfYear`|<span data-ttu-id="8efd1-282">表示每半年的第几天。</span><span class="sxs-lookup"><span data-stu-id="8efd1-282">Represents the day ordinal of a half-year.</span></span>|  
|`DayOfMonth`|<span data-ttu-id="8efd1-283">表示每月的第几天。</span><span class="sxs-lookup"><span data-stu-id="8efd1-283">Represents the day ordinal of a month.</span></span>|  
|`DayOfQuarter`|<span data-ttu-id="8efd1-284">表示每个季度的第几天。</span><span class="sxs-lookup"><span data-stu-id="8efd1-284">Represents the day ordinal of a quarter.</span></span>|  
|`DayOfTenDays`|<span data-ttu-id="8efd1-285">表示每十天的第几天。</span><span class="sxs-lookup"><span data-stu-id="8efd1-285">Represents the day ordinal of a ten-day period.</span></span>|  
|`DayOfTrimester`|<span data-ttu-id="8efd1-286">表示每四个月的第几天。</span><span class="sxs-lookup"><span data-stu-id="8efd1-286">Represents the day ordinal of a trimester.</span></span>|  
|`DayOfWeek`|<span data-ttu-id="8efd1-287">表示每周的第几天。</span><span class="sxs-lookup"><span data-stu-id="8efd1-287">Represents the day ordinal of a week.</span></span>|  
|`DayOfYear`|<span data-ttu-id="8efd1-288">表示每年的第几天。</span><span class="sxs-lookup"><span data-stu-id="8efd1-288">Represents the day ordinal of a year.</span></span>|  
|`Days`|<span data-ttu-id="8efd1-289">表示天数。</span><span class="sxs-lookup"><span data-stu-id="8efd1-289">Represents days.</span></span>|  
|`FiscalDate`|<span data-ttu-id="8efd1-290">表示会计日历中的日期。</span><span class="sxs-lookup"><span data-stu-id="8efd1-290">Represents a date in a fiscal calendar.</span></span>|  
|`FiscalDayOfHalfYear`|<span data-ttu-id="8efd1-291">表示会计日历中半年的第几天。</span><span class="sxs-lookup"><span data-stu-id="8efd1-291">Represents the day ordinal of a half-year in a fiscal calendar.</span></span>|  
|`FiscalDayOfMonth`|<span data-ttu-id="8efd1-292">表示会计日历中每月的第几天。</span><span class="sxs-lookup"><span data-stu-id="8efd1-292">Represents the day ordinal of a month in a fiscal calendar.</span></span>|  
|`FiscalDayOfQuarter`|<span data-ttu-id="8efd1-293">表示会计日历中每个季度的第几天。</span><span class="sxs-lookup"><span data-stu-id="8efd1-293">Represents the day ordinal of a quarter in a fiscal calendar.</span></span>|  
|`FiscalDayOfTrimester`|<span data-ttu-id="8efd1-294">表示会计日历中每四个月的第几天。</span><span class="sxs-lookup"><span data-stu-id="8efd1-294">Represents the day ordinal of a trimester in a fiscal calendar.</span></span>|  
|`FiscalDayOfWeek`|<span data-ttu-id="8efd1-295">表示会计日历中每周的第几天。</span><span class="sxs-lookup"><span data-stu-id="8efd1-295">Represents the day ordinal of a week in a fiscal calendar.</span></span>|  
|`FiscalDayOfYear`|<span data-ttu-id="8efd1-296">表示会计日历中每年的第几天。</span><span class="sxs-lookup"><span data-stu-id="8efd1-296">Represents the day ordinal of a year in a fiscal calendar.</span></span>|  
|`FiscalHalfYears`|<span data-ttu-id="8efd1-297">表示会计日历中的半年数。</span><span class="sxs-lookup"><span data-stu-id="8efd1-297">Represents half-years in a fiscal calendar.</span></span>|  
|`FiscalHalfYearOfYear`|<span data-ttu-id="8efd1-298">表示会计日历中每年的第几个半年。</span><span class="sxs-lookup"><span data-stu-id="8efd1-298">Represents the half-year ordinal of a year in a fiscal calendar.</span></span>|  
|`FiscalMonths`|<span data-ttu-id="8efd1-299">表示会计日历中的月数。</span><span class="sxs-lookup"><span data-stu-id="8efd1-299">Represents months in a fiscal calendar.</span></span>|  
|`FiscalMonthOfHalfYear`|<span data-ttu-id="8efd1-300">表示会计日历中每半年的第几个月。</span><span class="sxs-lookup"><span data-stu-id="8efd1-300">Represents the month ordinal of a half-year in a fiscal calendar.</span></span>|  
|`FiscalMonthOfQuarter`|<span data-ttu-id="8efd1-301">表示会计日历中每个季度的第几个月。</span><span class="sxs-lookup"><span data-stu-id="8efd1-301">Represents the month ordinal of a quarter in a fiscal calendar.</span></span>|  
|`FiscalMonthOfTrimester`|<span data-ttu-id="8efd1-302">表示会计日历中每四个月的第几个月。</span><span class="sxs-lookup"><span data-stu-id="8efd1-302">Represents the month ordinal of a trimester in a fiscal calendar.</span></span>|  
|`FiscalMonthOfYear`|<span data-ttu-id="8efd1-303">表示会计日历中每一年的第几个月。</span><span class="sxs-lookup"><span data-stu-id="8efd1-303">Represents the month ordinal of a year in a fiscal calendar.</span></span>|  
|`FiscalQuarters`|<span data-ttu-id="8efd1-304">表示会计日历中的季度数。</span><span class="sxs-lookup"><span data-stu-id="8efd1-304">Represents quarters in a fiscal calendar.</span></span>|  
|`FiscalQuarterOfHalfYear`|<span data-ttu-id="8efd1-305">表示会计日历中每半年的第几个季度。</span><span class="sxs-lookup"><span data-stu-id="8efd1-305">Represents the quarter ordinal of a half-year in a fiscal calendar.</span></span>|  
|`FiscalQuarterOfYear`|<span data-ttu-id="8efd1-306">表示会计日历中每年的第几个季度。</span><span class="sxs-lookup"><span data-stu-id="8efd1-306">Represents the quarter ordinal of a year in a fiscal calendar.</span></span>|  
|`FiscalTrimesters`|<span data-ttu-id="8efd1-307">表示会计日历中的四个月。</span><span class="sxs-lookup"><span data-stu-id="8efd1-307">Represents trimesters in a fiscal calendar.</span></span>|  
|`FiscalTrimesterOfYear`|<span data-ttu-id="8efd1-308">表示会计日历中每一年的第几个四个月。</span><span class="sxs-lookup"><span data-stu-id="8efd1-308">Represents the trimester ordinal of a year in a fiscal calendar.</span></span>|  
|`FiscalWeeks`|<span data-ttu-id="8efd1-309">表示会计日历中的周数。</span><span class="sxs-lookup"><span data-stu-id="8efd1-309">Represents weeks in a fiscal calendar.</span></span>|  
|`FiscalWeekOfHalfYear`|<span data-ttu-id="8efd1-310">表示会计日历中每半年的第几周。</span><span class="sxs-lookup"><span data-stu-id="8efd1-310">Represents the week ordinal of a half-year in a fiscal calendar.</span></span>|  
|`FiscalWeekOfMonth`|<span data-ttu-id="8efd1-311">表示会计日历中每月的第几周。</span><span class="sxs-lookup"><span data-stu-id="8efd1-311">Represents the week ordinal of a month in a fiscal calendar.</span></span>|  
|`FiscalWeekOfQuarter`|<span data-ttu-id="8efd1-312">表示会计日历中每个季度的第几周。</span><span class="sxs-lookup"><span data-stu-id="8efd1-312">Represents the week ordinal of a quarter in a fiscal calendar.</span></span>|  
|`FiscalWeekOfTrimester`|<span data-ttu-id="8efd1-313">表示会计日历中每四个月的第几周。</span><span class="sxs-lookup"><span data-stu-id="8efd1-313">Represents the week ordinal of a trimester in a fiscal calendar.</span></span>|  
|`FiscalWeekOfYear`|<span data-ttu-id="8efd1-314">表示会计日历中每年的第几周。</span><span class="sxs-lookup"><span data-stu-id="8efd1-314">Represents the week ordinal of a year in a fiscal calendar.</span></span>|  
|`FiscalYears`|<span data-ttu-id="8efd1-315">表示会计日历中的年数。</span><span class="sxs-lookup"><span data-stu-id="8efd1-315">Represents years in a fiscal calendar.</span></span>|  
|`HalfYears`|<span data-ttu-id="8efd1-316">表示半年。</span><span class="sxs-lookup"><span data-stu-id="8efd1-316">Represents half-years.</span></span>|  
|`HalfYearOfYear`|<span data-ttu-id="8efd1-317">表示每年的第几个半年。</span><span class="sxs-lookup"><span data-stu-id="8efd1-317">Represents the half-year ordinal of a year.</span></span>|  
|`Hours`|<span data-ttu-id="8efd1-318">表示小时。</span><span class="sxs-lookup"><span data-stu-id="8efd1-318">Represents hours.</span></span>|  
|`IsHoliday`|<span data-ttu-id="8efd1-319">指示某天是否为假日。</span><span class="sxs-lookup"><span data-stu-id="8efd1-319">Indicates whether a date is a holiday.</span></span>|  
|`ISO8601Date`|<span data-ttu-id="8efd1-320">表示 ISO 8601 日历中的日期。</span><span class="sxs-lookup"><span data-stu-id="8efd1-320">Represents a date in an ISO 8601 calendar.</span></span>|  
|`ISO8601DayOfWeek`|<span data-ttu-id="8efd1-321">表示 ISO 8601 日历中每周的第几天。</span><span class="sxs-lookup"><span data-stu-id="8efd1-321">Represents the day ordinal of a week in an ISO 8601 calendar.</span></span>|  
|`ISO8601DayOfYear`|<span data-ttu-id="8efd1-322">表示 ISO 8601 日历中每年的第几天。</span><span class="sxs-lookup"><span data-stu-id="8efd1-322">Represents the day ordinal of a year in an ISO 8601 calendar.</span></span>|  
|`ISO8601Weeks`|<span data-ttu-id="8efd1-323">表示 ISO 8601 日历中的周。</span><span class="sxs-lookup"><span data-stu-id="8efd1-323">Represents weeks in an ISO 8601 calendar.</span></span>|  
|`ISO8601WeekOfYear`|<span data-ttu-id="8efd1-324">表示 ISO 8601 日历中每年的第几周。</span><span class="sxs-lookup"><span data-stu-id="8efd1-324">Represents the week ordinal of a year in an ISO 8601 calendar.</span></span>|  
|`ISO8601Years`|<span data-ttu-id="8efd1-325">表示 ISO 8601 日历中的年。</span><span class="sxs-lookup"><span data-stu-id="8efd1-325">Represents years in an ISO 8601 calendar.</span></span>|  
|`IsPeakDay`|<span data-ttu-id="8efd1-326">指示日期是否是高峰日。</span><span class="sxs-lookup"><span data-stu-id="8efd1-326">Indicates whether a date is a peak day.</span></span>|  
|`IsWeekDay`|<span data-ttu-id="8efd1-327">指示日期是否为周工作日。</span><span class="sxs-lookup"><span data-stu-id="8efd1-327">Indicates whether a date is a weekday.</span></span>|  
|`IsWorkingDay`|<span data-ttu-id="8efd1-328">指示日期是否为工作日。</span><span class="sxs-lookup"><span data-stu-id="8efd1-328">Indicates whether a date is a working day.</span></span>|  
|`ManufacturingDate`|<span data-ttu-id="8efd1-329">表示生产日历中的日期。</span><span class="sxs-lookup"><span data-stu-id="8efd1-329">Represents a date in a manufacturing calendar.</span></span>|  
|`ManufacturingDayOfHalfYear`|<span data-ttu-id="8efd1-330">表示生产日历中每半年的第几天。</span><span class="sxs-lookup"><span data-stu-id="8efd1-330">Represents the day ordinal of a half-year in a manufacturing calendar.</span></span>|  
|`ManufacturingDayOfMonth`|<span data-ttu-id="8efd1-331">表示生产日历中每个月的第几天。</span><span class="sxs-lookup"><span data-stu-id="8efd1-331">Represents the day ordinal of a month in a manufacturing calendar.</span></span>|  
|`ManufacturingDayOfQuarter`|<span data-ttu-id="8efd1-332">表示生产日历中每个季度的第几天。</span><span class="sxs-lookup"><span data-stu-id="8efd1-332">Represents the day ordinal of a quarter in a manufacturing calendar.</span></span>|  
|`ManufacturingDayOfTrimester`|<span data-ttu-id="8efd1-333">表示生产日历中每四个月的第几天。</span><span class="sxs-lookup"><span data-stu-id="8efd1-333">Represents the day ordinal of a trimester in a manufacturing calendar.</span></span>|  
|`ManufacturingDayOfWeek`|<span data-ttu-id="8efd1-334">表示生产日历中每一周的第几天。</span><span class="sxs-lookup"><span data-stu-id="8efd1-334">Represents the day ordinal of a week in a manufacturing calendar.</span></span>|  
|`ManufacturingDayOfYear`|<span data-ttu-id="8efd1-335">表示生产日历中每一年的第几天。</span><span class="sxs-lookup"><span data-stu-id="8efd1-335">Represents the day ordinal of a year in a manufacturing calendar.</span></span>|  
|`ManufacturingHalfYears`|<span data-ttu-id="8efd1-336">表示生产日历中的半年数。</span><span class="sxs-lookup"><span data-stu-id="8efd1-336">Represents half-years in a manufacturing calendar.</span></span>|  
|`ManufacturingHalfYearOfYear`|<span data-ttu-id="8efd1-337">表示生产日历中每一年的第几个半年。</span><span class="sxs-lookup"><span data-stu-id="8efd1-337">Represents the half-year ordinal of a year in a manufacturing calendar.</span></span>|  
|`ManufacturingMonths`|<span data-ttu-id="8efd1-338">表示生产日历中的月数。</span><span class="sxs-lookup"><span data-stu-id="8efd1-338">Represents months in a manufacturing calendar.</span></span>|  
|`ManufacturingMonthOfHalfYear`|<span data-ttu-id="8efd1-339">表示生产日历中每半年的第几个月。</span><span class="sxs-lookup"><span data-stu-id="8efd1-339">Represents the month ordinal of a half-year in a manufacturing calendar.</span></span>|  
|`ManufacturingMonthOfQuarter`|<span data-ttu-id="8efd1-340">表示生产日历中每个季度的第几个月。</span><span class="sxs-lookup"><span data-stu-id="8efd1-340">Represents the month ordinal of a quarter in a manufacturing calendar.</span></span>|  
|`ManufacturingMonthOfTrimester`|<span data-ttu-id="8efd1-341">表示生产日历中每四个月的第几个月。</span><span class="sxs-lookup"><span data-stu-id="8efd1-341">Represents the month ordinal of a trimester in a manufacturing calendar.</span></span>|  
|`ManufacturingMonthOfYear`|<span data-ttu-id="8efd1-342">表示生产日历中每一年的第几个月。</span><span class="sxs-lookup"><span data-stu-id="8efd1-342">Represents the month ordinal of a year in a manufacturing calendar.</span></span>|  
|`ManufacturingQuarters`|<span data-ttu-id="8efd1-343">表示生产日历中的季度数。</span><span class="sxs-lookup"><span data-stu-id="8efd1-343">Represents quarters in a manufacturing calendar.</span></span>|  
|`ManufacturingQuarterOfHalfYear`|<span data-ttu-id="8efd1-344">表示生产日历中每半年的第几个季度。</span><span class="sxs-lookup"><span data-stu-id="8efd1-344">Represents the quarter ordinal of a half-year in a manufacturing calendar.</span></span>|  
|`ManufacturingQuarterOfYear`|<span data-ttu-id="8efd1-345">表示生产日历中每一年的第几个季度。</span><span class="sxs-lookup"><span data-stu-id="8efd1-345">Represents the quarter ordinal of a year in a manufacturing calendar.</span></span>|  
|`ManufacturingWeeks`|<span data-ttu-id="8efd1-346">表示生产日历中的周数。</span><span class="sxs-lookup"><span data-stu-id="8efd1-346">Represents weeks in a manufacturing calendar.</span></span>|  
|`ManufacturingWeekOfHalfYear`|<span data-ttu-id="8efd1-347">表示生产日历中每半年的第几周。</span><span class="sxs-lookup"><span data-stu-id="8efd1-347">Represents the week ordinal of a half-year in a manufacturing calendar.</span></span>|  
|`ManufacturingWeekOfMonth`|<span data-ttu-id="8efd1-348">表示生产日历中每月的第几周。</span><span class="sxs-lookup"><span data-stu-id="8efd1-348">Represents the week ordinal of a month in a manufacturing calendar.</span></span>|  
|`ManufacturingWeekOfQuarter`|<span data-ttu-id="8efd1-349">表示生产日历中每个季度的第几周。</span><span class="sxs-lookup"><span data-stu-id="8efd1-349">Represents the week ordinal of a quarter in a manufacturing calendar.</span></span>|  
|`ManufacturingWeekOfTrimester`|<span data-ttu-id="8efd1-350">表示生产日历中每四个月的第几周。</span><span class="sxs-lookup"><span data-stu-id="8efd1-350">Represents the week ordinal of a trimester in a manufacturing calendar.</span></span>|  
|`ManufacturingWeekOfYear`|<span data-ttu-id="8efd1-351">表示生产日历中每年的第几周。</span><span class="sxs-lookup"><span data-stu-id="8efd1-351">Represents the week ordinal of a year in a manufacturing calendar.</span></span>|  
|`ManufacturingYears`|<span data-ttu-id="8efd1-352">表示生产日历中的年数。</span><span class="sxs-lookup"><span data-stu-id="8efd1-352">Represents years in a manufacturing calendar.</span></span>|  
|`Minutes`|<span data-ttu-id="8efd1-353">表示分钟数。</span><span class="sxs-lookup"><span data-stu-id="8efd1-353">Represents minutes.</span></span>|  
|`Months`|<span data-ttu-id="8efd1-354">表示月数。</span><span class="sxs-lookup"><span data-stu-id="8efd1-354">Represents months.</span></span>|  
|`MonthOfHalfYear`|<span data-ttu-id="8efd1-355">表示每半年的第几个月。</span><span class="sxs-lookup"><span data-stu-id="8efd1-355">Represents the month ordinal of a half-year.</span></span>|  
|`MonthOfQuarter`|<span data-ttu-id="8efd1-356">表示每个季度的第几个月。</span><span class="sxs-lookup"><span data-stu-id="8efd1-356">Represents the month ordinal of a quarter.</span></span>|  
|`MonthOfTrimester`|<span data-ttu-id="8efd1-357">表示每四个月的第几个月。</span><span class="sxs-lookup"><span data-stu-id="8efd1-357">Represents the month ordinal of a trimester.</span></span>|  
|`MonthOfYear`|<span data-ttu-id="8efd1-358">表示每一年的第几个月。</span><span class="sxs-lookup"><span data-stu-id="8efd1-358">Represents the month ordinal of a year.</span></span>|  
|`Quarters`|<span data-ttu-id="8efd1-359">表示季度数。</span><span class="sxs-lookup"><span data-stu-id="8efd1-359">Represents quarters.</span></span>|  
|`QuarterOfHalfYear`|<span data-ttu-id="8efd1-360">表示每半年的第几个季度。</span><span class="sxs-lookup"><span data-stu-id="8efd1-360">Represents the quarter ordinal of a half-year.</span></span>|  
|`QuarterOfYear`|<span data-ttu-id="8efd1-361">表示每一年的第几个季度。</span><span class="sxs-lookup"><span data-stu-id="8efd1-361">Represents the quarter ordinal of a year.</span></span>|  
|`ReportingDate`|<span data-ttu-id="8efd1-362">表示报表日历中的日期。</span><span class="sxs-lookup"><span data-stu-id="8efd1-362">Represents a date in a reporting calendar.</span></span>|  
|`ReportingDayOfHalfYear`|<span data-ttu-id="8efd1-363">表示报表日历中每半年的第几天。</span><span class="sxs-lookup"><span data-stu-id="8efd1-363">Represents the day ordinal of a half-year in a reporting calendar.</span></span>|  
|`ReportingDayOfMonth`|<span data-ttu-id="8efd1-364">表示报表日历中每个月的第几天。</span><span class="sxs-lookup"><span data-stu-id="8efd1-364">Represents the day ordinal of a month in a reporting calendar.</span></span>|  
|`ReportingDayOfQuarter`|<span data-ttu-id="8efd1-365">表示报表日历中每个季度的第几天。</span><span class="sxs-lookup"><span data-stu-id="8efd1-365">Represents the day ordinal of a quarter in a reporting calendar.</span></span>|  
|`ReportingDayOfTrimester`|<span data-ttu-id="8efd1-366">表示报表日历中每四个月的第几天。</span><span class="sxs-lookup"><span data-stu-id="8efd1-366">Represents the day ordinal of a trimester in a reporting calendar.</span></span>|  
|`ReportingDayOfWeek`|<span data-ttu-id="8efd1-367">表示报表日历中每一周的第几天。</span><span class="sxs-lookup"><span data-stu-id="8efd1-367">Represents the day ordinal of a week in a reporting calendar.</span></span>|  
|`ReportingDayOfYear`|<span data-ttu-id="8efd1-368">表示报表日历中每一年的第几天。</span><span class="sxs-lookup"><span data-stu-id="8efd1-368">Represents the day ordinal of a year in a reporting calendar.</span></span>|  
|`ReportingHalfYears`|<span data-ttu-id="8efd1-369">表示报表日历中的半年数。</span><span class="sxs-lookup"><span data-stu-id="8efd1-369">Represents half-years in a reporting calendar.</span></span>|  
|`ReportingHalfYearOfYear`|<span data-ttu-id="8efd1-370">表示报表日历中每一年的第几个半年。</span><span class="sxs-lookup"><span data-stu-id="8efd1-370">Represents the half-year ordinal of a year in a reporting calendar.</span></span>|  
|`ReportingMonths`|<span data-ttu-id="8efd1-371">表示报表日历中的月数。</span><span class="sxs-lookup"><span data-stu-id="8efd1-371">Represents months in a reporting calendar.</span></span>|  
|`ReportingMonthOfHalfYear`|<span data-ttu-id="8efd1-372">表示报表日历中每半年的第几个月。</span><span class="sxs-lookup"><span data-stu-id="8efd1-372">Represents the month ordinal of a half-year in a reporting calendar.</span></span>|  
|`ReportingMonthOfQuarter`|<span data-ttu-id="8efd1-373">表示报表日历中每个季度的第几个月。</span><span class="sxs-lookup"><span data-stu-id="8efd1-373">Represents the month ordinal of a quarter in a reporting calendar.</span></span>|  
|`ReportingMonthOfTrimester`|<span data-ttu-id="8efd1-374">表示报表日历中每四个月的第几个月。</span><span class="sxs-lookup"><span data-stu-id="8efd1-374">Represents the month ordinal of a trimester in a reporting calendar.</span></span>|  
|`ReportingMonthOfYear`|<span data-ttu-id="8efd1-375">表示报表日历中每一年的第几个月。</span><span class="sxs-lookup"><span data-stu-id="8efd1-375">Represents the month ordinal of a year in a reporting calendar.</span></span>|  
|`ReportingQuarters`|<span data-ttu-id="8efd1-376">表示报表日历中的季度数。</span><span class="sxs-lookup"><span data-stu-id="8efd1-376">Represents quarters in a reporting calendar.</span></span>|  
|`ReportingQuarterOfHalfYear`|<span data-ttu-id="8efd1-377">表示报表日历中每半年的第几个季度。</span><span class="sxs-lookup"><span data-stu-id="8efd1-377">Represents the quarter ordinal of a half-year in a reporting calendar.</span></span>|  
|`ReportingQuarterOfYear`|<span data-ttu-id="8efd1-378">表示报表日历中每一年的第几个季度。</span><span class="sxs-lookup"><span data-stu-id="8efd1-378">Represents the quarter ordinal of a year in a reporting calendar.</span></span>|  
|`ReportingTrimesters`|<span data-ttu-id="8efd1-379">表示报表日历中的每四个月。</span><span class="sxs-lookup"><span data-stu-id="8efd1-379">Represents trimesters in a reporting calendar.</span></span>|  
|`ReportingTrimesterOfYear`|<span data-ttu-id="8efd1-380">表示报表日历中每一年的第几个四个月。</span><span class="sxs-lookup"><span data-stu-id="8efd1-380">Represents the trimester ordinal of a year in a reporting calendar.</span></span>|  
|`ReportingWeeks`|<span data-ttu-id="8efd1-381">表示报表日历中的周数。</span><span class="sxs-lookup"><span data-stu-id="8efd1-381">Represents weeks in a reporting calendar.</span></span>|  
|`ReportingWeekOfHalfYear`|<span data-ttu-id="8efd1-382">表示报表日历中每半年的第几周。</span><span class="sxs-lookup"><span data-stu-id="8efd1-382">Represents the week ordinal of a half-year in a reporting calendar.</span></span>|  
|`ReportingWeekOfMonth`|<span data-ttu-id="8efd1-383">表示报表日历中每个月的第几周。</span><span class="sxs-lookup"><span data-stu-id="8efd1-383">Represents the week ordinal of a month in a reporting calendar.</span></span>|  
|`ReportingWeekOfQuarter`|<span data-ttu-id="8efd1-384">表示报表日历中每个季度的第几周。</span><span class="sxs-lookup"><span data-stu-id="8efd1-384">Represents the week ordinal of a quarter in a reporting calendar.</span></span>|  
|`ReportingWeekOfTrimester`|<span data-ttu-id="8efd1-385">表示报表日历中每四个月的第几周。</span><span class="sxs-lookup"><span data-stu-id="8efd1-385">Represents the week ordinal of a trimester in a reporting calendar.</span></span>|  
|`ReportingWeekOfYear`|<span data-ttu-id="8efd1-386">表示报表日历中每年的第几周。</span><span class="sxs-lookup"><span data-stu-id="8efd1-386">Represents the week ordinal of a year in a reporting calendar.</span></span>|  
|`ReportingYears`|<span data-ttu-id="8efd1-387">表示报表日历中的年。</span><span class="sxs-lookup"><span data-stu-id="8efd1-387">Represents years in a reporting calendar.</span></span>|  
|`Seconds`|<span data-ttu-id="8efd1-388">表示秒数。</span><span class="sxs-lookup"><span data-stu-id="8efd1-388">Represents seconds.</span></span>|  
|`TenDayOfHalfYear`|<span data-ttu-id="8efd1-389">表示每半年的第几个十天周期。</span><span class="sxs-lookup"><span data-stu-id="8efd1-389">Represents the ten-day period ordinal of a half-year.</span></span>|  
|`TenDayOfMonth`|<span data-ttu-id="8efd1-390">表示每个月的第几个十天周期。</span><span class="sxs-lookup"><span data-stu-id="8efd1-390">Represents the ten-day period ordinal of a month.</span></span>|  
|`TenDayOfQuarter`|<span data-ttu-id="8efd1-391">表示每个季度的第几个十天周期。</span><span class="sxs-lookup"><span data-stu-id="8efd1-391">Represents the ten-day period ordinal of a quarter.</span></span>|  
|`TenDayOfTrimester`|<span data-ttu-id="8efd1-392">表示每四个月的第几个十天周期。</span><span class="sxs-lookup"><span data-stu-id="8efd1-392">Represents the ten-day period ordinal of a trimester.</span></span>|  
|`TenDayOfYear`|<span data-ttu-id="8efd1-393">表示每一年的第几个十天周期。</span><span class="sxs-lookup"><span data-stu-id="8efd1-393">Represents the ten-day period ordinal of a year.</span></span>|  
|`TenDays`|<span data-ttu-id="8efd1-394">表示为期十天的周期数。</span><span class="sxs-lookup"><span data-stu-id="8efd1-394">Represents ten-day periods.</span></span>|  
|`Trimesters`|<span data-ttu-id="8efd1-395">表示每四个月数。</span><span class="sxs-lookup"><span data-stu-id="8efd1-395">Represents trimesters.</span></span>|  
|`TrimesterOfYear`|<span data-ttu-id="8efd1-396">表示每一年的第几个四个月。</span><span class="sxs-lookup"><span data-stu-id="8efd1-396">Represents the trimester ordinal of a year.</span></span>|  
|`UndefinedTime`|<span data-ttu-id="8efd1-397">表示未定义的时间段。</span><span class="sxs-lookup"><span data-stu-id="8efd1-397">Represents an undefined time period.</span></span>|  
|`WeekOfYear`|<span data-ttu-id="8efd1-398">表示每年的第几周。</span><span class="sxs-lookup"><span data-stu-id="8efd1-398">Represents the week ordinal of a year.</span></span>|  
|`Weeks`|<span data-ttu-id="8efd1-399">表示周数。</span><span class="sxs-lookup"><span data-stu-id="8efd1-399">Represents weeks.</span></span>|  
|<span data-ttu-id="8efd1-400">**WinterSummerSeason**</span><span class="sxs-lookup"><span data-stu-id="8efd1-400">**WinterSummerSeason**</span></span>|<span data-ttu-id="8efd1-401">指示日期是否属于冬季/夏季。</span><span class="sxs-lookup"><span data-stu-id="8efd1-401">Indicates whether the date is part of the winter/summer season.</span></span>|  
|`Years`|<span data-ttu-id="8efd1-402">表示年数。</span><span class="sxs-lookup"><span data-stu-id="8efd1-402">Represents years.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8efd1-403">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8efd1-403">See Also</span></span>  
 <span data-ttu-id="8efd1-404">[属性和属性层次结构](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md) </span><span class="sxs-lookup"><span data-stu-id="8efd1-404">[Attributes and Attribute Hierarchies](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md) </span></span>  
 [<span data-ttu-id="8efd1-405">维度特性属性参考</span><span class="sxs-lookup"><span data-stu-id="8efd1-405">Dimension Attribute Properties Reference</span></span>](dimension-attribute-properties-reference.md)  
  
  
