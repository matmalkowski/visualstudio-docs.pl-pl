---
title: "Dodawanie niestandardowej weryfikacji architektury do diagramów zależności | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: dependency diagrams, adding custom validation
ms.assetid: fed7bc08-295a-46d6-9fd8-fb537f1f75f1
caps.latest.revision: "42"
author: alexhomer1
ms.author: ahomer
manager: douge
ms.openlocfilehash: fe3f64cf11542d0b8098bb9a47c02a2a47647253
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="add-custom-architecture-validation-to-dependency-diagrams"></a>Dodawanie niestandardowej weryfikacji architektury do diagramów zależności
W programie Visual Studio użytkowników można zweryfikować kodu źródłowego w projekcie modelu warstwy, dzięki czemu można zweryfikować, że kod źródłowy odpowiada zależności na diagramie zależności. Brak algorytmu weryfikacji standardowych, ale można zdefiniować rozszerzeń sprawdzania poprawności.  
  
 Gdy użytkownik wybierze **walidację architektury** polecenia na diagramie zależności wywoływana jest metoda weryfikacji standardowe, następuje wszystkich rozszerzeń sprawdzania poprawności, które zostały zainstalowane.  
  
> [!NOTE]
>  Na diagramie zależności w głównym celu zatwierdzenia jest porównania diagramu o kodzie programu w innych częściach rozwiązania.  
  
 Rozszerzenie weryfikacji warstwy można spakować do programu Visual Studio integracji rozszerzenia (VSIX), który można dystrybuować do innych użytkowników programu Visual Studio. Można umieścić z modułu sprawdzania poprawności w pliku VSIX samodzielnie lub połączyć ją w tym samym pliku VSIX jako inne rozszerzenia. Kod modułu sprawdzania poprawności należy zapisać w jego własnej projektu programu Visual Studio, nie znajduje się w tym samym projekcie jako inne rozszerzenia.  
  
