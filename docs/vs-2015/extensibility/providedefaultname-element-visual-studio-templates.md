---
title: Providedefaultname — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProvideDefaultName
helpviewer_keywords:
- ProvideDefaultName element [Visual Studio project templates]
ms.assetid: 7b0e7b20-fd6b-42e2-81d0-e5100cea0528
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0c97fdb245ba1ff066e19bcd32616649b47b9425
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42628482"
---
# <a name="providedefaultname-element-visual-studio-templates"></a>ProvideDefaultName — Element (szablony Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [providedefaultname — Element (szablony Visual Studio)](https://docs.microsoft.com/visualstudio/extensibility/providedefaultname-element-visual-studio-templates).  
  
Określa, czy [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] system projektu spowoduje wygenerowanie domyślna nazwa szablonu w **Dodaj nowy element** lub **nowy projekt** okno dialogowe.  
  
 \<VSTemplate>  
 \<TemplateData >  
 \<Providedefaultname — >  
  
## <a name="syntax"></a>Składnia  
  
```  
<ProvideDefaultName> true/false </ProvideDefaultName>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Klasyfikuje szablon i definiuje sposób wyświetlania albo **nowy projekt** lub **Dodaj nowy element** okno dialogowe.|  
  
## <a name="text-value"></a>Wartość tekstowa  
 Wartość tekstowa jest wymagana.  
  
 Tekst musi być albo `true` lub `false`, wskazującą, czy mają być Generowanie domyślna nazwa szablonu w **Dodaj nowy element** lub **nowy projekt** okno dialogowe.  
  
## <a name="remarks"></a>Uwagi  
 `ProvideDefaultName` element jest opcjonalny. Wartość domyślna to `true`.  
  
 Jeśli `ProvideDefaultName` element jest `false`, **nazwa** pola **Dodaj nowy element** i **nowy projekt** okna dialogowe zawierają wartość `<Enter_name>`.  
  
 Użyj [defaultname —](../extensibility/defaultname-element-visual-studio-templates.md) element, aby określić domyślną nazwę projektu lub elementu w **Dodaj nowy element** i **nowy projekt** okien dialogowych.  
  
## <a name="example"></a>Przykład  
 Poniższy kod ustawia przykład `ProvideDefaultName` elementu `false`.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <ProvideDefaultName>false</ProvideDefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)

