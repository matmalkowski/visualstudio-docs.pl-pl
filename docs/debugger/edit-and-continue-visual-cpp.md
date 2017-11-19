---
title: Edytuj i Kontynuuj (Visual C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 05/31/2017
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
- Edit and Continue [C++]
- debugging [C++], Edit and Continue
- C/C++, Edit and Continue
ms.assetid: 1815251e-a877-433e-9e5e-69bd9ba254c7
caps.latest.revision: "25"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c7099fdc72bc93d86d49727eb782d2fd072ec1e1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="edit-and-continue-visual-c"></a>Edytuj i kontynuuj (Visual C++)
Edytuj i Kontynuuj można użyć w projektach Visual C++. Zobacz [obsługiwane zmiany kodu (C++)](../debugger/supported-code-changes-cpp.md) informacji o ograniczeniach operacji Edytuj i Kontynuuj.
  
Aby uzyskać więcej informacji o usprawnieniach Visual Studio 2015 Update 3, zobacz [C++ Edytuj i Kontynuuj w Visual Studio 2015 Update 3](https://blogs.msdn.microsoft.com/vcblog/2016/07/01/c-edit-and-continue-in-visual-studio-2015-update-3/).  
  
 [/Zo (zwiększenia zoptymalizowanych pod kątem debugowania)](/cpp/build/reference/zo-enhance-optimized-debugging) opcję kompilatora, która została wprowadzona w programie Visual Studio 2013 Update 3 dodaje dodatkowe informacje do plików PDB (symbol) plików binarnych skompilowany bez [/Od (Wyłącz (Debuguj)) ](http://msdn.microsoft.com/library/aafb762y.aspx) opcji.  
  
 **/ZO** wyłącza Edytuj i Kontynuuj. Zobacz [porady: debugowanie zoptymalizowanego kodu](../debugger/how-to-debug-optimized-code.md).  
  
##  <a name="BKMK_Enable_or_disable_automatic_invocation_of_Edit_and_Continue"></a>Włącz lub wyłącz Edytuj i Kontynuuj  
 Możesz wyłączyć automatyczne wywołania operacji Edytuj i Kontynuuj w przypadku wprowadzania zmian do kodu, który nie ma zostać zastosowane podczas bieżącej sesji debugowania. Można także ponownie włączyć automatyczne Edytuj i Kontynuuj.

> [!IMPORTANT]
> Ustawienia kompilacji wymagane i inne informacje o funkcji zgodności, zobacz [C++ Edytuj i Kontynuuj w Visual Studio 2015 Update 3] (https://blogs.msdn.microsoft.com/vcblog/2016/07/01/c-edit-and-continue-in-visual-studio-2015-update-3/.
  
1.  Jeśli pracujesz w sesji debugowania, Zatrzymaj debugowanie (**Shift + F5**).

2. Na **narzędzia** menu, wybierz **opcje**.
  
3.  W **opcje** okno dialogowe, wybierz opcję **debugowanie > Ogólne**.

4.  Aby włączyć, wybierz **włączyć Edytuj i Kontynuuj**. Aby wyłączyć, wyczyść pole wyboru.
  
5.  W **Edytuj i Kontynuuj** grupy, wybierz lub wyczyść **włączyć natywnego Edytuj i Kontynuuj** pole wyboru.  
  
 Zmieniając to ustawienie ma wpływ na wszystkie projekty, które działają w. Nie trzeba odbudować aplikacji po zmianie tego ustawienia. Jeśli tworzysz aplikację z wiersza polecenia lub pliku reguł programu make, ale debugowania w środowisku Visual Studio, można nadal używać Edytuj i Kontynuuj po ustawieniu **/zi** opcji.  
  
##  <a name="BKMK_How_to_apply_code_changes_explicitly"></a>Sposób jawnie stosowania zmian kodu  
 W programie Visual C++ Edytuj i Kontynuuj można zastosować zmian w kodzie na dwa sposoby. Kod zmiany można zastosować niejawnie, po wybraniu polecenia wykonywania lub jawnie, przy użyciu **zastosowanie zmian kodu** polecenia.  
  
 Gdy jawnie zastosowania zmian w kodzie programu pozostaje w trybie przerwania — nie jest wykonywany.  
  
-   Aby zastosować zmiany kodu jawnie, na **debugowania** menu, wybierz **zastosowanie zmian kodu**.  
  
##  <a name="BKMK_How_to_stop_code_changes"></a>Zatrzymywanie zmian kodu  
 Edytuj i Kontynuuj jest w trakcie stosowania zmian kodu, można zatrzymać operacji.  
  
 Aby zatrzymać stosowanie zmian kodu:  
  
-   Na **debugowania** menu, wybierz **Zatrzymaj stosowanie zmian kodu**.  
  
 Ten element menu jest widoczny tylko wtedy, gdy Trwa stosowanie zmian kodu.  
  
 Jeśli wybierzesz tę opcję, żaden zmian kodu nie jest zatwierdzona.  
  
##  <a name="BKMK_How_to_reset_the_point_of_execution"></a>Jak można zresetować punktu wykonania  
 Niektóre zmiany kodu może spowodować punktu wykonywania można przenieść do nowej lokalizacji, gdy Edytuj i Kontynuuj stosuje te zmiany. Edytuj i Kontynuuj umieszcza punktu wykonania jak to możliwe, ale wyniki mogą być niepoprawne we wszystkich przypadkach.  
  
 W programie Visual C++ okno dialogowe informujące podczas zmiany punktu wykonania. Należy sprawdzić, czy lokalizacja jest poprawna, przed kontynuowaniem debugowania. Jeśli nie jest poprawny, użyj **ustawienia następnej instrukcji** polecenia. Aby uzyskać więcej informacji, zobacz [ustawi następną instrukcję do wykonania](http://msdn.microsoft.com/library/y740d9d3.aspx#BKMK_Set_the_next_statement_to_execute).  
  
##  <a name="BKMK_How_to_work_with_stale_code"></a>Jak pracować z kod nieodświeżony  
 W niektórych przypadkach Edytuj i Kontynuuj nie może od razu Zastosuj zmiany kodu do pliku wykonywalnego, ale można było zastosować zmiany kodu później, w przypadku kontynuowania debugowania. Dzieje się tak po zmodyfikowaniu funkcję, która wywołuje bieżącej funkcji lub jeśli dodasz więcej niż 64 bajtów zmiennych nowych funkcji w stosie wywołań  
  
 W takich przypadkach Debuger kontynuuje wykonywanie oryginalnego kodu do czasu zmiany można zastosować. Kod nieodświeżony jest wyświetlany jako okno pliku tymczasowego źródła, w oknie oddzielne źródło, z tytułem takich jak `enc25.tmp`. Edytowany źródła w dalszym ciągu są wyświetlane w oknie oryginalnego źródła. Jeśli próbujesz edytować kod nieodświeżony, pojawi się ostrzeżenie.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługiwane zmiany kodu (C++)](../debugger/supported-code-changes-cpp.md)