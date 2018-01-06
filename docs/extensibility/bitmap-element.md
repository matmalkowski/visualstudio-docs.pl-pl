---
title: Mapy bitowej elementu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: eb265aabdb4feda05512e036cda19abc574e2fd4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="bitmap-element"></a>Element mapy bitowej
Definiuje mapy bitowej. Mapa bitowa została załadowana z zasobu lub z pliku.  
  
## <a name="syntax"></a>Składnia  
  
```  
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Identyfikator GUID|Wymagany. Identyfikator GUID identyfikator GUID/identyfikator polecenia.<br /><br /> Atrybut identyfikatora guid dla mapy bitowej nie jest skojarzony z dowolnym pakiet VSPackage lub innej grupie polecenia.  Powinna być unikatowa w definicji mapy bitowej, a nie powinna być używana do innych celów.|  
|resID|Identyfikator GUID/identyfikator identyfikator polecenia. Wymagany jest resID lub atrybut href.<br /><br /> Atrybut resID jest liczbą całkowitą identyfikator zasobu określa paska mapy bitowej, który ma być załadowany podczas scalania tabeli polecenia.  Podczas ładowania tabeli poleceń, określony przez identyfikator zasobu mapy bitowej zostaną załadowane z zasobów tego samego modułu.|  
|usedList|Wymagane, jeśli obecny jest atrybut resID. Wybiera dostępnych obrazów w paska mapy bitowej.|  
|href|Ścieżka do mapy bitowej. Wymagany jest resID lub atrybut href.<br /><br /> Ścieżka include jest wyszukiwany plik wskazany obraz, który jest osadzony w wynikowego pliku binarnego.  Podczas scalania tabeli polecenia obraz jest kopiowany i nie wyszukiwania dodatkowych zasobów obciążenia jest wymagane ani.  Jeśli nie ma atrybutu usedList, dostępne są wszystkie obrazy na pasku. **Uwaga:** obrazy mogą być dostarczane w jednym z kilku formatów obejmujących bmp, PNG i GIF.  Wcześniejszej wersji kompilatora nie obsługuje 32-bitowe bitmapy, których zastosowano dane alfa przezroczystości częściowej. Obejście dla tych wersji jest w formacie PNG.|  
|Warunek|Opcjonalny. Zobacz [atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Bitmaps, element](../extensibility/bitmaps-element.md)|Grupuje elementy mapy bitowej.|  
  
## <a name="example"></a>Przykład  
  
```  
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />  
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"  
  usedList="1, 2, 3, 4"/>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)