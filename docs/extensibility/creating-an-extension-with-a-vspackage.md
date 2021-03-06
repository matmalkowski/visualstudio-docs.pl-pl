---
title: Tworzenie rozszerzenia za pomocą pakietu VSPackage | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 50af15e1c15b5d0b6318c498923229778e8c0169
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500777"
---
# <a name="create-an-extension-with-a-vspackage"></a>Tworzenie rozszerzenia za pomocą pakietu VSPackage
W tym instruktażu dowiesz się, jak utworzyć projekt VSIX i Dodaj element projektu pakietu VSPackage. Używamy pakietu VSPackage można pobrać usługi powłoki interfejsu użytkownika, aby wyświetlić okno komunikatu.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalacji programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-vspackage"></a>Tworzenie pakietu VSPackage  
  
1.  Utwórz projekt VSIX, o nazwie **FirstPackage**. Można znaleźć szablonu projektu VSIX w **nowy projekt** , okno dialogowe **Visual C#** > **rozszerzalności**.  
  
2.  Po otwarciu projektu, należy dodać szablon elementu pakietu Visual Studio o nazwie **FirstPackage**. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Dodaj** > **nowy element**. W **Dodaj nowy element** okno dialogowe, przejdź do **Visual C#** > **rozszerzalności** i wybierz **pakiet rozszerzeń Visual Studio**. W **nazwa** u dołu okna, Zmień nazwę pliku polecenia, aby *FirstPackage.cs*.  
  
3.  Skompiluj projekt, a następnie rozpocząć debugowanie.  
  
     Pojawi się doświadczalnym wystąpieniu programu Visual Studio. Aby uzyskać więcej informacji na temat wystąpienia eksperymentalnego zobacz [wystąpienie doświadczalne](../extensibility/the-experimental-instance.md).  
  
4.  W doświadczalnym wystąpieniu Otwórz **narzędzia** > **rozszerzenia i aktualizacje** okna. Powinien zostać wyświetlony **FirstPackage** rozszerzenia w tym miejscu. (Jeśli otworzysz **rozszerzenia i aktualizacje** wystąpienia pracy programu Visual Studio, nie będziesz widzieć **FirstPackage**).  
  
## <a name="load-the-vspackage"></a>Ładowanie pakietu VSPackage  
 W tym momencie rozszerzenia nie zostanie załadowany, ponieważ nie widać niczego, co powoduje, że do załadowania. Zazwyczaj można załadować rozszerzenia podczas interakcji z jego interfejsie użytkownika (kliknięcia polecenia menu, otwierając okno narzędzia) lub przez określenie, czy pakietu VSPackage powinny zostać załadowane w określonym kontekście interfejsu użytkownika. Aby uzyskać więcej informacji na temat ładowania interfejsu użytkownika i pakietów VSPackage kontekstów zobacz [ładowanie pakietów VSPackage](../extensibility/loading-vspackages.md). Do wykonania tej procedury pokażemy sposób ładowania pakietu VSPackage, gdy rozwiązanie jest otwarte.  
  
1.  Otwórz *FirstPackage.cs* pliku. Wyszukaj deklaracji `FirstPackage` klasy. Zamień istniejące atrybuty z następujących czynności:  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid(FirstPackage.PackageGuidString)]  
    public sealed class FirstPackage : Package  
    ```  
  
2.  Dodajmy komunikat, który informuje nas o tym, że został załadowany pakietu VSPackage. Używamy pakietu VSPackage `Initialize()` metodę, aby to zrobić, ponieważ mogą pobrać program Visual Studio services tylko wtedy, gdy pakietu VSPackage zostały zlokalizowane. (Aby uzyskać więcej informacji o pobieraniu usług, zobacz [porady: pobieranie usługi](../extensibility/how-to-get-a-service.md).) Zastąp `Initialize()` metody `FirstPackage` z kodem, który pobiera <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> usługa, która pobiera <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfejsu i wywołuje jego <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> metody.  
  
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
  
3.  Skompiluj projekt, a następnie rozpocząć debugowanie. Zostanie wyświetlone wystąpienie eksperymentalne.  
  
4.  Otwórz rozwiązanie w doświadczalnym wystąpieniu. Powinien zostać wyświetlony komunikat informujący, że **pierwszego pakietu wewnątrz Initialize()**.