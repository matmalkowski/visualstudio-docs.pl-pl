---
title: "Obsługa błędów i wartości zwracane | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b3a197bb5dd12c1d8404ddf63976f9dbf4b63823
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="error-handling-and-return-values"></a>Obsługa błędów i wartości zwracane
Pakiety VSPackage i modelu COM przy użyciu takiej samej architekturze błędy. `SetErrorInfo` i `GetErrorInfo` funkcje są częścią interfejsu programowania aplikacji (API) Win32. Wszelkie pakiet VSPackage w zintegrowane środowisko programistyczne (IDE) mogą wywoływać te globalne API Win32, aby informacje o błędzie sformatowanego rekordu po otrzymaniu powiadomienia o błędach. [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Zawiera zestawy międzyoperacyjne do zarządzania informacje o błędzie.  
  
## <a name="interop-methods"></a>Metody międzyoperacyjne  
 Dla wygody IDE udostępnia metodę, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>, aby użyć zamiast wywoływania interfejsów API systemu Win32. Używany kod zarządzany <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>. Po wystąpieniu błędu `HRESULT` dociera do poziomu, w której powinien być wyświetlany komunikat o błędzie (często jest to obiekt implementacja <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> programu obsługi poleceń), IDE używa innej metody, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>, aby wyświetlić odpowiedni komunikat. Używany kod zarządzany <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> metody.  
  
 Jako implementujący pakiet VSPackage, zwykle implementacji obiektów COM `ISupportErrorInfo`. `ISupportErrorInfo` Interfejsu gwarantuje, że informacje o błędzie sformatowanego można pionowo Przenieś w górę łańcuch wywołań. Obiekty, które mogą być używane przez procesy lub pomiędzy wątkami musi obsługiwać `ISupportErrorInfo` aby upewnić się, że informacje o błędzie sformatowanego jest poprawnie przekazywane wstecz do obiektu wywołującego.  
  
 Wszystkie obiekty, które są związane z VSPackages i są zaangażowane w IDE, takich jak fabryki edytora, edytory, hierarchii, rozszerzanie i udostępniane usługi, powinien obsługiwać informacje o błędzie sformatowanego. Gdy IDE nie wymaga tych obiektów pakiet VSPackage, aby zaimplementować `ISupportErrorInfo`, zawsze jest zalecane.  
  
 IDE jest odpowiedzialny za raportowanie informacji o błędach i wyświetlanie użytkownik [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zawsze, gdy `HRESULT` jest propagowana do środowiska IDE. IDE jest również mechanizm tworzenia `ErrorInfo` obiektów.  
  
## <a name="general-guidelines"></a>Ogólne wskazówki  
 Można użyć <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> metody do ustawiania i raportów o błędach, które są wewnętrzne dla danej implementacji pakiet VSPackage. Jednak jako ogólną regułę, należy wykonać te wytyczne dotyczące obsługi komunikatów o błędach w pakiecie VSPackage:  
  
-   Implementowanie `ISupportErrorInfo` w obiektów COM pakiet VSPackage.  
  
-   Utwórz mechanizm, który wywołuje raportowania błędów <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metody w obiektach, które implementują <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
-   Let IDE błędy są wyświetlane użytkownikom za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> metody.  
  
## <a name="error-information-in-the-ide"></a>Informacje o błędzie w środowisku IDE  
 Następujące reguły wskazuje sposób obsługi informacji o błędzie w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE:  
  
-   Jak tego wywołania funkcji obrony strategii w celu zagwarantowania, że informacje o błędzie starych nie został zgłoszony dla użytkowników, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> najpierw powinny wywoływać metodę <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metody. Przekazywanie `null` można wyczyścić pamięci podręcznej komunikaty przed wywołaniem niczego, który może ustawić nowe informacje o błędzie.  
  
-   Funkcje, które bezpośrednio nie będą zgłaszać komunikaty o błędach są dozwolone tylko w celu wywołania <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metodę, jeśli są one zwróciła błąd `HRESULT`. Dopuszcza się wyczyść `ErrorInfo` wpisu do funkcji lub zwracanie <xref:Microsoft.VisualStudio.VSConstants.S_OK>. Jedynym wyjątkiem od tej reguły jest po wywołaniu zwraca błąd `HRESULT` z którym otrzymującej można odzyskać jawnie lub zignorować.  
  
-   Każda strona, która jawnie ignoruje błąd `HRESULT` należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metody z <xref:Microsoft.VisualStudio.VSConstants.S_OK>. W przeciwnym razie `ErrorInfo` obiekt może przypadkowo używany podczas innej strony generuje błąd bez podawania własnych `ErrorInfo`.  
  
-   Wszystkie metody, które pochodzą błąd `HRESULT` zachęcamy do wywołania <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metodę, aby podać informacje o błędzie sformatowanego. Jeśli zwróconego `HRESULT` jest specjalnego `FACILITY_ITF` błąd, a następnie metoda jest wymagany do zapewnienia odpowiedniego `ErrorInfo`obiektu. Jeśli zwrócony kod błędu jest to błąd standardowy system (na przykład <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY>, <xref:Microsoft.VisualStudio.VSConstants.E_ABORT>, <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>, <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED>i tak dalej.) jest dopuszczalne zwracają kod błędu bez jawnego wywołania <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metody. Jako obrony strategii kodowania, gdy błąd pochodzący `HRESULT` (w tym błędów systemowych) zawsze wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> — metoda, za pomocą `ErrorInfo` opisujące błąd bardziej szczegółowo lub `null`.  
  
-   Wszystkie funkcje, które zwracają błąd, który został zainicjowany przez inne wywołanie musi przejść na informacje, które zostały odebrane z niepowodzeniem wywołania w `HRESULT` bez modyfikowania `ErrorInfo` obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [SetErrorInfo (Automatyzacja składnika)](http://msdn.microsoft.com/en-us/8eaacfac-fc37-4eaa-870b-10b99d598d66)   
 [GetErrorInfo](http://msdn.microsoft.com/en-us/03317526-8c4f-4173-bc10-110c8112676a)   
 [ISupportErrorInfo — interfejs](http://msdn.microsoft.com/en-us/42d33066-36b4-4a5b-aa5d-46682e560f32)