---
title: "Opóźnione ładowanie dokumentu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e69ee994f434e122894989d82b97ea79e4bd995c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="delayed-document-loading"></a>Opóźnione ładowanie dokumentu
Gdy użytkownik ponownie otwiera rozwiązanie Visual Studio, większość skojarzone dokumenty nie są ładowane bezpośrednio. Ramki okna dokumentu jest tworzony w stanie oczekiwania inicjowania i dokument symbolu zastępczego (o nazwie ramki stub) znajduje się w tabeli systemem dokumentu (Normalizacją).  
  
 Rozszerzenie może spowodować dokumentów projektu mają być niepotrzebnie załadowane przed załadowaniem, badając elementy w dokumentach. Może to zwiększyć ogólną zużycie pamięci dla programu Visual Studio.  
  
## <a name="document-loading"></a>Ładowanie dokumentu  
 Stub ramki i zarządzania dokumentami są w pełni zainicjowany gdy użytkownik uzyskuje dostęp do dokumentu, na przykład po wybraniu karty ramki okna. Dokument również mogą być inicjowane przez rozszerzenie żądań dane dokumentu, uzyskiwanie dostępu do Normalizacją bezpośrednio uzyskać dane dokumentu lub uzyskiwanie dostępu do Normalizacją pośrednio, wykonując jedną z następujących wywołania:  
  
-   Ramki okna Pokaż metody: <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>.  
  
-   Metoda GetProperty ramki okna <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> na dowolnym z następujących właściwości:  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
 Jeśli rozszerzenie korzysta z kodu zarządzanego, należy nie wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> chyba że masz pewność, że dokument nie jest w stanie oczekiwania na zainicjowanie lub dokument, który ma być w pełni zainicjowany. Jest to, ponieważ ta metoda zawsze zwraca dokumentów obiektu danych, w razie potrzeby go utworzyć. Zamiast tego należy wywołać jednej z metod interfejsu IVsRunningDocumentTable4.  
  
 Jeśli rozszerzenie używa języka C++, można przekazać `null` nie ma parametrów.  
  
 Ładowanie dokumentu niepotrzebnych można uniknąć, wywołując jedną z następujących metod, aby uzyskać odpowiednie właściwości: Aby uzyskać inne właściwości.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6>.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>., Ta metoda zwraca <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> obiekt, który zawiera wartość dla <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> Jeśli dokument nie została jeszcze zainicjowana.  
  
 Można dowiedzieć się, gdy dokument został załadowany przez subskrybowanie zdarzeń Normalizacją, które jest wywoływane, gdy dokument jest w pełni zainicjowany. Dostępne są dwie możliwości:  
  
-   Jeśli obiekt sink zdarzenia implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>, będzie możliwe subskrybowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>,  
  
-   W przeciwnym razie można subskrybować <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>.  
  
 Poniżej przedstawiono scenariusz dostępu hipotetyczny dokumentu. Visual Studio rozszerzenia mają być wyświetlane informacje o otwarte dokumenty, na przykład Edycja blokada liczby i coś o danych dokumentu. Wylicza go dokumentów za pomocą Normalizacją <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>, następnie wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> dla każdego dokumentu w celu pobrania danych dokumentu i liczba blokady edycji. Jeśli dokument jest w stanie oczekiwania na zainicjowanie, żąda danych dokumentu powoduje, że na można zainicjować niepotrzebnie.  
  
 Bardziej wydajny sposób zrobić, to jest użycie <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> Pobierz liczbę blokad edycji, a następnie użyć <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> ustalenie, czy dokument został zainicjowany. Jeśli nie ma flagi <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, dokument został już zainicjowany i żąda danych dokumentu z <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> nie powoduje, że wszystkie zbędne inicjowania. Jeśli dołączysz flagi <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, rozszerzenia należy unikać żąda danych dokumentu, dopóki dokument został zainicjowany. Można to wykryć OnAfterAttributeChange(Ex) programu obsługi zdarzeń.  
  
## <a name="testing-extensions-to-see-if-they-force-initialization"></a>Testowanie rozszerzeń, aby zobaczyć wymusić inicjowania  
 Nie ma żadnych widocznych oznak aktywacji wskazująca, czy dokument został zainicjowany, dlatego może być trudne dowiedzieć się, jeśli rozszerzenie jest wymuszenie inicjowania. Można ustawić klucz rejestru, który ułatwia weryfikacji, ponieważ powoduje ona tytuł każdego dokumentu, który nie jest w pełni zainicjowany tekstu `[Stub]` w tytule.  
  
 W **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\BackgroundSolutionLoad]**ustaw **StubTabTitleFormatString** do **{0} [Stub]**.