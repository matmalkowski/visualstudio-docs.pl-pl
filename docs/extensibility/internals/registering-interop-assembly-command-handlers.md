---
title: "Rejestrowanie programy obsługi poleceń zestawu międzyoperacyjnego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interop assemblies, command handlers
- command handling with interop assemblies, registering
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a25f8adc91efe9d9e8b96079b4fe2e35145abf25
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="registering-interop-assembly-command-handlers"></a>Rejestrowanie zestawu międzyoperacyjnego programy obsługi poleceń
Pakiet VSPackage należy zarejestrować się [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tak, aby prawidłowo polecenia kieruje zintegrowane środowisko programistyczne (IDE).  
  
 Rejestr może zostać zaktualizowana, edytując ręcznie lub za pomocą pliku rejestratora (.rgs). Aby uzyskać więcej informacji, zobacz [tworzenie skrypty rejestratora](/cpp/atl/creating-registrar-scripts).  
  
 Zarządzany pakiet Framework (MPF) zapewnia tę funkcję za pomocą <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> klasy.  
  
 [Polecenie Tabela z odwołaniami Format](http://msdn.microsoft.com/en-us/09e9c6ef-9863-48de-9483-d45b7b7c798f) zasoby znajdują się w niezarządzanych satelitarne bibliotek DLL interfejsu użytkownika.  
  
## <a name="command-handler-registration-of-a-vspackage"></a>Polecenie obsługi rejestracji pakiet VSPackage  
 Pakiet VSPackage działający jako program obsługi dla interfejsu użytkownika (UI) — na podstawie polecenia wymaga wpis rejestru o nazwie po pakiet VSPackage `GUID`. Ten wpis rejestru określa lokalizację pliku zasobu interfejsu użytkownika pakietu VSPackage i zasobów menu, w tym pliku. Wpis rejestru, sama znajduje się w obszarze HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\*\<wersji >*\Menus, gdzie  *\<wersji >* jest to wersja [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], na przykład 9.0.  
  
> [!NOTE]
>  Ścieżka katalogu głównego HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<wersji >* może zostać zastąpiona przez alternatywny główne, kiedy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] powłoki został zainicjowany. Aby uzyskać więcej informacji o ścieżce katalogu głównego, zobacz [instalowanie VSPackages z Instalatora Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md).  
  
### <a name="the-ctmenu-resource-registry-entry"></a>Wpis rejestru CTMENU zasobów  
 Struktura wpisu rejestru to:  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\  
  Menus\  
    <GUID> = <Resource Information>  
```  
  
 \<*Identyfikator GUID*> jest `GUID` z pakiet VSPackage w formie {XXXXXX-XXXX-XXXX-XXXX-XXXXXXXXX}.  
  
 *\<Informacje o zasobie >* składa się z trzech elementów oddzielonych przecinkami. Te elementy znajdują się w kolejności:  
  
 \<*Ścieżka do biblioteki DLL zasobu*>, \< *identyfikator zasobu Menu*>, \< *wersji Menu*>  
  
 W poniższej tabeli opisano pola \< *informacji o zasobie*>.  
  
|Element|Opis|  
|-------------|-----------------|  
|\<*Ścieżka do biblioteki DLL zasobu*>|Jest to pełna ścieżka do zasobów DLL, która zawiera zasób menu lub to pole pozostanie puste, co oznacza, że pakiet VSPackage zasobów DLL do użycia (jak określono w podkluczu pakiety rejestracji pakiet VSPackage, sam).<br /><br /> Jest zwyczajowe pozostawić to pole puste.|  
|\<*Identyfikator zasobu menu*>|To jest identyfikator zasobu `CTMENU` zasób, który zawiera wszystkie elementy interfejsu użytkownika dla pakiet VSPackage opracowane z [vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) pliku.|  
|\<*Wersja menu*>|Jest to liczba używana jako wersji dla `CTMENU` zasobów. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]używa tej wartości w celu określenia, czy wymagane remerge zawartość `CTMENU` zasobów z pamięci podręcznej wszystkich `CTMENU` zasobów. Remerge zostanie wywołany, wykonując polecenia devenv Instalatora.<br /><br /> Ta wartość powinna początkowo ustawiona na 1 i zwiększany po każdej zmianie w `CTMENU` zasobów i przed wystąpieniem remerge.|  
  
### <a name="example"></a>Przykład  
 Oto przykład kilka wpisów zasobów:  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\  
  Menus\  
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10  
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Jak VSPackages dodać elementy interfejsu użytkownika](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Polecenia i menu, w których używane są zestawy międzyoperacyjne](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)