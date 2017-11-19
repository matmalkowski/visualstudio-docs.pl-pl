---
title: Atrybuty warunkowe schematu VSCT XML | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b0a434800fef7029460854107e79f29a71c75285
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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
 [Tabela polecenia programu Visual Studio (. Pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)