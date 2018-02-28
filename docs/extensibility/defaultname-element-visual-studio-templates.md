---
title: "Defaultname — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#DefaultName
helpviewer_keywords:
- DefaultName element [Visual Studio project templates]
ms.assetid: 0ff056c8-b9d2-4747-9308-92adf1811491
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 6a20bd878e9c6f85e03ff0738ed2a92d274f6232
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="defaultname-element-visual-studio-templates"></a>DefaultName — Element (szablony Visual Studio)
Określa nazwę, która spowoduje wygenerowanie system projektu programu Visual Studio dla projektów lub elementów, podczas jego tworzenia.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<Defaultname — >  
  
## <a name="syntax"></a>Składnia  
  
```  
<DefaultName>  
    Default Project Name  
</DefaultName>  
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
  
 Ten tekst Określa domyślną nazwę projektu lub elementu.  
  
## <a name="remarks"></a>Uwagi  
 `DefaultName`to opcjonalny element.  
  
 W przypadku projektów ten element Określa nazwę katalogu, który przechowuje projektu na dysku. Dla elementów Określa nazwę pliku źródłowego.  
  
 Podczas tworzenia projektu lub elementu, można modyfikować przy użyciu nazwy domyślnej **nazwa** opcja, która jest dostępna z poziomu **nowy projekt** okno dialogowe lub **Dodaj nowy element** okno dialogowe.  
  
 Jeśli nie chcesz, aby system projektu, aby wygenerować domyślną nazwę dla projektu lub elementu, to wartość [providedefaultname —](../extensibility/providedefaultname-element-visual-studio-templates.md) elementu `False`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia metadane szablonu elementu standardowe dla [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] klasy.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <DefaultName>MyClass.cs</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem ReplaceParameters="true">MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)