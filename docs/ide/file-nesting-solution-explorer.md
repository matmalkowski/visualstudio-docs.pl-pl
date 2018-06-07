---
title: Plik zagnieżdżania reguły dla Eksploratora rozwiązań
ms.date: 05/25/2018
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
helpviewer_keywords:
- file nesting
- Solution Explorer, file nesting
author: angelosp
ms.author: angelpe
manager: douge
ms.openlocfilehash: 3dc06a19abdde00d4572e5c58895dc9b406ae6ba
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34582620"
---
# <a name="customize-file-nesting-in-solution-explorer"></a>Dostosowywanie pliku zagnieżdżenia w Eksploratorze rozwiązań

Zagnieżdżania powiązanych plików w **Eksploratora rozwiązań** nie jest nowe, ale do teraz miało kontroli nad regułami zagnieżdżenia. Możesz wybrać ustawienia wstępne **poza**, **domyślne** i **sieci Web**, ale można również dostosować zagnieżdżanie dokładnie do potrzeb użytkownika. Można również utworzyć określonego rozwiązania i ustawienia specyficzne dla projektu, ale więcej informacji na temat wszystkich później. Przejdź najpierw w ofercie poza pole.

> [!NOTE]
> Ta funkcja jest obecnie obsługiwane tylko dla projektów platformy ASP.NET Core.

## <a name="file-nesting-options"></a>Opcje zagnieżdżenia plików

![Przycisk służący do włączania pliku zagnieżdżania Włącz/Wyłącz](media/filenesting_onoff.png)

Dostępne opcje zagnieżdżenia bez dostosowania plików są następujące:

* **Wyłącz**: Ta opcja umożliwia płaska lista plików bez żadnych zagnieżdżania.

* **Domyślne**: Ta opcja umożliwia domyślnego pliku zagnieżdżania zachowanie w **Eksploratora rozwiązań**. Jeśli nie istnieją żadne ustawienia dla typu danego projektu, żadne pliki w projekcie są zagnieżdżone. Jeśli istnieją ustawienia, na przykład dla projektu sieci Web, zostanie zastosowane zagnieżdżenia.

* **Web**: Ta opcja ma zastosowanie **Web** pliku zagnieżdżenia zachowania do wszystkich projektów w bieżącym rozwiązaniu. Ma ona wiele reguł i firma Microsoft zachęca do go wyewidencjonować i powiedz nam, co myślisz. Poniższy zrzut ekranu wyróżnione kilka przykładów zachowanie zagnieżdżenia pliku, której można korzystać z tej opcji:

   ![Plik zagnieżdżania w Eksploratorze rozwiązań](media/filenesting.png)

## <a name="customize-file-nesting"></a>Dostosowywanie pliku zagnieżdżenia

Jeśli nie podoba, co możesz uzyskać poza pole, można utworzyć własnego, niestandardowego pliku zagnieżdżania ustawień, które poinstruować **Eksploratora rozwiązań** jak zagnieździć plików. Można dodać tyle niestandardowego pliku zagnieżdżenia ustawień, jak Ci się podoba i można przełączać się między nimi zgodnie z potrzebami. Aby utworzyć nowe ustawienie niestandardowych, można uruchomić z pusty plik, lub można użyć **Web** ustawienia jako punktu wyjścia:

![Dodawanie reguł zagnieżdżenia niestandardowego pliku](media/filenesting_addcustom.png)

Zalecane jest użycie **Web** ustawienia z rozpoczynaniem punktu, ponieważ możliwe jest łatwiejsze do pracy z coś już funkcji. Jeśli używasz **Web** ustawienia jako punktu początkowego *. filenesting.json* pliku wygląda podobnie do następującego pliku:

![Użyj istniejącego pliku zagnieżdżania reguły jako podstawa dla ustawień niestandardowych](media/filenesting_editcustom.png)

Ta funkcja pozwala skupić się na węźle **dependentFileProviders** i jego węzły podrzędne. Każdy węzeł podrzędny jest typem reguły, która umożliwia zagnieździć pliki programu Visual Studio. Na przykład **o takiej samej nazwie pliku, ale inne rozszerzenie** jest jeden typ reguły. Reguły dostępne są następujące:

* **extensionToExtension**: Użyj tego typu reguł Aby zagnieździć *file.js* w obszarze *file.ts*

