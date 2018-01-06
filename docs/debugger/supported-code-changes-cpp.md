---
title: "Obsługiwane zmiany kodu (C++) | Dokumentacja firmy Microsoft"
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
- Edit and Continue, limitations
- supported code changes
- object files, limitations of Edit and Continue
- C# language, supported code changes
- coding, supported code changes
- resource files, limitations of Edit and Continue
- code changes, handling in Edit and Continue
- what's new [C#], supported code changes
- code changes
ms.assetid: f5754363-8a56-417b-b904-b05d9dd26d03
caps.latest.revision: "26"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8b3ced43c776cc948467d68b2112fb808dd2a48c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="supported-code-changes-c"></a>Obsługiwane zmiany kodu (C++)
Edytuj i Kontynuuj dla języka Visual C++ obsługuje większość typów zmian w kodzie. Jednak niektóre zmiany nie można zastosować podczas wykonywania programu. Aby zastosować te zmiany, należy zatrzymać wykonywania i utworzyć nową wersję kodu.  
  
 Zobacz [Edytuj i Kontynuuj (Visual C++)](../debugger/edit-and-continue-visual-cpp.md) informacje na temat pracy z opcją Edytuj i Kontynuuj dla języka C++ w programie Visual Studio.  
  
##  <a name="BKMK_Unsupported_changes"></a>Nieobsługiwane zmiany  
 Nie można zastosować następujące zmiany w języku C/C++ podczas sesji debugowania:  
  
-   Większość zmian danych globalnych lub statycznych.  
  
-   Zmiany plików wykonywalnych, które są kopiowane z innego komputera i nie utworzony lokalnie.  
  
-   Zmiany do typu danych, które mają wpływ na układ obiektu, takie jak element członkowski danych klasy.  
  
-   Dodawanie więcej niż 64 KB danych lub nowy kod.  
  
-   Dodawanie zmiennych, które wymagają konstruktora w momencie przed wskaźnik instrukcji.  
  
-   Zmiany, które mają wpływ na kod, który wymaga inicjowania środowiska wykonawczego.  
  
-   Dodawanie programów obsługi wyjątków, w niektórych przypadkach.  
  
-   Zmiany plików zasobów.  
  
-   Zmiany kodu w plikach tylko do odczytu.  
  
-   Zmiany kodu bez odpowiedniego pliku PDB.  
  
-   Zmiany kodu, który nie ma obiektu pliku.  
  
 Jeśli jeden te zmiany, a następnie spróbuj zastosować zmian w kodzie, błąd lub ostrzeżenie pojawia się w **dane wyjściowe** okna.  
  
-   Edytuj i Kontynuuj nie aktualizuje bibliotek statycznych. Jeśli wprowadzisz zmiany w bibliotece statycznej wykonywania będzie kontynuowane przy użyciu starej wersji i ostrzeżenie nie jest generowane.  
  
##  <a name="BKMK_Unsupported_scenarios"></a>Nieobsługiwane scenariusze  
 Edytuj i Kontynuuj dla języka C/C++ jest niedostępny w następujących scenariuszach debugowania:  
  
-   Debugowanie aplikacji natywnych skompilowane z [/Zo (zwiększenia zoptymalizowanych pod kątem debugowania)](/cpp/build/reference/zo-enhance-optimized-debugging)  
  
-   W wersjach programu Visual Studio Wstecz, aby Visual Studio 2015 Update 1, debugowania aplikacji platformy uniwersalnej systemu Windows lub składników. Począwszy od programu Visual Studio 2015 Update 1, możesz użyć Edytuj i Kontynuuj w aplikacji platformy uniwersalnej systemu Windows w języku C++ oraz aplikacji DirectX, ponieważ obecnie obsługuje `/ZI` przełącznika kompilatora z `/bigobj` przełącznika. Umożliwia także Edytuj i Kontynuuj z plików binarnych skompilowanych z `/FASTLINK` przełącznika.  
  
-   Debugowanie w systemie Windows 98.  
  
-   Debugowanie trybu mieszanego (natywną/zarządzaną).  
  
-   Debugowanie JavaScript.  
  
-   Debugowanie SQL.  
  
-   Debugowania pliku zrzutu.  
  
-   Edytowanie kodu po wystąpieniu nieobsługiwanego wyjątku, gdy **Odwiń stos wywołań w przypadku nieobsługiwanych wyjątków** nie wybrano opcji.  
  
-   Debugowanie aplikacji przy użyciu **dołączyć do** zamiast uruchamiania aplikacji przez wybranie **Start** na **debugowania** menu.  
  
-   Debugowanie zoptymalizowanego kodu.  
  
-   Debugowanie starą wersję kodu po nowej wersji nie można skompilować z powodu błędów kompilacji.  
  
##  <a name="BKMK_Linking_limitations"></a>Łączenie ograniczenia  
  
###  <a name="BKMK_Linker_options_that_disable_Edit_and_Continue"></a>Opcje konsolidatora wyłączyć Edytuj i Kontynuuj  
 Następujące opcje konsolidatora Wyłącz Edytuj i Kontynuuj:  
  
