---
title: Ogólne właściwości projektu (Android C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 65f4868b-b864-4989-a275-1e51869ef599
author: corob
ms.author: mblome
manager: douge
f1_keywords:
- VC.Project.VCConfiguration.OutputDirectory
- VC.Project.VCConfiguration.IntermediateDirectory
- VC.Project.VCConfiguration.TargetName
- VC.Project.VCConfiguration.TargetExt
- VC.Project.VCConfiguration.DeleteExtensionsOnClean
- VC.Project.VCConfiguration.BuildLogFile
- VC.Project.VCConfiguration.PlatformToolset
- VC.Project.VCConfiguration.ConfigurationType
- VC.Project.VCConfiguration.DeleteExtensionsOnClean
- VC.Project.VCConfiguration.UseOfSTL
- VC.Project.VCConfiguration.ThumbMode
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: b72cbb0d2660507a0578781c79a7cbdf60be7d8b
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2018
ms.locfileid: "39252241"
---
# <a name="general-project-properties-android-c"></a>Ogólne właściwości projektu (Android C++)

Właściwość | Opis | Opcje
--- | ---| ---
Katalog wyjściowy | Określa ścieżkę względną do katalogu pliku wyjściowego; może zawierać zmienne środowiskowe.
Katalog pośredni | Określa ścieżkę względną do pośredniego katalogu plików; może zawierać zmienne środowiskowe.
Nazwa obiektu docelowego | Określa nazwę pliku, który zostanie wygenerowany przez projekt.
Rozszerzenie docelowe | Określa rozszerzenie pliku, który zostanie wygenerowany przez projekt. (Przykład: *.exe* lub *.dll*)
Rozszerzenia do usunięcia podczas oczyszczania | Rozdzielana średnikami Specyfikacja symboli wieloznacznych, które pliki w katalogu pośrednim mają zostać usunięte podczas oczyszczania lub ponownie skompiluj.
Plik dziennika kompilacji | Określa plik dziennika kompilacji do zapisu, gdy rejestrowanie kompilacji jest włączona.
Zestaw narzędzi platformy | Określa zestaw narzędzi, używana do tworzenia bieżącej konfiguracji; Jeśli nie jest używany zestaw, domyślny zestaw narzędzi
Typ konfiguracji | Określa typ danych wyjściowych generowanych przez tę konfigurację. | **Biblioteka dynamiczna (SO)** — Biblioteka dynamiczna (*SO*)<br>**Biblioteka statyczna (.a)** — biblioteka statyczna (*.a*)<br>**Narzędzie** — narzędzie<br>**Plik reguł programu make** -pliku reguł programu make<br>
Docelowy poziom interfejsu API | Android NDK docelowy poziom interfejsu API przez tę konfigurację.
Użycie biblioteki STL | Określa, które standardowej biblioteki języka C++ do użycia dla tej konfiguracji. | **Minimalny Biblioteka środowiska uruchomieniowego języka C++ (system)**<br>**Biblioteka statyczna środowiska uruchomieniowego języka C++ (gabi ++ _static)**<br>**Biblioteka udostępniona środowiska uruchomieniowego języka C++ (gabi ++ _shared)**<br>**Biblioteka statyczna środowiska uruchomieniowego STLport (stlport_static)**<br>**Biblioteka udostępniona środowiska uruchomieniowego STLport (stlport_shared)**<br>**Biblioteka statyczna GNU STL (gnustl_static)**<br>**Biblioteka udostępniona GNU STL (gnustl_shared)**<br>**Biblioteka libc ++ LLVM statyczne (c ++ _static)**<br>**Biblioteka libc ++ LLVM udostępnionego (c ++ _shared)**<br>
Tryb Thumb | Generuj kod wykonujący dla mikroarchitektury thumb. Dotyczy tylko architektury arm. | **Thumb**<br>**ARM**<br>**Wyłączone**<br>
