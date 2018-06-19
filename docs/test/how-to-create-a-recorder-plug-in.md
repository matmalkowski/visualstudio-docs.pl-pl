---
title: Tworzenie wtyczki dla testów wydajności sieci web rejestratora w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, recorder plug-in
ms.assetid: 6fe13be1-aeb5-4927-9bff-35950e194da9
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 008275d4e0ff094c7933b4e0bae89055acd4bf8e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31978180"
---
# <a name="how-to-create-a-recorder-plug-in"></a>Porady: tworzenie wtyczki rejestratora

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin> Umożliwia modyfikowanie zarejestrowane testu wydajności sieci Web. Modyfikacja występuje po wybraniu **zatrzymać** w wydajności sieci Web testów Rejestrator narzędzi, ale przed testu zapisano i prezentowane w edytorze testów wydajności sieci Web.

Wtyczka rejestratora umożliwia wykonywanie własnych niestandardowych korelacji na parametry dynamiczne. Z funkcji wbudowanych korelacji testów wydajności sieci Web wykrywanie parametrów dynamicznych w nagrania sieci Web po zakończeniu lub gdy używasz **Dodawanie parametrów dynamicznych do parametrów testów sieci Web** od wydajności sieci Web Pasek narzędzi edytora testu. Jednak wbudowanych w wykrywaniu funkcji nie zawsze znaleźć wszystkie parametry dynamiczne. Na przykład nie odnajdzie identyfikator sesji, które zwykle pobiera jego wartość została zmieniona od 5 do 30 minut. W związku z tym należy ręcznie przeprowadzić proces korelacji.

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin> Umożliwia pisanie kodu dla własnego niestandardowego dodatku typu plug-in. Ten dodatek, można przeprowadzić korelację lub zmodyfikować testu wydajności sieci Web na wiele sposobów przed jego są zapisywane i przedstawionych w edytorze testów wydajności sieci Web. W związku z tym jeśli okaże się, że określonej zmiennej dynamicznej ma zostać skorelowane dla partii nagrań, można zautomatyzować proces.

Inny sposób, że wtyczka rejestratora mogą być używane jest dodanie wyodrębniania i reguł sprawdzania poprawności, Dodawanie parametrów kontekstu lub test konwertowania komentarz do transakcji w wydajności sieci Web.

Poniższe procedury opisano sposób tworzenie wtyczki rejestratora kod podstawowe, wdrażanie wtyczki i wykonać wtyczki. Przykładowy kod następujące procedury przedstawiono sposób użycia języka Visual C# do tworzenie wtyczki rejestratora korelacji niestandardowego parametru dynamicznego.

## <a name="creating-a-recorder-plug-in"></a>Tworzenie wtyczki rejestratora

### <a name="to-create-a-recorder-plug-in"></a>Aby tworzenie wtyczki rejestratora

1.  Otwórz rozwiązanie, które zawiera wydajności sieci Web i obciążenia projektu testowego z testu wydajności sieci Web, dla którego chcesz tworzenie wtyczki rejestratora.

2.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy rozwiązanie, wybierz **Dodaj**, a następnie wybierz pozycję **nowy projekt**.

     **Dodawanie nowego projektu** zostanie wyświetlone okno dialogowe.

3.  W obszarze **zainstalowane szablony**, wybierz pozycję **Visual C#**.

4.  Na liście szablonów wybierz **biblioteki klas**.

5.  W **nazwa** polu tekstowym, wpisz nazwę wtyczka rejestratora.

     Biblioteka klas jest dodawany do Eksploratora rozwiązań i Nowa klasa jest otwarty w edytorze kodu.

6.  W Eksploratorze rozwiązań w nowym folderze projektu biblioteki klas, kliknij prawym przyciskiem myszy **odwołania** i wybierz polecenie **Dodaj odwołanie**.

    > [!TIP]
    > Przykładem nowego folderu projektu biblioteki klas jest **RecorderPlugins**.

     **Dodaj odwołanie** zostanie wyświetlone okno dialogowe.

7.  Wybierz **.NET** kartę.

8.  Przewiń w dół i wybierz **Microsoft.VisualStudio.QualityTools.WebTestFramework** , a następnie wybierz **OK**.

     **Microsoft.VisualStudio.QualityTools.WebTestFramework** został dodany w **odwołania** folder w Eksploratorze rozwiązań.

9. Pisanie kodu dla wtyczka rejestratora. Najpierw utwórz nową klasę publicznego pochodzącego od <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin>.

