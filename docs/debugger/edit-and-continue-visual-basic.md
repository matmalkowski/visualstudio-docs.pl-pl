---
title: Edytuj i Kontynuuj (Visual Basic) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/11/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue, 64-bit
- Edit and Continue [Visual Basic]
- debugging [Visual Basic], Edit and Continue
- Visual Basic, Edit and Continue
- 64-bit Edit and Continue
ms.assetid: 7e90f34f-e699-45ab-a4c9-a4b527c498c8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aa3b8c287129c164d8c6984ac52375d6012fbd68
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="edit-and-continue-visual-basic"></a>Edytuj i kontynuuj (Visual Basic)
Edytuj i Kontynuuj jest funkcją [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] debugowania, który umożliwia zmianę kodu podczas wykonywania w trybie przerwania. Po zastosowaniu edycji kodu można wznowić wykonywanie kodu nowe edycji w miejscu i zobaczyć efekt.  
  
 Można użyć edycji i kontynuowania funkcji zawsze, gdy tryb przerwania. W trybie przerwania, wskaźnik instrukcji, żółty grot strzałki w oknie źródła wskazuje na wiersz zawierający instrukcji wykonywalnej w treści metody lub właściwości, które zostaną wykonane dalej.

 Edytuj i Kontynuuj obsługuje większość zmian, które można wybrać podczas sesji debugowania, ale istnieją pewne wyjątki. Aby uzyskać więcej informacji, zobacz [obsługiwane zmiany kodu (C# i Visual Basic)](../debugger/supported-code-changes-csharp.md).   
  
 Po wprowadzeniu nieautoryzowanego edycji, zmiana jest oznaczony atrybutem purpurowa faliste podkreślenie i zadania jest wyświetlana na liście zadań. Jeśli chcesz nadal używać Edytuj i Kontynuuj, musisz cofnąć nieautoryzowanego edycji. Może być dozwolony pewnych nieautoryzowanych zmian, jeśli będą wykonywane poza Edytuj i Kontynuuj. Jeśli chcesz zachować wyniki nieautoryzowanego edycji, należy zatrzymać debugowanie i ponownie uruchom aplikację.  
  
 Edytuj i Kontynuuj jest obsługiwana w aplikacji platformy uniwersalnej systemu Windows dla systemu Windows 10 i x86 i x64 aplikacji przeznaczonych dla platformy .NET Framework 4.6 pulpitu lub nowszej wersji (.NET Framework jest tylko wersja desktop).

 > [!NOTE]
 > Nieobsługiwany aplikacji i platform obejmują ASP.NET 5, Silverlight 5 i Windows 8.1.
  
 Edytuj i Kontynuuj nie jest obsługiwana po rozpoczęciu debugowania przy użyciu **dołączyć do procesu**. Edytuj i Kontynuuj nie jest obsługiwana dla zoptymalizowanego kodu lub mieszane kodu zarządzanego i natywnego. Aby uzyskać więcej informacji, zobacz [obsługiwane zmiany kodu (C# i Visual Basic](../debugger/supported-code-changes-csharp.md).
  
 Tematy w tej sekcji zawierają dodatkowe szczegóły dotyczące sposobu używania tej funkcji i jakie zmiany są niedozwolone.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Porady: zastosowanie edytowania w trybie przerwania z opcją Edytuj i Kontynuuj](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md)  
 Wyjaśnia sposób stosowania zmian kodu w trybie przerwania.  
  
 [Obsługiwane zmiany kodu (C# i Visual Basic](../debugger/supported-code-changes-csharp.md)   
 W tym artykule opisano, jakie typy zmiany nie mogą być wykonywane w [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)] Edytuj i Kontynuuj.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Edytuj i Kontynuuj](../debugger/edit-and-continue.md)  
 Zawiera listę tematów po Edytuj i Kontynuuj.