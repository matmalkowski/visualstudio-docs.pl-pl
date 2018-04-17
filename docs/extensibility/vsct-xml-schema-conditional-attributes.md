---
title: Atrybuty warunkowe schematu VSCT XML | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 975ca2f5fa6f070baf07b26cbfa0d8c3aa3b67d2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="vsct-xml-schema-conditional-attributes"></a>Atrybuty warunkowe schematu VSCT XML
Atrybuty warunkowe może być stosowany do wszystkich list i elementów. Operatory logiczne i wyrażenia rozszerzenia symbol zwrócić wartość true lub false. Jeśli PRAWDA, skojarzone lista lub element znajduje się w dane wyjściowe.  
  
 Rozszerzenia tokenu można przetestować przed inne rozszerzenia tokenu lub stałymi. Funkcja Defined() służy do sprawdzenia, czy została zdefiniowana konkretnej nazwy, nawet jeśli go nie ma wartości.  
  
 Kiedy atrybut Condition jest stosowany do listy, warunek jest stosowany do każdego elementu podrzędnego, na liście. Jeśli elementu podrzędnego samego zawiera atrybut Condition, jego stan jest połączone w za pomocą wyrażenia nadrzędnego przez operację i.  
  
 Wartości 1, '1' i 'true' są traktowane jako wartość true, a 0, "0" i "false" są traktowane jako wartość false.  
  
## <a name="operators"></a>Operatory  
 Następujące operatory może służyć do oceny wyrażenia warunkowego.  
  
|Operator|Definicja|  
|--------------|----------------|  
|(,)|Grupowanie|  
|!|Logiczne NOT|  
|\<, >, \<=, >=, ==, !=|Relacyjne i porównania|  
|and|Boolean|  
|lub|Boolean|  
  
## <a name="examples"></a>Przykłady  
  
```  
<Menu Condition="Defined(DEBUG)" ...  
</Menu>  
  
<Menu Condition="%(SKU_MODE) = 'Demo'" ...  
</Menu>  
  
<Menus Condition="Defined(DEBUG)">  
    <Menu ...  
    </Menu>  
</Menus>  
  
<Menus Condition="Defined(DEMO_SKU)">  
    <Menus Condition="!Defined(DEBUG)">  
        <Menu ...  
        </Menu>  
    </Menus>  
  
    <Menu ...  
    </Menu>  
</Menus>  
  
<Menus Condition="(Defined(DEMO_SKU) or Defined(SAMPLE_SKU))   
and !Defined(DEBUG)">  
    <Menu ...  
    </Menu>  
</Menus>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)