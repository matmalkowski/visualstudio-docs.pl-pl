---
title: "Find — polecenie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: edit.find
helpviewer_keywords:
- Find command
- Edit.Find command
ms.assetid: f0c705dc-2b97-423d-abbf-5584d4827208
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: dde6bed2fda4dbf68a37636df83044e945a1f5d7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="find-command"></a>Find — Polecenie
Wyszukuje pliki przy użyciu podzbiór opcje dostępne na **Znajdź w plikach** karcie **Znajdź i Zamień** okna.  
  
## <a name="syntax"></a>Składnia  
  
```  
Edit.Find findwhat [/case] [/doc | /proc | /open | /sel]   
[/markall] [/options] [/reset] [/up] [/wild | /regex] [/word]  
```  
  
## <a name="arguments"></a>Argumenty  
 `findwhat`  
 Wymagany. Tekst do dopasowania.  
  
## <a name="switches"></a>Przełączniki  
 /Case lub /c  
 Opcjonalny. Dopasowań występuje tylko w przypadku wielkich i małych liter dokładnie odpowiadać określone w `findwhat` argumentu.  
  
 / doc lub /d  
 Opcjonalny. Wyszukuje tylko bieżącego dokumentu. Określ tylko jeden zakres wyszukiwania dostępnych `/doc`, `/proc`, `/open`, lub `/sel`.  
  
 /markall lub/m  
 Opcjonalny. Umieszcza grafiki w każdym wierszu, zawierający zgodność wyszukiwania w bieżącym dokumencie.  
  
 / Open lub /o  
 Opcjonalny. Przeszukuje wszystkie otwarte dokumenty, tak jakby były to jeden dokument. Określ tylko jeden zakres wyszukiwania dostępnych `/doc`, `/proc`, `/open`, lub `/sel`.  
  
 / Options lub /t  
 Opcjonalny. Wyświetla listę bieżące ustawienia opcji wyszukiwania, a nie przeprowadza wyszukiwanie.  
  
 /proc lub /p  
 Opcjonalny. Wyszukuje bieżącą procedurę. Określ tylko jeden zakres wyszukiwania dostępnych `/doc`, `/proc`, `/open`, lub `/sel`.  
  
 / Reset lub/e  
 Opcjonalny. Zwraca opcje Znajdź do ustawień domyślnych i nie wykonuje wyszukiwanie.  
  
 /SEL lub/s  
 Opcjonalny. Wyszukuje tylko bieżące zaznaczenie. Określ tylko jeden zakres wyszukiwania dostępnych `/doc`, `/proc`, `/open`, lub `/sel`.  
  
 /Up lub /u  
 Opcjonalny. Wyszukiwanie od bieżącej lokalizacji w pliku kierunku początku pliku. Domyślnie wyszukiwanie rozpoczyna się w bieżącej lokalizacji w pliku i wyszukiwania pod koniec pliku.  
  
 /regex lub /r  
 Opcjonalny. Używa wstępnie zdefiniowane znaki specjalne w `findwhat` argument jako notacji reprezentujących wzorce tekstu, a nie literał znaków. Pełną listę znaków wyrażenia regularnego, zobacz [wyrażeń regularnych](../../ide/using-regular-expressions-in-visual-studio.md).  
  
 /Wild lub/l  
 Opcjonalny. Używa wstępnie zdefiniowane znaki specjalne w `findwhat` argument jako notacji do reprezentowania znaków ani sekwencji znaków.  
  
 opcji lub /w  
 Opcjonalny. Wyszukuje tylko całe wyrazy.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie wykonuje wyszukiwanie z uwzględnieniem wielkości liter dla słowa "somestring" w aktualnie wybranej części kodu.  
  
```  
>Edit.Find somestring /sel /case  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Find/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)