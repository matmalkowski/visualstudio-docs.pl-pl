---
title: "Aktualizowanie interfejsu użytkownika | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
caps.latest.revision: "41"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: bea4f89d2894344069b8aa5b3037bd00b973a40e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="updating-the-user-interface"></a>Aktualizowanie interfejsu użytkownika
Po zaimplementowaniu polecenia, można dodać kod, aby zaktualizować stan Twoje nowe polecenia interfejsu użytkownika.  
  
 W typowej aplikacji Win32 stale sondowany zestawu poleceń i stan poszczególnych poleceń można dostosować zgodnie z ich wyświetlania. Jednak ponieważ [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] powłoki może obsługiwać nieograniczoną liczbę VSPackages, szeroką gamę sondowania może ulec obniżeniu reakcji, szczególnie sondowania przez zestawy międzyoperacyjne między kodu zarządzanego i modelu COM.  
  
### <a name="to-update-the-ui"></a>Aby zaktualizować interfejsu użytkownika  
  
1.  Wykonaj jedną z następujących czynności:  
  
    -   Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> metody.  
  
         <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> Można uzyskać interfejsu <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> usługi, w następujący sposób.  
  
        ```csharp  
        void UpdateUI(Microsoft.VisualStudio.Shell.ServiceProvider sp)  
        {  
            IVsUIShell vsShell = (IVsUIShell)sp.GetService(typeof(IVsUIShell));  
            if (vsShell != null)  
            {  
                int hr = vsShell.UpdateCommandUI(0);  
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr);  
            }  
        }  
  
        ```  
  
         Jeśli parametr <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> jest niezerowa (`TRUE`), a następnie aktualizacja jest wykonywana synchronicznie i natychmiast. Zaleca się, że przekazujesz zero (`FALSE`) dla tego parametru zapewnić dobrą wydajność. Jeśli chcesz uniknąć buforowania, zastosuj `DontCache` Flaga podczas tworzenia polecenia w pliku vsct. Niemniej jednak, Użyj flagi ostrożnie lub wydajność może ulec obniżeniu. Aby uzyskać więcej informacji o flagach polecenia, zobacz [Element Command flagi](../extensibility/command-flag-element.md) dokumentacji.  
  
    -   W pakiety VSPackage hostowania formantu ActiveX przy użyciu modelu aktywacji w miejscu, w oknie, może być bardziej wygodne <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> metody. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> Metody w <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfejsu i <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> metoda <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> interfejsu działają tak samo. Zarówno spowodować środowisko w celu ponownego sprawdzania stanu wszystkich poleceń. Zazwyczaj aktualizacji nie jest wykonywane bezpośrednio. Zamiast tego aktualizacji jest opóźnione aż do czasu bezczynności. Powłoka buforuje stan polecenia, aby zapewnić dobrą wydajność. Jeśli chcesz uniknąć buforowania, zastosuj `DontCache` Flaga podczas tworzenia polecenia w pliku vsct. Niemniej jednak ostrożnie użyć flagi ponieważ wydajność może ulec obniżeniu.  
  
         Należy zauważyć, że można uzyskać <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> interfejsu, wywołując `QueryInterface` metoda <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> obiektu lub przez Uzyskiwanie interfejsu z <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> usługi.  
  
## <a name="see-also"></a>Zobacz też  
 [Jak VSPackages dodać elementy interfejsu użytkownika](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Implementacja](../extensibility/internals/command-implementation.md)