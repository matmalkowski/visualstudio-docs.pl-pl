---
title: Microsoft Office Word klawiatury, ustawienia klawiatury Microsoft Office, opcje ― Okno dialogowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Word.Keyboard
- VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Word_Keyboard
- VST.WordOptions.KeyboardMappingScheme
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- keyboard shortcuts, Office development in Visual Studio
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9edd5cd987eb6a4e93b02c8e774adefbc7f969d2
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572114"
---
# <a name="microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>Microsoft Office Word klawiatura, ustawienia klawiatury Microsoft Office — okno dialogowe
  Program Microsoft Word pakietu Office i programu Visual Studio zarówno obsługi klawiszy skrótów. Inne polecenia w programie Word i w programie Visual Studio może zastąpić tej samej kombinacji klawiszy skrótów. Gdy program Word jest otwarty w projektach na poziomie dokumentu w programie Visual Studio, tylko jedną aplikację naraz odbiera poleceń klawiszy skrótów. Domyślnie program Visual Studio odbiera wszystkie polecenia klawiszy skrótu, ale można wprowadzić ich odbierania, gdy dokument ma fokus, wybierając Word **schemat klawiatury dynamiczne**.  
  
 Jeśli używasz klawisz skrótu, który nie jest przypisany do polecenia w aplikacji, która obecnie obsługuje klawiszy skrótów klawisz skrótu są przekazywane do innych aplikacji.  
  
 Należy wybrać opcję będą obowiązywać dla projektów programu Word dopóki nie zostanie zmieniony. Zaznaczenie nie ma wpływu na projektów programu Microsoft Office Excel; należy zmiany dla programu Excel, korzystając z opcji Microsoft Office Excel klawiatury.  
  
## <a name="uielement-list"></a>Lista elementów interfejsu użytkownika  
 **Schemat klawiatury w usłudze Visual Studio**  
 Visual Studio odbiera wszystkich poleceń klawiszy skrótów, nawet jeśli dokument programu Word ma fokus. Na przykład, jeśli naciśniesz klawisz funkcji **F5** podczas dokument ma fokus, Visual Studio rozpoczyna debugowanie rozwiązania.  
  
 **Schemat klawiatury dynamiczne**  
 Visual Studio odbiera poleceń klawiszy skrótów tylko wtedy, gdy fokus. Po aktywowaniu dokument programu Word, wyraz odbiera wszystkich poleceń klawiszy skrótów. Na przykład, jeśli naciśniesz klawisz funkcji **F5** podczas dokument programu Word ma fokus, wyświetlane jest okno **Znajdź i Zamień** okno dialogowe z **przejdź do** kartę zaznaczone. Jeśli naciśniesz **F5** podczas pracy programu Visual Studio ma fokus, Visual Studio rozpoczyna debugowanie rozwiązania.  
  
## <a name="see-also"></a>Zobacz także  
 [Microsoft Office Excel klawiatura, ustawienia klawiatury Microsoft Office — okno dialogowe](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)  
  
  