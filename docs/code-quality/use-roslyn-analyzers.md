---
title: Użyj i skonfiguruj analizatorów Roslyn w programie Visual Studio
ms.date: 03/26/2018
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 2eeebb1fb631c0890c7bcb11160109813a31eef1
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="configure-and-use-roslyn-analyzer-rules"></a>Konfigurowanie i używanie reguły analizatora Roslyn

Reguły analizatora platformy kompilatora .NET ("Roslyn"), lub *diagnostyki*, analiza kodu C# lub Visual Basic podczas pisania. Każdy Diagnostyka ma domyślne ważność i pomijania stan, który może zostać zastąpiona w projekcie. W tym artykule opisano ustawienia reguły ważność, korzystanie z zestawów reguł i pomijanie naruszeń.

## <a name="analyzers-in-solution-explorer"></a>Analizatory w Eksploratorze rozwiązań

Możliwość wiele dostosowań Diagnostyka analizatora z **Eksploratora rozwiązań**. Jeśli zostanie [zainstalować analizatorów](../code-quality/install-roslyn-analyzers.md) jako pakietu NuGet, **analizatorów** węzeł jest wyświetlany w obszarze **odwołania** lub **zależności** węzła w  **Eksplorator rozwiązań**. Po rozwinięciu **analizatorów**, a następnie rozwiń jedno ze zestawy analizatora, zobacz wszystkie diagnostyki w zestawie.

![Węzeł analizatorów w Eksploratorze rozwiązań](media/analyzers-expanded-in-solution-explorer.png)

Można wyświetlić właściwości diagnostyki, łącznie z jej opis i ważność domyślne w **właściwości** okna. Aby wyświetlić właściwości, kliknij prawym przyciskiem myszy reguły, a następnie wybierz **właściwości**, lub wybierz regułę, a następnie naciśnij klawisz **Alt**+**Enter**.

![Właściwości diagnostyki w oknie właściwości](media/analyzer-diagnostic-properties.png)

Aby wyświetlić dokumentację online dla diagnostyki, kliknij prawym przyciskiem myszy na dane diagnostyczne i wybierz **Wyświetl Pomoc**.

Ikony obok każdego diagnostyki w **Eksploratora rozwiązań** odpowiadają ikony zostanie wyświetlony w regule ustawić po otwarciu edytora:

