---
title: "Polecenie wyjściowe okna polecenie dziennika | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- tools.logcommandwindowoutput
helpviewer_keywords:
- log Command window output command
- View.LogCommandWindowOutput command
ms.assetid: d4ecec35-5af4-4954-8d60-2cd24583fbb4
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 7f5dffcd68447cac398c980f0b6c0ac2319c9060
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="log-command-window-output-command"></a>Zapisuj dane wyjściowe okna Polecenie — Polecenie
Kopiuje wszystkie dane wejściowe i wyjściowe z **polecenia** okna do pliku.  
  
## <a name="syntax"></a>Składnia  
  
```  
Tools.LogCommandWindowOutput [filename] [/on|/off] [/overwrite]  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Opcjonalny. Nazwa pliku dziennika. Domyślnie plik jest tworzony w folderze profilu użytkownika. Jeśli nazwa pliku już istnieje, dziennik jest dołączany na końcu istniejącego pliku. Jeśli plik nie zostanie określony, ostatni określony plik jest używany. Jeśli żaden poprzedniej plik nie istnieje, domyślny plik dziennika jest tworzony o nazwie cmdline.log.  
  
> [!TIP]
>  Aby zmienić lokalizację, w której jest zapisywany w pliku dziennika, należy wprowadzić pełną ścieżkę pliku ujęta w cudzysłów, jeśli ścieżka zawiera spacje.  
  
## <a name="switches"></a>Przełączniki  
 /on  
 Opcjonalny. Rozpoczyna się w dzienniku **polecenia** okna w określonym pliku i dołącza go przy użyciu nowych informacji.  
  
 / Wyłącz  
 Opcjonalny. Zatrzymuje dziennika **polecenia** okna.  
  
 / overwrite  
 Opcjonalny. Jeśli plik określony w `filename` argument odpowiada istniejącego pliku, plik jest zastępowany.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli nie określono żadnych pliku, cmdline.log plik zostanie utworzony domyślnie. Domyślnie alias dla tego polecenia jest dziennika.  
  
## <a name="examples"></a>Przykłady  
 W tym przykładzie tworzy nowy plik dziennika cmdlog i uruchamia polecenie dziennika.  
  
```  
>Tools.LogCommandWindowOutput cmdlog  
```  
  
 W tym przykładzie zatrzymuje rejestrowanie poleceń.  
  
```  
>Tools.LogCommandWindowOutput /off  
```  
  
 W tym przykładzie wznawia rejestrowanie w pliku dziennika wcześniej używanych poleceń.  
  
```  
>Tools.LogCommandWindowOutput /on  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Find/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)