---
title: Find — polecenie | Dokumentacja firmy Microsoft
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
- edit.find
helpviewer_keywords:
- Find command
- Edit.Find command
ms.assetid: f0c705dc-2b97-423d-abbf-5584d4827208
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6deea29955bac41fb9714f094456775862259b40
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42681053"
---
# <a name="find-command"></a>Find — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [polecenia Find](https://docs.microsoft.com/visualstudio/ide/reference/find-command).  
  
  
Przeszukuje pliki za pomocą podzestawu opcji dostępnych w **Znajdź w plikach** karcie **Znajdź i Zamień** okna.  
  
## <a name="syntax"></a>Składnia  
  
```  
Edit.Find findwhat [/case] [/doc | /proc | /open | /sel]   
[/markall] [/options] [/reset] [/up] [/wild | /regex] [/word]  
```  
  
## <a name="arguments"></a>Argumenty  
 `findwhat`  
 Wymagane. Tekst do dopasowania.  
  
## <a name="switches"></a>Przełączniki  
 /Case lub /c  
 Opcjonalna. Dopasowuje występują tylko wtedy, gdy wielkich i małych liter dokładnie odpowiadać, określone w `findwhat` argumentu.  
  
 / doc lub /d  
 Opcjonalna. Wyszukuje w bieżącym dokumencie. Określ tylko jeden zakres wyszukiwania dostępnych `/doc`, `/proc`, `/open`, lub `/sel`.  
  
 /markall lub/m  
 Opcjonalna. Umieszcza grafiki na każdy wiersz zawiera dopasowanie wyszukiwania w bieżącym dokumencie.  
  
 / Open lub /o  
 Opcjonalna. Przeszukuje wszystkie otwarte dokumenty, jakby pochodziły z jednego dokumentu. Określ tylko jeden zakres wyszukiwania dostępnych `/doc`, `/proc`, `/open`, lub `/sel`.  
  
 / Options lub/t  
 Opcjonalna. Wyświetla listę bieżących ustawień opcji wyszukiwania, a nie wyszukiwania.  
  
 /proc lub /p  
 Opcjonalna. Wyszukuje bieżącą procedurę. Określ tylko jeden zakres wyszukiwania dostępnych `/doc`, `/proc`, `/open`, lub `/sel`.  
  
 / Reset i/e  
 Opcjonalna. Zwraca opcje wyszukiwania do ustawień domyślnych, a nie wyszukiwania.  
  
 /SEL lub /s  
 Opcjonalna. Wyszukuje w bieżącym zaznaczeniu. Określ tylko jeden zakres wyszukiwania dostępnych `/doc`, `/proc`, `/open`, lub `/sel`.  
  
 /Up lub /u  
 Opcjonalna. Wyszukiwanie w bieżącej lokalizacji w pliku w kierunku początku pliku. Domyślnie wyszukiwanie rozpoczyna się w bieżącej lokalizacji w pliku i wyszukiwania na końcu pliku.  
  
 /regex lub/r  
 Opcjonalna. Używa wstępnie zdefiniowanych znaków specjalnych w `findwhat` argument jako notacji, które reprezentują wzorców tekstu, a nie jako znaki literału. Aby uzyskać pełną listę znaki wyrażenia regularnego, zobacz [wyrażeń regularnych](../../ide/using-regular-expressions-in-visual-studio.md).  
  
 /Wild lub/l  
 Opcjonalna. Używa wstępnie zdefiniowanych znaków specjalnych w `findwhat` argument jako notacji do reprezentowania znaku lub sekwencji znaków.  
  
 opcji lub Wn  
 Opcjonalna. Wyszukiwanie tylko całe wyrazy.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przeprowadza wyszukiwanie dla słowa "somestring" w obecnie zaznaczonej sekcji kodu.  
  
```  
>Edit.Find somestring /sel /case  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Znajdź/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)



