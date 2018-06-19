---
title: AppliesTo — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: 8fb1334b-d78c-405f-98b4-786e9f6b58d7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2e27ee1ab0ba42a82d61e2adbe9fb4c6c81cbb48
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31100263"
---
# <a name="appliesto-element-visual-studio-templates"></a>AppliesTo — Element (szablony Visual Studio)
Określa opcjonalne wyrażenie porównywania z jedną lub kilkoma funkcjami (zobacz <xref:Microsoft.VisualStudio.Shell.Interop.VsProjectCapabilityExpressionMatcher>). Możliwości są ujawniane przez typy projektu za pośrednictwem hierarchii jako właściwość <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID5>. W ten sposób szablon może być współużytkowany przez wiele typów projektów, które mają wspólne odnośne funkcje.  
  
 Ten element jest opcjonalny. Plik szablonu może zawierać maksymalnie jedno jego wystąpienie. Element umożliwia jedynie potwierdzenie zgodności szablonu elementu z funkcjami aktualnie zaznaczonego aktywnego projektu. Nie można za jego pomocą ustawić niezgodności szablonu. Jeśli `AppliesTo` jest nieobecny lub wyrażenie, które pomyślnie zgadzaj się, następnie `TemplateID` lub `TemplateGroupID` umożliwia szablon ma to zastosowanie, jak w poprzednich wersjach produktu.  
  
 Wprowadzona w programie Visual Studio 2013 Update 2. Aby odwołać poprawnej wersji, zobacz [odwołania do zestawów dostarczane w Visual Studio 2013 SDK Update 2](http://msdn.microsoft.com/en-us/42b65c3e-e42b-4c39-98c8-bea285f25ffb).  
  
 \<VSTemplate>  
 \<TemplateData >  
 \<Element AppliesTo >  
  
## <a name="syntax"></a>Składnia  
  
```  
<AppliesTo>Capability1</AppliesTo>   
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Nadawanie szablonowi kategorii.|  
  
## <a name="text-value"></a>Wartość tekstowa  
 Wartość tekstowa jest wymagana. Tekst określa funkcje projektu.  
  
 Prawidłową składnię wyrażeń definiuje się następująco:  
  
-   Wyrażenie możliwości, takie jak "(VisualC &#124; CSharp) + (MSTest &#124; NUnit)".  
  
-   "&#124;" Jest operatora OR.  
  
-   "&" I "+" znaki są oba operatory i.  
  
-   Znak „!” jest operatorem NIE.  
  
-   Nawiasy wymuszają kolejność pierwszeństwa w ocenie.  
  
-   Wyrażenie o wartości null lub puste jest interpretowane jako zgodność.  
  
-   Możliwości projektu może być dowolny znak z wyjątkiem następujących zarezerwowanych znaków: "" :;,+-*/\\! ~&#124;& %$@^()={} <> []? \t\b\n\r  
  
## <a name="example"></a>Przykład  
 W przykładzie poniżej widać trzy różne szablony. `Template1` ma zastosowanie do wszystkich typów projektów C# lub innego typu projektu, który obsługuje `WindowsAppContainer` możliwości. `Template2` ma zastosowanie do wszystkich projektów C# dowolnego rodzaju. `Template3` ma zastosowanie do projektów C#, które nie są `WindowsAppContainer` projektów.  
  
```xml  
<!--  Template 1 -->  
<?xml version="1.0" encoding="utf-8"?>  
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <AppliesTo>CSharp | WindowsAppContainer</AppliesTo>   
    </TemplateData>  
</VSTemplate>  
  
<!--  Template 2 -->  
<?xml version="1.0" encoding="utf-8"?>  
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <AppliesTo>CSharp</AppliesTo>   
    </TemplateData>  
</VSTemplate>  
  
<!--  Template 1 -->  
<?xml version="1.0" encoding="utf-8"?>  
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <AppliesTo>CSharp_Class + (!WindowsAppContainer)</AppliesTo>   
    </TemplateData>  
</VSTemplate>  
  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)