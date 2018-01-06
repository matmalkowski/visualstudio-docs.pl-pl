---
title: "Customparameters — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameters
helpviewer_keywords: CustomParameters element [Visual Studio project templates]
ms.assetid: cf3efc91-1532-4022-bbb8-a18658424fee
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1b5fa3543113641666977816fadec49a02bc912a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="customparameters-element-visual-studio-templates"></a>CustomParameters — Element (szablony Visual Studio)
Grupy niestandardowe parametry, które mają być przekazane do Kreatora szablonów, gdy Kreator sprawia, że parametr zamiany.  
  
## <a name="syntax"></a>Składnia  
  
```  
<CustomParameters>  
    <CustomParameter/>  
    <CustomParameter/>  
</CustomParameters>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|Element opcjonalny.<br /><br /> Zawiera nazwę niestandardowego parametru i wartości do użycia podczas tworzenia projektów lub elementów z szablonu. Może wynosić zero lub więcej `CustomParameter` elementów w `CustomParameters` elementu.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Określa zawartość szablonu.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie kilku parametry niestandardowe w szablonie. Podczas tworzenia projektów lub elementów z szablonu z następującymi parametrami niestandardowych wszystkie wystąpienia `$color1$` i `$color2$` w szablonie pliki zostaną zastąpione `Red` i `Blue`odpowiednio.  
  
```  
<CustomParameters>  
    <CustomParameter Name="$color1$" Value="Red"/>  
    <CustomParameter Name="$color2$" Value="Blue "/>  
</CustomParameters>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [CustomParameter — Element (szablony Visual Studio)](../extensibility/customparameter-element-visual-studio-templates.md)   
 [Parametry szablonu](../ide/template-parameters.md)   
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)