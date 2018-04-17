---
title: Parametry niestandardowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2fb61109a05b84eeb83b887ba0fc1a9f9fef299f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="custom-parameters"></a>Parametry niestandardowe
Parametry niestandardowe kontroli działania kreatora, po uruchomieniu kreatora. Plik .vsz powiązane zawiera tablicę parametrów zdefiniowanych przez użytkownika, które opakowane przez zintegrowane środowisko programistyczne (IDE) i przekazać do kreatora jako tablica ciągów, po uruchomieniu kreatora. Następnie Kreator analizuje tablicy ciągów i używa tych informacji do sterowania działaniem rzeczywiste kreatora. W ten sposób kreatora można dostosować funkcjonalność w zależności od zawartości pliku .vsz.  
  
 Parametry kontekstu z drugiej strony, zdefiniuj stan projektu po uruchomieniu kreatora. Aby uzyskać więcej informacji, zobacz [parametrów kontekstu](../../extensibility/internals/context-parameters.md).  
  
 Poniżej znajduje się przykład pliku .vsz, który ma parametry niestandardowe:  
  
```  
VSWIZARD 8.0  
Wizard=VsWizard.VsWizard_Engine  
Param="WIZARD_NAME = Sample Wizard"  
Param="WIZARD_UI = FALSE"  
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"  
Param="PREPROCESS_FUNCTION = CanAddATLSupport"  
Param="PROJECT_TYPE = CSPROJ"  
```  
  
 Autor pliku .vsz dodaje wartości parametrów. Gdy użytkownik wybierze **nowy projekt** lub **Dodaj nowy element** menu Plik lub klikając prawym przyciskiem myszy projekt w **Eksploratora rozwiązań**, IDE zbiera te wartości w tablicy ciągi. IDE wywołuje projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> metody z <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> Flaga zestawu i wywołania projektu <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> metodę, która jest odpowiedzialna za uruchamianie kreatora i zwrócenia wyniku.  
  
 Kreator jest odpowiedzialny za analizowanie tablicy ciągów i odpowiednio działają na ciągi. W ten sposób dzięki implementacji niestandardowych parametrów można utworzyć jednego kreatora, który wykonuje różne funkcje. Innymi słowy jednego kreatora może mieć trzy .vsz różne pliki. Każdy plik przekazuje różnych zestawów niestandardowych parametrów do sterowania zachowaniem kreatora w różnych sytuacjach.  
  
 Aby uzyskać więcej informacji, zobacz [kreatora (. Pliku Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 [Parametry kontekstu](../../extensibility/internals/context-parameters.md)   
 [Kreatorzy](../../extensibility/internals/wizards.md)   
 [Kreator (plik Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)