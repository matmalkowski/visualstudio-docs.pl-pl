---
title: Diagnostyka grafiki programu Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: fa69c550-62a7-41b5-bb1f-7eb04af1a6e8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1974480a2abefaaa38c05f4b1e4588eaddfd480e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="visual-studio-graphics-diagnostics"></a>Diagnostyka grafiki programu Visual Studio
Visual Studio*diagnostyki grafiki* jest zestaw narzędzi dla rejestrowanie i analizowanie danych renderowania i problemom z wydajnością w aplikacjach Direct3D. Diagnostyka grafiki można w aplikacji, które są uruchomione lokalnie na komputerze z systemem Windows w emulatorze urządzenia z systemem Windows lub na zdalnym komputerze lub urządzeniu.  
  
 Przepływ pracy diagnostyki grafiki rozpoczyna się przez Przechwytywanie rekordu w jaki sposób Twoja aplikacja korzysta z Direct3D — na żywo podczas jego wykonywania — tak, aby jego zachowanie można analizować natychmiast, udostępnione lub zapisać na później. Można zainicjować sesji przechwytywania i kontrolować ręcznie z programu Visual Studio lub za pomocą narzędzia wiersza polecenia przechwytywania **dxcap.exe**. Sesje przechwytywania można również zainicjować i kontrolować programowo, za pomocą interfejsów API przechwytywania diagnostyki grafiki.  
  
 Po zarejestrowano sesję przechwytywania jego zawartość może zostać odtworzone przez program Visual Studio *analizatora grafiki* w dowolnym momencie odtworzenie ramki przechwycone przy użyciu dokładnie tych samych zasobów i renderowanie aplikacji używane polecenia. Następnie korzystając z narzędzi dostępnych w oknie Analyer grafiki, dowolnej ramki przechwycone można analizować szczegółowe. Te narzędzia można zbadać każde wywołanie interfejsu API programu Direct3D, zasobów, obiekt stanu potoku, etap potoku lub nawet całą historię dowolny piksel w przechwyconej ramce. Za pomocą tych narzędzi w porozumieniu, problem z renderowaniem można przedstawione intuicyjnie, zaczynając od sposobu jej wyświetlania w przechwyconej ramce i przechodzenie do jego głównej przyczyny w aplikacji źródła kodu, programów do cieniowania lub grafiki zasoby.  
  
 Aby zdiagnozować problemy z wydajnością, przechwyconej ramce można analizować przy użyciu *analizy ramek* narzędzia. To narzędzie Eksploruje potencjalnych optymalizacji wydajności przez automatycznie zmienia sposób aplikacja korzysta z Direct3D i testowania wydajności wszystkich zmian dla Ciebie. W przeszłości może wprowadzono i ręcznie tylko badany rodzaju zmiany można znaleźć out, które z nich wprowadzone różnicy. Z analizy ramek wystarczy wprowadzić zmiany, które już znasz będą przydatne.  
  
 Diagnostyka grafiki pomaga graficznie sformatowanego Direct3D aplikacji wyszukiwania, a następnie uruchom najlepiej.  
  
 Nadal [omówienie](overview-of-visual-studio-graphics-diagnostics.md) Aby dowiedzieć się więcej na temat diagnostyki grafiki w programie Visual Studio oferuje.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Omówienie](overview-of-visual-studio-graphics-diagnostics.md)  
 Wprowadza przepływu pracy diagnostyki grafiki i narzędzia.  
  
 [Wprowadzenie](getting-started-with-visual-studio-graphics-diagnostics.md)  
 W tej sekcji dowiesz się, jak zainstalować diagnostyki grafiki w programie Visual Studio i jak rozpocząć korzystanie z aplikacji Direct3D diagnostyki grafiki.  
  
 [Przechwytywanie informacji graficznych](capturing-graphics-information.md)  
 Aby zbadać problem z renderowaniem w aplikacji przy użyciu diagnostyki grafiki, zapisanie informacji o używaniu aplikacji DirectX. Podczas sesji rejestrowania, co aplikacja działa normalnie, możesz *przechwytywania* (to znaczy, wybrać) ramek, które Cię interesują. Przechwytywanie zawiera szczegółowe informacje na temat sposobu renderowania ramki. Przechwycone dane można zapisać jako grafiki dokument dziennika, aby przejrzeć później lub udostępniać innym członkom zespołu.  
  
 [Użycie procesora GPU](gpu-usage.md)  
 Aby użyć diagnostyki grafiki do profilu aplikacji, użyj narzędzia użycie procesora GPU. Użycie procesora GPU może służyć w połączeniu z innymi narzędziami profilowania, takie jak użycie procesora CPU, służące do skorelowania procesora CPU i procesora GPU działanie, które mogą przyczynić się do problemów z wydajnością w Twojej aplikacji.  
  
 [Dokument dziennika grafiki](graphics-log-document.md)  
 Aby rozpocząć badanie dziennika grafiki zarejestrowane, użyj okna Dokument dziennika grafiki wybierz przechwyconej ramce — lub nawet określonych pikseli — tak, aby zbadać szczegóły *zdarzenia* (to znaczy DirectX wywołania interfejsu API) wpływających na jego .  
  
 [Analiza ramek](graphics-frame-analysis.md)  
 Po zaznaczeniu ramki, należy użyć analiza ramek grafiki do badania i dostrajaniu renderowania.  
  
 [Lista zdarzeń](graphics-event-list.md)  
 Po wybraniu ramki, użyj **listy zdarzeń grafiki** aby zbadać jego zdarzeń, aby określić, czy są one związane z renderowaniem problem.  
  
 [Stan](graphics-state.md)  
 Okno stanu pomaga w zrozumieniu stanu grafiki, który jest aktywny w momencie bieżącego zdarzenia.  
  
 [Etapy potoku](graphics-pipeline-stages.md)  
 W **etapy potoku grafiki** okna, Zbadaj, jak aktualnie zaznaczonego zdarzenia jest przetwarzany przez każdy etap potoku grafiki, dzięki czemu można zidentyfikować, gdy problem z renderowaniem jest najpierw wyświetlany. Badanie etapy potoku jest szczególnie przydatne, gdy obiekt nie pojawia się ze względu na nieprawidłowe transformacji lub jednego z etapów generuje dane wyjściowe, odpowiada kolejnego etapu oczekuje.  
  
 [Stos wywołań zdarzeń](graphics-event-call-stack.md)  
 Możesz użyć **stosu wywołań zdarzeń grafiki** do sprawdzenia stos wywołań aktualnie zaznaczonego zdarzenia, dzięki czemu można nawigować do kodu aplikacji, który dotyczy problem renderowania.  
  
 [Historia pikseli](graphics-pixel-history.md)  
 Za pomocą **Historia pikseli grafiki** okna do analizy wpływu pikseli aktualnie zaznaczonego zdarzenia, które wpływ, można zidentyfikować zdarzenia lub kombinację zdarzenia, które powodują niektóre rodzaje problemów renderowania. Historia pikseli jest szczególnie przydatne w przypadku, gdy obiekt jest renderowany niepoprawnie, ponieważ dane wyjściowe programu do cieniowania pikseli niepoprawna lub została połączona niepoprawnie buforu ramki, lub gdy obiekt nawet nie pojawia się, ponieważ jego pikseli zostały odrzucone. przed dotarciem buforu ramki.  
  
 [Tabela obiektów](graphics-object-table.md)  
 Możesz użyć **tabeli obiektów grafiki** do sprawdzenia właściwości i zawartość z określonymi obiektami Direct3D i zasobów, które obowiązują dla aktualnie zaznaczonego zdarzenia. W tabeli obiektu może pomóc ustalić kontekst urządzenia grafiki, który jest aktywny podczas zdarzenia i sprawdź zawartość zasobów graficznych, takich jak stałe bufory, buforów wierzchołków i tekstury.  
  
 [Debuger HLSL](hlsl-shader-debugger.md)  
 Aby sprawdzić, jak kod programu do cieniowania dla aktualnie zaznaczonego zdarzenia i grafiki etap potoku ma zachowywać się, należy użyć **debuger HLSL** krokowo kodu, sprawdź zawartość zmienne i wykonywanie innych typowych zadań debugowania. Debuger HLSL umożliwia również sprawdzić kod programu do cieniowania obliczeń, niezależnie od tego, czy wyniki są dalej przetwarzane przez potok grafiki i są tylko do odczytu przez aplikację.  
  
 [Narzędzie wiersza polecenia do przechwytywania](command-line-capture-tool.md)  
 Szybkie przechwytywania i odtwarzanie informacji graficznych bez korzystania z programu Visual Studio i przechwycenie programowe za pomocą narzędzia wiersza polecenia przechwytywania. W szczególności można użyć narzędzia wiersza polecenia przechwytywania, automatyzacji lub w środowisku testowym.  
  
 [Przykłady](graphics-diagnostics-examples.md)  
 Przykłady pokazują, jak za pomocą narzędzi diagnostyki grafiki razem diagnozowanie różnego rodzaju problemy z renderowaniem.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Przegląd funkcji debugera](../debugging-in-visual-studio.md)|Wprowadza funkcji debugowania w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].|  
|[Grafika DirectX i gier](http://go.microsoft.com/fwlink/?LinkId=256498)|Zawiera artykuły, które omówiono w nim technologii grafiki DirectX.|