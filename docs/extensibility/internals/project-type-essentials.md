---
title: Projekt typu Essentials | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 899d2758be1561d9b5fbda3280230333cc0ac8a3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="project-type-essentials"></a>Essentials typ projektu
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]obejmuje kilka typów projektów dla języków, takich jak [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] lub [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Umożliwia również tworzenie własnych typów projektów.  
  
 Jeśli chcesz dodać niestandardowe polecenia, edytory lub okna narzędzi do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], możesz to zrobić bez tworzenia nowego typu projektu. Więcej informacji znajduje się w następujących tematach:  
  
-   [Polecenia, menu i paski narzędzi](../../extensibility/internals/commands-menus-and-toolbars.md)  
  
-   [Rozszerzenia edytora i usługi językowej](../../extensibility/editor-and-language-service-extensions.md)  
  
-   [Rozszerzanie i dostosowywanie okien narzędzi](../../extensibility/extending-and-customizing-tool-windows.md)  
  
 Podobnie jeśli chcesz dostosować zachowanie podane [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] i [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] typów projektów, można wykonać za pomocą podtypów projektu. Aby uzyskać więcej informacji, zobacz [podtypów projektu](../../extensibility/internals/project-subtypes.md).  
  
 Należy utworzyć nowy typ projektu dla projektów, które są oparte na języku innym niż [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] i [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] aby obsługuje co najmniej jednej z następujących czynności:  
  
-   Kompilacja  
  
-   wdrażania  
  
-   Wiele konfiguracji  
  
-   Kontrola źródła  
  
-   Debugowanie  
  
-   Elementy projektu w Eksploratorze rozwiązań  
  
-   **Otwórz projekt** lub **nowy projekt** okien dialogowych  
  
-   Zagnieżdżanie projektu  
  
-   Aby uzyskać więcej informacji na temat możliwości typów projektów zobacz następujące tematy:  
  
-   Typy projektów są obiekty pakiet VSPackage, które implementuje zestawu interfejsów [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] oczekuje. Jeśli używasz języka C# umożliwiające tworzenie typu projektu, klasy projektu zarządzane Framework pakietu zaimplementować interfejsów wymaganych i umożliwiają dziedziczą tę implementację. Aby uzyskać więcej informacji, zobacz [przy użyciu platformy pakietu zarządzania do zaimplementowania typ projektu (C#)](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md).  
  
-   Dla deweloperów języka C++ z klas w bibliotece HierUtil działa w podobny sposób. Aby uzyskać więcej informacji, zobacz [nie znajduje się w kompilacji: przy użyciu HierUtil7 projektu klasy do zaimplementowania typ projektu (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
-   Typy projektów może obsługiwać danych innych niż pliki kodu źródłowego typowe, które w zestawie .exe lub .dll. Na przykład [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projektów baz danych zawierają odwołania do skryptu i zapytań plików przechowywanych na dysku i dodać polecenia do **Eksploratora rozwiązań** do wykonywania skryptów i zapytań dotyczących bazy danych, ale projektów nie obsługują Tworzenie zachowanie. Aby uzyskać więcej informacji, zobacz [otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md).  
  
-   Typ projektu nie ma użycie na wszystkich plików. Na przykład typ projektu może przechowywać wszystkie jej dane w bazie danych. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]udostępnia typy projektów pełną kontrolę nad jak stają się dostępne dane dla projektów i elementów projektu. Aby uzyskać więcej informacji, zobacz [decyzji projektowych typ projektu](../../extensibility/internals/project-type-design-decisions.md).  
  
-   Podaj typów projektów *fabrykę projektów*, który jest obiektem, który tworzy wystąpienie projektu zawsze, gdy typ [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] informację, aby otworzyć lub utworzyć projekt, który jest oparty na tym typie projektu. Aby uzyskać więcej informacji, zobacz [tworzenia projektu wystąpień przez za pomocą fabryk projektów przez ustawienie](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
-   Typy projektów podać szablonów dla projektów i elementów projektu. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]używa szablonów, gdy użytkownicy tworzyć nowe projekty i dodawania nowych elementów do istniejących projektów. Aby uzyskać więcej informacji, zobacz [Dodawanie projekt oraz szablony elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
-   Typy projektów może obsługiwać wiele konfiguracji, takich jak Debug i Release. Użytkownicy mogą zmieniać różne konfiguracje projektu za pomocą stron właściwości, które należy podać. Aby uzyskać więcej informacji, zobacz [zarządzanie opcje konfiguracji](../../extensibility/internals/managing-configuration-options.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wdrażanie typów projektów](../../extensibility/internals/deploying-project-types.md)