---
title: Zasoby w VSPackages | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d252f61a9f634f4bb8435626c41c586bbe5cb839
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="resources-in-vspackages"></a>Zasoby w VSPackages
Zlokalizowane zasoby można osadzić w natywnej satelitarnej biblioteki DLL interfejsu użytkownika, zarządzanych satelitarnej biblioteki dll, lub zarządzanych pakiet VSPackage sam.  
  
 Niektóre zasoby nie mogą być osadzone w VSPackages. Można ją osadzić następujące typy zarządzane:  
  
-   Ciągi  
  
-   Klucze ładowania pakietu, (które są również ciągi)  
  
-   Narzędzie okna ikony  
  
-   Skompilowane pliki polecenia tabeli danych wyjściowych (CTO)  
  
-   Mapy bitowe CTO  
  
-   Pomoc wiersza polecenia  
  
-   Dane okna dialogowego — informacje  
  
 Wybrano zasobów w pakiecie zarządzanych przez identyfikator zasobu. Wyjątkiem jest pliku CTO, który musi mieć nazwę CTMENU. Pliku CTO musi występować w tabeli zasobu jako `byte[]`. Wszystkie pozostałe elementy zasobów są identyfikowane według typu.  
  
 Można użyć <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> atrybutu, aby poinformować [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dostępnych zasobów zarządzanych.  
  
 [!code-csharp[VSSDKResources#1](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs)]
 [!code-vb[VSSDKResources#1](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]  
  
 Ustawienie <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> w ten sposób oznacza, że [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ignorować niezarządzane satelitarne bibliotek dll podczas wyszukiwania przez nią zasoby, na przykład za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>. Jeśli [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] napotka dwóch lub więcej zasobów, które mają ten sam identyfikator zasobu używa pierwszego znajdzie zasobu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład jest zarządzany reprezentację ikonę okna narzędzia.  
  
```  
<data name="1001"  
type="System.Resources.ResXFileRef,System.Windows.Forms">  
     <value>  
     MyToolWinIcon.bmp;  
     System.Drawing.Bitmap,  
     System.Drawing,  
     Version=1.0.0.0,  
     Culture=neutral,  
     PublicKeyToken=b03f5f7f11d50a3a  
     </value>  
</data>  
```  
  
 W poniższym przykładzie pokazano sposób osadzania tablicy bajtów CTO, który musi mieć nazwę CTMENU.  
  
```  
<data name="CTMENU"  
type="System.Resources.ResXFileRef,System.Windows.Forms">  
     <value>  
     MyPackage.cto;  
     System.Byte[],  
     mscorlib,  
     Version=1.0.0.0,  
     Culture=neutral,  
     PublicKeyToken=b03f5f7f11d50a3a  
     </value>  
</data>  
```  
  
## <a name="implementation-notes"></a>Uwagi dotyczące implementacji  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Ładowanie opóźnienia VSPackages, jeśli to możliwe. Konsekwencją osadzenia pliku CTO w pakiet VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] musi załadować takie VSPackages w pamięci podczas instalacji, który jest podczas tworzenia tabeli polecenia scalone. Zasoby można wyodrębnić z pakiet VSPackage, sprawdzając metadanych bez uruchamiania kodu w pakiecie VSPackage. Pakiet VSPackage nie został zainicjowany w tej chwili, dzięki czemu utrata wydajności jest minimalny.  
  
 Gdy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] żądań zasobu z pakiet VSPackage po zakończeniu instalacji, tego pakietu prawdopodobnie już załadowany i zainicjowany, dzięki czemu utrata wydajności jest minimalny.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie VSPackages](../../extensibility/managing-vspackages.md)   
 [Zasoby zlokalizowane w aplikacjach MFC: biblioteki DLL Satellite](/cpp/build/localized-resources-in-mfc-applications-satellite-dlls)   
