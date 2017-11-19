---
title: "Tworzenie szablony projektów i elementów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- templates [Visual Studio], projects
- item templates, about item templates
- templates [Visual Studio], item
- Visual Studio templates, item
- Visual Studio templates, about templates
- project templates [Visual Studio], about project templates
- Visual Studio templates, project
- templates [Visual Studio], about templates
ms.assetid: a6ce501a-699b-4e3e-ade8-c81895645c20
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7d95781c2c5c4370e09c13b382016b015ec1a0d5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="creating-project-and-item-templates"></a>Tworzenie szablony projektów i elementów
Szablony projektu i elementu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zapewniają fragmenty do ponownego użycia udostępniające użytkownikom podstawowy kod i struktury, które można wykorzystać do własnych celów.  
  
## <a name="visual-studio-templates"></a>Szablony Visual Studio  
 Wiele wstępnie zdefiniowanych szablonów projektu i elementu jest instalowane podczas instalacji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] i [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] szablonów aplikacji formularzy systemu Windows i biblioteki klas, które są dostępne w **nowy projekt** okno dialogowe przedstawiono przykłady szablonów projektu. Szablony elementów zainstalowane są dostępne w **Dodaj nowy element** okna dialogowego pole i obejmują elementy, takie jak pliki kodu, pliki XML, stron HTML i arkuszy stylów.  
  
 Te szablony zapewniają punkt wyjścia dla użytkowników rozpoczynających tworzenie projektów lub rozszerzanie bieżących projektów. Szablony projektów dostarczają pliki, które są wymagane dla określonego typu projektu, zawierają odwołania do standardowego zestawu i ustawiają domyślne opcje kompilatora i właściwości projektu. Złożoność szablonów elementów może mieścić od zaledwie jednego pustego pliku, który ma poprawne rozszerzenie nazwy pliku po element wieloplikowy, który zawiera na przykład, pliki kodu źródłowego z kodem skróconym, informacje o projektancie plików i zasoby osadzone.  
  
 Oprócz zainstalowanych szablonów w **nowy projekt** i **Dodaj nowy element** okien dialogowych, można tworzyć własne szablony lub pobierania i użyj tworzone przez społeczność. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie szablonów projektów](../ide/how-to-create-project-templates.md) i [porady: Tworzenie szablonów elementów](../ide/how-to-create-item-templates.md).  
  
## <a name="contents-of-a-template"></a>Zawartość szablonu  
 Wszystkie szablony projektów i elementów, instalowane wraz z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] lub utworzone przez użytkownika, działają na podstawie tych samych zasad i spisu treści. Wszystkie szablony zawierają następujące elementy:  
  
-   Pliki, które można utworzyć, jeśli jest używany szablon. Dotyczy to plików kodu źródłowego, zasobów osadzonych, plików projektu i tak dalej.  
  
-   Jeden plik .vstemplate. Ten plik zawiera metadanych, który zapewnia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] informacji należy wyświetlić szablon **nowy projekt** i **Dodaj nowy element** okien dialogowych i tworzenia projektu lub elementu z szablon. Aby uzyskać więcej informacji na temat plików .vstemplate zobacz [parametrów szablonu](../ide/template-parameters.md).  
  
 Jeśli te pliki są skompresowane w pliku .zip i umieszcza w prawidłowym folderze [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automatycznie wyświetla je. Szablony projektu są wyświetlane w **Moje szablony** sekcji **nowy projekt** okien dialogowych i szablony elementów są wyświetlane w **Dodaj nowy element** okien dialogowych. Aby uzyskać więcej informacji o folderach szablonów, zobacz [porady: Znajdź i organizowanie szablonów](../ide/how-to-locate-and-organize-project-and-item-templates.md).  
  
## <a name="starter-kits"></a>Zestawy początkowe  
 Zestawy startowe są rozszerzone przez szablony, które mogą być współużytkowane z innymi członkami społeczności. Zestaw startowy zawiera przykłady kodu, które kompilują, dokumentację i inne zasoby, aby pomóc użytkownikom poznać nowe narzędzia i techniki programowania, podczas tworzenia użytecznych, rzeczywistych aplikacji. Podstawowe zawartości i procedury zestawu startowego są identyczne z tymi szablonami. Aby uzyskać więcej informacji, zobacz [porady: tworzenie Starter Kit](../ide/how-to-create-starter-kits.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Tworzenie szablonów projektów](../ide/how-to-create-project-templates.md)   
 [Porady: Tworzenie szablonów elementu](../ide/how-to-create-item-templates.md)   
 [Parametry szablonu](../ide/template-parameters.md)   
 [Dostosowywanie szablonów](../ide/customizing-project-and-item-templates.md)   
 [Porady: tworzenie zestawów początkowych](../ide/how-to-create-starter-kits.md)