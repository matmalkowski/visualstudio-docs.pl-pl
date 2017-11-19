---
title: "Clang właściwości konsolidatora (Android C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 10/23/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 66e88848-116c-4eb0-bc57-183394d35b57
author: corob
ms.author: mblome
manager: ghogen
f1_keywords:
- VC.Project.VCLinkerTool.OutputFile
- VC.Project.VCLinkerTool.ShowProgress
- VC.Project.VCLinkerTool.Version
- VC.Project.VCLinkerTool.VerboseOutput
- VC.Project.VCLinkerTool.IncrementalLink
- VC.Project.VCLinkerTool.SharedLibrarySearchPath
- VC.Project.VCLinkerTool.AdditionalLibraryDirectories
- VC.Project.VCLinkerTool.UnresolvedReferences
- VC.Project.VCLinkerTool.OptimizeForMemory
- VC.Project.VCLinkerTool.IgnoreDefaultLibraryNames
- VC.Project.VCLinkerTool.ForceSymbolReferences
- VC.Project.VCLinkerTool.ForceFileOutput
- VC.Project.VCLinkerTool.OmitDebuggerSymbolInformation
- VC.Project.VCLinkerTool.GenerateMapFile
- VC.Project.VCLinkerTool.Relocation
- VC.Project.VCLinkerTool.FunctionBinding
- VC.Project.VCLinkerTool.NoExecStackRequired
- VC.Project.WholeArchive
- VC.Project.AdditionalOptionsPage
- VC.Project.VCLinkerTool.AdditionalDependencies
- VC.Project.VCLinkerTool.LibraryDependencies
ms.openlocfilehash: 0e7b1d5b417250282092a780afc30aee965e4dfa
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="clang-linker-properties-android-c"></a>Clang właściwości konsolidatora (Android C++)

Właściwość | Opis | Opcje
--- | ---| ---
Plik wyjściowy | Opcja przesłania domyślną nazwę i lokalizację programu tworzonego przez konsolidatora. (-o).
Pokaż postęp | Drukuje wiadomości dotyczące postępu konsolidatora.
Wersja | -Version — opcja nakazuje konsolidatorowi umieszczenie numeru wersji w nagłówku pliku wykonywalnego.
Włącz pełne dane wyjściowe | Verbose — opcja nakazuje konsolidatorowi wysyłanie pełnych komunikatów na potrzeby debugowania.
Włączenie konsolidowania przyrostowego | Ta opcja nakazuje konsolidatorowi włączenie konsolidowania przyrostowego.
Ścieżka wyszukiwania biblioteki udostępnionej | Umożliwia użytkownikowi wypełnienie ścieżki wyszukiwania biblioteki udostępnionej.
Katalogi bibliotek dodatkowe | Umożliwia użytkownikowi przesłanianie ścieżki środowiskowej biblioteki. (-L folder).
Raport nierozpoznanych odwołań do symboli | Włączenie tej opcji będzie zgłaszać nierozpoznanych odwołań do symboli.
Optymalizuj pod kątem użycia pamięci | Optymalizuj pod kątem użycia pamięci przez ponowne odczytanie tabel symboli, jeśli to konieczne.
Ignoruj określone biblioteki domyślne | Określa jedną lub więcej nazw bibliotek domyślnych do zignorowania.
Wymuś odwołania do symboli | Wymuś symbolu, które zostaną wprowadzone w pliku wyjściowym jako niezdefiniowanego symbolu.
Informacje o symbolach debugera | Informacje o symbolach z pliku danych wyjściowych debugera. | **Uwzględnij wszystkie**<br>**Pomiń niepotrzebne symbole na potrzeby przetwarzania relokacji**<br>**Pomiń informacje o symbolach debugera tylko**<br>**Pomiń informacje o wszystkich symbolach**<br>
Informacje o symbolach debugera pakietu | Usuwanie informacji o symbolach debugera przed opakowania.  Kopia oryginalnego pliku binarnego będzie służyć do debugowania.
Nazwa pliku mapy | Opcja Map nakazuje konsolidatorowi utworzenie pliku mapy o nazwie określonej przez użytkownika.
Oznacz zmienne tylko do odczytu po relokacji | Ta opcja oznacza zmienne jako tylko do odczytu po relokacji.
Włącz natychmiastowe powiązanie funkcji | Ta opcja oznacza obiekt do natychmiastowego powiązania funkcji.
Wymagaj stosu wykonywalnego | Ta opcja oznacza dane wyjściowe jako niewymagające stosu wykonywalnego.
Całe archiwum | Całe archiwum używa całego kodu ze źródeł i zależności dodatkowych.
Dodatkowe opcje | Dodatkowe opcje.
Dodatkowe zależności | Określa dodatkowe elementy do dodania do wiersza polecenia konsolidacji.
Zależności biblioteki | Ta opcja umożliwia określenie dodatkowych bibliotek, które mają zostać dodane do wiersza polecenia konsolidatora. Dodatkowe biblioteki zostaną dodane do końca uruchomienia wiersza polecenia konsolidatora z "lib" i kończyć się rozszerzeniem ".a" lub ".so".  (-lFILE)
