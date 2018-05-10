---
title: Zapisuj dane wyjściowe okna Polecenie — Polecenie
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- tools.logcommandwindowoutput
helpviewer_keywords:
- log Command window output command
- View.LogCommandWindowOutput command
ms.assetid: d4ecec35-5af4-4954-8d60-2cd24583fbb4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2de9b21f55765706a56110aee84959b2003e994e
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="log-command-window-output-command"></a>Zapisuj dane wyjściowe okna Polecenie — Polecenie
Kopiuje wszystkie dane wejściowe i wyjściowe z **polecenia** okna do pliku.

## <a name="syntax"></a>Składnia

```cmd
Tools.LogCommandWindowOutput [filename] [/on|/off] [/overwrite]
```

## <a name="arguments"></a>Argumenty
 `filename`

 Opcjonalna. Nazwa pliku dziennika. Domyślnie plik jest tworzony w folderze profilu użytkownika. Jeśli nazwa pliku już istnieje, dziennik jest dołączany na końcu istniejącego pliku. Jeśli plik nie zostanie określony, ostatni określony plik jest używany. Jeśli żaden poprzedniej plik nie istnieje, domyślny plik dziennika jest tworzony o nazwie cmdline.log.

> [!TIP]
> Aby zmienić lokalizację, w której jest zapisywany w pliku dziennika, należy wprowadzić pełną ścieżkę pliku ujęta w cudzysłów, jeśli ścieżka zawiera spacje.


## <a name="switches"></a>Przełączniki
 /on

 Opcjonalna. Rozpoczyna się w dzienniku **polecenia** okna w określonym pliku i dołącza go przy użyciu nowych informacji.

 / Wyłącz

 Opcjonalna. Zatrzymuje dziennika **polecenia** okna.

 / overwrite

 Opcjonalna. Jeśli plik określony w `filename` argument odpowiada istniejącego pliku, plik jest zastępowany.

## <a name="remarks"></a>Uwagi
 Jeśli nie określono żadnych pliku, cmdline.log plik zostanie utworzony domyślnie. Domyślnie alias dla tego polecenia jest dziennika.

## <a name="examples"></a>Przykłady
 W tym przykładzie tworzy nowy plik dziennika cmdlog i uruchamia polecenie dziennika.

```cmd
>Tools.LogCommandWindowOutput cmdlog
```

 W tym przykładzie zatrzymuje rejestrowanie poleceń.

```cmd
>Tools.LogCommandWindowOutput /off
```

 W tym przykładzie wznawia rejestrowanie w pliku dziennika wcześniej używanych poleceń.

```cmd
>Tools.LogCommandWindowOutput /on
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Find/Command — pole](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)