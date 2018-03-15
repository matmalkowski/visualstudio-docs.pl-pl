---
title: Polecenie implementacji | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 2e56fbdb6056ba02df0cafac73dd4baab60ab3be
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="command-implementation"></a>Wykonanie polecenia
Aby zaimplementować polecenia w pakiet VSPackage, należy wykonać następujące zadania:  
  
1.  W pliku vsct grupę polecenia, a następnie dodaj polecenie do niego. Aby uzyskać więcej informacji, zobacz [tabeli poleceń w usłudze Visual Studio (. Pliki Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)"  
  
2.  Zarejestruj polecenia programu Visual Studio.  
  
3.  Wykonuje polecenia.  
  
 W poniższych sekcjach opisano, jak się zarejestrować i wdrożyć poleceń.  
  
## <a name="registering-commands-with-visual-studio"></a>Rejestrowanie poleceń z programem Visual Studio  
 Jeśli polecenie ma być wyświetlany na menu, musisz dodać <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> pakiet VSPackage, a jako wartość nazwy menu lub jego identyfikator zasobu.  
  
```  
[ProvideMenuResource("Menus.ctmenu", 1)]  
...  
    public sealed class MyPackage : Package  
    {.. ..}  
  
```  
  
 Ponadto należy zarejestrować polecenie z <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>. Tę usługę można uzyskać za pomocą <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> metodę, jeśli jest pochodną VSPackage <xref:Microsoft.VisualStudio.Shell.Package>.  
  
```  
OleMenuCommandService mcs = GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
if ( null != mcs )  
{  
    // Create the command for the menu item.  
    CommandID menuCommandID = new CommandID(guidCommandGroup, myCommandID);  
    MenuCommand menuItem = new MenuCommand(MenuItemCallback, menuCommandID );  
    mcs.AddCommand( menuItem );  
}  
  
```  
  
## <a name="implementing-commands"></a>Implementacja poleceń  
 Istnieje wiele sposobów, aby zaimplementować poleceń. Polecenia menu statyczne, który jest zawsze wyświetlany taki sam sposób, jak i w tym samym menu polecenie, utworzyć polecenia przy użyciu <xref:System.ComponentModel.Design.MenuCommand> jak przedstawiono w przykładach w poprzedniej sekcji. Aby utworzyć polecenie statycznych, musisz podać program obsługi zdarzeń jest odpowiedzialny za wykonywania polecenia. Ponieważ polecenie jest zawsze włączone i są widoczne, nie należy podać jego stan dla programu Visual Studio. Jeśli chcesz zmienić stan polecenia w zależności od określonych warunków, można utworzyć polecenie jako wystąpienie <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> klasy, a w jego konstruktora udostępniają program obsługi zdarzeń można wykonać polecenia i obsługi stanu zapytania do powiadamiania Visual Studio po zmianie stanu polecenia. Można też wdrożyć <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> jako część klasy poleceń lub, można zaimplementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Jeśli udostępniasz polecenia w ramach projektu. Dwa interfejsy i <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> wszystkie klasy mają metod, które powiadamiają o Visual Studio o zmianie stanu polecenia i innych metod, które zapewniają wykonanie polecenia.  
  
 Polecenie zostanie dodany do usługi polecenia, staje się jeden z łańcucha poleceń. Po zaimplementowaniu stan powiadomień i wykonywanie metod dla polecenia zajmie się tylko dla tego konkretnego polecenia i przekaż wszystkich innych przypadkach do innych poleceń w łańcuchu. Jeśli nie zostanie ona przekazać polecenie (zwykle przez zwrócenie <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>), programu Visual Studio może przestać działać prawidłowo.  
  
## <a name="query-status-methods"></a>Metody stan zapytań  
 W przypadku wdrażania albo <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> metoda, sprawdź, czy identyfikator GUID zestaw, do której należy polecenie poleceń i identyfikator polecenia. Skorzystaj z następujących wskazówek:  
  
-   Jeśli identyfikator GUID nie został rozpoznany, implementacji w metodzie musi zwracać <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP>.  
  
-   Jeśli implementacji w metodzie rozpoznaje identyfikatora GUID, ale nie została zaimplementowana polecenia, a następnie metoda powinna zwrócić <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>.  
  
-   Implementacji w metodzie rozpoznaje zarówno identyfikator GUID i polecenia, a następnie metoda powinna ustawić pole flagi polecenie każdego polecenia (w `prgCmds` parametru) przy użyciu następujących <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> flag:  
  
    -   OLECMDF_SUPPORTED — Jeśli polecenie jest obsługiwane.  
  
    -   OLECMDF_INVISIBLE — Jeśli polecenie nie powinny być widoczne.  
  
    -   OLECMDF_LATCHED — Jeśli polecenie jest włączone na i prawdopodobnie zostały sprawdzone.  
  
    -   OLECMDF_ENABLED — Jeśli polecenie jest włączone.  
  
    -   OLECMDF_DEFHIDEONCTXTMENU — polecenie powinien być ukryty, jeśli wygląda na to, w menu skrótów.  
  
    -   OLECMDF_NINCHED — Jeśli polecenie jest kontrolerem menu i nie jest włączona, ale swoją listę rozwijaną nie jest pusty i jest dostępny. (Ta flaga jest rzadko używana.)  
  
-   Jeśli polecenie zostało zdefiniowane w pliku vsct z `TextChanges` Flaga, ustaw następujące parametry:  
  
    -   Ustaw `rgwz` elementu `pCmdText` parametru na nowy tekst polecenia.  
  
    -   Ustaw `cwActual` elementu `pCmdText` parametru do rozmiaru ciąg polecenia.  
  
 Upewnij się również czy bieżącego kontekstu nie jest funkcją automatyzacji chyba, że polecenie jest przeznaczony specjalnie do obsługi funkcji automatyzacji.  
  
 Aby wskazać, że obsługuje konkretnego polecenia, zwróć <xref:Microsoft.VisualStudio.VSConstants.S_OK>. W przypadku innych poleceń zwracają <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>.  
  
 W poniższym przykładzie metoda zapytania status najpierw sprawdza, czy kontekst nie jest funkcją automatyzacji, a następnie umożliwia znalezienie poprawny zestaw poleceń identyfikator GUID i identyfikator polecenia. Samo polecenie ustawiono włączony i obsługiwane. Wszystkie inne polecenia są obsługiwane.  
  
```  
public int QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
{  
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))  
    {  
        if (pguidCmdGroup == VSConstants.VSStd2K && cCmds > 0)  
        {  
            // make the Right command visible   
            if ((uint)prgCmds[0].cmdID == (uint)VSConstants.VSStd2KCmdID.RIGHT)  
            {  
                prgCmds[0].cmdf = (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_ENABLED | (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_SUPPORTED;  
                return VSConstants.S_OK;  
            }  
        }  
        return Constants.OLECMDERR_E_NOTSUPPORTED;  
    }  
}  
  
```  
  
## <a name="execution-methods"></a>Metody wykonywania  
 Implementacja metody badanie stanu jest podobny do implementacji metody execute. Najpierw upewnij się, że kontekst nie jest funkcją automatyzacji. Następnie sprawdź identyfikator GUID i identyfikator polecenia. Jeśli identyfikator GUID lub identyfikator polecenia nie został rozpoznany, zwraca <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>.  
  
 Do obsługi polecenia, wykonaj go i zwraca <xref:Microsoft.VisualStudio.VSConstants.S_OK> Jeśli wykonanie zakończy się powodzeniem. Polecenie odpowiada za wykrywanie błędów oraz powiadomienia; w związku z tym zwróciła kod błędu, jeśli wykonanie nie powiedzie się. W poniższym przykładzie pokazano implementowania metody wykonywania.  
  
```  
public int Exec(ref Guid pguidCmdGroup, uint nCmdID, uint nCmdexecopt, IntPtr pvaIn, IntPtr pvaOut)  
{  
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))  
    {  
        if (pguidCmdGroup == VSConstants.GUID_VSStandardCommandSet97)  
        {  
             if (nCmdID ==(uint) uint)VSConstants.VSStd2KCmdID.RIGHT)  
            {  
                //execute the command  
                return VSConstants.S_OK;  
            }  
        }  
    }  
    return Constants.OLECMDERR_E_NOTSUPPORTED;  
}  
  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie elementów interfejsu użytkownika przy użyciu pakietów VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)