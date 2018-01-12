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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 0f50342fd82826aec8cf0d9694454afdc2db4080
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
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
  
  