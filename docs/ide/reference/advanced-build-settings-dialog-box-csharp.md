---
title: "Zaawansowane ustawienia kompilacji — okno dialogowe (C#) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 06/20/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cs.AdvancedBuildSettings
helpviewer_keywords:
- Build options [C#], advanced
ms.assetid: 141f2dee-1563-4ce6-ba37-32920b082519
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 44694e84fc0ab83ca4caf7bf80535dcae50a636f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="advanced-build-settings-dialog-box-c"></a>Zaawansowane ustawienia kompilacji (C#) — Okno dialogowe

Użyj **Zaawansowane ustawienia kompilacji** okna dialogowego **projektanta projektu** do określenia zaawansowane właściwości konfiguracji kompilacji projektu. Dotyczy to okno dialogowe [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] tylko projekty.

## <a name="general"></a>Ogólne

 Poniższe opcje pozwalają na ogólne ustawienia zaawansowane.

 **Wersja językowa** Określa wersję języka. Zestaw funkcji różni się w każdej wersji, ta opcja może służyć do wymusić kompilatora, aby zezwolić tylko podzbiór funkcji zaimplementowanych lub Włącz tylko te funkcje, które są zgodne ze standardem istniejących. To ustawienie ma następujące opcje:

 - **default**

   Przeznaczony dla bieżącej wersji.

- **ISO-1** i **ISO-2**

  Dotyczy funkcji standardowe ISO-1 i ISO 2 odpowiednio.

- **C# [numer wersji]**

 Dotyczy określonej wersji języka C#. Aby uzyskać więcej informacji, zobacz [/langversion (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option).


 **Raportowanie wewnętrznych błędów kompilatora** Określa, czy do raportów o błędach kompilatora do firmy Microsoft. Jeśli ustawiono **wiersza** (ustawienie domyślne), jeśli zostanie wyświetlony monit o wystąpi błąd wewnętrzny kompilatora, dzięki któremu można elektronicznie wysyłania raportów o błędach do firmy Microsoft. Jeśli ustawiono **wysyłania**, raport o błędzie wysyłany jest automatycznie. Jeśli ustawiono **kolejki**, raporty o błędach zostaną umieszczone w kolejce. Jeśli ustawiono **Brak**, błąd jest zgłaszany tylko przez kompilator tekstowych danych wyjściowych. Aby uzyskać więcej informacji, zobacz [/errorreport (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option).

 **Sprawdzaj przepełnienie/niedopełnienie arytmetyczne** Określa, czy instrukcji arytmetyczne całkowitą nie jest w zakresie [zaznaczone](/dotnet/csharp/language-reference/keywords/checked) lub [niezaznaczone](/dotnet/csharp/language-reference/keywords/unchecked) słów kluczowych i czy wynikiem jest wartość poza obszarem danych typu spowoduje, że wyjątek czasu wykonywania. Aby uzyskać więcej informacji, zobacz [/ checked (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option).

 **Nie odwołuj się do pliku mscorlib.dll** Określa, czy mscorlib.dll zostaną zaimportowane do programu Definiowanie całą <xref:System> przestrzeni nazw. Zaznacz to pole wyboru, jeśli chcesz zdefiniować lub utworzyć własne <xref:System> przestrzeni nazw i obiektów. Aby uzyskać więcej informacji, zobacz [/nostdlib (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option).

## <a name="output"></a>Dane wyjściowe

 Poniższe opcje pozwalają określić opcje wyjściowe zaawansowanych.

 **Informacje o debugowaniu** Określa typ informacji dotyczących debugowania generowanych przez kompilator. Aby uzyskać informacje na temat konfigurowania wydajność debugowania aplikacji, zobacz [ułatwiając obraz do debugowania](http://msdn.microsoft.com/Library/7d90ea7a-150f-4f97-98a7-f9c26541b9a3). To ustawienie ma następujące opcje:

- **Brak**

  Określa, że żadne informacje debugowania będą generowane.

- **Pełna**

  Umożliwia dołączenie debugera do działającego programu.

- **pdbonly**

  Umożliwia debugowanie, gdy program jest uruchamiany w debugerze, ale będą wyświetlane tylko asemblera jeśli uruchomiony program jest podłączony do debugera kodu źródłowego.
- **przenośne**

  Tworzy. Plik PDB, plik symboli nie poszczególnych platform, przenośne z innych narzędzi, szczególnie debuger, informacje o tym, co w głównym pliku wykonywalnego i jak został utworzony. Zobacz [przenośnych PDB](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) Aby uzyskać więcej informacji.

- **osadzone**

  Osadza informacje o symbolach przenośny w zestawie. Nie zewnętrznych. Plik PDB jest generowany.

Aby uzyskać więcej informacji, zobacz [/Debug (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option).

**Plik wyrównanie** Określa rozmiar sekcji w pliku wyjściowym. Prawidłowe wartości to **512**, **1024**, **2048**, **4096**, i **8192**. Te wartości są mierzone w bajtach. Każdej sekcji będzie wyrównany na granicy, który jest wielokrotnością tej wartości mające wpływ na rozmiar pliku wyjściowego. Aby uzyskać więcej informacji, zobacz [/filealign (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option).

**Adres podstawowy biblioteki** Określa preferowany adres podstawowy, w którym można załadować biblioteki DLL. Domyślny adres podstawowy biblioteki DLL jest ustawiana przez [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)] środowisko uruchomieniowe języka wspólnego. Aby uzyskać więcej informacji, zobacz [/baseAddress (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option).

## <a name="see-also"></a>Zobacz też

 [Opcje kompilatora C#](/dotnet/csharp/language-reference/compiler-options/index) [strona kompilacji, Projektant projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md)
