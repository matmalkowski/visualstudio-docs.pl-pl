---
title: Wyświetlanie wartości rejestru w debugerze programu Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ceadd2f131a75e01cec67c21dca0d7837b02738a
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551850"
---
# <a name="view-register-values-and-use-the-registers-window-in-the-visual-studio-debugger"></a>Wyświetlanie wartości rejestru i korzystanie z okna rejestrów w debugerze programu Visual Studio
Okno rejestrów jest dostępna tylko wtedy, gdy debugowanie na poziomie adresów jest włączone w **opcje** okno dialogowe **debugowanie** węzła **ogólne** kategorii.  
  
 **Rejestruje** okna wyświetla zawartość rejestru. Jeśli zachowasz **rejestruje** otwarte, jak krok po kroku przez program okno, możesz zobaczyć zmiany wartości rejestru, jak kod jest wykonywany. Wartości, które zostały zmienione ostatnio są wyświetlane w kolorze czerwonym. Możesz edytować wartości rejestru. Aby uzyskać więcej informacji, zobacz [porady: Edytowanie wartości rejestru](../debugger/how-to-edit-a-register-value.md).  
  
 Aby zwiększyć czytelność, **rejestruje** okna organizuje rejestrów w grupach, które zależą od platformy i procesora typu. Można wyświetlić lub ukryć grup, jak chcesz. Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie i ukrywanie grup rejestru](../debugger/how-to-display-and-hide-register-groups.md).  
  
 Ogólne wprowadzenie do pojęć dotyczących rejestrów i z okna rejestrów, zobacz [podstawy debugowania: okno rejestrów](../debugger/debugging-basics-registers-window.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-display-the-registers-window"></a>Aby wyświetlić okno rejestrów  
  
-   Na **debugowania** menu, wybierz **Windows**, a następnie wybierz **rejestruje** (lub wybierz **Ctrl** + **Alt**   +  **G**).  
  
     Debuger musi być uruchomiona lub w trybie przerwania.  
  
    > [!NOTE]
    >  Informacje rejestru nie są dostępne dla skryptu lub aplikacji SQL.  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawy debugowania: Okno rejestrów](../debugger/debugging-basics-registers-window.md)   
 [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)   
 [Podstawy debugowania: okno rejestrów](../debugger/debugging-basics-registers-window.md)