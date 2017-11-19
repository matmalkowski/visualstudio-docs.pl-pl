---
title: RequiredPlatformVersion, Element (szablony Visual Studio) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8f7eb4ada8378ff9009987f56341a65670a3c412
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>RequiredPlatformVersion, element (szablony Visual Studio)
Określa minimalną wersję systemu operacyjnego, który szablon projektu wymaga, aby działać poprawnie. Ten element służy do szablonów projektu, które utworzyć [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikacji.  
  
 `RequiredPlatformVersion` Wartość jest porównywana bezpośrednio z wersją systemu operacyjnego. Jeśli `RequiredPlatformVersion` jest wyższa niż wersja systemu operacyjnego nie ma szablonu **nowy projekt** okno dialogowe. Aby określić szablon dla [!INCLUDE[win8](../debugger/includes/win8_md.md)] lub nowszej, ustaw `RequiredPlatformVersion` do 6.2.0. Aby określić szablon dla [!INCLUDE[win81](../debugger/includes/win81_md.md)] lub nowszej, ustaw RequiredPlatformVersion do 6.3.0.  
  
 Szablony, które określają `RequiredPlatformVersion`= 8 są zgodne z poprzedniego odbiorcy [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] szablonów.  
  
 VSTemplate  
TemplateData  
..... TargetPlatformName  
RequiredPlatformVersion  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<RequiredPlatformVersion> OperatingSystem </RequiredPlatformVersion>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 Brak.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[TemplatePlatformName](../extensibility/templatedata-element-visual-studio-templates.md)|Określa platformę, które obiekty docelowe szablonu projektu.|  
  
## <a name="text-value"></a>Wartość tekstowa  
 Wartość tekstowa jest wymagana.  
  
## <a name="remarks"></a>Uwagi  
 Ten tekst Określa minimalnej wersji systemu operacyjnego wymagane przez szablon.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie określa, że elementy docelowe projektu szablonu [!INCLUDE[win8](../debugger/includes/win8_md.md)] lub nowszym.  
  
```xml  
<VSTemplate Type="Project" Version="3.0.0"    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <TargetPlatformName>Windows</TargetPlatformName>  
            <RequiredPlatformVersion>6.3.0</RequiredPlatformVersion>  
  
    </TemplateData>  
    <TemplateContent>  
  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [TargetPlatformName, Element (szablony Visual Studio)](../extensibility/targetplatformname-element-visual-studio-templates.md)   
 [Tworzenie szablony projektów i elementów](../ide/creating-project-and-item-templates.md)   
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)