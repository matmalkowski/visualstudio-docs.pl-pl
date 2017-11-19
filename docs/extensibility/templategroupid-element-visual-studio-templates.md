---
title: "TemplateGroupID — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/vstemplate/2005#TemplateGroupID
helpviewer_keywords:
- TemplateGroupID element [Visual Studio Templates]
- <TemplateGroupID> element [Visual Studio Templates]
ms.assetid: bce7b49a-90bc-4691-aff3-a87e209f6d83
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e8f68b3a64fab519e31876d120f223961c10fffc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="templategroupid-element-visual-studio-templates"></a>TemplateGroupID — Element (szablony Visual Studio)
Określa, jaki rodzaj projektu szablonów elementów będą widoczne w. Ten element jest istotne, kiedy [ShowByDefault (szablony Visual Studio)](../extensibility/showbydefault-visual-studio-templates.md) ma ustawioną wartość `false`. Gdy [ShowByDefault (szablony Visual Studio)](../extensibility/showbydefault-visual-studio-templates.md) ma ustawioną wartość `true`, szablon elementu jest dostępna we wszystkich typach projektu.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<TemplateGroupID >  
  
## <a name="syntax"></a>Składnia  
  
```  
<TemplateGroupID> ... </TemplateGroupID>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Kategoryzuje szablonu i definiuje sposób wyświetlania albo **nowy projekt** lub **Dodaj nowy element** okno dialogowe.|  
  
## <a name="text-value"></a>Wartość tekstowa  
 Wartość tekstowa jest wymagana.  
  
 Tekst Określa identyfikator kategorii szablonów elementów.  
  
## <a name="remarks"></a>Uwagi  
 `TemplateGroupID`jest elementem.  
  
 Wartość `TemplateGroupID` element jest używany wraz z rejestracji systemu projektu (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<numer wersji >*\Projects\\) Szablony filtru, które pojawiają się w **Dodaj nowy element** okno dialogowe.  
  
|Visual C++ wartość|Znaczenie|  
|------------------------|-------------|  
|VC natywne|Używany dla projektów natywnych. Również domyślny, jeśli nie można określić typu projektu.|  
|Zarządzane VC|Używany do zarządzanego (/ clr) projektów|  
|VC Windows|Używane dla wszystkich projektów przeznaczonych dla platformy systemu windows (macierzysty/managed/magazyn)|  
|WinRT-Native-UAP|Używane w przypadku projektów Sklepu Windows 10|  
|CodeSharing natywne|Używane w przypadku projektów elementu Shared|  
|WinRT-Native-6.3|Używane w przypadku projektów Sklepu Windows 8.1|  
|WinRT-Native-Phone-6.3|Używane w przypadku projektów Windows Phone 8.1|  
|Natywne WinRT|Używane w przypadku projektów Sklepu Windows 8.0|  
|VC Android|Używane w przypadku projektów dla systemu Android|  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Tworzenie szablony projektów i elementów](../ide/creating-project-and-item-templates.md)