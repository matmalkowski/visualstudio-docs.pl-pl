---
title: "Kiedy należy utworzyć typy projektu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: project types, conditions for creating
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b532ad4e72fb15cd9409c362259347f6f3833d2e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="when-to-create-project-types"></a>Kiedy należy utworzyć typy projektów
Tworzenie nowego typu projektu stanowi podstawę do dostosowywania [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dla użytkowników. Tworzenie nowego typu projektu nie jest jednak wymagana dla wszystkich [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dostosowań. Poniższe wskazówki powinny pomóc w określeniu, czy nowy typ projektu jest niezbędna dla danego scenariusza.  
  
## <a name="create-a-new-project-type"></a>Utwórz nowy typ projektu  
 Należy utworzyć typ projektu, jeśli chcesz dostosować [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] do działania w co najmniej jednej z następujących sposobów:  
  
-   Uczestniczy w kompilacji, wdrażanie, konfiguracji i kontroli źródła.  
  
-   Oferuje obsługę debugowania.  
  
-   Wyświetl elementy projektu w **Eksploratora rozwiązań**.  
  
-   Użyj **Otwórz projekt** lub **nowy projekt** okno dialogowe.  
  
-   Obsługuje zagnieżdżenia projektu.  
  
## <a name="extend-an-existing-project-type"></a>Rozszerzanie istniejący typ projektu  
 Należy utworzyć nowy typ projektu, którego można używać [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] w następujący sposób zmodyfikować lub rozszerzyć zachowanie istniejącego typu projektu, na przykład modyfikowanie proces kompilacji [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projektów:  
  
-   Praca z wieloma plikami jako pojedyncza jednostka.  
  
-   Wyświetl pojedynczy plik jako hierarchię elementów podrzędnych.  
  
-   Wyświetlanie w kontekście polecenia wokół edytory.  
  
-   Wyświetlanie w kontekście usługi dla edytory.  
  
## <a name="use-an-existing-project-type"></a>Użyj istniejącego typu projektu  
 Tworzenie nowego projektu Czasami nie jest konieczne. W poniższej tabeli przedstawiono zadania, które nie mają typu projektu dla tworzenia.  
  
|Zadanie|Opis|  
|----------|-----------------|  
|Obsługa poleceń|Wszelkie pakiet VSPackage może obsługiwać poleceń.|  
|Tworzenie edytora|Edytory niestandardowe mogą być rejestrowane. Aby uzyskać więcej informacji, zobacz [okna dokumentów i edytory](http://msdn.microsoft.com/en-us/603625e1-62b6-413a-bc44-089346e166bc).|  
|Właścicielem systemu windows|Można tworzyć zarówno narzędzia i zarządzania dokumentami systemu windows bez dodawania nowego typu projektu.|  
|Udostępnianie właściwości w oknie właściwości|Wszystkie obiekty można ujawnić właściwości.|  
  
## <a name="create-a-project-subtype"></a>Utwórz podtypu projektu  
 Podtypów projektu umożliwia rozszerzanie typu zarządzanego projektu bez konieczności tworzenia nowego typu projektu. Podtypów projektu umożliwia rozszerzanie projektów zarządzanych napisane w programie Microsoft agregacji COM [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] lub [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]. Z agregacją COM można ponownie użyć wiele implementacji systemu zarządzanego projektu i nadal dostosować do danego scenariusza za pośrednictwem agregacji i korzystanie z interfejsów pomocniczych. Aby uzyskać więcej informacji na temat podtypów projektu, zobacz [podtypów projektu](../../extensibility/internals/project-subtypes.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Okna dokumentów i Redaktorzy](http://msdn.microsoft.com/en-us/603625e1-62b6-413a-bc44-089346e166bc)   
 [Lista kontrolna: Tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Hierarchie w programie Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)