-   Ustawienie **/OPT:REF**, **/OPT: ICF**, lub **/incremental: No** wyłącza Edytuj i kontynuuj następujące ostrzeżenie:  
  
     ŁĄCZA: ostrzeżenie LNK4075: Ignorowanie/editandcontinue z powodu od  
  
     specyfikacja  
  
-   Ustawienie **/kolejność**, **/RELEASE**, lub **/FORCE** wyłącza Edytuj i Kontynuuj to ostrzeżenie:  
  
     ŁĄCZA: ostrzeżenie LNK4075: Ignorowanie/incremental z powodu/Option  
  
     specyfikacja  
  
-   Ustawienie każda opcja, która uniemożliwia tworzenie pliku bazy danych (.pdb) program wyłącza Edytuj i Kontynuuj bez określone ostrzeżenia.  
  
###  <a name="BKMK_Auto_relinking_limitations"></a>Automatyczne ponowne łączenie ograniczenia  
 Domyślnie Edytuj i Kontynuuj relinks programu z końcem sesji debugowania, aby utworzyć plik wykonywalny aktualne.  
  
 Edytuj i Kontynuuj nie może ponownie połączyć program Jeśli debugowany z lokalizacji innych niż do oryginalnej lokalizacji kompilacji. Komunikat informuje, należy odbudować ręcznie.  
  
 Edytuj i Kontynuuj nie odbudować bibliotek statycznych. Jeśli wprowadzisz zmiany w bibliotece statycznej przy użyciu Edytuj i Kontynuuj, musisz ręcznie odbudować aplikacje biblioteki i ponowna konsolidacja za jego pomocą.  
  
 Edytuj i kontynuuj nie wywołuje niestandardowych kroków kompilacji. Jeśli program używa niestandardowych kroków kompilacji, można ponownie skompilować ręcznie, aby można było wywołać niestandardowe kroki kompilacji. W takim przypadku, można wyłączyć ponowne połączenie po wykonaniu Edytuj i kontynuuj, aby zapewnić, że zostaniesz poproszony o ponowną kompilację ręczną.  
  
 **Aby wyłączyć, ponowne łączenie po Edytuj i Kontynuuj**  
  
1.  Na **debugowania** menu, wybierz **opcje i ustawienia**.  
  
2.  W **opcje** okna dialogowego, w obszarze **debugowanie** , a następnie wybierz węzeł **Edytuj i Kontynuuj** węzła.  
  
3.  Wyczyść **Konsoliduj ponownie zmiany kodu po debugowaniu** pole wyboru.  
  
##  <a name="BKMK_Precompiled_Header_Limitations"></a>Ograniczenia prekompilowanego nagłówka  
 Domyślnie Edytuj i Kontynuuj prekompilowanych nagłówków obciążeń i procesy w tle w celu przyspieszenia przetwarzania zmian w kodzie. Ładowanie prekompilowanych nagłówków wymaga alokacji pamięci fizycznej, może to stanowić problem, jeśli kompilacja na maszynie z ograniczoną ilością pamięci RAM. Można określić, czy może to być spowodowane problemem za pomocą Menedżera zadań systemu Windows, aby określić ilość dostępnej pamięci fizycznej podczas debugowania. Jeśli ta liczba jest większa niż rozmiar prekompilowanych nagłówków, nie powinny wystąpić problemy w trybie Edytuj i kontynuuj. Jeśli wartość jest mniejsza niż rozmiar nagłówków prekompilowanych, uniemożliwi Edytuj i Kontynuuj ładowania prekompilowanych nagłówków w tle.  
  
 **Aby wyłączyć ładowanie tła nagłówków prekompilowanych Edytuj i Kontynuuj**  
  
1.  Na **debugowania** menu, wybierz **opcje i ustawienia**.  
  
2.  W **opcje** okna dialogowego, w obszarze **debugowanie** , a następnie wybierz węzeł **Edytuj i Kontynuuj** węzła.  
  
3.  Wyczyść **Zezwalaj Prekompilowanie** pole wyboru.  
  
##  <a name="BKMK_IDL_Attribute_Limitations"></a>Ograniczenia dotyczące atrybutów języka IDL  
 Edytuj i Kontynuuj nie ponownie wygenerować pliki definicji (IDL) interfejsu. W związku z tym zmiany atrybutów pliku IDL nie zostaną uwzględnione, podczas debugowania. Aby zobaczyć efekt zmian atrybuty IDL, musisz zatrzymać debugowanie i skompiluj ponownie aplikację. Edytuj i Kontynuuj nie generuje błąd lub ostrzeżenie, jeśli atrybuty IDL zostały zmienione. Aby uzyskać więcej informacji, zobacz [atrybuty IDL](/cpp/windows/idl-attributes).  
  
## <a name="see-also"></a>Zobacz też  
 [Edytuj i kontynuuj (Visual C++)](../debugger/edit-and-continue-visual-cpp.md)