10. Zastąpienie <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*> metody.

    ```csharp
    public class Class1 : WebTestRecorderPlugin
        {
            public override void PostWebTestRecording(object sender, PostWebTestRecordingEventArgs e)
            {
                base.PostWebTestRecording(sender, e);
            }
        }
    ```

     Argumenty zdarzenia zostaną wyświetlone dwa obiekty do pracy z: wynik zarejestrowane i zarejestrowane testu wydajności sieci Web. Umożliwi to iterację wyników wyszukiwania dla niektórych wartości, a następnie skok do tego samego żądania testu wydajności sieci Web w celu wprowadzenia zmian. Także po prostu można zmodyfikować testu wydajności sieci Web, jeśli chcesz dodać parametr kontekstowy lub parametryzacja części adresu URL.

    > [!NOTE]
    > Jeśli zmodyfikujesz testu wydajności sieci Web, należy również ustawić <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestRecordingEventArgs.RecordedWebTestModified*> właściwości na wartość true: `e.RecordedWebTestModified = true;`

11. Dodaj więcej kodu w zależności od tego, czego szukasz Rejestrator wtyczki do wykonania po wystąpieniu nagrania sieci Web. Na przykład można dodać kod obsługi korelacji niestandardowych, jak pokazano w poniższym przykładzie. Można również utworzyć wtyczki dla takich elementów rejestratora, jak przetestować konwertowania komentarz do transakcji lub Dodawanie reguły walidacji na wydajność sieci Web.

12. Na **kompilacji** menu, wybierz kompilacji \<Nazwa projektu biblioteki klas >.

13. Następnie należy wdrożyć Rejestrator wtyczki, aby go zarejestrować za pomocą programu Visual Studio.

### <a name="deploy-the-recorder-plug-in"></a>Wdrażanie wtyczka rejestratora

Po skompilowaniu wtyczka rejestratora należy umieścić w jednej z dwóch lokalizacji wynikowa Biblioteka DLL:

-   %ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies\WebTestPlugins

-   %USERPROFILE%\My Documents\Visual Studio \< *wersji*> \WebTestPlugins

> [!WARNING]
> Po skopiowaniu wtyczka rejestratora do jednej z dwóch lokalizacji należy ponownie uruchomić program Visual Studio dla wtyczki rejestrowana rejestratora.

### <a name="to-execute-the-recorder-plug-in"></a>Aby wykonać wtyczka rejestratora

1.  Tworzenie nowego testu wydajności sieci Web.

     **Włączyć WebTestRecordPlugins** Wyświetla okno dialogowe.

2.  Zaznacz pole wyboru dla wtyczka rejestratora, a następnie kliknij przycisk OK.

     Po zakończeniu rejestrowania testu wydajności sieci Web zostaną wykonane nowe wtyczka rejestratora.

    > [!WARNING]
    > Po uruchomieniu testu wydajności sieci Web lub testu obciążenia, który korzysta z dodatku wystąpił błąd może uzyskać podobny do następującego:
    >
    > **Żądanie nie powiodło się: wyjątek w \<wtyczki > zdarzeń: nie można załadować pliku lub zestawu "\<pliku dll"Nazwa wtyczki">, wersja =\<n.n.n.n >, Culture = neutral, PublicKeyToken = null" lub jednej z jego zależności. System nie może odnaleźć określonego pliku.**
    >
    > Jest to spowodowane Jeśli dokonać zmian w kodzie wszelkie wtyczki i utworzyć nową wersję biblioteki DLL **(wersja = 0.0.0.0)**, ale wtyczki nadal odwołuje się do oryginalnej wersji dodatku plug-in. Aby rozwiązać ten problem, wykonaj następujące kroki:
    >
    > 1.  W wydajności sieci Web i obciążenia projekt testowy zostanie wyświetlone ostrzeżenie w odwołaniach. Usuń i ponownie dodać odwołanie do biblioteki DLL dodatku plug-in.
    > 2.  Usuń wtyczki z testu lub odpowiednią lokalizację, a następnie dodaj ją ponownie.

## <a name="example"></a>Przykład

Ten przykład przedstawia sposób tworzenia dostosowanego Rejestrator testu wydajności sieci Web wtyczki do wykonywania niestandardowego parametru dynamicznego korelacji.

> [!NOTE]
> Pełna lista przykładowy kod znajduje się w dolnej części tego tematu.

 **Przeglądanie przykładowy kod**

## <a name="iterate-through-the-result-to-find-first-page-with-reportsession"></a>Iterowanie za pośrednictwem wyników, aby znaleźć pierwszej strony z ReportSession

Ta część przykładowy kod iteruje każdego obiektu zarejestrowane i wyszukuje treść odpowiedzi ReportSession.

