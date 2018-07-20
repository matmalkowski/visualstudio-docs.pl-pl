---
title: Ustawienia dla konfiguracji debugowania w języku C# projektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debug configurations, C#
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debugging [C#], debugger settings
ms.assetid: e30ca810-66e9-4d6e-9cf6-9f285cd0b100
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 043bd6e2c97ad3785ab783456fc911334d3d6cd0
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153692"
---
# <a name="project-settings-for--c-debug-configurations"></a>Ustawienia projektu dla konfiguracji debugowania w C#
Możesz zmienić ustawienia projektu dla konfiguracji debugowania języka C# w **stron właściwości** zgodnie z opisem w oknie [konfiguracji Debug i Release](../debugger/how-to-set-debug-and-release-configurations.md). W poniższej tabeli przedstawiono, gdzie można znaleźć ustawienia związane z debugerem w **stron właściwości** okna.  
  
> [!WARNING]
>  W tym temacie nie ma zastosowania do aplikacji platformy uniwersalnej systemu Windows. Zobacz [uruchomić sesję debugowania (VB, C#, C++ i XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
##  <a name="BKMK_Debug_tab"></a> Debugowanie kartę  
  
|**Ustawienie**|**Opis**|  
|-----------------|---------------------|  
|**Konfiguracja**|Ustawia tryb do kompilowania aplikacji. Można wybrać jedną z **aktywna (debugowanie)**, **debugowania**, **wersji**, **wszystkie konfiguracje**.|  
|**Akcja uruchamiania**|Ta grupa formantów Określa akcję, która ma miejsce, gdy z menu debugowanie wybierz przycisk Start.<br /><br /> -   **Rozpocznij projekt** jest ustawieniem domyślnym i uruchamia projekt startowy do debugowania. Aby uzyskać więcej informacji, zobacz [Wybieranie projektu startowego](http://msdn.microsoft.com/en-us/222e3f32-a6fe-4941-bf37-6b2a921129fd).<br />-   **Uruchom zewnętrzny program** pozwala uruchomić i Dołącz do programu, który nie jest częścią [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektu. Aby uzyskać więcej informacji, zobacz [dołączanie do uruchamiania programu](http://msdn.microsoft.com/en-us/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4).<br />-   **Uruchom przeglądarkę w adresie URL** umożliwia debugowanie aplikacji sieci Web.|  
|**Argumenty wiersza polecenia**|Określa argumenty wiersza polecenia dla programu do debugowania. Nazwa polecenia jest nazwa programu, określone w uruchomienia programu zewnętrznego. Jeśli akcja uruchamiania jest ustawiony na początkowy adres URL, nie można określić argumenty wiersza polecenia.|  
|**Katalog roboczy**|Określa katalog roboczy debugowanego programu. W [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], katalog roboczy jest katalog, aplikacja zostanie uruchomiona z \bin\debug domyślny.|  
|**Użyj komputera zdalnego**|Nazwa komputera zdalnego, gdy aplikacja zostanie uruchomiona na potrzeby debugowania lub [nazwy serwera Msvsmon](../debugger/remote-debugging.md). Lokalizacja pliku EXE na komputerze zdalnym jest określona przez właściwość ścieżkę wyjściową w folderze właściwości konfigurowania kategorii kompilacji. Lokalizacja musi być możliwe do udostępnienia katalogu na komputerze zdalnym.|
|**Włącz debugowanie kodu niezarządzanego**|Umożliwia debugowanie wywołań do kodu natywnego (niezarządzanego) Win32 z zarządzanych aplikacji.|  
|**Włącz debugowanie programu SQL Server**|Umożliwia debugowanie obiektów bazy danych programu SQL Server.|  
  
##  <a name="BKMK_Build_tab"></a> Tworzenie karty  
  
|Ustawienie|Opis|  
|-------------|-----------------|  
|**Symbole kompilacji warunkowej:**|Stałe debugowania i śledzenia są zdefiniowane w tym miejscu.<br /><br /> Te stałe Włącz kompilację warunkową [Klasa Debug](/dotnet/api/system.diagnostics.debug) i [klasa śledzenia](/dotnet/api/system.diagnostics.trace). Za pomocą tych zdefiniowanych stałych, debugowania i śledzenia metod klasy generują dane wyjściowe do [okno danych wyjściowych](../ide/reference/output-window.md). Bez tych stałe debugowania i śledzenia metod klasy nie są kompilowane i generowane żadne dane wyjściowe.<br /><br /> -Debug jest zwykle zdefiniowane w wersji debugowania programu i niezdefiniowana w pełnej wersji.<br />-Śledzenia jest zwykle definiowany w wersjach zarówno Debug i Release.|  
|**Optymalizuj kod**|Jeśli nie możesz znaleźć usterkę, która pojawia się tylko w zoptymalizowanym kodzie, należy pozostawić to ustawienie wyłączone w wersji do debugowania. Zoptymalizowany kod jest trudniejszy do debugowania, ponieważ instrukcje nie odpowiadają bezpośrednio do instrukcji w źródłowych z systemem windows.|  
|**Ścieżka wyjściowa:**|Ustaw zazwyczaj bin\Debug do debugowania.|

> [!NOTE]
> Aby uzyskać więcej informacji na temat opcji debugowania, możesz znaleźć w **zaawansowane** przycisk, zobacz [okno dialogowe Zaawansowane ustawienia kompilacji (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md). Przenośne format plików symboli (.pdb) jest najbardziej aktualną format dla wielu platform .NET Core. 
  
## <a name="see-also"></a>Zobacz też  
 [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)