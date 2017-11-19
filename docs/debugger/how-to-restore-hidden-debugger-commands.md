---
title: "Porady: Przywracanie ukrytych poleceń debugera | Dokumentacja firmy Microsoft"
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
- JScript
helpviewer_keywords:
- debugger, restoring commands
- debugging [Visual Studio], restoring commands
- commands, debugger
ms.assetid: 76ac9b77-f536-43b5-a9fc-984854b1c566
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 561fa92e9797bd3a4343a4f2c6e23bd1e91ccab0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-restore-hidden-debugger-commands"></a>Porady: przywracanie ukrytych poleceń debugera
Podczas konfigurowania programu Visual Studio, zostanie wyświetlona prośba o wybranie zestaw domyślnych ustawień IDE podstawowy język programowania. Domyślne ustawienia IDE w przypadku niektórych języków może ukryć niektórych poleceń debugera.  
  
 Jeśli chcesz korzystać z funkcji debugera, który jest ukryty przez ustawienia domyślne IDE, można dodać polecenia do menu za pomocą poniższej procedury.  
  
### <a name="to-restore-hidden-debugger-commands"></a>Aby przywrócić ukrytych poleceń debugera  
  
1.  Z projektem otwarty na **narzędzia** menu, kliknij przycisk **Dostosuj**.  
  
2.  W **Dostosuj** okno dialogowe, kliknij przycisk **polecenia** kartę.  
  
3.  W **paska Menu:** listy rozwijanej, wybierz pozycję **debugowania** menu, które ma zawierać polecenia przywrócone.  
  
4.  Kliknij przycisk **Dodaj polecenie...**  przycisku.  
  
5.  W **polecenia Add** wybierz polecenie, które chcesz dodać, a następnie kliknij przycisk **OK**.  
  
6.  Powtórz poprzedni krok, aby dodać innego polecenia.  
  
7.  Kliknij przycisk **Zamknij** po ukończeniu Dodawanie poleceń do menu.  
  
    > [!WARNING]
    >  Niektóre elementy menu są wyświetlane, gdy debuger jest w trybach określonych, takie jak tryb uruchamiania lub w trybie przerwania. W związku z tym dodanego elementu nie można od razu widoczne po wykonaniu tych kroków.  
  
## <a name="restoring-commands-not-available-from-the-customize-dialog-box"></a>Przywracanie poleceń nie jest dostępna w oknie dialogowym Dostosuj  
 Nie można przywrócić niektórych poleceń, zwłaszcza tych, które w menu hierarchiczna z **Dostosuj** okno dialogowe. Aby przywrócić te polecenia, należy zaimportować nową kolekcję ustawień IDE.  
  
#### <a name="to-import-new-ide-settings"></a>Aby zaimportować nowe ustawienia IDE  
  
1.  Na **narzędzia** menu, kliknij przycisk **Import i eksport ustawień**.  
  
2.  Na **Kreator importowania i eksportowania ustawień-Zapraszamy** kliknij przycisk **Importuj wybrane ustawienia środowiska**, a następnie kliknij przycisk **dalej**.  
  
3.  Na **zapisać bieżące ustawienia** zdecyduj, czy chcesz zapisać Twoje istniejące ustawienia, a następnie kliknij pozycję **dalej**.  
  
4.  Na **wybierz kolekcję ustawień do zaimportowania** w obszarze **ustawienia domyślne** folderu, wybierz kolekcję ustawień środowiska ma polecenia, którego chcesz użyć. Jeśli nie wiadomo, które kolekcji, spróbuj **ogólne ustawienia środowiska deweloperskiego** lub **ustawienia środowiska deweloperskiego w usłudze Visual C++**, które zapewniają najbardziej poleceń debugera.  
  
5.  Kliknij przycisk **Dalej**.  
  
6.  Na **wybierz ustawienia do importowania** w obszarze **opcje**, upewnij się, że **debugowanie** jest zaznaczone. Usuń zaznaczenie innych pól wyboru, chyba że chcesz zaimportować te ustawienia, a także.  
  
7.  Kliknij przycisk **Zakończ**.  
  
8.  Na **pełny Import** Przejrzyj błędy skojarzone z Resetowanie ustawień w obszarze **szczegóły**.  
  
9. Kliknij przycisk **Zamknij**.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Podstawowe informacje o debugerze](../debugger/debugger-basics.md)