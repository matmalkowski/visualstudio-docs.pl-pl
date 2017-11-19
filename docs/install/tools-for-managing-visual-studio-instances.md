---
title: "Narzędzia do wykrywania i Zarządzanie wystąpieniami programu Visual Studio | Dokumentacja firmy Microsoft"
description: "{{SYMBOL ZASTĘPCZY}}"
ms.date: 08/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 85686707-14C0-4860-9B7A-66485D43D241
author: timsneath
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 2f53d41f0501f5fb314b3235540edb4344b9cf7d
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2017
---
# <a name="tools-for-detecting-and-managing-visual-studio-instances"></a>Narzędzia do wykrywania i Zarządzanie wystąpieniami programu Visual Studio

## <a name="detecting-existing-visual-studio-instances"></a>Wykrywanie istniejącego wystąpienia programu Visual Studio
Wprowadzono kilka narzędzi pomagających wykrywać i zarządzanie nimi zainstalowanych wystąpieniami programu Visual Studio na komputerach klienckich:

* [VSWhere](https://github.com/microsoft/vswhere): plik wykonywalny wbudowanych w programie Visual Studio lub dostępne oddzielne dystrybucji, która pomaga znaleźć lokalizacji wszystkich wystąpień programu Visual Studio na określonym komputerze.
* [VSSetup.PowerShell](https://github.com/microsoft/vssetup.powershell): skrypty programu PowerShell, które identyfikują zainstalowanego wystąpienia programu Visual Studio za pomocą interfejsu API konfiguracji instalacji.
* [VS-Instalator — przykłady](https://github.com/microsoft/vs-setup-samples): C# i C++ przykłady, które przedstawiają sposób zapytania istniejącej instalacji za pomocą interfejsu API konfiguracji instalacji.

Ponadto [ustawienia konfiguracji API](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.setup.configuration.aspx) udostępnia interfejsy dla deweloperów, którzy chcą tworzyć własne narzędzia przeszukiwania wystąpieniami programu Visual Studio.

## <a name="using-vswhereexe"></a>Przy użyciu vswhere.exe
`vswhere.exe`jest automatycznie uwzględnione w Visual Studio 2017 wersji 15,2 lub powyżej, lub użytkownik może go pobrać z [strony wersjach](https://github.com/Microsoft/vswhere/releases). Użyj `vswhere -?` można pobrać informacji na temat narzędzia pomocy. Na przykład to polecenie przedstawia wszystkich wersji programu Visual Studio, w tym starsze wersje produktu i uwzględniane wersje wstępne i umieszcza wyniki w formacie JSON:

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Installer> vswhere.exe -legacy -prerelease -format json
```

>[!TIP]
>Aby uzyskać więcej informacji na temat instalacji programu Visual Studio 2017 zobacz [artykuły blogu Grunwald kondycji](https://blogs.msdn.microsoft.com/heaths/tag/vs2017/).


## <a name="editing-the-registry-for-a-visual-studio-instance"></a>Edycja rejestru dla wystąpienia programu Visual Studio
W programie Visual Studio 2017 r ustawień rejestru są przechowywane w prywatnej lokalizacji, która umożliwia wielu wystąpień side-by-side tej samej wersji programu Visual Studio na tym samym komputerze.

Jak te wpisy nie są przechowywane w rejestrze globalnej, istnieją specjalne instrukcje dotyczące używania Edytora rejestru, aby zmienić ustawienia rejestru:

1. Jeśli masz otwarte wystąpienie programu Visual Studio 2017, należy go zamknąć.
2. Uruchom `regedit.exe`.
3. Wybierz `HKEY_LOCAL_MACHINE` węzła.
4. Wybierz z menu głównego Regedit **Plik -> Hive obciążenia...**  , a następnie wybierz plik rejestru prywatny, który jest przechowywany w **AppData\Local** folderu. Na przykład:
   ```
   %localappdata%\Microsoft\VisualStudio\<config>\privateregistry.bin
   ```

> [!NOTE]
> `<config>`odnosi się do wystąpienia programu Visual Studio, który chcesz przeglądać.

Pojawi się monit o podanie nazwy hive, która staje się nazwa sieci izolowanej hive. Po wykonaniu tej czynności można przeglądać rejestru w gałęzi izolowanego utworzony.

> [!IMPORTANT]
> Przed ponownym uruchomieniu programu Visual Studio musi zwolnić gałąź izolowanym, utworzony. Aby to zrobić, wybierz Plik -> Zwolnij gałąź rejestru z poziomu menu głównego Regedit. (Jeśli nie zrobisz, następnie plik jest zablokowany i nie będzie można uruchomić programu Visual Studio)

## <a name="get-support"></a>Uzyskaj pomoc techniczną
Czasami może wystąpienia problemów. W przypadku niepowodzenia instalacji programu Visual Studio, zobacz [problemy dotyczące instalacji i uaktualniania Rozwiązywanie problemów z programu Visual Studio 2017](troubleshooting-installation-issues.md) stronę porady dotyczące rozwiązywania problemów. Jak również zgłosić problemy produktu z nami za pośrednictwem [zgłosić Problem](../ide/how-to-report-a-problem-with-visual-studio-2017.md) narzędzia w programie Visual Studio IDE lub udział sugestia z nami na [UserVoice](https://visualstudio.uservoice.com/forums/121579). Można śledzić problemy z produktu w [Visual Studio Developer Community](https://developercommunity.visualstudio.com/), zadawać pytania i odpowiedzi. Można również kontaktowaniu się z nami i innymi deweloperami Visual Studio za pomocą naszych [konwersacji programu Visual Studio w społeczności Gitter](https://gitter.im/Microsoft/VisualStudio) (wymaga [GitHub](https://github.com/) konta).
