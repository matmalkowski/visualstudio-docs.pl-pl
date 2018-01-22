---
title: "Ustawienia konfiguracji debugowania języka Visual Basic projektu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vbProjectPropertiesDebug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- debugging [Visual Basic], debugger settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debug configurations, Visual Basic
ms.assetid: 72a8483a-af0b-4403-8b0d-ee9ad71ee435
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a9d9b9c5cee3dc69698320af77a7cc909b344a2d
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/22/2018
---
# <a name="project-settings-for-a-visual-basic-debug-configuration"></a>Ustawienia projektu dla konfiguracji debugowania w Visual Basic
Możesz zmienić ustawienia projektu dla [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] konfiguracji debugowania w **strony właściwości** okna, zgodnie z opisem w [konfiguracji Debug i Release](../debugger/how-to-set-debug-and-release-configurations.md). W poniższych tabelach przedstawiono gdzie można znaleźć ustawień debugera w **strony właściwości** okna.  
  
> [!WARNING]
>  Ten temat nie dotyczy aplikacji platformy uniwersalnej systemu Windows. Zobacz [rozpocząć sesję debugowania: (VB, C#, C++ i XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
### <a name="debug-tab"></a>Karta debugowania  
  
|Ustawienie|Opis|  
|-------------|-----------------|  
|**Konfiguracja**|Ustawia tryb dla kompilowania aplikacji. Wybierz spośród **aktywny (debugowanie)**, **debugowania**, **wersji**, **wszystkie konfiguracje**.|  
|**Uruchomienie akcji**|Ta grupa formantów Określa akcję, która ma miejsce, gdy wybierzesz Start z menu Debugowanie.<br /><br /> -   **Uruchom projekt** jest ustawieniem domyślnym i uruchamia projekt startowy do debugowania. <br />-   **Uruchom program zewnętrznych** umożliwia start i Dołącz do programu, który nie jest częścią [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektu. Aby uzyskać więcej informacji, zobacz [dołączyć do uruchamiania procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).<br />-   **Uruchom przeglądarkę w adresie URL** pozwala na debugowanie aplikacji sieci Web.|  
|**Argumenty wiersza polecenia**|Określa argumenty wiersza polecenia dla programu do debugowania. Nazwa polecenia jest nazwa programu określone w uruchomienia programu zewnętrznego. Argumenty wiersza polecenia są ignorowane, jeśli akcja uruchamiania początkowy adres URL.|  
|**Katalog roboczy**|Określa katalog roboczy debugowany program. W [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], katalog roboczy jest aplikacja jest uruchamiana w katalogu. Domyślny katalog roboczy jest \bin\Debug lub \bin\Release, w zależności od bieżącej konfiguracji.|  
|**Użyj komputera zdalnego**|Gdy pole wyboru jest zaznaczone, włączone jest debugowanie zdalne. W polu tekstowym, możesz wpisać nazwę komputera zdalnego, gdy aplikacja będzie uruchamiana na potrzeby debugowania lub [nazwy serwera polecenia Msvsmon](../debugger/remote-debugging.md). Lokalizacja pliku exe na komputerze zdalnym jest określony przez właściwość ścieżki wyjściowej na karcie kompilacji. Lokalizacja musi być możliwe do udostępnienia katalog na komputerze zdalnym.|  
|**Debugowanie kodu niezarządzanego**|Umożliwia debugowanie wywołania do kodu natywnego Win32 (niezarządzany) z zarządzanych aplikacji. Jest to ten sam efekt co Wybór mieszany dla typu debugera w [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] projektu.|  
|**Debugowanie SQL Server**|Pozwala na debugowanie obiektów bazy danych programu SQL Server.|  
  
### <a name="compile-tab-press-advanced-compile-options-button"></a>Kompiluj kartę: kliknij przycisk Zaawansowane opcje kompilacji  
  
|Ustawienie|Opis|  
|-------------|-----------------|  
|**Włącz optymalizacje**|Ta opcja powinna być zaznaczone. Optymalizacja powoduje, że kod, który faktycznie jest wykonywany różni się od kodu źródłowego w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]i w związku z tym powoduje, że profilowanie trudne. Jeśli kod jest zoptymalizowany, symbole nie są ładowane automatycznie podczas debugowania tylko mój kod.|  
|**Generowanie informacji o debugowaniu**|Domyślnie w zarówno debug i release zdefiniowane wersje, to ustawienie (odpowiada opcji kompilatora/Debug) tworzy informacji o debugowaniu w czasie kompilacji. Debuger używa tych informacji do wyświetlenia nazwy zmiennych i inne informacje w postaci przydatne podczas debugowania. Jeśli kompilacja programu bez tych informacji funkcjonalność debuger będzie ograniczona. Aby uzyskać więcej informacji, zobacz [/debug](/dotnet/visual-basic/reference/command-line-compiler/debug).|  
|**Zdefiniuj stała debugowania**|Definiowanie tego symbolu umożliwia kompilowanie warunkowe funkcji danych wyjściowych z [Klasa Debug](/dotnet/api/system.diagnostics.debug). Z tego symbolu zdefiniowanych metod klasy debugowania Generowanie danych wyjściowych do [okno danych wyjściowych](../ide/reference/output-window.md). Bez tego symbolu debugowania metod klasy nie są kompilowane i generowane żadne dane wyjściowe. Ten symbol należy określić w wersji do debugowania i nie jest zdefiniowany w wersji. Definiowanie ten symbol w wersji tworzy niepotrzebne kod, który spowalnia programu.|  
|**Zdefiniuj stała śledzenia**|Definiowanie tego symbolu umożliwia kompilowanie warunkowe funkcji danych wyjściowych z [klasa śledzenia](/dotnet/api/system.diagnostics.trace.aspx). Z tego symbolu zdefiniowanych metod klasy śledzenia Generowanie danych wyjściowych do [okno danych wyjściowych](../ide/reference/output-window.md). Bez tego symbolu metod klasy śledzenia nie są kompilowane i są generowane nie dane wyjściowe śledzenia. Ten symbol jest zdefiniowany zarówno debugującej i zwalniającej mają domyślnie.|  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawienia debugowania i przygotowanie](../debugger/debugger-settings-and-preparation.md)