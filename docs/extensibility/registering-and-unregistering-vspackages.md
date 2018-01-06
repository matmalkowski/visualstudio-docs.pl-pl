---
title: Rejestrowanie i wyrejestrowywanie VSPackages | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
caps.latest.revision: "35"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7e82b299398d83509883ff152c5f97bd43e800b3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="registering-and-unregistering-vspackages"></a>VSPackages rejestrowania i wyrejestrowywania
Atrybuty służy do rejestrowania pakiet VSPackage, ale  
  
## <a name="registering-a-vspackage"></a>Rejestrowanie pakiet VSPackage  
 Atrybuty można użyć do kontrolowania rejestracji zarządzanych VSPackages. Wszystkie informacje rejestracyjne znajduje się w pliku .pkgdef. Aby uzyskać więcej informacji dotyczących rejestracji opartych na plikach, zobacz [elementu CreatePkgDef narzędzie](../extensibility/internals/createpkgdef-utility.md).  
  
 Poniższy kod przedstawia sposób użycia atrybutów rejestracji standardowej zarejestrować VSPackage.  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]  
public sealed class BasicPackage : Package  
{. . .}  
```  
  
## <a name="unregistering-an-extension"></a>Wyrejestrowywanie rozszerzenia  
 Jeśli były zmieniane wiele różnych VSPackages i chcesz je usunąć z eksperymentalne wystąpienie, można uruchomić tylko **zresetować** polecenia. Wyszukaj **Zresetuj Visual Studio eksperymentalne wystąpienie programu** na stronie początkowej komputera, lub uruchomić to polecenie w wierszu polecenia:  
  
```vb  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp  
```  
  
 Jeśli chcesz odinstalować rozszerzenia, które zainstalowano na programowanie wystąpienia programu Visual Studio, przejdź do **narzędzia / rozszerzenia i aktualizacje**znaleźć rozszerzenia i kliknij przycisk **Odinstaluj**.  
  
 Jeśli zaistnieje powiedzie się żadna z tych metod w odinstalowywania rozszerzenia, można wyrejestrować zestawu pakiet VSPackage z wiersza polecenia w następujący sposób:  
  
```  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>  
```  
  
<a name="using-a-custom-registration-attribute-to-register-an-extension"></a>  
  
## <a name="use-a-custom-registration-attribute-to-register-an-extension"></a>Użyj atrybutu niestandardowego rejestracji, aby zarejestrować rozszerzenie  
  
W niektórych przypadkach może być konieczne utworzyć nowy atrybut rejestracji dla rozszerzenia. Atrybuty rejestracji służy do dodawania nowych kluczy rejestru lub aby dodać nowe wartości do istniejących kluczy. Nowy atrybut musi pochodzić od <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>, i musi ono przesłonić <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> i <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> metody.  
  
### <a name="creating-a-custom-attribute"></a>Tworzenie atrybutów niestandardowych  
  
Poniższy kod przedstawia sposób tworzenia nowego atrybutu rejestracji.  
  
```csharp  
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]  
    public class CustomRegistrationAttribute : RegistrationAttribute  
    {  
    }  
```  
  
 <xref:System.AttributeUsageAttribute> Na klas atrybutów służy do określenia elementu programu (klasy, metody, itp.), którego dotyczy ten atrybut określa, czy można więcej niż jeden raz i czy mogą być dziedziczone.  
  
### <a name="creating-a-registry-key"></a>Tworzenie klucza rejestru  
  
Poniższy kod tworzy atrybutu niestandardowego **niestandardowych** podkluczy klucza dla pakiet VSPackage, który jest rejestrowany.  
  
```csharp  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + @"}\Custom");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
    }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveKey(@"Packages\" + context.ComponentType.GUID + @"}\Custom");  
}  
```  
  
### <a name="creating-a-new-value-under-an-existing-registry-key"></a>Tworzenie nowej wartości istniejącego klucza rejestru  
  
Wartości niestandardowe można dodać do istniejącego klucza. Poniższy kod przedstawia sposób dodawania nową wartość do klucza rejestracji pakiet VSPackage.  
  
```csharp  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + "}");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
                }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveValue(@"Packages\" + context.ComponentType.GUID, "NewCustom");  
}  
```
  
## <a name="see-also"></a>Zobacz też  
 [Pakiety VSPackage](../extensibility/internals/vspackages.md)