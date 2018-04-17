---
title: Znajdź w plikach — polecenie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- edit.findinfiles
helpviewer_keywords:
- Edit.FindInFiles command
- find in files command
ms.assetid: 2fc78bfe-b339-4599-97f9-4cafd8a194d9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 115d096c56568b0c30387a65352cd1585adf15c3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="find-in-files-command"></a>Znajdź w plikach — Polecenie
Wyszukiwania plików przy użyciu podzbiór opcje dostępne na **Znajdź w plikach** karcie **Znajdź i Zamień** okna.  
  
## <a name="syntax"></a>Składnia  
  
```  
Edit.FindinFiles findwhat [/case] [/ext:extensions]  
[/lookin:searchpath] [/names] [/options] [/reset] [/stop] [/sub]  
[/text2] [/wild|/regex] [/word]  
```  
  
## <a name="arguments"></a>Argumenty  
 `findwhat`  
 Wymagany. Tekst do dopasowania.  
  
## <a name="switches"></a>Przełączniki  
 /Case lub /c  
 Opcjonalny. Dopasowań występuje tylko w przypadku wielkich i małych liter dokładnie odpowiadać określone w `findwhat` argumentu.  
  
 /ext: `extensions`  
 Opcjonalny. Określa rozszerzenia plików dla plików do przeszukania. Jeśli nie zostanie określony, poprzednie rozszerzenie zostanie użyty, jeśli zostało wprowadzone wcześniej.  
  
 /lookin: `searchpath`  
 Opcjonalny. Katalog do wyszukiwania. Jeśli ścieżka zawiera spacje, ujmij całą ścieżkę w cudzysłów.  
  
 /names lub /n  
 Opcjonalny. Wyświetla listę nazw plików, które zawierają dopasowania.  
  
 / Options lub /t  
 Opcjonalny. Wyświetla listę bieżące ustawienia opcji wyszukiwania, a nie przeprowadza wyszukiwanie.  
  
 /regex lub /r  
 Opcjonalny. Używa wstępnie zdefiniowane znaki specjalne w `findwhat` argument jako notacji reprezentujących wzorce tekstu, a nie literał znaków. Pełną listę znaków wyrażenia regularnego, zobacz [wyrażeń regularnych](../../ide/using-regular-expressions-in-visual-studio.md).  
  
 / Reset lub/e  
 Opcjonalny. Zwraca opcje Znajdź do ustawień domyślnych i nie wykonuje wyszukiwanie.  
  
 / stop  
 Opcjonalny. Zatrzymuje bieżącą operację wyszukiwania, jeśli jest w toku. Wyszukiwanie ignoruje wszystkie inne argumenty podczas `/stop` został określony. Na przykład aby zatrzymać bieżące wyszukiwanie należy wprowadzić następujące:  
  
```  
>Edit.FindinFiles /stop  
```  
  
 /Sub lub/s  
 Opcjonalny. Wyszukuje podfolderów znajdujących się w katalogu określonym w /lookin:`searchpath` argumentu.  
  
 /text2 lub /2  
 Opcjonalny. Wyświetla wyniki wyszukiwania w oknie Znajdź 2 wyników.  
  
 /Wild lub/l  
 Opcjonalny. Używa wstępnie zdefiniowane znaki specjalne w `findwhat` argument jako notacji do reprezentowania znaków ani sekwencji znaków.  
  
 opcji lub /w  
 Opcjonalny. Wyszukuje tylko całe wyrazy.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie szuka btnCancel we wszystkich plikach .cls znajdujące się w folderze "Moje projektów programu Visual Studio" i wyświetla informacje dopasowania w oknie Znajdź 2 wyniki.  
  
```  
>Edit.FindinFiles btnCancel /lookin:"c:/My Visual Studio Projects" /ext:*.cls /text2  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Znajdź w plikach](../../ide/find-in-files.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Find/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)