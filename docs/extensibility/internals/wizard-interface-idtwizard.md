---
title: Kreator interfejsu (IDTWizard) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ba6952bce6d99149f2a8f18b7d2eac12cbd08761
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="wizard-interface-idtwizard"></a>Kreator interfejsu (IDTWizard)
Zintegrowane środowisko programistyczne (IDE) używa <xref:EnvDTE.IDTWizard> interfejs do komunikacji z kreatorów. Kreatorzy musi implementować ten interfejs, aby mogło zostać zainstalowane w środowisku IDE.  
  
 <xref:EnvDTE.IDTWizard.Execute%2A> Metoda jest jedyną metodą skojarzone z <xref:EnvDTE.IDTWizard> interfejsu. Kreatorzy zaimplementować tę metodę i IDE wywołuje metodę w interfejsie. W poniższym przykładzie przedstawiono podpis metody.  
  
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
  
 Mechanizm start przypomina zarówno **nowy projekt** i **Dodaj nowy element**kreatorów. Aby rozpocząć, albo, należy wywołać <xref:EnvDTE.IDTWizard> zdefiniowane w Dteinternal.h interfejsu. Jedyną różnicą jest zestaw kontekstu i niestandardowe parametry przekazywane do interfejsu wywołanego interfejsu.  
  
 Poniżej opisano <xref:EnvDTE.IDTWizard> interfejs, który musi implementować kreatorów, aby pracować w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Wywołania IDE <xref:EnvDTE.IDTWizard.Execute%2A> metody w Kreatorze przekazanie jej przez następujące:  
  
-   Obiekt DTE  
  
     Obiekt DTE jest elementem głównym model automatyzacji.  
  
-   Dojście do okna dialogowego okna, jak pokazano w segment kodu `hwndOwner ([in] long)`.  
  
     Kreator używa to `hwndOwner` jako elementu nadrzędnego dla okna dialogowego kreatora.  
  
-   Kontekst parametry przekazywane do interfejsu jako wariant dla parametru SAFEARRAY pokazany w segment kodu `[in] SAFEARRAY (VARIANT)* ContextParams`.  
  
     Parametry kontekstu zawierać tablicę wartości, które są specyficzne dla rodzaju uruchomienie kreatora i bieżący stan projektu. IDE przekazuje parametrów kontekstu do kreatora. Aby uzyskać więcej informacji, zobacz [parametrów kontekstu](../../extensibility/internals/context-parameters.md).  
  
-   Niestandardowe parametry przekazywane do interfejsu jako wariant dla parametru SAFEARRAY pokazany w segment kodu `[in] SAFEARRAY (VARIANT)* CustomParams`.  
  
     Parametry niestandardowe zawiera tablicę parametrów zdefiniowanych przez użytkownika. Plik .vsz przekazuje parametry niestandardowe do środowiska IDE. Wartości są określane przez `Param=` instrukcje. Aby uzyskać więcej informacji, zobacz [niestandardowe parametry](../../extensibility/internals/custom-parameters.md).  
  
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
 [Kreator (. Pliku Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)