- "i" w okręgu wskazuje [ważność](#rule-severity) z **informacji**
- "!" w trójkąt wskazuje [ważność](#rule-severity) z **ostrzeżenie**
- "x" w koło oznacza [ważność](#rule-severity) z **błąd**
- Wskazuje "i" w okrąg na tle jasnego [ważność](#rule-severity) z **ukryty**
- dół Strzałka w koło informuje, że dane diagnostyczne jest pomijane

![Ikony diagnostyki w Eksploratorze rozwiązań](media/diagnostics-icons-solution-explorer.png)

## <a name="rule-sets"></a>Zestawy reguł

A [zestaw reguł](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) jest plik XML, który zapisuje stan ważność i pomijania dla poszczególnych diagnostyki. Zestawy reguł dotyczą pojedynczego projektu, a projekt może mieć wiele zestawów reguł. Aby wyświetlić dla aktywnego zestawu reguł w edytorze, kliknij prawym przyciskiem myszy **analizatorów** w węźle **Eksploratora rozwiązań** i wybierz **otwórz aktywny zestaw reguł**. Jeśli jest to wartość po raz pierwszy używasz reguły, plik o nazwie  *\<projectname > .ruleset* zostanie dodany do projektu i zostanie wyświetlony w **Eksploratora rozwiązań**.

> [!NOTE]
> Zestawy reguł obejmują zarówno analizy statycznej kodu (binarnego), jak i Roslyn reguły analizatora.

Można zmienić aktywnego zestawu reguł dla projektu na **analizy kodu** we właściwościach projektu. Wybierz dla zestawu reguł w **Uruchom ten zestaw reguł** listy rozwijanej. Można również otworzyć zestawu z reguł **analizy kodu** strony właściwości, wybierając **Otwórz**.

## <a name="rule-severity"></a>Ważność reguły

Można skonfigurować ważność reguły analizatora lub *diagnostyki*, jeśli użytkownik [zainstalować analizatorów](../code-quality/install-roslyn-analyzers.md) jako pakietu NuGet. W poniższej tabeli przedstawiono opcje ważność diagnostyki:

|Ważność|Zachowania w czasie kompilacji|Zachowanie edytora|
|-|-|-|
|Błąd|Naruszenia są wyświetlane jako *błędy* w **listy błędów** w wierszu polecenia dane wyjściowe kompilacji i spowodować niepowodzenie kompilacji.|Naruszeń kodu jest podkreślona czerwonym dowolnym kształcie i oznaczone przy małych czerwonym prostokątem na pasku przewijania.|
|Ostrzeżenie|Naruszenia są wyświetlane jako *ostrzeżenia* w **listy błędów** w wierszu polecenia dane wyjściowe kompilacji, ale nie powodują kompilacji zakończyć się niepowodzeniem.|Naruszeń kodu jest podkreślona z zielonym dowolnym kształcie i oznaczone przy małych zielone pole na pasku przewijania.|
|Informacje o|Naruszenia są wyświetlane jako *wiadomości* w **listy błędów**i w ogóle w danych wyjściowych kompilacji wiersza polecenia.|Naruszeń kodu jest podkreślona z szary dowolnym kształcie i oznaczone przez małe pole szarym pasku przewijania.|
|Hidden|Non widoczny dla użytkownika.|Non widoczny dla użytkownika. Dane diagnostyczne jest jednak zgłoszone aparat diagnostycznych IDE.|
|Brak|Całkowicie pominięty.|Całkowicie pominięty.|

Ponadto można "zresetować" ważność reguły przez ustawienie jej na **domyślne**. Każdy Diagnostyka ma ważność domyślne, które są widoczne w **właściwości** okna.

Poniższy zrzut ekranu przedstawia trzy różne naruszeń diagnostycznych w edytorze kodu w trzech różnych ważności. Zwróć uwagę, kolor dowolnym kształcie, a także małe pole na pasku przewijania po prawej stronie.

![Naruszenie błędu, ostrzeżenia i informacje w edytorze kodu](media/diagnostics-severity-colors.png)

Poniższy zrzut ekranu przedstawia tego samego naruszeń trzy, w jakiej występują **listy błędów**:

![Naruszenie błędu, ostrzeżenia i informacje o liście błędów](media/diagnostics-severities-in-error-list.png)

Można zmienić ważność reguły z **Eksploratora rozwiązań**, lub w  *\<projectname > .ruleset* pliku, który zostanie dodany do rozwiązania, po zmianie ważność regułę w  **Eksplorator rozwiązań**.

![Pliku zestawu reguł w Eksploratorze rozwiązań](media/ruleset-in-solution-explorer.png)

### <a name="to-set-rule-severity-from-solution-explorer"></a>Aby ustawić ważność reguły z Eksploratora rozwiązań

1. W **Eksploratora rozwiązań**, rozwiń węzeł **odwołania** > **analizatorów** (**zależności**  >  **Analizatorów** dla platformy .NET Core projektów).

1. Rozwiń zestaw zawierający regułę, którą chcesz ustawić waga.

1. Kliknij prawym przyciskiem myszy na reguły i wybierz **ustawić ważność ustawić reguły**. W menu wysuwanego wybierz jedną z opcji ważności.

   Ważność reguły są zapisywane w pliku zestawu reguł aktywne.

### <a name="to-set-rule-severity-in-the-rule-set-file"></a>Aby ustawić regułę ważność w regule pliku zestawu

1. Otwórz plik zestawu reguł przez dwukrotne kliknięcie w **Eksploratora rozwiązań**, wybierając żądane **otwórz aktywny zestaw reguł** menu kliknij prawym przyciskiem myszy **analizatorów** węzła, lub wybierając **Otwórz** na **analizy kodu** stronę właściwości projektu.

1. Przejdź do reguły, rozwijając zawierający go zestaw.

1. W **akcji** kolumnę, wybierz wartość otwarcie listy rozwijanej i wybierz żądany ważność z listy.

   ![Pliku zestawu reguł jest otwarty w edytorze](media/ruleset-file-in-editor.png)

## <a name="suppress-violations"></a>Pomiń naruszeń

Istnieje wiele sposobów, aby pominąć naruszeń zasady:

- Aby pominąć wszystkie bieżące naruszenia, wybierz **Analizuj** > **Uruchom analizę kodu i Pomiń aktywne problemy** na pasku menu. Jest to czasami określane jako "określania poziomu odniesienia".

- Aby pominąć Diagnostyka z **Eksploratora rozwiązań**, ustawić jego ważność **Brak**.

- Aby pominąć diagnostyki w edytorze zestawu reguł, usuń zaznaczenie pola wyboru obok jego nazwy lub ustawić **akcji** do **Brak**.

- Aby pominąć diagnostyki w edytorze kodu, umieść kursor w wierszu kodu za pomocą naruszenie i naciśnij klawisz **Ctrl**+**.** Aby otworzyć **szybkie akcje** menu. Wybierz **Pomiń CAxxxx** > **w źródle** lub **Pomiń CAxxxx** > **w pliku pominięć**.

   ![Pomiń diagnostycznych z menu Szybkie akcje](media/suppress-diagnostic-from-editor.png)

- Aby pominąć Diagnostyka z **listy błędów**, kliknij prawym przyciskiem myszy na błąd, ostrzeżenie lub komunikat i wybierz **Pomiń** > **źródła w** lub **Pomiń** > **w pliku pominięć**.

   - W przypadku wybrania **źródła w**, **podgląd zmian** okno dialogowe zostanie otwarte i Podgląd języka C# [ostrzeżenie #pragma](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) lub Visual Basic [ostrzeżenie #Disable](/dotnet/visual-basic/language-reference/directives/directives) dyrektywy, który jest dodawany do kodu źródłowego.

      ![Podgląd Dodawanie ostrzeżenie #pragma w pliku kodu](media/pragma-warning-preview.png)

   - W przypadku wybrania **w pliku pominięć**, **podgląd zmian** okno dialogowe zostanie otwarte i pokazuje podgląd <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atrybut, który zostanie dodany do pliku pominięć globalnych.

      ![Podgląd dodanie atrybutu SuppressMessage do pliku pominięć](media/preview-changes-in-suppression-file.png)

   W **podgląd zmian** okno dialogowe, wybierz opcję **Zastosuj**.

> [!NOTE]
> W projekcie platformy .NET Core Jeśli możesz dodać odwołania do projektu, który ma analizatorów NuGet te analizatory są automatycznie dodawane do projektów zależnych zbyt. Aby wyłączyć to zachowanie, na przykład jeśli projekt zależny jest jednostkowy projekt testowy, oznacz pakietu NuGet jako prywatny w *.csproj* lub *vbproj* pliku przywoływanego projektu:
>
> ```xml
> <PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers" Version="2.6.0" PrivateAssets="all" />
> ```

## <a name="see-also"></a>Zobacz także

- [Omówienie analizatorów Roslyn w programie Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Zgłaszanie usterki analizator Roslyn](https://github.com/dotnet/roslyn-analyzers/issues)
- [Korzystanie z zestawów reguł](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Pomijanie ostrzeżeń analizy kodu](../code-quality/in-source-suppression-overview.md)