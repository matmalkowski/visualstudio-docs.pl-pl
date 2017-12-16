---
title: "Projekt ustawienia konfiguracji debugowania w języku C# | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "22"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d588f43271b127c675a6ec2fdf9e55ef388eadf2
ms.sourcegitcommit: 1e08318a8a684b21609af7a5e48b56abcc3239e6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/13/2017
---
# <a name="project-settings-for--c-debug-configurations"></a>Ustawienia projektu dla konfiguracji debugowania w C#
Możesz zmienić ustawienia projektu dla konfiguracji debugowania C# w **strony właściwości** okna, zgodnie z opisem w [konfiguracji Debug i Release](../debugger/how-to-set-debug-and-release-configurations.md). W poniższych tabelach przedstawiono gdzie można znaleźć ustawień debugera w **strony właściwości** okna.  
  
> [!WARNING]
>  Ten temat nie dotyczy aplikacji platformy uniwersalnej systemu Windows i Windows 8.1. Zobacz [rozpocząć sesję debugowania: (VB, C#, C++ i XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
##  <a name="BKMK_Debug_tab"></a>Karta debugowania  
  
|**Ustawienie**|**Opis**|  
|-----------------|---------------------|  
|**Konfiguracja**|Ustawia tryb dla kompilowania aplikacji. Wybierz spośród **aktywny (debugowanie)**, **debugowania**, **wersji**, **wszystkie konfiguracje**.|  
|**Uruchomienie akcji**|Ta grupa formantów Określa akcję, która ma miejsce, gdy wybierzesz Start z menu Debugowanie.<br /><br /> -   **Uruchom projekt** jest ustawieniem domyślnym i uruchamia projekt startowy do debugowania. Aby uzyskać więcej informacji, zobacz [Wybieranie projekt startowy](http://msdn.microsoft.com/en-us/222e3f32-a6fe-4941-bf37-6b2a921129fd).<br />-   **Uruchom program zewnętrznych** umożliwia start i Dołącz do programu, który nie jest częścią [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektu. Aby uzyskać więcej informacji, zobacz [dołączanie do uruchamiania programu](http://msdn.microsoft.com/en-us/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4).<br />-   **Uruchom przeglądarkę w adresie URL** pozwala na debugowanie aplikacji sieci Web.|  
|**Argumenty wiersza polecenia**|Określa argumenty wiersza polecenia dla programu do debugowania. Nazwa polecenia jest nazwa programu określone w uruchomienia programu zewnętrznego. Jeśli akcja uruchamiania początkowy adres URL nie można określić argumentów wiersza polecenia.|  
|**Katalog roboczy**|Określa katalog roboczy debugowany program. W [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], katalog roboczy jest katalogiem, aplikacja jest uruchamiana z \bin\debug domyślnie.|  
|**Użyj komputera zdalnego**|Nazwa komputera zdalnego, gdy aplikacja będzie uruchamiana na potrzeby debugowania lub [nazwy serwera polecenia Msvsmon](../debugger/remote-debugging.md). Lokalizacja pliku exe na komputerze zdalnym jest określony przez właściwość ścieżki wyjściowej w folderze właściwości konfiguracji kompilacji kategorii. Lokalizacja musi być możliwe do udostępnienia katalog na komputerze zdalnym.|
|**Włącz debugowanie kodu niezarządzanego**|Umożliwia debugowanie wywołania do kodu natywnego Win32 (niezarządzany) z zarządzanych aplikacji.|  
|**Włącz debugowanie serwera SQL**|Pozwala na debugowanie obiektów bazy danych programu SQL Server.|  
  
##  <a name="BKMK_Build_tab"></a>Karta kompilacji  
  
|Ustawienie|Opis|  
|-------------|-----------------|  
|**Symbole kompilacji warunkowej:**|Stałe debugowania i śledzenia są zdefiniowane w tym miejscu.<br /><br /> Kompilacja warunkowa z Włącz te stałe [Klasa Debug](/dotnet/api/system.diagnostics.debug) i [klasa śledzenia](/dotnet/api/system.diagnostics.trace). Za pomocą tych stałych zdefiniowane, debugowania i śledzenia metod klasy Generowanie danych wyjściowych do [okno danych wyjściowych](../ide/reference/output-window.md). Bez tych stałe debugowania i śledzenia metod klasy nie są kompilowane i generowane żadne dane wyjściowe.<br /><br /> -Debug jest zazwyczaj zdefiniowane w wersji do debugowania programu i w wersji.<br />-Śledzenia zwykle jest zdefiniowany w wersji zarówno Debug i Release.|  
|**Optymalizacja kodu**|Jeśli nie możesz znaleźć usterkę, która jest wyświetlana tylko w zoptymalizowanym kodzie, należy pozostawić to ustawienie wyłączone w wersji do debugowania. Kod zoptymalizowany jest trudniej debugowania, ponieważ nie odpowiadają instrukcje bezpośrednio do instrukcji w oknach źródła.|  
|**Ścieżka wyjściowa:**|Zwykle ustawiana na bin\Debug do debugowania.|

> [!NOTE]
> Aby uzyskać więcej informacji na temat opcji debugowania, możesz znaleźć w **zaawansowane** przycisku, zobacz [okno dialogowe Zaawansowane ustawienia kompilacji (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md). Format przenośnej plików symboli (.pdb) jest najnowszych format i platform .NET Core. 
  
## <a name="see-also"></a>Zobacz też  
 [Ustawienia debugowania i przygotowanie](../debugger/debugger-settings-and-preparation.md)