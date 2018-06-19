---
title: Tworzenie rozszerzenia z pakiet VSPackage | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 706cdcd26df18af9ccd79b5bf83890c47b1faf57
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109454"
---
# <a name="creating-an-extension-with-a-vspackage"></a>Tworzenie rozszerzenia z pakiet VSPackage
W tym przewodniku przedstawiono sposób tworzenia projektu VSIX i Dodaj element projektu pakiet VSPackage. Pakiet VSPackage zostanie wykorzystany do pobrania usługi powłoki interfejsu użytkownika, aby pokazać okno komunikatu.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, użytkownik nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest uwzględniona jako opcjonalna funkcja w Instalatorze programu Visual Studio. Można także zainstalować zestawu SDK dla programu późniejsze. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-vspackage"></a>Tworzenie pakiet VSPackage  
  
1.  Tworzenie projektu VSIX o nazwie **FirstPackage**. Można znaleźć szablonu projektu VSIX w **nowy projekt** , okno dialogowe **Visual C# / rozszerzalności**.  
  
2.  Po otwarciu projektu dodać szablon elementu pakietu Visual Studio o nazwie **FirstPackage**. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Add / nowy element**. W **Dodaj nowy element** okno dialogowe, przejdź do **Visual C# / rozszerzalności** i wybierz **pakiet programu Visual Studio**. W **nazwa** u dołu okna, Zmień nazwę pliku polecenia, aby **FirstPackage.cs**.  
  
3.  Skompiluj projekt i Rozpocznij debugowanie.  
  
     Pojawi się eksperymentalne wystąpienie programu Visual Studio. Aby uzyskać więcej informacji na temat eksperymentalne wystąpienie, zobacz [eksperymentalne wystąpienie](../extensibility/the-experimental-instance.md).  
  
4.  Otwórz w eksperymentalnym wystąpieniu **narzędzia / rozszerzenia i aktualizacje** okna. Powinny pojawić się **FirstPackage** rozszerzenia tutaj. (Jeśli otworzysz **rozszerzenia i aktualizacje** wystąpienia pracy programu Visual Studio, nie zobaczysz **FirstPackage**).  
  
## <a name="loading-the-vspackage"></a>Podczas ładowania pakietu VSPackage  
 W tym momencie rozszerzenie nie zostanie załadowany, ponieważ nie ma nic, która go załadować. Ogólnie można załadować rozszerzenia przypadku interakcji z jego interfejsie użytkownika (kliknięcia polecenia menu, otwierając okno narzędzia) lub przez określenie, że pakiet VSPackage powinny zostać załadowane w określonym kontekście interfejsu użytkownika. Aby uzyskać więcej informacji na temat ładowania kontekstów pakiety VSPackage i interfejsu użytkownika, zobacz [ładowania VSPackages](../extensibility/loading-vspackages.md). Ta procedura pokażemy ci jak załadować pakiet VSPackage, gdy rozwiązanie jest otwarte.  
  
1.  Otwórz plik FirstPackage.cs. Poszukaj deklaracja klasy FirstPackage. Zamień istniejące atrybuty następujące czynności:  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid(FirstPackage.PackageGuidString)]  
    public sealed class FirstPackage : Package  
    ```  
  
2.  Teraz Dodaj komunikat, który pozwala nam, że pakiet VSPackage został załadowany. Używamy metodę Initialize() pakiet VSPackage Aby to zrobić, ponieważ usługi Visual Studio można uzyskać tylko wtedy, gdy pakiet VSPackage zostały zlokalizowane. (Aby uzyskać więcej informacji na temat uzyskiwania usług, zobacz [porady: uzyskiwanie usługi](../extensibility/how-to-get-a-service.md).) Zastąp metodę Initialize() FirstPackage kod, który pobiera <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> usługa pobiera <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfejsu i wywołania jego <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> metody.  
  
    ```csharp  
    protected override void Initialize()  
    {  
        base.Initialize();  
  
        IVsUIShell uiShell = (IVsUIShell)GetService(typeof(SVsUIShell));  
        Guid clsid = Guid.Empty;  
        int result;  
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(uiShell.ShowMessageBox(  
            0,  
            ref clsid,  
            "FirstPackage",  
             string.Format(CultureInfo.CurrentCulture, "Inside {0}.Initialize()", this.GetType().FullName),  
            string.Empty,  
            0,  
            OLEMSGBUTTON.OLEMSGBUTTON_OK,  
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,  
            OLEMSGICON.OLEMSGICON_INFO,  
            0,  
            out result));  
    }  
    ```  
  
3.  Skompiluj projekt i Rozpocznij debugowanie. Pojawi się eksperymentalne wystąpienie.  
  
4.  Otwórz rozwiązanie w eksperymentalnym wystąpieniu. Powinien zostać wyświetlony komunikat informujący o **pierwszego pakietu wewnątrz Initialize()**.