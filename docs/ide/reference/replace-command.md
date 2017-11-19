---
title: "Zastąp — polecenie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: edit.replace
helpviewer_keywords:
- Edit.Replace command
- Replace command
ms.assetid: a15767f1-5a3d-44f5-8c77-7b0f1157f340
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7201086ade629dc7c6d39039c088333be815cc26
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="replace-command"></a>Zastąp — Polecenie
Zamienia tekst w plikach za pomocą podzbiór opcje dostępne na **Zastąp w plikach** karcie **Znajdź i Zamień** okna.  
  
## <a name="syntax"></a>Składnia  
  
```  
Edit.Replace findwhat replacewith [/all] [/case]  
[/doc|/proc|/open|/sel] [/hidden] [/options] [/reset] [/up]  
[/wild|/regex] [/word]  
```  
  
## <a name="arguments"></a>Argumenty  
 `findwhat`  
 Wymagany. Tekst do dopasowania.  
  
 `replacewith`  
 Wymagany. Tekst do zastąpienia dla dopasowanego tekstu.  
  
## <a name="switches"></a>Przełączniki  
 / all lub /a  
 Opcjonalny. Zamienia wszystkie wystąpienia tekstu wyszukiwania tekst zastępczy.  
  
 /Case lub /c  
 Opcjonalny. Dopasowań występuje tylko wtedy, gdy po wielkich i małych liter dokładnie odpowiadać określone w `findwhat` argumentu.  
  
 / doc lub /d  
 Opcjonalny. Wyszukuje tylko bieżącego dokumentu. Określ tylko jeden zakres wyszukiwania dostępnych `/doc`, `/proc`, `/open`, lub `/sel`.  
  
 / hidden lub /h  
 Opcjonalny. Wyszukiwanie tekstu ukryte i zwinięte, takich jak metadanych formant czasu projektowania, ukryty obszar konspektu dokumentu lub zwinięte klasy lub metody.  
  
 / Open lub /o  
 Opcjonalny. Przeszukuje wszystkie otwarte dokumenty, tak jakby były to jeden dokument. Określ tylko jeden zakres wyszukiwania dostępnych `/doc`, `/proc`, `/open`, lub `/sel`.  
  
 / Options lub /t  
 Opcjonalny. Wyświetla listę bieżące ustawienia opcji wyszukiwania, a nie przeprowadza wyszukiwanie.  
  
 /proc lub /p  
 Opcjonalny. Wyszukuje bieżącą procedurę. Określ tylko jeden zakres wyszukiwania dostępnych `/doc`, `/proc`, `/open`, lub `/sel`.  
  
 /regex lub /r  
 Opcjonalny. Używa wstępnie zdefiniowane znaki specjalne w `findwhat` argument jako notacji reprezentujących wzorce tekstu, a nie literał znaków. Pełną listę znaków wyrażenia regularnego, zobacz [wyrażeń regularnych](../../ide/using-regular-expressions-in-visual-studio.md).  
  
 / Reset lub/e  
 Opcjonalny. Zwraca opcje Znajdź do ustawień domyślnych i nie wykonuje wyszukiwanie.  
  
 /SEL lub/s  
 Opcjonalny. Wyszukuje tylko bieżące zaznaczenie. Określ tylko jeden zakres wyszukiwania dostępnych `/doc`, `/proc`, `/open`, lub `/sel`.  
  
 /Up lub /u  
 Opcjonalny. Wyszukiwanie z bieżącej lokalizacji w pliku w kierunku do góry pliku. Domyślnie wyszukiwanie rozpoczyna się w bieżącej lokalizacji w pliku i wcześniejszym kierunku końca pliku.  
  
 /Wild lub/l  
 Opcjonalny. Używa wstępnie zdefiniowane znaki specjalne w `findwhat` argument jako notacji do reprezentowania znaków ani sekwencji znaków.  
  
 opcji lub /w  
 Opcjonalny. Wyszukuje tylko całe wyrazy.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie zastępuje `btnSend` z `btnSubmit` we wszystkich otwieranie dokumentów.  
  
```  
>Edit.Replace btnSend btnSubmit /open  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Znajdowanie i zastępowanie tekstu](../../ide/finding-and-replacing-text.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Find/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)