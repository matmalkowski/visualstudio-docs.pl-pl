---
title: Edytuj i Kontynuuj — okno dialogowe komunikat błędu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 06/22/2017
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.ENC.SupportedButNotAvaiable
- vs.debug.ENC.CannotEditWhileException
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue Error Message dialog box
ms.assetid: f98c91c0-447a-4533-85b6-87170a0dc4c3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5b521eafcc62a49f2dd2a4c327158070bdbe62ce
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31471840"
---
# <a name="edit-and-continue-error-message-dialog-box"></a>Komunikat o błędzie Edytuj i kontynuuj — Okno dialogowe
To okno dialogowe pojawia się podczas debugowania w języku, który obsługuje Edytuj i Kontynuuj, ale **Edytuj i Kontynuuj** nie jest dostępna tylko dla typu zmiany kodu zostały wykonane. Komunikat o błędzie wewnątrz pola zawiera bardziej szczegółowy opis. Możliwe przyczyny przy przeglądaniu to okno dialogowe, które obejmują:  

-   Próbowano edytować kod programu SQL Server.

-   Próbowano edytować zoptymalizowanego kodu. (Może być konieczne przełączyć się z kompilacji wydania do kompilacji debugowanej).

-   Próbowano edytować kodu została uruchomiona (zamiast podczas wstrzymaniu w debugerze). Spróbuj [ustawienia punktu przerwania](../debugger/using-breakpoints.md) i Edycja kodu podczas wstrzymania.

-   Próbowano edytować kodu zarządzanego gdy włączono debugowanie niezarządzane. Edytuj i Kontynuuj nie działa z [debugowanie w trybie mieszanym](../debugger/how-to-debug-in-mixed-mode.md).

-   Wprowadzone zmiany kodu, który nie jest obsługiwany przez Edytuj i Kontynuuj języka programowania. Aby uzyskać więcej informacji, zobacz Tematy nieobsługiwany kod zmiany w [C#](../debugger/supported-code-changes-csharp.md), [Visual Basic](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md), i [C++](../debugger/supported-code-changes-cpp.md).
  
-   Próbowano edytować kodu w programie dołączonego do zamiast od **debugowania** menu.  
  
-   Próbowano edytować kodu podczas debugowania odzyskiwania po awarii. Watson zrzutu.  
  
-   Próbowano edytować kod po Wystąpił nieobsługiwany wyjątek i opcję "**Odwiń stos wywołań w przypadku nieobsługiwanych wyjątków**" nie zostały wybrane.  
  
-   Próbowano edytować kodu podczas debugowania aplikacji osadzonych środowiska wykonawczego.
  
-   Próbowano edytować kodu zarządzanego za pomocą .NET Framework w wersji przed 4.5.1 i obiekt docelowy jest aplikacją 64-bitową. Jeśli chcesz Użyj Edytuj i Kontynuuj, musisz ustawić dla obiektu docelowego x86. (*projectname* **właściwości**, **skompilować** karcie **zaawansowane kompilatora** ustawienie.).  
  
-   Próbowano edytować kod w zestawie, do którego został zmodyfikowany podczas debugowania i został ponownie załadowany.  
  
-   Próbowano edytować kod w zestawie, który nie został załadowany.  
  
-   Można uruchomić debugowania starą wersję aplikacji (ponieważ nowa wersja ma błędy kompilacji).
  
## <a name="uielement-list"></a>Lista elementów UI  
 **OK**  
 Zamknij okno dialogowe i anulować bezpośrednio poprzednie próbę edycji.  
  
## <a name="see-also"></a>Zobacz też  
 [C++, Edytuj i Kontynuuj blogu post](https://blogs.msdn.microsoft.com/vcblog/2016/07/01/c-edit-and-continue-in-visual-studio-2015-update-3/)  
 [Obsługiwane zmiany kodu (C++)](../debugger/supported-code-changes-cpp.md)