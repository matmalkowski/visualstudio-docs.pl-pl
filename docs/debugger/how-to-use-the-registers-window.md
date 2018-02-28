---
title: "Wyświetl wartości rejestru w debugerze programu Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.registers
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- registers, debugging
- register contents
- flags, Registers window
- register groups
- debugging [Visual Studio], Registers window
- Registers window
ms.assetid: 2918ffa2-562f-40d6-9053-ef321bbeb767
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 7aa89b6e8d36c3eb47168c8672fb7eea1e3507db
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="view-register-values-and-use-the-registers-window-in-the-visual-studio-debugger"></a>Wyświetl wartości rejestru i korzystanie z okna rejestrów w debugerze programu Visual Studio
Okno rejestrów jest dostępna tylko wtedy, gdy debugowanie poziomie adresu jest włączone w **opcje** okno dialogowe **debugowanie** węzła, **ogólne** kategorii.  
  
 **Rejestruje** zawartość rejestru są wyświetlane. Jeśli zachowasz **rejestruje** okna otwarte podczas wykonywania kroków za pomocą programu, zostanie wyświetlony zmiany wartości rejestru, gdy kod jest wykonywana. Wartości, które zostały zmienione ostatnio są wyświetlane na czerwono. Można edytować wartości rejestru. Aby uzyskać więcej informacji, zobacz [porady: Edytowanie wartości rejestru](../debugger/how-to-edit-a-register-value.md).  
  
 Aby zwiększyć czytelność, **rejestruje** okna organizuje rejestrów w grupach, które różnią się zależnie od platformy i procesora typu. Możesz wyświetlić lub ukryć grup można dowolnie. Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie i ukrywanie grup rejestru](../debugger/how-to-display-and-hide-register-groups.md).  
  
 Ogólne wprowadzenie do pojęć dotyczących rejestrów i z okna rejestrów, zobacz [podstawy debugowania: okno rejestrów](../debugger/debugging-basics-registers-window.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-display-the-registers-window"></a>Aby wyświetlić okno rejestrów  
  
-   Na **debugowania** menu, wybierz **Windows**, a następnie wybierz pozycję **rejestruje**.  
  
     Debuger musi być uruchomione lub w trybie przerwania.  
  
    > [!NOTE]
    >  Informacje rejestru nie są dostępne dla skryptu lub aplikacji SQL.  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawy debugowania: Okno rejestrów](../debugger/debugging-basics-registers-window.md)   
 [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)   
 [Podstawy debugowania: Okno rejestrów](../debugger/debugging-basics-registers-window.md)