---
title: Współtworzenie Dodaj nowy element — okno dialogowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6d8b35537828f99fe3683e03feac3960d6ca4adc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="contributing-to-the-add-new-item-dialog-box"></a>Współtworzenie Dodaj nowy element — okno dialogowe
Podtyp projektu zapewniają pełną nowy katalog elementów dla **Dodaj nowy element** okno dialogowe rejestrując **Dodaj element** szablonów w obszarze `Projects` podklucza rejestru.  
  
## <a name="registering-add-new-item-templates"></a>Rejestrowanie szablonów Dodaj nowy element  
 W tej sekcji znajduje się w obszarze **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects** w rejestrze. Załóżmy z poniższych wpisów rejestru [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projektu agregowane przez podtypu projektu hipotetycznych. Wpisy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projektu są wymienione poniżej.  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}]  
@="#2143"  
"DefaultProjectExtension"="vbproj"  
"PossibleProjectExtensions"="vbproj;vbp"  
"ProjectTemplatesDir"="visualStudioInstallPath\\Vb\\.\\VBProjects"  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}\AddItemTemplates\TemplateDirs\{12345678-1234-1234-1122334455667788}\/1]  
@="#100"  
"TemplatesDir"="projectSubTypeTemplatesDir\\VBProjectItems"  
```  
  
 `AddItemTemplates\TemplateDirs` Podklucz zawiera wpisy rejestru ze ścieżką do katalogu, w którym elementy udostępniona w **Dodaj nowy element** znajdują się okno dialogowe.  
  
 Środowisko automatycznie ładuje wszystkie `AddItemTemplates` dane w ramach `Projects` podklucza rejestru. Mogą to być dane dla implementacji podstawowej projektu, a także danych dla określonego projektu podtyp typów. Każdy podtyp projektu jest identyfikowany przez typ projektu `GUID`. Podtyp projektu można określić, że zestaw alternatywny `Add Item` szablony powinny być używane do wystąpienia określonego projektu przeznaczonego dzięki obsłudze `VSHPROPID_ AddItemTemplatesGuid` wyliczenie z <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> w <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> wykonania zwraca identyfikator GUID wartość podtypu projektu. Jeśli `VSHPROPID_AddItemTemplatesGuid` nie określono właściwości projektu podstawowy identyfikator GUID jest używany.  
  
 Można filtrować elementy **Dodaj nowy element** okno dialogowe zaimplementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> interfejsu w obiekcie agregatora podtypu projektu. Na przykład podtyp projektu implementujący projekt bazy danych przez agregowanie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projekt, można filtrować [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] określonych elementów z **Dodaj nowy element** okno dialogowe zaimplementowanie filtrowania, a w wyłączyć, dodać elementy określonego projektu bazy danych dzięki obsłudze `VSHPROPID_ AddItemTemplatesGuid` w <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>. Aby uzyskać więcej informacji o filtrowaniu i dodawanie elementów do **Dodaj nowy element** okno dialogowe, zobacz [Dodawanie elementów do dodawania nowego elementu okien dialogowych](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Identyfikatory CATID obiektów, które są zwykle używane do rozszerzania projektów](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)