* **fileSuffixToExtension**: Użyj tego typu reguł Aby zagnieździć *vsdoc.js pliku* w obszarze *file.js*

* **addedExtension**: Użyj tego typu reguł Aby zagnieździć *file.html.css* w obszarze *file.html*

* **pathSegment**: Użyj tego typu reguł Aby zagnieździć *jquery.min.js* w obszarze *jquery.js*

* **allExtensions**: Użyj tego typu reguł Aby zagnieździć *pliku.* * w obszarze *file.js*

* **fileToFile**: Użyj tego typu reguł Aby zagnieździć *bower.json* w obszarze *.bowerrc*

### <a name="the-extensiontoextension-provider"></a>Dostawca extensionToExtension

Ten dostawca pozwala zdefiniować reguły zagnieżdżenia pliku przy użyciu określonych rozszerzeń plików. Rozważmy następujący przykład:

![extentionToExtension przykład reguły](media/filenesting_extensiontoextension.png) ![efekt przykład extentionToExtension](media/filenesting_extensiontoextension_effect.png)

* *Cart.js* jest zagnieżdżony w obszarze *cart.ts* ze względu na pierwszy **extensionToExtension** reguły

* *Cart.js* nie jest zagnieżdżony w obszarze *cart.tsx* ponieważ **TS** znajduje się przed **.tsx** w zasadach, i może zawierać tylko jeden obiekt nadrzędny

* *pliku Light.CSS* jest zagnieżdżony w obszarze *light.sass* z powodu drugiego **extensionToExtension** reguły

* *Home.HTML* jest zagnieżdżony w obszarze *home.md* ze względu na trzeci **extensionToExtension** reguły

### <a name="the-filesuffixtoextension-provider"></a>Dostawca fileSuffixToExtension

Ten dostawca działa tak samo jak **extensionToExtension** dostawcy z tylko różnica jest reguła wygląda na sufiks zamiast tylko rozszerzenia pliku. Rozważmy następujący przykład:

![fileSuffixToExtension przykład reguły](media/filenesting_filesuffixtoextension.png) ![efekt przykład fileSuffixToExtension](media/filenesting_filesuffixtoextension_effect.png)

* *Portal vsdoc.js* jest zagnieżdżony w obszarze *portal.js* z powodu **fileSuffixToExtension** reguły

* wszystkie inne aspekty reguły działa tak samo jak **extensionToExtension**

### <a name="the-addedextension-provider"></a>Dostawca addedExtension

Ten dostawca zagnieżdżony pliki z rozszerzeniem dodatkowe w pliku bez rozszerzenia dodatkowe. Dodatkowe rozszerzenia może wystąpić tylko na końcu Pełna nazwa pliku. Rozważmy następujący przykład:

![addedExtension przykład reguły](media/filenesting_addedextension.png) ![efekt przykład addedExtension](media/filenesting_addedextension_effect.png)

* *File.HTML.CSS* jest zagnieżdżony w obszarze *file.html* z powodu **addedExtension** reguły

### <a name="the-pathsegment-provider"></a>Dostawca pathSegment

Ten dostawca zagnieżdżony pliki z rozszerzeniem dodatkowe w pliku bez rozszerzenia dodatkowe. Dodatkowe rozszerzenia może wystąpić tylko w środku Pełna nazwa pliku. Rozważmy następujący przykład:

![pathSegment przykład reguły](media/filenesting_pathsegment.png) ![efekt przykład pathSegment](media/filenesting_pathsegment_effect.png)

* *jquery.min.js* jest zagnieżdżony w obszarze *jquery.js* z powodu **pathSegment** reguły

### <a name="the-allextensions-provider"></a>Dostawca allExtensions

Ten dostawca pozwala zdefiniować reguły zagnieżdżenia pliku dla plików z dowolnego rozszerzenia, ale tej samej nazwie pliku podstawowego. Rozważmy następujący przykład:

![allExtensions przykład reguły](media/filenesting_allextensions.png) ![efekt przykład allExtensions](media/filenesting_allextensions_effect.png)

* *Template.cs* i *szablon.doc* są zagnieżdżone w obszarze *template.tt* z powodu **allExtensions** reguły.

### <a name="the-filetofile-provider"></a>Dostawca fileToFile

