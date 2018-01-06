---
title: "Skoroszyt użyty do tworzenia tego projektu zawiera formanty ActiveX, których projektant nie może załadować | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VST.SelectDocWizard.ContainsActiveXControls
dev_langs:
- VB
- CSharp
ms.assetid: 91e9c6ee-7543-41e3-be0c-6c000cfd32d1
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2227af08d42b6cf47f7db4ba68e568b9e315bae6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
  
  