---
title: Skoroszyt użyty do tworzenia tego projektu zawiera formanty ActiveX, których projektant nie może załadować | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 8d31674f54ce454db50a63572c24f92031e7d886
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="the-workbook-used-to-create-this-project-contains-activex-controls-that-the-designer-cannot-load"></a>Skoroszyt użyty do tworzenia tego projektu zawiera kontrolki ActiveX, których projektant nie może załadować
  Ten błąd jest wyświetlany, gdy formant zostanie dodany do dokumentu programu Word lub arkuszu programu Excel programowo, Zapisz dokument lub skoroszyt, a następnie utwórz nowe rozwiązanie poziomie dokumentów na podstawie dokumentu lub skoroszytu.  
  
 Informacje opisujące typ zarządzany formantu nie są zapisywane wraz z dokumentu lub skoroszytu. Podczas tworzenia nowego rozwiązania na podstawie tego dokumentu lub skoroszyt programu Visual Studio nie ma wystarczających informacji, aby załadować formantu w Projektancie elementu host.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Otwórz dokument lub skoroszytu.  
  
2.  Usuwanie formantów, które zostały dodane w czasie wykonywania. Można to zrobić, wybierając je w dokumencie lub skoroszyt i naciskając klawisz DELETE.  
  
3.  Tworzenie rozwiązania poziomie dokumentów na podstawie dokumentu lub skoroszytu.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  