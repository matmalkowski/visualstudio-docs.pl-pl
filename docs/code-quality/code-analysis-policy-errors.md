---
title: Błędy zasad analizy kodu
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- vs.codeanalysis.policyfailures
helpviewer_keywords:
- policy errors, code analysis
ms.assetid: d1f221cd-68c0-4277-9397-b76ad0dbae77
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 625b67972095728d1e9f5c0fd9fa9e5d8da60786
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="code-analysis-policy-errors"></a>Błędy zasad analizy kodu
Następujące błędy wystąpić, jeśli zasad analizy kodu nie jest spełniony na zaewidencjonowania:

 **Ustawienia analizy kodu dla jednego lub więcej projektów nie są zgodne z zasadami analizy kodu.**

 Nie spełniono wymagania dotyczące analizy kodu, ewidencjonowanie do kontroli źródła projektu zespołowego dla jednego lub więcej projektów kodu. Ten błąd może być spowodowany przez jedną lub więcej z następujących warunków:

1.  Nie włączono analizy kodu podczas kompilacji dla wszystkich projektów w rozwiązaniu.

2.  Dla zestawu dla projektu programu Visual Studio ma mniej restrykcyjnych reguł lokalnych **akcji** ustawienie niż zestawu reguł projektu team na przykład regułę, która ma ustawioną wartość **akcji**=**błąd**  na serwerze ma jego **akcji** ustawioną **ostrzeżenie** lub **Brak** w regule ustawić uruchomione w programie Visual Studio).

3.  Zestaw określony w programie Visual Studio reguł nie zawiera wszystkich reguł, które są określone w regule zasad ewidencjonowania analizy kodu dla projektu zespołowego określony zestaw.

 **Zasady analizy kodu nie powiodło się. Wystąpiły błędy w projekcie {0} lub kompilacja nie jest aktualny.**

 Albo kompilacji zawiera błędy, lub błędy zostały usunięte, ale analizy kodu nie została wykonana po poprawki.

 **Zaewidencjonowania nie powiodła się. Zasady analizy kodu wymagają, aby zaewidencjonowania za pomocą programu Visual Studio z otwartym rozwiązaniem.**

 Zasady analizy kodu wymagają, że wszystkie pliki, które zostały zaewidencjonowane musi należeć do aktualnie otwartego rozwiązania. Aby rozwiązać ten problem, otwórz rozwiązanie, które zawiera plik do wyewidencjonowania.

 **Nie wszystkie pliki w oknie oczekujące zaewidencjonowania znajdują się w aktualnie otwartego rozwiązania.**

 Zasady analizy kodu wymagają, że wszystkie pliki, które zostały zaewidencjonowane musi należeć do aktualnie otwartego rozwiązania. Ten błąd jest wywoływane, gdy Otwórz rozwiązanie, ale niektóre pliki w widoku "oczekujące zaewidencjonowania" nie są częścią aktualnie otwarte rozwiązanie. Aby rozwiązać ten problem, otwórz rozwiązanie, które zawiera plik do wyewidencjonowania.

 **Wersja "{0}" jest nieprawidłowa. Silna nazwa-określonym w zasadach jest "{1}".**

 Ten błąd ma zastosowanie do projektów platformy .NET. Biblioteka DLL reguł wymagany przez zasady analizy kodu istnieje na komputerze lokalnym, ale klucza publicznego i wersji jest niezgodny. Aby rozwiązać ten problem, twórca zasad należy zaktualizować bibliotek DLL w *C:\Program Files\Microsoft Visual Studio 8\Team Tools\Static Analysis Tools\FxCop\Rules\\*  katalogu na swoim komputerze.

 **określonym w zasadach zestawu "{0}" nie istnieje.**

 Ten błąd ma zastosowanie do projektów platformy .NET. Reguła wymagane przez zasad analizy kodu nie ma odpowiedniej biblioteki dll zainstalowany na komputerze klienckim. Aby rozwiązać ten problem, twórca zasad należy zaktualizować biblioteki dll w *C:\Program Files\Microsoft Visual Studio 8\Team Tools\Static Analysis Tools\FxCop\Rules\\*  katalogu na swoim komputerze.

 **Ustawienia reguły {0} projektu nie są wyświetlane zgodnie z zasadami analizy kodu.**

 Ten błąd ma zastosowanie do projektów platformy .NET. Ustawienia reguły kodu zarządzanego nie są tak rygorystyczne zasady wymagają. Aby rozwiązać ten problem, ustawienia klienta muszą być takie same lub bardziej restrykcyjne od wymagania zasad na serwerze.

 **Kod — analiza nie jest włączona na aktywną konfigurację. Przełącz do {0} konfiguracji i kompilacji projektu {1} przed zaewidencjonowaniem.**

 W [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], aktywnej konfiguracji nie ma włączone analizy kodu, ale istnieje co najmniej jeden kod — analiza włączone.

 **Należy włączyć analizy kodu dla zarządzanych danych binarnych we właściwościach projektu {0} i kompilacji przed zaewidencjonowaniem.**

 Ten błąd dotyczy [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] aplikacji .NET. Zasady wymagają analiza kodu zarządzanego do wykonania, ale nie jest włączone w bieżącym projekcie na kliencie.

 **Należy włączyć we właściwościach projektu {0} analizy kodu i kompilacji przed zaewidencjonowaniem.**

 Ten błąd dotyczy [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i projektów sieci Web. Zasady wymagają analiza kodu zarządzanego do wykonania, ale nie jest włączone w bieżącym projekcie na kliencie.

 **Należy włączyć analiza kodu C/C++ we właściwościach projektu {0} i kompilacji przed zaewidencjonowaniem.**

 Ten błąd dotyczy niezarządzane projektów. Zasady analizy kodu wymagają analizy kodu dla C/C++, ale nie jest włączone w bieżącym projekcie na kliencie.

## <a name="see-also"></a>Zobacz też
 [Błędy zgłaszane przez aplikację do analizy kodu](../code-quality/code-analysis-application-errors.md)