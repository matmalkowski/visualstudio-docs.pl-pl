---
title: Interfejs kreatora (IDTWizard) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fb811f0ea6ae3d1be01b5d00f6359503d8f0d581
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42676508"
---
# <a name="wizard-interface-idtwizard"></a>Interfejs kreatora (IDTWizard)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [interfejs kreatora (IDTWizard)](https://docs.microsoft.com/visualstudio/extensibility/internals/wizard-interface-idtwizard).  
  
Używa zintegrowanego środowiska programistycznego (IDE) <xref:EnvDTE.IDTWizard> interfejs do komunikacji za pomocą kreatorów. Kreatorzy musi implementować ten interfejs, aby mogło zostać zainstalowane w środowisku IDE.  
  
 <xref:EnvDTE.IDTWizard.Execute%2A> Metody jest jedyną metodą, które są skojarzone z <xref:EnvDTE.IDTWizard> interfejsu. Kreatorzy zaimplementować tę metodę i IDE wywołuje metodę w interfejsie. Poniższy przykład pokazuje podpis metody.  
  
```  
/* IDTWizard Method */  
STDMETHOD(Execute)(THIS_  
   /* [in] */ IDispatch *Application,  
   /* [in] */ long hwndOwner,  
   /* [in] */ SAFEARRAY * *ContextParams,  
   /* [in] */ SAFEARRAY * *CustomParams,  
   /* [out] [in] */ wizardResult *RetVal  
   );  
```  
  
 Mechanizm rozpoczęcia jest podobny dla obu **nowy projekt** i **Dodaj nowy element**kreatorów. Aby rozpocząć, albo, należy wywołać <xref:EnvDTE.IDTWizard> interfejsem zdefiniowanym w Dteinternal.h. Jedyna różnica polega na zestaw kontekstu i parametry niestandardowe, które są przekazywane do interfejsu, po wywołaniu interfejsu.  
  
 Poniższe informacje zawierają opis <xref:EnvDTE.IDTWizard> interfejs, który musi implementować kreatorów, aby pracować w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE. Wywołania środowiska IDE <xref:EnvDTE.IDTWizard.Execute%2A> kreatora, podając mu następujące metody:  
  
-   Obiekt DTE  
  
     Obiekt DTE jest głównym modelu automatyzacji.  
  
-   Dojście do pokazanego poniżej segment kodu, okno dialogowe `hwndOwner ([in] long)`.  
  
     Kreator używa to `hwndOwner` jako element nadrzędny dla okna dialogowego kreatora.  
  
-   Kontekst parametry przekazywane do interfejsu jako wariant dla SAFEARRAY zgodnie z informacjami w segmencie kodu `[in] SAFEARRAY (VARIANT)* ContextParams`.  
  
     Parametry kontekstu zawierać tablicę wartości, które są specyficzne dla rodzaju uruchomieniu kreatora i bieżącego stanu projektu. IDE przekazuje parametrów kontekstu do kreatora. Aby uzyskać więcej informacji, zobacz [parametrów kontekstu](../../extensibility/internals/context-parameters.md).  
  
-   Niestandardowe parametry przekazywane do interfejsu jako wariant dla SAFEARRAY zgodnie z informacjami w segmencie kodu `[in] SAFEARRAY (VARIANT)* CustomParams`.  
  
     Parametry niestandardowe zawierać tablicę parametrów zdefiniowanych przez użytkownika. Plik .vsz przekazuje parametry niestandardowe do środowiska IDE. Wartości są określane przez `Param=` instrukcji. Aby uzyskać więcej informacji, zobacz [parametry niestandardowe](../../extensibility/internals/custom-parameters.md).  
  
-   Są zwracane wartości dla interfejsu  
  
    ```  
    wizardResultSuccess = -1,  
    wizardResultFailure = 0  
    wizardResultCancel = 1  
    wizardResultBackout = 2  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Parametry kontekstu](../../extensibility/internals/context-parameters.md)   
 [Parametry niestandardowe](../../extensibility/internals/custom-parameters.md)   
 [Kreatorzy](../../extensibility/internals/wizards.md)   
 [Kreator (plik Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)