```csharp
foreach (WebTestResultUnit unit in e.RecordedWebTestResult.Children)
 {
     WebTestResultPage page = unit as WebTestResultPage;
     if (page != null)
     {
         if (!foundId)
         {
             int indexOfReportSession = page.RequestResult.Response.BodyString.IndexOf("ReportSession");
             if (indexOfReportSession > -1)
             {
```

## <a name="add-an-extraction-rule"></a>Dodawanie reguły wyodrębniania

Teraz, gdy znaleziono odpowiedzi, należy dodać reguły wyodrębniania. Ta część przykładowy kod tworzy przy użyciu reguł wyodrębniania <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRuleReference> klasy, a następnie wyszukuje poprawne żądania w Dodawanie reguły wyodrębniania do testu wydajności sieci Web. Każdy obiekt wyniku ma nową dodana właściwość o nazwie DeclarativeWebTestItemId, czyli, co jest używany w kodzie można odczytać prawidłowe żądania testu wydajności sieci Web.

```csharp
ExtractionRuleReference ruleReference = new ExtractionRuleReference();
     ruleReference.Type = typeof(ExtractText);
     ruleReference.ContextParameterName = "SessionId";
     ruleReference.Properties.Add(new PluginOrRuleProperty("EndsWith", "&ControlID="));
     ruleReference.Properties.Add(new PluginOrRuleProperty("HtmlDecode", "True"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("IgnoreCase", "True"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("Index", "0"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("Required", "True"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("StartsWith", "ReportSession="));
     ruleReference.Properties.Add(new PluginOrRuleProperty("UseRegularExpression", "False"));

     WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
     if (requestInWebTest != null)
     {
         requestInWebTest.ExtractionRuleReferences.Add(ruleReference);
         e.RecordedWebTestModified = true;
     }
```

## <a name="replace-query-string-parameters"></a>Zastąp parametry ciągu zapytania

Teraz kod znajduje wszystkie zapytania parametrów ciągu, które ReportSession jako nazwy i zmień wartość na {{SessionId}}, jak pokazano w tej części przykładowy kod:

```csharp
WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
if (requestInWebTest != null)
{
    foreach (QueryStringParameter param in requestInWebTest.QueryStringParameters)
    {
         if (param.Name.Equals("ReportSession"))
         {
             param.Value = "{{SessionId}}";
         }
     }
 }
```

```csharp
using System.ComponentModel;
using Microsoft.VisualStudio.TestTools.WebTesting;
using Microsoft.VisualStudio.TestTools.WebTesting.Rules;

namespace RecorderPlugin
{
    [DisplayName("Correlate ReportSession")]
    [Description("Adds extraction rule for Report Session and binds this to querystring parameters that use ReportSession")]
    public class CorrelateSessionId : WebTestRecorderPlugin
    {
        public override void PostWebTestRecording(object sender, PostWebTestRecordingEventArgs e)
        {
            //first find the session id
            bool foundId = false;
            foreach (WebTestResultUnit unit in e.RecordedWebTestResult.Children)
            {
                WebTestResultPage page = unit as WebTestResultPage;
                if (page != null)
                {
                    if (!foundId)
                    {
                        int indexOfReportSession = page.RequestResult.Response.BodyString.IndexOf("ReportSession");
                        if (indexOfReportSession > -1)
                        {
                            //add an extraction rule to this request
                            // Get the corresponding request in the Declarative Web performance test
                            ExtractionRuleReference ruleReference = new ExtractionRuleReference();

                            ruleReference.Type = typeof(ExtractText);
                            ruleReference.ContextParameterName = "SessionId";
                            ruleReference.Properties.Add(new PluginOrRuleProperty("EndsWith", "&ControlID="));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("HtmlDecode", "True"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("IgnoreCase", "True"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("Index", "0"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("Required", "True"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("StartsWith", "ReportSession="));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("UseRegularExpression", "False"));

                            WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
                            if (requestInWebTest != null)
                            {
                                requestInWebTest.ExtractionRuleReferences.Add(ruleReference);
                                e.RecordedWebTestModified = true;
                            }
                            foundId = true;

                        }
                    }
                    else
                    {
                        //now update query string parameters
                        WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
                        if (requestInWebTest != null)
                        {
                            foreach (QueryStringParameter param in requestInWebTest.QueryStringParameters)
                            {
                                if (param.Name.Equals("ReportSession"))
                                {
                                    param.Value = "{{SessionId}}";
                                }
                            }
                        }
                    }
                }
            }
        }
    }
}
```

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRuleReference>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*>
- [Tworzenie niestandardowych kodów i wtyczek dla testów obciążenia](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Generowanie i Uruchamianie testów wydajności sieci web kodowane](../test/generate-and-run-a-coded-web-performance-test.md)