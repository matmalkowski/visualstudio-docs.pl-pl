---
title: Rejestrowanie generatory pojedynczy plik | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 29cbc142be40d4c4e2e8780304767bd17d1d94fe
ms.sourcegitcommit: f36eb7f989efbdbed0d0a087afea8ffe27d8ca15
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2017
---
# <a name="registering-single-file-generators"></a>Rejestrowanie generatory pojedynczego pliku
Aby udostępnić narzędzia niestandardowego w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], musi być zarejestrowany tak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wystąpienie można dodać i kojarzy ją z typu określonego projektu.  
  
### <a name="to-register-a-custom-tool"></a>Aby zarejestrować narzędzia niestandardowego  
  
1.  Zarejestruj to narzędzie niestandardowe biblioteki DLL w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rejestrze lokalnym lub w rejestrze systemu HKEY_CLASSES_ROOT.  
  
     Na przykład poniżej przedstawiono informacje o rejestracji dla zarządzanych MSDataSetGenerator narzędzia niestandardowego, który jest dostarczany z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]:  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]  
    @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"  
    "ThreadingModel"="Both"  
    "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"  
    ```  
  
2.  Utwórz klucz rejestru w żądaną [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gałęzi w obszarze generatory\\*GUID* gdzie *GUID* identyfikator GUID jest definiowana za pomocą określonego języka systemu projektu lub usługi. Nazwa klucza staje się Nazwa programowa własnych narzędzi niestandardowych. Klucz niestandardowe narzędzie ma następujące wartości:  
  
    -   (Domyślnie)  
  
         Opcjonalny. Zawiera opis przyjazną dla użytkownika narzędzia niestandardowego. Ten parametr jest opcjonalny, ale zalecane.  
  
    -   IDENTYFIKATOR CLSID  
  
         Wymagany. Określa identyfikator biblioteki klas składnika modelu COM, który implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>.  
  
    -   GeneratesDesignTimeSource  
  
         Wymagany. Wskazuje, czy typy z utworzonego przez to narzędzie niestandardowe pliki są udostępniane wizualnych projektantów. Wartość tego parametru musi być 0 (zero) dla typów nie jest dostępny do wizualnych projektantów lub 1 (jeden) dla typów dostępne dla wizualnych projektantów.  
  
    > [!NOTE]
    >  Należy zarejestrować narzędzia niestandardowego osobno dla każdego języka, dla której ma zostać narzędzie niestandardowe, które mają być dostępne.  
  
     Na przykład MSDataSetGenerator rejestruje się jeden raz dla każdego języka:  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{164b10b9-b200-11d0-8c61-00a0c91e29d5}\MSDataSetGenerator]  
    @="Microsoft VB Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{fae04ec1-301f-11d3-bf4b-00c04f79efbc}\MSDataSetGenerator]  
    @="Microsoft C# Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>   
 [Implementowanie generatory pojedynczego pliku](../../extensibility/internals/implementing-single-file-generators.md)   
 [Udostępnianie typów wizualnych projektantów](../../extensibility/internals/exposing-types-to-visual-designers.md)   
 [Obiekt BuildManager — wprowadzenie](http://msdn.microsoft.com/en-us/50080ec2-c1c9-412c-98ef-18d7f895e7fa)