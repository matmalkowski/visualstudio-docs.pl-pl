---
title: TargetPlatformName, Element (szablony Visual Studio) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a6b1f45-b5d6-418e-add1-87ee8f15033d
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 10aa5bca7a71294c7dbe297e9e4befb5da485bb7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="targetplatformname-element-visual-studio-templates"></a>TargetPlatformName, element (szablony Visual Studio)
Określa platformę, które obiekty docelowe szablonu projektu. Ten element jest używany do określenia, że szablon projektu jest używany do tworzenia [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<VSTemplate>  
    <TemplateData>   
        <TargetPlatformName> OperatingSystem</TargetPlatformName>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[RequiredPlatformVersion](../extensibility/requiredplatformversion-element-visual-studio-templates.md)|Określa wersję system operacyjny który elementy docelowe projektu szablonu.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Kategoryzuje szablonu i definiuje sposób wyświetlania albo **nowy projekt** lub **Dodaj nowy element** okno dialogowe.|  
  
## <a name="text-value"></a>Wartość tekstowa  
 Wartość tekstowa jest wymagana.  
  
## <a name="remarks"></a>Uwagi  
 Tekst musi być **Windows**.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie określa, że elementy docelowe projektu szablonu [!INCLUDE[win8](../debugger/includes/win8_md.md)] lub nowszym.  
  
```xml  
<VSTemplate Type="Project" Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">   
    <TemplateData>   
        <TargetPlatformName>Windows</TargetPlatformName>   
        <RequiredPlatformVersion>8</RequiredPlatformVersion>   
    </TemplateData>   
    <TemplateContent> </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie szablony projektów i elementów](../ide/creating-project-and-item-templates.md)   
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)