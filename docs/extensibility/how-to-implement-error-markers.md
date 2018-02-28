---
title: "Porady: Implementowanie znaczników błąd | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - error markers
ms.assetid: e8e78514-5720-4fc2-aa43-00b6af482e38
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: d41c1bf063ea074df217934a00f73291a10e051d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-error-markers"></a>Porady: Implementowanie znaczników błąd
Znaczniki błędów (lub czerwone faliste podkreślenie) są najbardziej trudne do zaimplementowania dostosowań edytora tekstu. Jednak korzyści, które umożliwiają użytkownikom VSPackage może znacznie ważniejsze niż koszt, aby zapewnić użytkownikom. Znaczniki błędów pisowni zaznaczenia tekstu, który z analizatora języka uzna niepoprawne o dowolnym kształcie lub faliste wiersz czerwony. Ten wskaźnik pomaga programistów, wyświetlając wizualnie niepoprawny kod.  
  
 Użycie znaczników tekstu do zaimplementowania czerwone faliste podkreślenie. Zgodnie z zasadą usługi języka Dodaj czerwone faliste podkreślenie do buforu tekstu jako przebiegu tła, w czasie bezczynności lub w wątku w tle.  
  
### <a name="to-implement-the-red-wavy-underline-feature"></a>Aby zaimplementować funkcję gramatyczne  
  
1.  Zaznacz tekst, w którym mają być gramatyczne.  
  
2.  Utwórz znacznik typu `MARKER_CODESENSE_ERROR`. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie standardowych znaczników tekstu](../extensibility/how-to-add-standard-text-markers.md).  
  
3.  Następnie należy przekazać w <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> wskaźnika interfejsu.  
  
 Ten proces umożliwia również tworzenie tekst porady lub menu kontekstowego specjalne za pośrednictwem danej znacznika. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie standardowych znaczników tekstu](../extensibility/how-to-add-standard-text-markers.md).  
  
 Następujące obiekty są wymagane, przed wyświetleniem błędu znaczników.  
  
-   Analizator.  
  
-   Dostawcy zadań (to znaczy, że implementacja interfejsu <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2>) który przechowuje rekord zmian w wierszu informacji w celu identyfikowania wiersze, które mają być ponownie przeanalizowane.  
  
-   Filtr widoku tekstu, który przechwytuje karetkę zdarzenia zmian z widoku przy użyciu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents.OnChangeCaretLine%2A>) metody.  
  
 Analizator, dostawcy zadań i filtr Podaj dokonanie możliwe znaczników błąd infrastruktury. W poniższych krokach przedstawiono proces wyświetlania błędów znaczników.  
  
1.  Widok jest filtrowany filtr uzyskuje wskaźnik do zadania skojarzonego z tym widoku danych.  
  
    > [!NOTE]
    >  Można użyć tego samego filtru polecenia, dla porady — metoda, uzupełniania instrukcji, znaczniki błędów i tak dalej.  
  
2.  Gdy filtr odbierze zdarzenie wskazujące, że zostały przeniesione do nowego wiersza, aby sprawdzić błędy utworzeniu zadania.  
  
3.  Zadanie obsługi sprawdza, czy wiersz został zmieniony. Jeśli tak, analizuje linii błędy.  
  
4.  W przypadku znalezienia błędów dostawcy zadań tworzy wystąpienie elementu zadania. To wystąpienie tworzy znacznika tekstu używanego środowiska jako znacznik błędów w widoku tekstu.  
  
## <a name="see-also"></a>Zobacz też  
 [Przy użyciu znaczników tekstu przy użyciu interfejsu API starsza wersja](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Porady: Dodawanie znaczników tekstu standardowego](../extensibility/how-to-add-standard-text-markers.md)   
 [Porady: Tworzenie niestandardowego tekstu znaczników](../extensibility/how-to-create-custom-text-markers.md)   
 [Porady: Użyj znacznikach tekstu](../extensibility/how-to-use-text-markers.md)