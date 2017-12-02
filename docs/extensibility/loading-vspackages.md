---
title: "Ładowanie VSPackages | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 29022d14311e71b7ee33f5339f8e450c47d1ce5c
ms.sourcegitcommit: b7d3b90d0be597c9d01879338dd2678c881087ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/01/2017
---
# <a name="loading-vspackages"></a>Ładowanie VSPackages
Pakiety VSPackage są ładowane do programu Visual Studio, tylko wtedy, gdy ich jest wymagane. Na przykład pakiet VSPackage jest ładowany podczas fabrykę projektów lub usługa, która implementuje pakiet VSPackage korzysta z programu Visual Studio. Ta funkcja jest nazywana opóźnionego ładowania, który jest używany, jeśli to możliwe zwiększyć wydajność.  
  
> [!NOTE]
>  Visual Studio można określić pewne informacje pakiet VSPackage, takich jak polecenia, które oferuje pakiet VSPackage, bez ładowania pakiet VSPackage.  
  
 VSPackages można ustawić na automatyczne ładowanie w kontekście interfejsu danego użytkownika, na przykład po otwarciu rozwiązania. <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> Atrybut ustawia w tym kontekście.  
  
### <a name="autoloading-a-vspackage-in-a-specific-context"></a>Autoloading pakiet VSPackage w określonym kontekście  
  
-   Dodaj `ProvideAutoLoad` atrybutu pakiet VSPackage atrybuty:  
  
    ```csharp  
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID  
    public class MyAutoloadedPackage : Package  
    {. . .}  
    ```  
  
     Zobacz wyliczanych pól <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> listę konteksty interfejsu użytkownika i ich wartości identyfikatora GUID.  
  
-   Ustaw punkt przerwania <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metody.  
  
-   Skompiluj pakiet VSPackage i Rozpocznij debugowanie.  
  
-   Załadowanie rozwiązania lub utworzyć.  
  
     Pakiet VSPackage ładuje i zatrzymuje się na punkt przerwania.  
  
## <a name="forcing-a-vspackage-to-load"></a>Wymuszanie pakiet VSPackage załadować  
 W pewnych okolicznościach pakiet VSPackage może zajść potrzeba wymuszenia inny pakiet VSPackage do załadowania. Na przykład lekki pakiet VSPackage może załadować większy pakiet VSPackage w kontekście, który nie jest dostępny jako CMDUIContext.  
  
 Można użyć <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> metodę wymuszania pakiet VSPackage załadować.  
  
-   Wstaw ten kod do <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metody pakiet VSPackage, który wymusza inny pakiet VSPackage załadować:  
  
    ```csharp  
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;  
    if (shell == null) return;  
  
    IVsPackage package = null;  
    Guid PackageToBeLoadedGuid =   
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);  
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);  
  
    ```  
  
     Po zainicjowaniu pakiet VSPackage zostanie wymuszone `PackageToBeLoaded` do załadowania.  
  
     Ładowanie życie nie powinien służyć do komunikacji pakiet VSPackage. Użyj [Using i dostarczanie usług](../extensibility/using-and-providing-services.md) zamiast tego.
  
## <a name="see-also"></a>Zobacz też  
 [Pakiety VSPackage](../extensibility/internals/vspackages.md)
