---
title: Umieść Element | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Include
helpviewer_keywords:
- Include element (VSCT XML schema)
- VSCT XML schema elements, Include
ms.assetid: c923dfe6-084a-4105-aec1-f0a3f8399c54
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9dd762d9232443230dae29e94efd78f2e67d66f7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42680089"
---
# <a name="include-element"></a>Include, element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [obejmują Element](https://docs.microsoft.com/visualstudio/extensibility/include-element).  
  
Include element Określa plik, który może znajdować się w podanym ścieżkę załączania dla wstawiania do bieżącego pliku.  Wszystkie symbole i typy zdefiniowane staną się częścią wynik.  
  
## <a name="syntax"></a>Składnia  
  
```csharp  
<Include href="stdidcmd.h" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|href|Wymagane. Ścieżka do pliku nagłówka:<br /><br /> href="stdidcmd.h"|  
|Warunek|Opcjonalna. Zobacz [atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|Brak.|Brak.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[CommandTable, element](../extensibility/commandtable-element.md)|Definiuje wszystkie elementy, które reprezentują poleceń — czyli elementy menu, menu, paski narzędzi i pola kombi — zapewniającej pakietu VSPackage IDE.|  
  
## <a name="example"></a>Przykład  
  
```  
<Include href="PackagePlacements.vsct"/>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

