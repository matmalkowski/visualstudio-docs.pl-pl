---
title: Licencja — Element (VSIX Language Pack schemat) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 57dac3b7-0cdd-405c-9af5-30ed9ca45e53
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ecf1913878137d84346275beccb512027f74f8f3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42680623"
---
# <a name="license-element-vsix-language-pack-schema"></a>Element licencji (schemat VSIX Language Pack)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [licencji, Element (VSIX Language Pack schemat)](https://docs.microsoft.com/visualstudio/extensibility/license-element-vsix-language-pack-schema).  
  
Opcjonalna. Ścieżka zlokalizowaną wersję pliku licencji dla rozszerzenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
<License>FilePath\license.txt</License>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Brak||  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|Brak||  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Element pakietu językowego VSIX](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|Wymagane. Zawiera element główny pakietu językowego VSIX.|  
  
## <a name="text-value"></a>Wartość tekstowa  
 Ścieżka względna pliku zlokalizowanego licencji, które mają być wyświetlane.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `License` jest zdefiniowany element, a następnie tekst pliku licencji wyznaczonym jest wyświetlany podczas instalacji i użytkownik musi zaakceptować licencję, aby kontynuować.  
  
## <a name="element-information"></a>Informacje o elementach  
  
|||  
|-|-|  
|Przestrzeń nazw|http://schemas.microsoft.com/developer/vsx-schema-lp/2010|  
|Nazwa schematu|VSIX Language Pack schematu|  
|Plik walidacji|VSIXLanguagePackSchema.xsd|  
|Może być pusta|Nie dotyczy|  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu VSX Language Pack](../extensibility/vsx-language-pack-schema-reference.md)   
 [Lokalizowanie pakietów VSIX](../extensibility/localizing-vsix-packages.md)   
 [Odwołanie do schematu 1.0 rozszerzenia VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)

