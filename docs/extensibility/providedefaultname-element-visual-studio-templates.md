---
title: "Providedefaultname — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/vstemplate/2005#ProvideDefaultName
helpviewer_keywords: ProvideDefaultName element [Visual Studio project templates]
ms.assetid: 7b0e7b20-fd6b-42e2-81d0-e5100cea0528
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 48dbc92687a813dcd2a99659b9c2a8cc26129c79
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="providedefaultname-element-visual-studio-templates"></a>ProvideDefaultName — Element (szablony Visual Studio)
Określa, czy [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektu system będzie generował domyślną nazwę szablonu w **Dodaj nowy element** lub **nowy projekt** okno dialogowe.  
  
 \<VSTemplate >  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Kategoryzuje szablonu i definiuje sposób wyświetlania albo **nowy projekt** lub **Dodaj nowy element** okno dialogowe.|  
  
## <a name="text-value"></a>Wartość tekstowa  
 Wartość tekstowa jest wymagana.  
  
 Tekst musi być równa albo `true` lub `false`, wskazującą, czy chcesz wygenerować domyślną nazwę szablonu w **Dodaj nowy element** lub **nowy projekt** okno dialogowe.  
  
## <a name="remarks"></a>Uwagi  
 `ProvideDefaultName`to opcjonalny element. Wartość domyślna to `true`.  
  
 Jeśli `ProvideDefaultName` jest element `false`, **nazwa** pola **Dodaj nowy element** i **nowy projekt** okien dialogowych zawierają wartość `<Enter_name>`.  
  
 Użyj [defaultname —](../extensibility/defaultname-element-visual-studio-templates.md) element, aby określić domyślną nazwę projektu lub elementu **Dodaj nowy element** i **nowy projekt** okien dialogowych.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przykładzie `ProvideDefaultName` elementu `false`.  
  
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