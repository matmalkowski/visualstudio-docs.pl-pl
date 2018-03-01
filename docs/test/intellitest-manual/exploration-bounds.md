---
title: "Granice eksploracji | Narzędzie Test Microsoft IntelliTest dewelopera | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IntelliTest, Exploration bounds
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 6ddcaaac8d814b1f77351a54de121eb641e7fe49
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2018
---
# <a name="exploration-bounds"></a>Granice eksploracji

**PexSettingsAttributeBase** jest abstrakcyjna klasa podstawowa dla ustawienia granic jako atrybuty. Zobacz [wykresu kaskadowego ustawienia](settings-waterfall.md) omówienie ustawień w IntelliTest.

Można zmodyfikować ustawienia za pomocą nazwane właściwości tej lokacji i jego atrybuty pochodne:

```
[PexClass(MaxRuns = 10)]
public partial class FooTest {...}
```

* **Ograniczenia rozwiązywania granic**
  * [MaxConstraintSolverTime](#maxconstraintsolvertime) -liczbę sekund [moduł rozwiązywania ograniczeń](input-generation.md#constraint-solver) ma wejść, które spowodują wykonanie inną ścieżkę należy stosować odnajdywania.
  * [MaxConstraintSolverMemory](#maxconstraintsolvermemory) — rozmiar w megabajtach który [moduł rozwiązywania ograniczeń](input-generation.md#constraint-solver) mogą być używane do wykrywania danych wejściowych.<p />
* **Eksploracja ścieżce zakresem**
  * [MaxBranches](#maxbranches) — maksymalna liczba gałęzie, które mogą zostać podjęte w ścieżce pojedynczego uruchomienia.
  * [MaxCalls](#maxcalls) — maksymalna liczba wywołań, które mogą być nawiązywane podczas ścieżki pojedynczego uruchomienia.
  * [MaxStack](#maxstack) — maksymalny rozmiar stosu w czasie ścieżką pojedynczego uruchomienia, mierzona jako liczba ramek aktywnego połączenia.
  * [MaxConditions](#maxconditions) — maksymalna liczba warunków w danych wejściowych, które mogą być sprawdzane podczas ścieżki pojedynczego uruchomienia.<p />
* **Granice eksploracji**
  * [MaxRuns](#maxruns) — maksymalna liczba uruchomień, które będą podejmowane podczas eksploracji.
  * [MaxRunsWithoutNewTests](#maxrunswithoutnewtests) -maksymalną liczbę kolejnych jest uruchamiana bez nowego testu jest emitowany.
  * [MaxRunsWithUniquePaths](#maxrunswithuniquepaths) — maksymalna liczba uruchomień ze ścieżkami unikatowy wykonanie, które będą podejmowane podczas eksploracji.
  * [MaxExceptions](#maxexceptions) -maksymalną liczbę wyjątków, które mogą znajdować się dla wszystkich ścieżek wykonywania odnalezionych kombinacji.<p />
* **Ustawienia generowania kodu zestawu testów**
  * [TestExcludePathBoundsExceeded](#testexcludepathboundsexceeded) — gdy ma wartość true, wykonanie ścieżek, przekraczające granic ścieżki ([MaxCalls](#maxcalls), [MaxBranches](#maxbranches), [MaxStack](#maxstack), [ MaxConditions](#maxconditions)) są ignorowane.
  * [TestEmissionFilter](#testemissionfilter) — wskazuje, w jakich okolicznościach IntelliTest powinien Emituj testy.
  * [TestEmissionBranchHits](#testemissionbranchhits) — Określa, ile testów emituje IntelliTest.

<a name="maxconstraintsolvertime"></a>
## <a name="maxconstraintsolvertime"></a>MaxConstraintSolverTime

Liczba sekund [moduł rozwiązywania ograniczeń](input-generation.md#constraint-solver) ma można obliczyć danych wejściowych, które spowodują wykonanie inną ścieżkę podjąć. Jest to opcja **PexSettingsAttributeBase** i jego typów pochodnych.

Głębiej tego IntelliTest Eksploruje ścieżek wykonania programu, staną się bardziej złożonych systemów ograniczenia, które IntelliTest tworzy na podstawie przepływu sterowania i przepływu danych programu. W zależności od Twojego ograniczenia czasowe można ustawić tej wartości umożliwia IntelliTest podjęcie bardziej lub mniej czasu odnajdowania nowe wykonywania ścieżki.

Zazwyczaj Przyczyna przekroczenie limitu czasu jest IntelliTest próbuje znaleźć rozwiązania dla systemu ograniczenia, który nie ma rozwiązania, że nie został powiadomiony o tym fakcie. Ponieważ jest to najbardziej typowych przypadkach limitu czasu, może nie mieć warto zwiększyć granicy.

<a name="maxconstraintsolvermemory"></a>
## <a name="maxconstraintsolvermemory"></a>MaxConstraintSolverMemory

Liczba megabajtów który [moduł rozwiązywania ograniczeń](input-generation.md#constraint-solver) ma można obliczyć danych wejściowych, które spowodują wykonanie inną ścieżkę podjąć. Jest to opcja **PexSettingsAttributeBase** i jego typów pochodnych.

Bardziej IntelliTest Eksploruje ścieżek wykonania programu, tym bardziej złożone, które stają się systemów ograniczenia, które IntelliTest tworzy na podstawie przepływu sterowania i przepływu danych programu. W zależności od dostępności pamięci komputera można ustawić tej wartości, aby umożliwić IntelliTest w celu spełnienia bardziej złożonych systemów ograniczenia.

Zazwyczaj Przyczyna przekroczenie limitu czasu jest IntelliTest próbuje znaleźć rozwiązania dla systemu ograniczenia, który nie ma rozwiązania, że nie został powiadomiony o tym fakcie. Ponieważ jest to najczęstsza Przyczyna sytuacji braku pamięci, może nie mieć warto zwiększyć granicy.

<a name="maxbranches"></a>
## <a name="maxbranches"></a>MaxBranches

Maksymalna liczba gałęzie, które mogą zostać podjęte w ścieżce pojedynczego uruchomienia.

Motywacją za to eksploracji powiązany jest ograniczenie długości żadnych ścieżka wykonywania prowadząca IntelliTest Eksploruje podczas [wejściowych generowania](input-generation.md). W szczególności uniemożliwia IntelliTest przestanie odpowiadać, jeśli program przechodzi w pętli nieskończonej.

Każda gałąź warunkowe i bezwarunkowe wykonane i monitorowanych kodu jest liczony kierunku ten limit, w tym gałęzie, które nie są zależne od wejść test sparametryzowany.

Na przykład następujący kod zużywa gałęzie w kolejności 100:

```
for (int i=0; i<100; i++) { }
```

<a name="maxcalls"></a>
## <a name="maxcalls"></a>MaxCalls

Maksymalna liczba wywołań, które mogą być nawiązywane podczas ścieżki pojedynczego uruchomienia.

Motywacją za to eksploracji powiązany jest ograniczenie długości żadnych ścieżka wykonywania prowadząca IntelliTest Eksploruje podczas [wejściowych generowania](input-generation.md). W szczególności uniemożliwia IntelliTest przestanie odpowiadać, gdy program wywołuje cyklicznie metoda nieograniczoną liczbę godzin, które mogłyby spowodować przepełnienie stosu, który IntelliTest nie można odzyskać z.

Każde wywołanie (bezpośrednie, pośrednie, wirtualne, przeskoku) kodu wykonane i monitorowanych zalicza się do tego limitu.

<a name="maxstack"></a>
## <a name="maxstack"></a>MaxStack

Maksymalny rozmiar stosu w czasie ścieżką pojedynczego uruchomienia mierzony przez liczbę ramek aktywnego połączenia.

Motywacją za to eksploracji powiązany ma limit rozmiaru stosu żadnych ścieżka wykonywania prowadząca IntelliTest Eksploruje podczas [wejściowych generowania](input-generation.md). W szczególności uniemożliwia IntelliTest przy użyciu wszystkich miejsca na stosie dostępne, które mogłyby spowodować przepełnienie stosu, który IntelliTest nie można odzyskać.

<a name="maxconditions"></a>
## <a name="maxconditions"></a>MaxConditions

Liczba emaximum warunków w danych wejściowych, które mogą być sprawdzane podczas ścieżki pojedynczego uruchomienia.

Motywacją za to eksploracji powiązany jest ograniczenie złożoności żadnych ścieżka wykonywania prowadząca IntelliTest Eksploruje podczas [wejściowych generowania](input-generation.md). Każda gałąź warunkowa, która zależy od wejść test sparametryzowany zalicza się do tego limitu.

Na przykład każda ścieżka w poniższym kodzie zużywa n + 1 warunki:

```
[PexMethod]
void ParameterizedTest(int n) 
{
     for (int i=0; i<n; i++) { // conditions are "0<n", "1<n", ..., "!(n<n)"
          ...
     }
     for (int i=0; i<100; i++) { // irrelevant for MaxConditions, since conditions do not depend on input
          ...
     }
}
```

<a name="maxruns"></a>
## <a name="maxruns"></a>MaxRuns

TH emaximum Liczba uruchomień IntelliTest zostanie ponowiona podczas eksploracji testu.

Motywacją za to eksploracji powiązany jest dowolny kod, który będzie zawierać pętli lub rekursji może być nieskończona liczba ścieżek wykonywania, czy w związku z tym IntelliTest musi być ograniczona podczas [wejściowych generowania](input-generation.md). 

Dwa ustawienia **MaxRuns** i **MaxRunsWithUniquePaths** są powiązane w następujący sposób: 

* Program IntelliTest zostanie do wywołania metody test sparametryzowany **MaxRuns** czasów dane wejściowe innego testu.
* Jeśli wykonanie kodu jest deterministyczna, IntelliTest potrwa ścieżka wykonywania różnych każdego. 
  Jednak w niektórych warunkach wykonanego kodu może skorzystać z ścieżka wykonywania już trwało przed, z różnych danych wejściowych. 
* IntelliTest zlicza liczbę ścieżek wykonywania unikatowy znajdzie; Ta liczba jest ograniczone przez **MaxRunsWithUniquePaths** opcji.

<a name="maxrunswithoutnewtests"></a>
## <a name="maxrunswithoutnewtests"></a>MaxRunsWithoutNewTests

Maksymalna liczba kolejnych jest uruchamiana bez nowego testu jest emitowany.

Gdy IntelliTest często można znaleźć wiele interesujące dane wejściowe testu w krótkim czasie, po chwili go nie znajdzie żadnego więcej nowe dane wejściowe testu i będzie emitować już testów jednostkowych. Ta opcja konfiguracji umieszcza powiązanej na liczbę kolejnych prób IntelliTest mogą działać bez emitowanie nowego testu. Po przekroczeniu jej spowoduje zatrzymanie badań. 

<a name="maxrunswithuniquepaths"></a>
## <a name="maxrunswithuniquepaths"></a>MaxRunsWithUniquePaths

Maksymalna liczba unikatowych ścieżek, które program IntelliTest zostanie należy wziąć pod uwagę podczas eksploracji.

Motywacją za to eksploracji powiązany jest dowolny kod zawierający pętli lub rekursji może być nieskończona liczba ścieżek wykonywania, czy tak IntelliTest muszą być ograniczone podczas [wejściowych generowania](input-generation.md).

Dwa ustawienia **MaxRuns** i **MaxRunsWithUniquePaths** są powiązane w następujący sposób: 

* Program IntelliTest zostanie do wywołania metody test sparametryzowany **MaxRuns** czasów dane wejściowe innego testu.
* Jeśli wykonanie kodu jest deterministyczna, IntelliTest potrwa ścieżka wykonywania różnych każdego. 
  Jednak w niektórych warunkach wykonanego kodu może skorzystać z ścieżka wykonywania już trwało przed, z różnych danych wejściowych. 
* IntelliTest zlicza liczbę ścieżek wykonywania unikatowy znajdzie; Ta liczba jest ograniczone przez **MaxRunsWithUniquePaths** opcji.

<a name="maxexceptions"></a>
## <a name="maxexceptions"></a>MaxExceptions

Maksymalna liczba wyjątków, które można napotkano przed eksploracji jest zatrzymany.

Motywacją za to eksploracji powiązany jest zatrzymanie eksploracji kodu, który zawiera wiele usterek.
Jeśli program IntelliTest znajdzie zbyt wiele błędów w kodzie, Eksploracja została zatrzymana.

<a name="testexcludepathboundsexceeded"></a>
## <a name="testexcludepathboundsexceeded"></a>TestExcludePathBoundsExceeded

Wykonanie ścieżek, które przekraczają granice skonfigurowanej ścieżki [MaxCalls](#maxcalls), [MaxBranches](#maxbranches), [MaxStack](#maxstack), i [MaxConditions](#maxconditions) są ignorowane.

Motywacją za to eksploracji powiązany jest radzenia sobie z testów niepowodujący (najprawdopodobniej). Gdy program IntelliTest osiągnie eksploracji powiązany, takich jak [MaxCalls](#maxcalls), [MaxBranches](#maxbranches), [MaxStack](#maxstack), lub [MaxConditions](#maxconditions), zakłada się test nie będzie niepowodujący procesu czy nie spowoduje przepełnienie stosu później.
Takie przypadki testowe może spowodować problemy z innych platform testów, a ten atrybut zapewnia sposób zapobiec IntelliTest emitowanie przypadków testowych dla procesów potencjalnie niepowodujący lub przypadków testowych, które będą powodować przepełnienia stosu.

<a name="testemissionfilter"></a>
## <a name="testemissionfilter"></a>TestEmissionFilter

Wskazuje typy testów, które powinny Emituj IntelliTest. Możliwe wartości to:

* **Wszystkie** -Emituj testów dla wszystkich, włącznie z naruszeniem założeń.
* **FailuresAndIncreasedBranchHits** (domyślnie) — Emituj testów dla wszystkich błędów unikatowy i po każdej zmianie przypadkiem testowym zwiększa pokrycia kontrolowane przez [TestEmissionBranchHits](#testemissionbranchhits).
* **FailuresAndUniquePaths** — Emituj testów dla wszystkie błędy znalezione IntelliTest, a także dla każdego testu danych wejściowych, która powoduje ścieżka wykonywania unikatowy.
* **Błędy** -Emituj testy tylko błędów.

<a name="testemissionbranchhits"></a>
## <a name="testemissionbranchhits"></a>TestEmissionBranchHits

W zależności od bieżącej [TestEmissionFilter](#testemissionfilter) ustawienie IntelliTest emituje nowych przypadków testowych z podczas obejmują gałęzi w programie, który nie jest objęty przed.

**TestEmissionBranchHits** ustawienie określa, jeśli IntelliTest tylko należy rozważyć, czy cały objęte gałąź (**TestEmissionBranchHits = 1**), jeśli test objętych usługą, jego raz lub dwa razy ( **TestEmissionBranchHits = 2**) i tak dalej.

**TestEmissionBranchHits = 1** spowoduje utworzenie zestawu testów niewielkie, która będzie obejmować wszystkie gałęzie IntelliTest może skontaktować. W szczególności ten zestaw testów również obejmować wszystkie bloki podstawowe i instrukcjach osiągnął. 

Wartość domyślna dla tej opcji to **TestEmissionBranchHits = 2**, generująca bardziej obszerne zestaw testów, który jest również lepiej dostosowane do wykrywania błędów w przyszłości regresji.

## <a name="got-feedback"></a>Masz opinię?

Publikowania własnych pomysłów i funkcji żądań na  **[UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest)**.
