---
title: Parametry kontekstu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 642b0cecd700d66db30385f149a30cd09113fc7d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="context-parameters"></a>Parametry kontekstu
W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowane środowisko programistyczne (IDE), możesz dodać kreatorów, aby **nowy projekt**, **Dodaj nowy element**, lub **dodać projektu podrzędnego** okien dialogowych. Dodano kreatorzy są dostępne na **pliku** menu lub klikając prawym przyciskiem myszy projekt w **Eksploratora rozwiązań**. IDE przekazuje parametrów kontekstu do wykonania kreatora. Parametrów kontekstu Zdefiniuj stan projektu, gdy IDE wywołuje kreatora.  
  
 Kreatorów w IDE rozpoczyna się przez ustawienie <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> flagi w wywołaniu IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> metody dla projektu. Po ustawieniu projektu mogą powodować `IVsExtensibility::RunWizardFile` metodę można wykonać przy użyciu nazwy zarejestrowanych kreatora lub identyfikator GUID i innych parametrów kontekstu, które IDE przekazuje do niego.  
  
## <a name="context-parameters-for-new-project"></a>Parametr kontekstu dla nowego projektu  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`WizardType`|Zarejestrowany typ kreatora (<xref:EnvDTE.Constants.vsWizardNewProject>) lub identyfikator GUID, który wskazuje typ kreatora. W [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] implementacji, identyfikator GUID dla kreatora jest {0F90E1D0-4999-11D1-B6D1-00A0C90F2744}.|  
|`ProjectName`|Ciąg, który jest unikatowy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nazwę projektu.|  
|`LocalDirectory`|Lokalizacji lokalnej pracy pliki projektu.|  
|`InstallationDirectory`|Ścieżka katalogu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jest instalacja.|  
|`FExclusive`|Flaga logiczna, która wskazuje, czy projekt powinien zostać zamknięty otwieranie rozwiązań.|  
|`SolutionName`|Nazwa pliku rozwiązania bez części katalogu lub rozszerzenie .sln. Nazwa pliku .suo jest również tworzony przy użyciu `SolutionName`. Jeśli ten argument nie jest ciągiem pustym, kreator używa <xref:EnvDTE._Solution.Create%2A> przed dodaniem projektu z <xref:EnvDTE._Solution.AddFromTemplate%2A>. Jeśli ta nazwa jest ciągiem pustym, użyj <xref:EnvDTE._Solution.AddFromTemplate%2A> bez wywoływania elementu <xref:EnvDTE._Solution.Create%2A>.|  
|`Silent`|Wartość logiczna wskazująca, czy kreatora należy wykonać w trybie cichym tak, jakby **Zakończ** kliknięty (`TRUE`).|  
  
## <a name="context-parameters-for-add-new-item"></a>Parametry kontekstu Dodaj nowy element  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`WizardType`|Zarejestrowany typ kreatora (<xref:EnvDTE.Constants.vsWizardAddItem>) lub identyfikator GUID, który wskazuje typ kreatora. W [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] implementacji, identyfikator GUID dla kreatora jest {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}.|  
|`ProjectName`|Ciąg, który jest unikatowy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nazwę projektu.|  
|`ProjectItems`|Lokalizacji lokalnej, który zawiera pliki projektu pracy.|  
|`ItemName`|Nazwa elementu, który ma zostać dodany. Ta nazwa jest domyślną nazwę pliku lub nazwę pliku, który użytkownik wpisze z **Dodaj elementy** okno dialogowe. Nazwa jest oparta na flagi, które są ustawione w pliku .vsdir. Nazwa może być wartością null.|  
|`InstallationDirectory`|Ścieżka katalogu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jest instalacja.|  
|`Silent`|Wartość logiczna wskazująca, czy kreatora należy wykonać w trybie cichym tak, jakby **Zakończ** kliknięty (`TRUE`).|  
  
## <a name="context-parameters-for-add-sub-project"></a>Parametr kontekstu dla projektu podrzędnego Dodaj  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`WizardType`|Zarejestrowany typ kreatora (<xref:EnvDTE.Constants.vsWizardAddSubProject>) lub identyfikator GUID, który wskazuje typ kreatora. W [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] implementacji, identyfikator GUID dla kreatora jest {0F90E1D2-4999-11D1-B6D1-00A0C90F2744}.|  
|`ProjectName`|Ciąg, który jest unikatowy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nazwę projektu.|  
|`ProjectItems`|Wskaźnik do `ProjectItems` kolekcji, na którym działa Kreator. Ten wskaźnik jest przekazywany do kreatora na podstawie wybranego projektu hierarchii. Zazwyczaj wybiera folder, w którym ma zostać umieszczony element użytkownika, a następnie wywołuje projektu **Dodaj element** okno dialogowe.|  
|`LocalDirectory`|Lokalizacji lokalnej pracy pliki projektu.|  
|`ItemName`|Nazwa elementu, który ma zostać dodany. Ta nazwa jest domyślną nazwę pliku lub nazwę pliku, który użytkownik wpisze z **Dodaj elementy** okno dialogowe. Nazwa jest oparta na flagi, które są ustawione w pliku .vsdir. Nazwa może być wartością null.|  
|`InstallationDirectory`|Ścieżka katalogu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jest instalacja.|  
|`Silent`|Wartość logiczna wskazująca, czy kreatora należy wykonać w trybie cichym tak, jakby **Zakończ** kliknięty (`TRUE`).|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>   
 [Parametry niestandardowe](../../extensibility/internals/custom-parameters.md)   
 [Kreatorzy](../../extensibility/internals/wizards.md)   
 [Kreator (. Pliku Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)   
 [Parametr kontekstu dla uruchamiania kreatorów](http://msdn.microsoft.com/Library/051a10f4-9e45-4604-b344-123044f33a24)