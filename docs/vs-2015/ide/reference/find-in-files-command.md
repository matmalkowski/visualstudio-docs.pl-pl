---
title: Znajdź w plikach — polecenie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- edit.findinfiles
helpviewer_keywords:
- Edit.FindInFiles command
- find in files command
ms.assetid: 2fc78bfe-b339-4599-97f9-4cafd8a194d9
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1a05aec2867d050e7b9a1a49705a7882b396892f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42681542"
---
# <a name="find-in-files-command"></a>Znajdź w plikach — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [Znajdź w plikach — polecenie](https://docs.microsoft.com/visualstudio/ide/reference/find-in-files-command).  
  
  
Wyszukiwanie plików za pomocą podzestawu opcji dostępnych w **Znajdź w plikach** karcie **Znajdź i Zamień** okna.  
  
## <a name="syntax"></a>Składnia  
  
```  
Edit.FindinFiles findwhat [/case] [/ext:extensions]  
[/lookin:searchpath] [/names] [/options] [/reset] [/stop] [/sub]  
[/text2] [/wild|/regex] [/word]  
```  
  
## <a name="arguments"></a>Argumenty  
 `findwhat`  
 Wymagane. Tekst do dopasowania.  
  
## <a name="switches"></a>Przełączniki  
 /Case lub /c  
 Opcjonalna. Dopasowuje występują tylko wtedy, gdy wielkich i małych liter dokładnie odpowiadać, określone w `findwhat` argumentu.  
  
 /ext: `extensions`  
 Opcjonalna. Określa rozszerzenia plików dla plików do przeszukania. Jeśli nie zostanie określony, poprzednie rozszerzenie jest używana, jeśli wcześniej zostało wprowadzone.  
  
 /lookin: `searchpath`  
 Opcjonalna. Katalog do przeszukania. Jeśli ścieżka zawiera spacje, należy ująć w znaki cudzysłowu pełną ścieżkę.  
  
 /names lub /n  
 Opcjonalna. Wyświetla listę nazw plików, które zawierają dopasowania.  
  
 / Options lub/t  
 Opcjonalna. Wyświetla listę bieżących ustawień opcji wyszukiwania, a nie wyszukiwania.  
  
 /regex lub/r  
 Opcjonalna. Używa wstępnie zdefiniowanych znaków specjalnych w `findwhat` argument jako notacji, które reprezentują wzorców tekstu, a nie jako znaki literału. Aby uzyskać pełną listę znaki wyrażenia regularnego, zobacz [wyrażeń regularnych](../../ide/using-regular-expressions-in-visual-studio.md).  
  
 / Reset i/e  
 Opcjonalna. Zwraca opcje wyszukiwania do ustawień domyślnych, a nie wyszukiwania.  
  
 / stop  
 Opcjonalna. Zatrzymuje bieżącą operację wyszukiwania, jeśli jest w toku. Wyszukiwania ignoruje wszystkie inne argumenty po `/stop` została określona. Na przykład można zatrzymać bieżące wyszukiwanie możesz wprowadzić następujące czynności:  
  
```  
>Edit.FindinFiles /stop  
```  
  
 / Sub lub /s  
 Opcjonalna. Wyszukuje podfoldery znajdujące się w katalogu wskazanym na /lookin:`searchpath` argumentu.  
  
 /text2 lub /2  
 Opcjonalna. Wyświetla wyniki wyszukiwania w oknie Znajdź wyniki 2.  
  
 /Wild lub/l  
 Opcjonalna. Używa wstępnie zdefiniowanych znaków specjalnych w `findwhat` argument jako notacji do reprezentowania znaku lub sekwencji znaków.  
  
 opcji lub Wn  
 Opcjonalna. Wyszukiwanie tylko całe wyrazy.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie wyszukuje btnCancel we wszystkich plikach .cls znajduje się w folderze "Moje projektów programu Visual Studio" i wyświetla informacje o dopasowania w oknie Znajdź wyniki 2.  
  
```  
>Edit.FindinFiles btnCancel /lookin:"c:/My Visual Studio Projects" /ext:*.cls /text2  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Znajdź w plikach](../../ide/find-in-files.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Znajdź/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)



