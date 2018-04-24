---
title: 'Porady: Włącz i Wyłącz Edytuj i Kontynuuj (C#, VB, C++) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /INCREMENTAL linker option
- Apply Code Changes command
- Edit and Continue, disabling
- code changes, applying in break mode
- INCREMENTAL linker option
- Edit and Continue, enabling
- break mode, applying code changes
- Edit and Continue, applying code changes
- Step command
- Go command
ms.assetid: fd961a1c-76fa-420d-ad8f-c1a6c003b0db
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: 9070913d1106eb5e2ca04160ad95c6a6fd46f752
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-enable-and-disable-edit-and-continue-c-vb-c"></a>Porady: Włącz i Wyłącz Edytuj i Kontynuuj (C#, VB, C++)
Można wyłączyć lub włączyć Edytuj i Kontynuuj w **opcje** okno dialogowe w czasie projektowania. Nie można zmienić to ustawienie podczas debugowania.  
  
Edytuj i Kontynuuj działa tylko w przypadku kompilacji do debugowania. Dla natywnych języka C++, Edytuj i Kontynuuj wymaga przy użyciu / incremental — opcja. Aby uzyskać więcej informacji o wymaganiach dotyczących funkcji języka C++, zobacz [wpis w blogu](https://blogs.msdn.microsoft.com/vcblog/2016/07/01/c-edit-and-continue-in-visual-studio-2015-update-3/) i [Edytuj i Kontynuuj (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).
  
#### <a name="to-enabledisable-edit-and-continue"></a>Aby włączyć lub wyłączyć Edytuj i Kontynuuj  
  
1.  Jeśli pracujesz w sesji debugowania, Zatrzymaj debugowanie (**Shift + F5**).

2.  Otwórz stronę opcji debugowania (**Narzędzia > Opcje > debugowanie**).
  
3.  Wybierz **ogólne**i przewiń w dół do **Edytuj i Kontynuuj** kategorii (po prawej).  
  
4.  Aby włączyć, wybierz **włączyć Edytuj i Kontynuuj** pole wyboru. Aby wyłączyć, wyczyść pole wyboru.  
  
    > [!NOTE]
    >  Zbieranie zarówno zdarzeń funkcji IntelliTrace i informacje o wywołaniach IntelliTrace jest włączona, Edytuj i Kontynuuj jest wyłączona. Aby uzyskać więcej informacji, zobacz [IntelliTrace](../debugger/intellitrace.md).

5. (C++) Aby włączyć, wybierz **włączyć natywnego Edytuj i Kontynuuj**. Aby wyłączyć, wyczyść pole wyboru.

6. (C++) Ustaw dodatkowe opcje dla kodu natywnego.

    - **Zastosuj zmiany przy kontynuowaniu (tylko kod natywny)**  
        Visual Studio kompiluje i automatycznie stosuje zmiany kodu oczekujących, wprowadzonych podczas kontynuowanie procesu w stanie przerwania. Nie wybrano można zastosować zmian przy użyciu elementu "Zastosowanie zmian kodu" w menu debugowania.  
  
    - **Ostrzegaj o nieodświeżonym kodzie (tylko kod natywny)**  
        Pobierz ostrzeżenia o kodzie nieodświeżonym. 
  
7.  Kliknij przycisk **OK**.    
  
## <a name="see-also"></a>Zobacz też  
 [Edytuj i Kontynuuj](../debugger/edit-and-continue.md)