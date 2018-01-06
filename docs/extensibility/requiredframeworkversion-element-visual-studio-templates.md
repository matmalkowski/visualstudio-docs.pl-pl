---
title: "RequiredFrameworkVersion — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <RequiredFrameworkVersion> (Visual Studio Templates)
- RequiredFrameworkVersion (Visual Studio Templates)
ms.assetid: 08a4f609-51a5-4723-b89f-99277fb18871
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1583f5a0fab15c65d70819eb1b6e76cac5660ea5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="requiredframeworkversion-element-visual-studio-templates"></a>RequiredFrameworkVersion — Element (szablony Visual Studio)
Określa minimalną wersję .NET Framework, która jest wymagana przez szablon. Hierarchia schematu.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<RequiredFrameworkVersion >  
  
## <a name="syntax"></a>Składnia  
  
```  
<RequiredFrameworkVersion> .... </RequiredFrameworkVersion>  
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
  
 Tekst musi być minimalna liczba wersji programu .NET Framework, która jest wymagana dla szablonu.  
  
## <a name="remarks"></a>Uwagi  
 `RequiredFrameworkVersion`to opcjonalny element. Użyj tego elementu, jeśli szablon obsługuje tylko określonych minimalnej wersji i nowszymi wersjami, jeśli występują programu .NET Framework.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Tworzenie szablony projektów i elementów](../ide/creating-project-and-item-templates.md)   
 [Określanie konkretnej wersji programu .NET Framework jako docelowej](../ide/targeting-a-specific-dotnet-framework-version.md)