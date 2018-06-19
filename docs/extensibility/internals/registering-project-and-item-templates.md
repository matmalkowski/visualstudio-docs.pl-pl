---
title: Rejestrowanie szablony projektów i elementów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding items
- registry, Add New Item dialog box
- Add New Item dialog box
- Add New Project dialog box
- registry, Add New Project dialog box
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 85c22d0191d015979dff5a4845c4dda0af96ee60
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133750"
---
# <a name="registering-project-and-item-templates"></a>Rejestrowanie szablony projektów i elementów
Typy projektów należy zarejestrować katalogów, w którym znajdują się ich szablonów projektu i elementu projektu. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] informacje rejestracji skojarzony z typami Twojego projektu są używane do określenia, jakie można wyświetlić w **Dodawanie nowego projektu** i **Dodaj nowy element** okien dialogowych.  
  
 Aby uzyskać więcej informacji o szablonach, zobacz [Dodawanie projekt oraz szablony elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
## <a name="registry-entries-for-projects"></a>Wpisy rejestru dla projektów  
 W poniższych przykładach pokazano wpisy rejestru w HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<*wersji*>. Tabele towarzyszący opisano elementy przykłady.  
  
```  
[Projects\{ProjectGUID}]  
@="MyProjectType"  
"DisplayName"="#2"  
"Package"="{VSPackageGUID}"  
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"  
```  
  
|Nazwa|Typ|Opis|  
|----------|----------|-----------------|  
|@|REG_SZ|Domyślna nazwa projektów tego typu.|  
|Nazwa wyświetlana|REG_SZ|Identyfikator zasobu nazwy mają zostać pobrane z satelitarnej biblioteki DLL zarejestrowany pod pakietów.|  
|Package|REG_SZ|Identyfikator klasy pakietu zarejestrowany pod pakietów.|  
|ProjectTemplatesDir|REG_SZ|Domyślna ścieżka plików szablonu projektu. Pliki szablonów projektu są wyświetlane przez **nowy projekt** szablonu.|  
  
### <a name="registering-item-templates"></a>Rejestrowanie szablony elementu  
 Należy zarejestrować katalog przechowywania szablonów elementów.  
  
```  
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]  
@="#7"  
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "  
"TemplatesLocalizedSubDir"="#10"  
"SortPriority"=dword:00000064  
```  
  
|Nazwa|Typ|Opis|  
|----------|----------|-----------------|  
|@|REG_SZ|Identyfikator zasobu dla szablonów Dodaj element.|  
|TemplatesDir|REG_SZ|Ścieżka projektu elementy wyświetlane w oknie dialogowym **Dodaj nowy element** kreatora.|  
|TemplatesLocalizedSubDir|REG_SZ|Identyfikator zasobu ciągu nazwy podkatalogu TemplatesDir, który zawiera zlokalizowane szablony. Ponieważ [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] obciążeń zasobu ciągu z biblioteki DLL satellite jeśli je, każdy satelitarnej biblioteki DLL może zawierać nazwę podkatalogu zlokalizowane w różnych.|  
|SortPriority|REG_DWORD|Ustaw SortPriority dotyczące kolejności wyświetlania szablonów w **Dodaj nowy element** okno dialogowe. Większe wartości SortPriority są wyświetlane we wcześniejszej części listy szablonów.|  
  
### <a name="registering-file-filters"></a>Rejestrowanie filtry plików  
 Opcjonalnie można zarejestrować filtry który [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] używa podczas jego monit o podanie nazwy pliku. Na przykład [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] Filtruj **Otwórz plik** okno dialogowe jest:  
  
 **Pliki Visual C# (\*.cs,\*resx,\*.settings,\*XSD,\*.wsdl);\*. CS,\*resx,\*.settings,\*XSD,\*.wsdl)**  
  
 Do obsługi rejestracji wielu filtrów, każdy filtr jest zarejestrowany w jego własnej podklucza w HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<*wersji*> \Projects\\{ \< *ProjectGUID*>} \Filters\\<*podklucz*>. Nazwa podklucza jest dowolnego; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ignoruje nazwa podklucza i używa tylko jego wartości.  
  
 Można kontrolować kontekstów, w których filtr jest używany przez ustawienie flagi pokazano w poniższej tabeli. Jeśli filtr nie ma żadnych flag, będzie wyświetlane po filtry wspólne w **Dodaj istniejący element** okno dialogowe i **Otwórz plik** okno dialogowe, ale nie będą używane w **Znajdź w plikach**  okno dialogowe.  
  
```  
[Projects\{ProjectGUID}\Filters\MyLanguageFilter]  
@="#3"  
"CommonOpenFilesFilter"=dword:00000000  
"CommonFindFilesFilter"=dword:00000000  
"FindInFilesFilter"=dword:00000000  
"NotOpenFileFilter"=dword:00000000  
"NotAddExistingItemFilter"=dword:00000000  
"SortPriority"=dword:00000064  
```  
  
|Nazwa|Typ|Opis|  
|----------|----------|-----------------|  
|CommonFindFilesFilter|REG_DWORD|Powoduje, że filtr jednym z typowych filtrów w **Znajdź w plikach** okno dialogowe. Filtry wspólne są wyświetlane na liście filtrów przed filtrami nieoznaczona jako wspólne.|  
|CommonOpenFilesFilter|REG_DWORD|Powoduje, że filtr jednym z typowych filtrów w **Otwórz plik** okno dialogowe. Filtry wspólne są wyświetlane na liście filtrów przed filtrami nieoznaczona jako wspólne.|  
|FindInFilesFilter|REG_DWORD|Wyświetla filtr po filtry wspólne w **Znajdź w plikach** okno dialogowe.|  
|NotOpenFileFilter|REG_DWORD|Wskazuje, czy filtr nie jest używany w **Otwórz plik** okno dialogowe.|  
|NotAddExistingItemFilter|REG_DWORD|Wskazuje, czy filtr nie jest używany w **Dodaj istniejący element** okno dialogowe.|  
|SortPriority|REG_DWORD|Ustaw SortPriority dotyczące kolejności wyświetlania filtrów. Większe wartości SortPriority są wyświetlane wcześniej na liście filtrów.|  
  
## <a name="directory-structure"></a>Struktura katalogów  
 VSPackages można umieścić pliki szablonów i foldery dowolne miejsce na dysku lokalnym lub zdalnym tak długo, jak lokalizacja jest rejestrowane za pomocą zintegrowanego środowiska projektowego (IDE). Jednak w celu ułatwienia organizacji, firma Microsoft zaleca następującą strukturę katalogów w ścieżce instalacji produktu.  
  
 \Templates  
  
 \Projects (zawiera szablony projektów)  
  
 \Applications  
  
 \Components  
  
 \ ...  
  
 \ProjectItems (zawiera elementy projektu)  
  
 \Class  
  
 \Form  
  
 \Web strony  
  
 \HelperFiles (zawiera pliki używane w elementach projektu wielu plików)  
  
 \WizardFiles  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie projekt oraz szablony elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Kreatorzy](../../extensibility/internals/wizards.md)   
 [Lokalizowanie aplikacji](../../ide/localizing-applications.md)   
 [Identyfikatory CATID obiektów, które są zwykle używane do rozszerzania projektów](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)