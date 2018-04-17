---
title: Aliasy poleceń programu Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- aliases, Visual Studio commands
- Visual Studio, commands
- predefined command aliases
- commands, aliases
- Visual Studio commands
- pre-defined command aliases
- command aliases
ms.assetid: de8bb378-8c1c-4087-a9a5-537fa8314c19
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 05699b5791bf8493ac8dd19c6f3dbd28ab5b2ce1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="visual-studio-command-aliases"></a>Visual Studio — Aliasy poleceń
Aliasy umożliwiają wprowadzanie polecenia do **Find/Command** pole lub **polecenia** okna skracając tekst potrzebne do wykonania polecenia. Na przykład zamiast wprowadzania `>File.OpenFile` do wyświetlenia **Otwórz plik** okno dialogowe, można użyć wstępnie zdefiniowanych alias `>of`.  
  
 Typ `alias` w **polecenia**okno, aby wyświetlić listę aliasów bieżący oraz ich definicje. Typ `>cls` aby wyczyścić zawartość **polecenia** okna. Jeśli chcesz zobaczyć aliasu dla określonego polecenia, wpisz `alias <command name>`.  
  
 Możesz łatwo utworzyć aliasu dla jednego z poleceń Visual Studio (z lub bez argumentów). Na przykład składnia aliasów `File.NewFile MyFile.txt` jest `alias MyAlias File.NewFile MyFile.txt`. Usunięciem aliasy z `alias <alias name> /delete`  
  
 Poniższa tabela zawiera listę wstępnie zdefiniowane aliasy poleceń Visual Studio. Niektóre nazwy polecenia mają więcej niż jeden alias wstępnie zdefiniowane. Kliknij łącza poniżej, aby wyświetlić szczegółowych tematów poprawnej składni, argumentów i przełączników dla tych poleceń, nazw poleceń.  
  
