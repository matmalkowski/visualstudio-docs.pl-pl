---
title: Skoroszyt użyty do tworzenia tego projektu zawiera kontrolki ActiveX, których projektant nie może załadować
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.SelectDocWizard.ContainsActiveXControls
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9d47ee32f23ca0eb856b2a8f618d60fae552a027
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34693074"
---
# <a name="the-workbook-used-to-create-this-project-contains-activex-controls-that-the-designer-cannot-load"></a>Skoroszyt użyty do tworzenia tego projektu zawiera kontrolki ActiveX, których projektant nie może załadować
  Ten błąd jest wyświetlany, gdy formant zostanie dodany do dokumentu programu Word lub arkuszu programu Excel programowo, Zapisz dokument lub skoroszyt, a następnie utwórz nowe rozwiązanie poziomie dokumentów na podstawie dokumentu lub skoroszytu.  
  
 Informacje opisujące typ zarządzany formantu nie są zapisywane wraz z dokumentu lub skoroszytu. Podczas tworzenia nowego rozwiązania na podstawie tego dokumentu lub skoroszyt programu Visual Studio nie ma wystarczających informacji, aby załadować formantu w Projektancie elementu host.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Otwórz dokument lub skoroszytu.  
  
2.  Usuń formantów, które zostały dodane w czasie wykonywania. Można to zrobić, wybierając je w dokumencie lub skoroszyt i naciskając klawisz **usunąć** klucza.  
  
3.  Tworzenie rozwiązania poziomie dokumentów na podstawie dokumentu lub skoroszytu.  
  
## <a name="see-also"></a>Zobacz także  
 [Porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  