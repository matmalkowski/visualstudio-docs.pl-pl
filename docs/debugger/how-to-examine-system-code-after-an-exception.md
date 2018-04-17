---
title: 'Porady: Badanie kodu systemu po wystąpieniu wyjątku | Dokumentacja firmy Microsoft'
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
- debugging, exceptions
- exceptions, debugging
ms.assetid: a38ad49b-7cf3-483d-91c4-eb3116eba50c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2914aab911d3c700b38c58eac009b2e21e94420e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-examine-system-code-after-an-exception"></a>Porady: badanie kodu systemu po wystąpieniu wyjątku
Po wystąpieniu wyjątku, może być konieczne zbadanie kodu wewnątrz wywołania systemu, aby ustalić przyczynę tego wyjątku. W poniższej procedurze wyjaśniono, jak to zrobić, jeśli nie masz symbole załadowany na potrzeby kod systemu lub jeśli włączono opcję tylko mój kod.  
  
### <a name="to-examine-system-code-following-an-exception"></a>Aby badanie kodu systemu po wyjątku  
  
1.  W **stos wywołań** okna, kliknij prawym przyciskiem myszy, następnie kliknij przycisk **Pokaż kod zewnętrzny**.  
  
     Jeśli nie włączono opcję tylko mój kod, ta opcja nie jest dostępne w menu skrótów i kod systemu jest wyświetlany domyślnie.  
  
2.  Kliknij prawym przyciskiem myszy ramek zewnętrznego kodu, które pojawiają się teraz **stos wywołań** okna.  
  
3.  Wskaż **Załaduj symbole z** , a następnie kliknij przycisk **serwerów symboli firmy Microsoft**.  
  
    1.  Jeśli włączono opcję tylko mój kod, zostanie wyświetlone okno dialogowe. Stany go, że tylko mój kod teraz został wyłączony. Jest to niezbędne do Wkraczanie do wywołań systemowych.  
  
    2.  **Pobieranie symboli publicznych** zostanie wyświetlone okno dialogowe. Zniknie po zakończeniu pobierania.  
  
4.  Teraz można sprawdzić kod systemu w **stos wywołań** oknami. Na przykład możesz kliknąć dwukrotnie ramki stosu wywołań, aby wyświetlić kod w źródle lub **dezasemblacji** okna.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie wyjątkami za pomocą debugera](../debugger/managing-exceptions-with-the-debugger.md)