|Nazwa polecenia|Alias|Pełna nazwa|  
|------------------|-----------|-------------------|  
|[Drukuj, polecenie](../../ide/reference/print-command.md)|?|Debug.Print|  
|[Szybka czujka, polecenie](../../ide/reference/quick-watch-command.md)|??|Debug.quickwatch —|  
|Dodaj nowy projekt|AddProj|File.AddNewProject|  
|[Alias, polecenie](../../ide/reference/alias-command.md)|Alias|Tools.alias —|  
|okno zmiennych automatycznych|Automatycznych|Debug.Autos|  
|Okno punktów przerwania|czarnej listy|Debug.Breakpoints|  
|Przełącz punkt przerwania|najlepszych praktyk w zakresie|Debug.togglebreakpoint —|  
|Stos wywołań, okno|Stos wywołań|Debug.CallStack|  
|Wyczyść zakładki|ClearBook|Edit.ClearBookmarks|  
|Zamknięcie|Zamknięcie|File.Close|  
|Zamknij wszystkie dokumenty|CloseAll|Window.CloseAllDocuments|  
|Wyczyść wszystko|ze specyfikacją CLS|Edit.ClearAll|  
|Tryb polecenia|Cmd|View.CommandWindow|  
|Kod widoku|kod|View.ViewCode|  
|[Lista pamięci, polecenie](../../ide/reference/list-memory-command.md)|d|Debug.listmemory —|  
|[Lista pamięci — polecenie](../../ide/reference/list-memory-command.md) jako ANSI|da|Debug.listmemory — /Ansi|  
|[Lista pamięci — polecenie](../../ide/reference/list-memory-command.md) format jednego bajtu|bazy danych|Debug.listmemory — /Format:OneByte|  
|[Lista pamięci — polecenie](../../ide/reference/list-memory-command.md) jako ANSI z formatem czterech bajtów|Kontroler domeny|Debug.listmemory — /Format:FourBytes /Ansi|  
|[Lista pamięci — polecenie](../../ide/reference/list-memory-command.md) format czterech bajtów|dd|Debug.listmemory — /Format:FourBytes|  
|Usuń do dokumentacji książki online|DelBOL|Edit.DeleteToBOL|  
|Usuń do EOL|DelEOL|Edit.DeleteToEOL|  
|Usuń odstępy w poziomie|DelHSp|Edit.DeleteHorizontalWhitespace|  
|Pokaż projektanta|projektant|View.ViewDesigner|  
|[Lista pamięci — polecenie](../../ide/reference/list-memory-command.md) format liczb zmiennoprzecinkowych|DF|Debug.ListMemory/Format:Float|  
|Dezasemblacja, okno|disasm|Debug.Disassembly|  
|[Lista pamięci — polecenie](../../ide/reference/list-memory-command.md) format 8-bajtowej|dq —|Debug.listmemory — /Format:EightBytes|  
|[Lista pamięci — polecenie](../../ide/reference/list-memory-command.md) jako Unicode|du|Debug.listmemory — /Unicode|  
|[Oceń instrukcję, polecenie](../../ide/reference/evaluate-statement-command.md)|Eval|Debug.evaluatestatement —|  
|Zakończ|Zakończ|File.Exit|  
|Wybieranie formatu|format|Edit.FormatSelection|  
|Pełny ekran|Pełny ekran|View.FullScreen|  
|[Uruchomienie, polecenie](../../ide/reference/start-command.md)|g|Debug.Start|  
|[Przejdź do, polecenie](../../ide/reference/go-to-command.md)|GotoLn|Edit.GoTo|  
|Przejdź do nawiasu klamrowego|GotoBrace|Edit.GotoBrace|  
|F1Help|Pomoc|Help.F1Help|  
|Trybie natychmiastowym|natychmiast|Tools.ImmediateMode|  
|Wstaw plik jako tekst|InsertFile|Edit.InsertFileAsText|  
|[Lista stosu wywołań, polecenie](../../ide/reference/list-call-stack-command.md)|KB|Debug.listcallstack —|  
|Wprowadź małe litery|LCase|Edit.MakeLowercase|  
|Wytnij wiersza|LineCut|Edit.LineCut|  
|Usuń wiersz|LineDel|Edit.LineDelete|  
|Lista składników|Wyświetlanie członków|Edit.ListMembers|  
|okno zmiennych lokalnych|Zmienne lokalne|Debug.Locals|  
|[Zapisuj dane wyjściowe okna Polecenie, polecenie](../../ide/reference/log-command-window-output-command.md)|Log|Tools.LogCommandWindowOutput|  
|Tryb oznaczania okno polecenia|Oznacz|Tools.CommandWindowMarkMode|  
|okno pamięci|Memory1 pamięci|Debug.Memory1|  
|Okno pamięci 2|Memory2|Debug.Memory2|  
|Okno pamięci 3|Pamięci3|Debug.Memory3|  
|Okno pamięci 4|Memory4|Debug.Memory4|  
|[Ustaw Radix, polecenie](../../ide/reference/set-radix-command.md)|n|Debug.setradix —|  
|[ShowWebBrowser, polecenie](../../ide/reference/showwebbrowser-command.md)|Przejdź NAV|View.showwebbrowser —|  
|Następna zakładka|NextBook|Edit.NextBookmark|  
|[Nowy plik, polecenie](../../ide/reference/new-file-command.md)|NF|File.NewFile|  
|Nowy projekt|potoki NewProj|File.NewProject|  
|[Otwórz plik, polecenie](../../ide/reference/open-file-command.md)|jest on otwarty|File.OpenFile|  
|[Otwórz projekt, polecenie](../../ide/reference/open-project-command.md)|OP|File.OpenProject|  
|Zwiń do definicji/Stop zwijania|OutlineDefs StopOutlining|Edit.CollapsetoDefinitions|  
|Przekrocz|p|Debug.StepOver|  
|Informacje o parametrach|ParamInfo|Edit.ParameterInfo|  
|Wyjdź|Oczyść|Debug.StepOut|  
|Poprzednia zakładka|PrevBook|Edit.PreviousBookmark|  
|Drukowanie plików|Drukuj|File.Print|  
|Okno Właściwości|właściwości|View.PropertiesWindow|  
|Zatrzymywanie|q|Debug.StopDebugging|  
|Wykonaj ponownie|Wykonaj ponownie|Edit.Redo|  
|Okno rejestrów|rejestry|Debug.Registers|  
|Uruchom do kursora|RTC|Debug.RunToCursor|  
|Zapisywanie wybranych elementów|Zapisz|File.SaveSelectedItems|  
|Zapisz wszystko|SaveAll|File.SaveAll|  
|Zapisz jako|Zapisz jako|File.SaveSelectedItemsAs|  
|[Powłoka, polecenie](../../ide/reference/shell-command.md)|powłoka|Tools.Shell —|  
|Zatrzymaj Znajdź w plikach|StopFind|Edit.findinfiles — / Stop|  
|Zamień zakotwiczenie|SwapAnchor|Edit.SwapAnchor|  
|Wkrocz|t|Debug.StepInto|  
|Tabify — formatowanie zaznaczenia|tabify — formatowanie|Edit.TabifySelection|  
|Tasklist okna|TaskList|View.TaskList|  
|Okno wątków|Wątki|Debug.Threads|  
|Sąsiadująco w poziomie|TileH|Window.TileHorizontally|  
|Sąsiadująco w pionie|TileV|Window.TileVertically|  
|Przełącz zakładkę|ToggleBook|Edit.ToggleBookmark|  
|Okno przybornika|przybornik|View.Toolbox|  
|[Lista dezasemblacji, polecenie](../../ide/reference/list-disassembly-command.md)|u|Debug.listdisassembly —|  
|Upewnij się wielkie litery|UCase|Edit.MakeUppercase|  
|Cofnij|Cofnij|Edit.Undo|  
|Untabify zaznaczenia|Untabify|Edit.UntabifySelection|  
|okno czujki|Czujki|Debug.WatchN|  
|Przełącz zawijanie tekstu|WordWrap|Edit.ToggleWordWrap|  
|Lista procesów|&#124;|Debug.ListProcesses|  
|[Lista wątków, polecenie](../../ide/reference/list-threads-command.md)|~ ~ * k ~\*kb|Debug.listthreads — Debug.ListTheads /AllThreads|  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Find/Command — pole](../../ide/find-command-box.md)