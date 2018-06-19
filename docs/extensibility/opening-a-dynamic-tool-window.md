---
title: Otwieranie okna narzędzia dynamiczne | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bdd3a4a8d85ed7d0f5884e7f11b8778eb3b420a2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138291"
---
# <a name="opening-a-dynamic-tool-window"></a>Otwieranie okna narzędzia dynamiczne
Narzędzia windows zwykle są otwierane z polecenia w menu lub skrótu klawiaturowego równoważne. Czasami jednak może być konieczne okna narzędzia, która otwiera za każdym razem kontekście konkretnego interfejsu użytkownika ma zastosowanie i zostanie zamknięte po kontekstu interfejsu użytkownika nie ma zastosowania. Tego rodzaju okna narzędzi są nazywane *dynamiczne* lub *automatycznie widoczne*.  
  
> [!NOTE]
>  Lista wstępnie zdefiniowanych kontekstów interfejsu użytkownika, zobacz <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT>. Dla  
  
 Jeśli chcesz otworzyć okna narzędzia dynamicznej podczas uruchamiania i istnieje możliwość tworzenia się niepowodzeniem, musi implementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> interfejsu i przetestować awarię w <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> metody. Aby powłoki dowiedzieć się, że masz dynamiczne okno, który powinien zostać otwarty podczas uruchamiania, należy dodać `SupportsDynamicToolOwner` ma wartość (1) do rejestracji pakietu. Ta wartość nie jest częścią standardowej <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>, dlatego należy utworzyć niestandardowy atrybut ją dodać. Aby uzyskać więcej informacji dotyczących atrybutów niestandardowych, zobacz [przy użyciu niestandardowych atrybutów rejestracji, aby zarejestrować rozszerzenie](../extensibility/registering-and-unregistering-vspackages.md#using-a-custom-registration-attribute-to-register-an-extension).  
  
 Użyj <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> można otworzyć okna narzędzia. Okna narzędzi jest tworzony w razie potrzeby.  
  
> [!NOTE]
>  Dynamiczne okno może zostać zamknięty przez użytkownika. Jeśli chcesz utworzyć polecenia menu, więc użytkownik może ponownie otworzyć okno narzędzia polecenia menu powinno być włączone w tym samym kontekście interfejsu użytkownika, którego kliknięcie spowoduje otwarcie okna narzędzia i wyłączone w inny sposób.  
  
### <a name="to-open-a-dynamic-tool-window"></a>Aby otworzyć okno narzędzia dynamiczne  
  
1.  Tworzenie projektu VSIX o nazwie **DynamicToolWindow** i dodać szablon elementu okna narzędzia o nazwie **DynamicWindowPane.cs**. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia z okna narzędzia](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
2.  W pliku DynamicWindowPanePackage.cs odnaleźć deklaracji DynamicWindowPanePackage. Dodaj <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> i <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute> atrybutów, aby zarejestrować okna narzędzia.  
  
    ```vb  
    [ProvideToolWindow(typeof(DynamicWindowPane)]  
    [ProvideToolWindowVisibility(typeof(DynamicWindowPane), VSConstants.UICONTEXT.SolutionExists_string)]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [ProvideToolWindow(typeof(DynamicToolWindow.DynamicWindowPane))]  
    [Guid(DynamicWindowPanePackage.PackageGuidString)]  
    public sealed class DynamicWindowPanePackage : Package  
    {. . .}  
    ```  
  
     Atrybuty powyżej rejestru o nazwie DynamicWindowPane jako przejściowa okna, które nie jest trwały, po zamknięciu programu Visual Studio i ponownie otworzyć okno narzędzia. Zostanie otwarty DynamicWindowPane zawsze, gdy <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> ma zastosowanie, a w przeciwnym razie zamknięte.  
  
3.  Skompiluj projekt i Rozpocznij debugowanie. Eksperymentalne wystąpienie powinny być wyświetlane. Nie powinna zostać wyświetlona okna narzędzia.  
  
4.  Otwórz projekt w eksperymentalnym wystąpieniu. Powinny być wyświetlane okna narzędzia.