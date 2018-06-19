---
title: Dodawanie katalogów, aby dodać nowe okno dialogowe elementu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b8d9989e8cf4ec8f0eb714a26e73d89fba339b71
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31127751"
---
# <a name="adding-directories-to-the-add-new-item-dialog-box"></a>Dodawanie katalogów do dodania okno dialogowe Nowy element
Poniższy przykład kodu pokazuje, jak zarejestrować nowy zestaw katalogów **Dodaj nowy element** okno dialogowe. Katalogi do **Dodaj nowy element** okno dialogowe są różne dla każdego projektu. W związku z tym katalogi są rejestrowane w podkluczu projektów znalezione w \<HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects >:  
  
## <a name="the-registry-script"></a>Skrypt rejestru  
  
```  
NoRemove Projects  
{  
  NoRemove %GUID_Project%  
  {  
    NoRemove AddItemTemplates  
    {  
      NoRemove TemplateDirs  
      {  
        ForceRemove %CLSID_Package%  
        {  
      ForceRemove /1 = s '#%Folder_Label_ResID%'  
          {  
            val TemplatesDir = s '%Template_Path%'     
            val SortPriority = d 2000  
          }  
        }  
      }  
    }  
  }  
}  
```  
  
 Wartość Template_Path Określa pełną ścieżkę katalogu, który zawiera szablony projektów. Szablony te można .vsz plików lub pliki szablonów prototypowego w klonowania.  
  
 Wartość SortPriority określa priorytet sortowania.  
  
## <a name="adding-items-to-an-existing-project"></a>Dodawanie elementów do istniejącego projektu  
 Można również dodać elementy do istniejącego projektu. Na przykład w przypadku [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] projektu, można dodać elementy do \<główny > \Program Files\Microsoft Visual Studio \VC#\CSharpProjectItems\LocalProjectItems folderu. W takim przypadku `%GUID_Project%` to identyfikator GUID projektu C# ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).  
  
 Istniejący projekt można rozszerzać przez programowania podtypu projektu. Z podtypem projektu można rozszerzyć projektu bez pisania nowy typ projektu. Aby uzyskać więcej informacji na temat podtypów projektu, zobacz [podtypów projektu](../../extensibility/internals/project-subtypes.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Rejestrowanie szablony projektów i elementów](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Dodawanie elementów do Dodaj nowy element okien dialogowych](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Dodawanie katalogów do okna dialogowego Nowy projekt](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)