Ten dostawca pozwala zdefiniować reguły zagnieżdżenia pliku na podstawie całej nazw plików. Rozważmy następujący przykład:

![fileToFile przykład reguły](media/filenesting_filetofile.png) ![efekt przykład fileToFile](media/filenesting_filetofile_effect.png)

* *bower.JSON* jest zagnieżdżony w obszarze *.bowerrc* z powodu **fileToFile** reguły

### <a name="rule-order"></a>Kolejność reguł

Kolejność jest ważne w każdej części pliku ustawień niestandardowych. Można zmienić kolejność, w której reguły są wykonywane przenosząc je w górę lub w dół wewnątrz **dependentFileProvider** węzła. Na przykład, jeśli jedna reguła, która sprawia, że **file.js** nadrzędny **file.ts** i inną regułę, która sprawia, że **file.coffee** nadrzędny **file.ts**, kolejność, w jakiej występują w pliku nakazują zagnieżdżenia zachowanie, gdy wszystkie trzy pliki są obecne. Ponieważ **file.ts** może mieć tylko jednego zdarzenia nadrzędnego, niezależnie od zasada wykonuje wins pierwszy.

Kolejność są też ważne dla sekcji reguły, nie tylko dla plików znajdujących się w sekcji. Jak parę plików jest zgodny z regułą zagnieżdżenia pliku, dalej do innych reguł w dół w pliku są ignorowane, a dalej parę plików jest przetwarzany.

### <a name="file-nesting-button"></a>Przycisk zagnieżdżenia plik

Wszystkie ustawienia, tym własnych ustawień niestandardowych, za pomocą tego samego przycisku w można zarządzać **Eksploratora rozwiązań**:

![Aktywuj reguły zagnieżdżenia niestandardowego pliku](media/filenesting_activatecustom.png)

## <a name="create-solution-specific-and-project-specific-settings"></a>Tworzenie rozwiązania dotyczące projektu i ustawień

Można tworzyć rozwiązania dotyczące projektu i ustawień za pomocą menu kontekstowego każdego rozwiązania i projektu:

![Rozwiązanie i reguły zagnieżdżenia specyficznego dla projektu](media/filenesting_solutionprojectspecific.png)

Rozwiązania dotyczące projektu i ustawień są łączone z aktywne ustawienia programu Visual Studio. Na przykład może być puste ustawienia specyficzne dla projektu pliku, ale **Eksploratora rozwiązań** nadal jest zagnieżdżanie plików. Zachowanie zagnieżdżenia pochodzi z ustawienia specyficzne dla rozwiązania lub ustawienia programu Visual Studio. Pierwszeństwo do scalenia pliku ustawień zagnieżdżenia jest: Visual Studio > rozwiązania > Projekt.

Visual Studio, aby zignorować rozwiązania dotyczące projektu i ustawień, można określić, nawet jeśli pliki znajdują się na dysku, włączając opcję **Ignoruj ustawienia rozwiązań i projektów** w obszarze **narzędzia**  >  **Opcje** > **platformy ASP.NET Core** > **pliku zagnieżdżenia**.

Można nie odwrotnie i przekaż programowi Visual Studio do *tylko* użyć określonego rozwiązania lub ustawienia specyficzne dla projektu, ustawiając **głównego** węzeł, aby **true**. Visual Studio zatrzymuje scalanie plików na tym poziomie i nie połączyć ją z plików w górę hierarchii.

Rozwiązania dotyczące projektu i ustawień można wyewidencjonowany do kontroli źródła i całego zespołu działa na codebase może udostępniać je.

## <a name="disable-global-file-nesting-rules-for-a-particular-solution-or-project"></a>Wyłącz pliku globalnego zagnieżdżenia reguły dla danego rozwiązania lub projektu

Istniejących reguł zagnieżdżenia pliku globalnego dla określonych rozwiązań lub projektów można wyłączyć za pomocą **Usuń** akcji dla dostawcy zamiast **dodać**. Na przykład dodaj następujący kod ustawień do projektu wszystkie **pathSegment** reguł, które mogą istnieć globalnie dla tego konkretnego projektu są wyłączone:

```json
"dependentFileProviders": {
  "remove": {
    "pathSegment": {}
  }
}
```

## <a name="see-also"></a>Zobacz także

- [Personalizowanie środowiska IDE](../ide/personalizing-the-visual-studio-ide.md)
