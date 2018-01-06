---
title: Elementy modelu projektu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], implementation considerations
- project models
- projects [Visual Studio SDK], elements
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c5f230da41efa8dd2fa522a5f86ae1402991b2cc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="elements-of-a-project-model"></a>Elementy modelu projektu
Interfejsy i implementacje wszystkich projektów w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] udostępnić podstawowej struktury: modelu projektu dla danego typu projektu. W modelu projektu jest pakiet VSPackage, tworzysz, tworzenia obiektów, które spełniają swoje decyzje dotyczące projektu i współdziała z globalnej funkcji udostępnianych przez usługę IDE. Mimo że można kontrolować, jak element projektu jest trwały, na przykład nie kontrolujesz powiadomienia musi zostać utrwalony pliku. Gdy użytkownik umieszcza fokus w elemencie Otwórz projekt i wybiera **zapisać** na **pliku** menu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] menu paska, kodzie typ projektu musi przechwycić polecenie z IDE, utrwalić pliku, i Wyślij powiadomienie do środowiska IDE nie jest już zmiany pliku.  
  
 VSPackage współdziała z IDE za pośrednictwem usług, które zapewniają dostęp do interfejsów IDE. Na przykład za pomocą określonej usługi, należy monitorować i trasy poleceń i podaj informacje o kontekście dla wybranych w projekcie. Wszystkie globalne IDE funkcje wymagane dla VSPackage są udostępniane przez usługi. Aby uzyskać więcej informacji na temat usług, zobacz [porady: uzyskiwanie usługi](../../extensibility/how-to-get-a-service.md).  
  
 Inne uwagi dotyczące implementacji:  
  
-   Model pojedynczego projektu może zawierać więcej niż jeden typ projektu.  
  
-   Typy projektów i fabryk towarzyszącej projektu są zarejestrowane niezależnie z identyfikatorami GUID.  
  
-   Każdy projekt musi mieć plik szablonu lub kreatora w celu zainicjowania nowego pliku projektu, gdy użytkownik tworzy nowy projekt za pomocą [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interfejsu użytkownika. Na przykład [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] szablony zainicjować co przestać .vcproj — pliki.  
  
 Na poniższej ilustracji przedstawiono podstawowy interfejsów, usług i obiekty tworzące wykonania typowych projektu. Pomocnik aplikacji, HierUtil7, można użyć do tworzenia obiektów i inne elementy programowania standardowe. Aby uzyskać więcej informacji na temat HierUtil7 pomocnika aplikacji, zobacz [nie znajduje się w kompilacji: przy użyciu HierUtil7 projektu klasy do zaimplementowania typ projektu (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
 ![Grafika przedstawiająca Visual Studio modelu projektu](../../extensibility/internals/media/vsprojectmodel.gif "vsProjectModel")  
model projektu  
  
 Aby uzyskać więcej informacji na temat interfejsów i usługami wymienionymi w poprzedni diagram i inne opcjonalne interfejsy nie są uwzględnione w diagramie, zobacz [projektu modelu podstawowe składniki](../../extensibility/internals/project-model-core-components.md).  
  
 Projekty może obsługiwać poleceń i dlatego musi implementować <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu do udziału w routing poleceń za pomocą polecenia kontekstu identyfikatorów GUID.  
  
## <a name="see-also"></a>Zobacz też  
 [Lista kontrolna: Tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Nie w kompilacji: Używanie klas projektu HierUtil7 do zaimplementowania typ projektu (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [Projekt modelu podstawowe składniki](../../extensibility/internals/project-model-core-components.md)   
 [Tworzenie wystąpień projektu za pomocą fabryk projektu](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)   
 [Porady: uzyskiwanie usługi](../../extensibility/how-to-get-a-service.md)   
 [Tworzenie typów projektów](../../extensibility/internals/creating-project-types.md)