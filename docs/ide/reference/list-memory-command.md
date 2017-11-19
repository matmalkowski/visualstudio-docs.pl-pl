---
title: "Lista pamięci — polecenie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: debug.listmemory
helpviewer_keywords:
- Debug.ListMemory command
- ListMemory command
- list memory command
ms.assetid: a84de361-a6a6-4f6d-96aa-a0d4a424371e
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ae04c23a986107125edc9be149d6317a05c5b58a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="list-memory-command"></a>Lista pamięci — Polecenie
Wyświetla zawartość z pamięci podanego zakresu.  
  
## <a name="syntax"></a>Składnia  
  
```  
Debug.ListMemory [/ANSI|Unicode] [/Count:number] [/Format:formattype]  
[/Hex|Signed|Unsigned] [expression]  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Opcjonalny. Adres pamięci, z którego ma zostać rozpoczęta wyświetlanie pamięci.  
  
## <a name="switches"></a>Przełączniki  
 / ANSI &#124; Unicode  
 Opcjonalny. Wyświetl pamięć jako znaków odpowiadającej liczbę bajtów pamięci, ANSI lub Unicode.  
  
 / Liczba:`number`  
 Opcjonalny. Określa liczbę bajtów pamięci, aby wyświetlić, zaczynając od `expression`.  
  
 / Format:`formattype`  
 Opcjonalny. Format typu podczas wyświetlania informacji w pamięci w **pamięci** okna; może być OneByte, TwoBytes, FourBytes, EightBytes, Float (32-bitowe) lub dwukrotnie (64-bitowe). Użycie OneByte `/Unicode` jest niedostępny.  
  
 /Hex &#124; Podpisana &#124; Bez znaku  
 Opcjonalny. Określa format wyświetlania liczb: jak podpisem, bez znaku lub szesnastkową.  
  
## <a name="remarks"></a>Uwagi  
 Zamiast zapisywania pełnego **Debug.listmemory —** polecenie z wszystkich przełączników, można wywołać polecenia przy użyciu wstępnie zdefiniowane aliasy z przełącznikami, niektórych ustawień do określonej wartości. Na przykład zamiast wprowadzania:  
  
```  
>Debug.ListMemory /Format:float /Count:30 /Unicode  
```  
  
 Można napisać:  
  
```  
>df /Count:30 /Unicode  
```  
  
 Poniżej przedstawiono listę dostępnych aliasów dla **Debug.listmemory —** polecenia:  
  
|Alias|Polecenia i przełączniki|  
|-----------|--------------------------|  
|**d**|Debug.listmemory —|  
|**da**|Debug.listmemory — /Ansi|  
|**bazy danych**|Debug.listmemory — /Format:OneByte|  
|**Kontroler domeny**|Debug.listmemory — /Format:FourBytes /Ansi|  
|**dd**|Debug.listmemory — /Format:FourBytes|  
|**DF**|Debug.listmemory — /Format:Float|  
|**dq —**|Debug.listmemory — /Format:EightBytes|  
|**du**|Debug.listmemory — /Unicode|  
  
## <a name="example"></a>Przykład  
  
```  
>Debug.ListMemory /Format:float /Count:30 /Unicode  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Lista stosu wywołań — polecenie](../../ide/reference/list-call-stack-command.md)   
 [Lista wątków — polecenie](../../ide/reference/list-threads-command.md)   
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Find/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)