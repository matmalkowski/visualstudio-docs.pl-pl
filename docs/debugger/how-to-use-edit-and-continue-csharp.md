---
title: 'Porady: Korzystanie z opcji Edytuj i Kontynuuj (C#) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], about Edit and Continue
ms.assetid: 40e136d8-a08c-43bd-b313-fb821c55eb3c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 587ee3bb7221c0fce82048112945ac8581796d23
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-use-edit-and-continue-c"></a>Porady: korzystanie z opcji edytuj i kontynuuj (C#)
Z opcją Edytuj i Kontynuuj dla języka C# można wprowadzić zmiany w kodzie w trybie przerwania podczas debugowania. Zmiany można zastosować bez konieczności zatrzymać i uruchomić ponownie sesję debugowania.  
  
 Edytuj i Kontynuuj jest wywoływana automatycznie, gdy można wprowadzić zmiany w trybie przerwania, a następnie wybierz wykonywania debugera polecenia, takich jak **Kontynuuj**, **krok**, lub **ustawienia następnej instrukcji**, lub obliczyć wartości funkcji w oknie debugera.  
  
> [!NOTE]
>  Edytuj i Kontynuuj nie jest obsługiwane podczas debugowania zoptymalizowany kod, kod mieszany natywną/zarządzaną lub SQL Server wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) integracji kod. Uzyskać informacji o innych nieobsługiwanych scenariuszy, zobacz [obsługiwane zmiany kodu (C# i Visual Basic)](../debugger/supported-code-changes-csharp.md). Podjęcie próby zastosowania zmian w kodzie w jednym z tych scenariuszy Wyświetla debugera, okno dialogowe pola wyjaśniający, który Edytuj i Kontynuuj nie jest obsługiwane.  
  
### <a name="to-invoke-edit-and-continue-automatically"></a>Aby wywołać Edytuj i Kontynuuj automatycznie  
  
1.  W trybie przerwania zmiany kodu źródłowego.  
  
2.  Z **debugowania** menu, kliknij przycisk **Kontynuuj**, **krok**, lub **ustawienia następnej instrukcji** lub obliczyć wartości funkcji w oknie debugera.  
  
     Nowy kod jest skompilowany i debugowanie kontynuuje nowy kod. Niektóre zmiany nie są obsługiwane przez Edytuj i Kontynuuj. Aby uzyskać więcej informacji, zobacz [obsługiwane zmiany kodu (C# i Visual Basic)](../debugger/supported-code-changes-csharp.md).  
  
### <a name="to-enabledisable-edit-and-continue"></a>Aby włączyć lub wyłączyć Edytuj i Kontynuuj  
  
1.  Na **narzędzia** menu, kliknij przycisk **opcje**.  
  
2.  W **opcje** okna dialogowego rozwiń **debugowanie** , a następnie wybierz węzeł **Edytuj i Kontynuuj**.  
  
3.  W **opcje** okno dialogowe **Edytuj i Kontynuuj** wybierz lub wyczyść **włączyć Edytuj i Kontynuuj** pole wyboru.  
  
     Ustawienie ma obowiązywać po ponownym uruchomieniu sesji debugowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Edytuj i Kontynuuj (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)   
 [Obsługiwane zmiany kodu (C# i Visual Basic)](../debugger/supported-code-changes-csharp.md)   