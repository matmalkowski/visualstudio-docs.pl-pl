---
title: Okno dialogowe Opcje programu Microsoft Office Excel klawiatury, ustawienia klawiatury Microsoft Office, | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VST.ExcelOptions.KeyboardMappingScheme
- VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Excel_Keyboard
- VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Excel.Keyboard
dev_langs:
- VB
- CSharp
helpviewer_keywords: keyboard shortcuts, Office development in Visual Studio
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: d52b7baf1283f986ee378c800114836da606eca8
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>Klawiatura Microsoft Office Excel, ustawienia klawiatury Microsoft Office — Okno dialogowe
  Program Microsoft Excel pakietu Office i programu Visual Studio zarówno obsługi klawiszy skrótów. Inne polecenia w programie Excel, jak i w programie Visual Studio może zastąpić tej samej kombinacji klawiszy skrótów. Gdy program Excel jest otwarty w projektach na poziomie dokumentu w programie Visual Studio, tylko jedną aplikację naraz odbiera poleceń klawiszy skrótów. Domyślnie program Visual Studio odbiera wszystkie polecenia klawiszy skrótu, ale można wprowadzić ich odbierania, gdy dokument ma fokus, wybierając Excel **schemat klawiatury dynamiczne**.  
  
 Jeśli używasz klawisz skrótu, który nie jest przypisany do polecenia w aplikacji, która obecnie obsługuje klawiszy skrótów klawisz skrótu są przekazywane do innych aplikacji.  
  
 Należy wybrać opcję będą obowiązywać dla projektów programu Excel dopóki nie zostanie zmieniony. Zaznaczenie nie ma wpływu na projektów programu Microsoft Office Word; należy zmiany dla programu Word, korzystając z opcji Microsoft Office Word klawiatury.  
  
## <a name="uielement-list"></a>Lista elementów UI  
 **Schemat klawiatury w usłudze Visual Studio**  
 Visual Studio odbiera wszystkich poleceń klawiszy skrótów, nawet jeśli Excel ma fokus. Na przykład jeśli naciśniesz klawisz funkcji F5 podczas Excel ma fokus, Visual Studio rozpoczyna debugowanie rozwiązania.  
  
 **Schemat klawiatury dynamiczne**  
 Visual Studio odbiera poleceń klawiszy skrótów tylko wtedy, gdy fokus. Po aktywowaniu Excel Excel odbiera wszystkie polecenia klawiszy skrótów. Na przykład, jeśli naciśniesz klawisz funkcji F5 podczas Excel ma fokus, zostanie otwarty **przejdź do** okno dialogowe. Jeśli podczas, gdy fokus jest Visual Studio naciśnij klawisz F5, Visual Studio rozpoczyna debugowanie rozwiązania.  
  
## <a name="see-also"></a>Zobacz też  
 [Klawiatura Microsoft Office Word, ustawienia klawiatury Microsoft Office, Opcje — okno dialogowe](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)  
  
  