> [!WARNING]
>  Po utworzeniu projektu sprawdzania poprawności, skopiuj [przykładowy kod](#example) na końcu tego tematu a następnie Edytuj, aby do własnych potrzeb.  
  
## <a name="requirements"></a>Wymagania  
 Zobacz [wymagania](../modeling/extend-layer-diagrams.md#prereqs).  
  
## <a name="defining-a-layer-validator-in-a-new-vsix"></a>Definiowanie warstwy moduł weryfikacji w ramach nowego pliku VSIX  
 Najszybszą metodą tworzenia moduł weryfikacji ma użyć szablonu projektu. Kod i manifestu VSIX to umieszczenie w tym samym projekcie.  
  
#### <a name="to-define-an-extension-by-using-a-project-template"></a>Aby zdefiniować rozszerzenia za pomocą szablonu projektu  
  
1.  Tworzenie projektu na nowe rozwiązanie, za pomocą **nowy projekt** na **pliku** menu.  
  
2.  W **nowy projekt** okna dialogowego, w obszarze **projektów modelowania**, wybierz pozycję **rozszerzenia weryfikacji projektanta warstwy**.  
  
     Szablon tworzy projekt, który zawiera krótki przykład.  
  
    > [!WARNING]
    >  Do szablonu makethe działają prawidłowo:  
    >   
    >  -   Edytuj wywołań `LogValidationError` usunąć Argumenty opcjonalne `errorSourceNodes` i `errorTargetNodes`.  
    > -   Jeśli używasz właściwości niestandardowe, należy zastosować aktualizację wymienionych w [Dodawanie właściwości niestandardowych do diagramów zależności](../modeling/add-custom-properties-to-layer-diagrams.md).  
  
3.  Edytuj kod, aby zdefiniować z weryfikacji. Aby uzyskać więcej informacji, zobacz [programowania weryfikacji](#programming).  
  
4.  Aby przetestować rozszerzenia, zobacz [Walidacja warstw debugowania](#debugging).  
  
    > [!NOTE]
    >  Stosowana metoda zostanie wywołana tylko w określonych okolicznościach, a punkty przerwania nie będą działać automatycznie. Aby uzyskać więcej informacji, zobacz [Walidacja warstw debugowania](#debugging).  
  
5.  Aby zainstalować rozszerzenie w głównym wystąpienie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], lub na innym komputerze, należy znaleźć **.vsix** w pliku **bin\\\***. Skopiuj go na komputerze, na którym chcesz zainstalować, a następnie kliknij go dwukrotnie. Aby go odinstalować, użyj **rozszerzenia i aktualizacje** na **narzędzia** menu.  
  
## <a name="adding-a-layer-validator-to-a-separate-vsix"></a>Dodawanie warstwy moduł weryfikacji do oddzielnego pliku VSIX  
 Jeśli chcesz utworzyć jedną VSIX, które zawiera warstwy modułów sprawdzania poprawności, polecenie i inne rozszerzenia, zaleca się utworzenie jednego projektu do definiowania pliku VSIX i oddzielne projektów dla programów obsługi. 
  
#### <a name="to-add-layer-validation-to-a-separate-vsix"></a>Aby dodać Walidacja warstw do oddzielnego pliku VSIX  
  
1.  Tworzenie projektu biblioteki klas w nowego lub istniejącego rozwiązania Visual Studio. W **nowy projekt** okno dialogowe, kliknij przycisk **Visual C#** , a następnie kliknij przycisk **biblioteki klas**. Ten projekt będzie zawierać klasy weryfikacji warstwy.  
  
2.  Zidentyfikuj lub tworzenia projektu VSIX w rozwiązaniu. Projektu VSIX zawiera plik o nazwie **source.extension.vsixmanifest**. Jeśli trzeba dodać projektu VSIX, wykonaj następujące kroki:  
  
    1.  W **nowy projekt** oknie dialogowym wybierz **Visual C#**, **rozszerzalności**, **projektu VSIX**.  
  
    2.  W **Eksploratora rozwiązań**, w menu skrótów projektu VSIX **Ustaw jako projekt startowy**.  
  
3.  W **source.extension.vsixmanifest**w obszarze **zasoby**, Dodaj projekt weryfikacji warstwy jako składnik MEF:  
  
    1.  Wybierz **nowe**.  
  
    2.  W **Dodaj nowy element zawartości** okno dialogowe, zestaw:  
  
         **Typ** = **Microsoft.VisualStudio.MefComponent**  
  
         **Źródło** = **projekt w bieżącym rozwiązaniu**  
  
         **Projekt** = *projektu modułu sprawdzania poprawności*  
  
4.  Należy również dodać jako Walidacja warstw:  
  
    1.  Wybierz **nowe**.  
  
    2.  W **Dodaj nowy element zawartości** okno dialogowe, zestaw:  
  
         **Typ** = **Microsoft.VisualStudio.ArchitectureTools.Layer.Validator**. Nie jest jedną z opcji na liście rozwijanej. Należy wprowadzić go z klawiatury.  
  
         **Źródło** = **projekt w bieżącym rozwiązaniu**  
  
         **Projekt** = *projektu modułu sprawdzania poprawności*  
  
5.  Wróć do projektu weryfikacji warstwy i dodaj następujące odwołania do projektu:  
  
    |**Odwołanie**|**Co to umożliwia**|  
    |-------------------|------------------------------------|  
    |Microsoft.VisualStudio.GraphModel.dll|Wykres architektury do odczytu|  
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema.dll|Przeczytaj modelu DOM kodu skojarzonego z warstwy|  
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.dll|Odczytywanie modelu warstwy|  
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility|Odczytywanie i aktualizowanie kształtów i diagramów.|  
    |System.ComponentModel.Composition|Zdefiniuj składnika weryfikacji przy użyciu Managed Extensibility Framework (MEF)|  
    |Microsoft.VisualStudio.Modeling.Sdk. [wersja]|Zdefiniuj rozszerzenia modelowania|  
  
6.  Skopiuj przykładowy kod na końcu tego tematu do pliku klasy w projekcie biblioteki modułu sprawdzania poprawności zawiera kod z weryfikacji. Aby uzyskać więcej informacji, zobacz [programowania weryfikacji](#programming).  
  
7.  Aby przetestować rozszerzenia, zobacz [Walidacja warstw debugowania](#debugging).  
  
    > [!NOTE]
    >  Stosowana metoda zostanie wywołana tylko w określonych okolicznościach, a punkty przerwania nie będą działać automatycznie. Aby uzyskać więcej informacji, zobacz [Walidacja warstw debugowania](#debugging).  
  
8.  Aby zainstalować pliku VSIX w głównym wystąpienie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], lub na innym komputerze, należy znaleźć **.vsix** w pliku **bin** katalogu projektu VSIX. Skopiuj go na komputerze, na którym chcesz zainstalować pliku VSIX. Kliknij dwukrotnie plik VSIX w Eksploratorze Windows. (Eksploratorze plików w systemie Windows 8).  
  
     Aby go odinstalować, użyj **rozszerzenia i aktualizacje** na **narzędzia** menu.  
  
##  <a name="programming"></a>Sprawdzanie poprawności programowania  
 Aby zdefiniować rozszerzenia weryfikacji warstwy, należy zdefiniować klasę, która ma następującą charakterystykę:  
  
-   Formularz ogólny deklaracji jest w następujący sposób:  
  
    ```  
  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema;  
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;  
    using Microsoft.VisualStudio.GraphModel;  
    ...  
     [Export(typeof(IValidateArchitectureExtension))]  
      public partial class Validator1Extension :  
                      IValidateArchitectureExtension  
      {  
        public void ValidateArchitecture(Graph graph)  
        {  
           GraphSchema schema = graph.DocumentSchema;  
          ...  
      } }  
    ```  
  
-   Po odnalezieniu błąd mogą raportować ją przy użyciu `LogValidationError()`.  
  
    > [!WARNING]
    >  Nie używaj opcjonalne parametry `LogValidationError`.  
  
 Gdy użytkownik wywołuje **walidację architektury** polecenia menu, system plików wykonywalnych warstwy analizy warstwy i ich artefaktów do utworzenia wykresu. Wykres ma czterech części:  
  
-   Modele warstw z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozwiązania, które są reprezentowane jako węzły i łącza na wykresie.  
  
-   Kod, elementy projektu i pozostałych artefaktów, które są zdefiniowane w rozwiązaniu i reprezentowane jako węzły i linki reprezentujące zależności wykryte przez proces analizowania.  
  
-   Łącza z węzłów warstwy do węzłów artefaktu kodu.  
  
-   Węzły, które reprezentują błędy wykryte przez moduł sprawdzania.  
  
 Gdy wykresu został utworzony, wywoływana jest metoda standardowa sprawdzania poprawności. Po zakończeniu tej operacji, wszystkie metody weryfikacji zainstalowanego rozszerzenia są nazywane w nieokreślonej kolejności. Wykres jest przekazywana do każdej `ValidateArchitecture` metodę, która pozwala na skanowanie wykres i zgłoszonych błędów, które uzna.  
  
> [!NOTE]
>  Nie jest taka sama jak proces weryfikacji, które mogą być używane w językach specyficznego dla domeny.  
  
 Model warstwy lub kod, który jest sprawdzana, nie należy zmieniać metody sprawdzania poprawności.  
  
 Model wykresu jest zdefiniowany w <xref:Microsoft.VisualStudio.GraphModel>. Jej główną klas są <xref:Microsoft.VisualStudio.GraphModel.GraphNode> i <xref:Microsoft.VisualStudio.GraphModel.GraphLink>.  
  
 Każdy węzeł i każde łącze ma co najmniej jednej kategorii, które określają typ elementu lub relacji, która reprezentuje. Węzły typowy wykres ma następujące kategorie:  
  
-   Dsl.LayerModel  
  
-   Dsl.Layer  
  
-   Dsl.Reference  
  
-   CodeSchema_Type  
  
-   CodeSchema_Namespace  
  
-   CodeSchema_Type  
  
-   CodeSchema_Method  
  
-   CodeSchema_Field  
  
-   CodeSchema_Property  
  
 Łącza od warstwy do elementów w kodzie mają kategorię "Reprezentuje".  
  
##  <a name="debugging"></a>Debugowanie sprawdzania poprawności  
 Aby debugować rozszerzenie weryfikacji warstwy, naciśnij klawisze CTRL + F5. Eksperymentalne wystąpienie programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] otwiera. W tym wystąpieniu otwarcia lub utworzenia modelu warstwy. Ten model musi być skojarzony z kodem i musi mieć co najmniej jedną zależność.  
  
### <a name="test-with-a-solution-that-contains-dependencies"></a>Test z rozwiązaniem, która zawiera zależności  
 Weryfikacja nie została wykonana, chyba że znajdują się następujące właściwości:  
  
-   Istnieje co najmniej jedno łącze zależności na diagramie zależności.  
  
-   Ma warstwy modelu, które są skojarzone z elementy kodu.  
  
 Uruchom eksperymentalne wystąpienie programu po raz pierwszy [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Aby przetestować rozszerzenia sprawdzania poprawności, otwarcia lub utworzenia rozwiązania, które ma następujące cechy.  
  
### <a name="run-clean-solution-before-validate-architecture"></a>Architektura sprawdzania poprawności uruchamiania czystego rozwiązanie przed  
 Po zaktualizowaniu kodu sprawdzania poprawności, użyj **czystą rozwiązania** na **kompilacji** menu w rozwiązaniu eksperymentalne, aby przetestować polecenia sprawdzania poprawności. Jest to konieczne, ponieważ są buforowane wyniki weryfikacji. Jeśli nie zaktualizowano diagramu zależności testowego lub jego kod, nie można wykonać metody sprawdzania poprawności.  
  
### <a name="launch-the-debugger-explicitly"></a>Uruchom debuger jawnie  
 Sprawdzanie poprawności jest uruchamiany w oddzielnych procesach. W związku z tym punkty przerwania w metodę sprawdzania poprawności nie zostanie wywołany. Należy dołączyć debuger do procesu jawnie podczas sprawdzania poprawności została uruchomiona.  
  
 Aby dołączyć debuger do procesu sprawdzania poprawności, wstawianie wywołania do `System.Diagnostics.Debugger.Launch()` na początku metodę sprawdzania poprawności. Gdy pojawi się okno dialogowe debugowania, wybierz główny wystąpienia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Alternatywnie można wstawić wywołania `System.Windows.Forms.MessageBox.Show()`. Po wyświetleniu okna komunikatu, przejdź do wystąpienia głównego [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i na **debugowania** kliknij menu **dołączyć do procesu**. Wybierz proces o nazwie **Graphcmd.exe**.  
  
 Zawsze uruchamiaj eksperymentalne wystąpienie, naciskając klawisze CTRL + F5 (**uruchomić bez debugowania**).  
  
### <a name="deploying-a-validation-extension"></a>Wdrażanie rozszerzenia sprawdzania poprawności  
 Aby zainstalować rozszerzenie sprawdzania poprawności na komputerze, na którym zainstalowano odpowiedniej wersji programu Visual Studio, otwórz plik VSIX na komputerze docelowym. Aby zainstalować na komputerze, na którym [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] jest zainstalowany, należy ręcznie wyodrębnić zawartość pliku VSIX do folderu rozszerzeń. Aby uzyskać więcej informacji, zobacz [wdrażanie rozszerzenia modelu warstwy](../modeling/deploy-a-layer-model-extension.md).  
  
##  <a name="example"></a>Przykładowy kod  
  
```csharp  
using System;  
using System.ComponentModel.Composition;  
using System.Globalization;  
using System.Linq;  
using System.Text.RegularExpressions;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;  
using Microsoft.VisualStudio.GraphModel;  
  
namespace Validator3  
{  
    [Export(typeof(IValidateArchitectureExtension))]  
    public partial class Validator3Extension : IValidateArchitectureExtension  
    {  
        /// <summary>  
        /// Validate the architecture  
        /// </summary>  
        /// <param name="graph">The graph</param>  
        public void ValidateArchitecture(Graph graph)  
        {  
            if (graph == null) throw new ArgumentNullException("graph");  
  
            // Uncomment the line below to debug this extension during validation  
            // System.Windows.Forms.MessageBox.Show("Attach 2 to GraphCmd.exe with process id " + System.Diagnostics.Process.GetCurrentProcess().Id);  
  
            // Get all layers on the diagram  
            foreach (GraphNode layer in graph.Nodes.GetByCategory("Dsl.Layer"))  
            {  
                System.Threading.Thread.Sleep(100);  
                // Get the required regex property from the layer node  
                string regexPattern = "^[a-zA-Z]+$"; //layer[customPropertyCategory] as string;  
                if (!string.IsNullOrEmpty(regexPattern))  
                {  
                    Regex regEx = new Regex(regexPattern);  
  
                    // Get all referenced types in this layer including those from nested layers so each  
                    // type is validated against all containing layer constraints.  
                    foreach (GraphNode containedType in layer.FindDescendants().Where(node => node.HasCategory("CodeSchema_Type")))  
                    {  
                        // Check the type name against the required regex                          
                        CodeGraphNodeIdBuilder builder = new CodeGraphNodeIdBuilder(containedType.Id, graph);  
                        string typeName = builder.Type.Name;  
                        if (!regEx.IsMatch(typeName))  
                        {  
                            // Log an error  
                            string message = string.Format(CultureInfo.CurrentCulture, Resources.InvalidTypeNameMessage, typeName);  
                            this.LogValidationError(graph, typeName + "TypeNameError", message, GraphErrorLevel.Error, layer);  
                        }  
                    }  
                }  
  
            }  
  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie diagramy zależności](../modeling/extend-layer-diagrams.md)
