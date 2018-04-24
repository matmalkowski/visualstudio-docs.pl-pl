---
title: Analizowanie użycia sieci w aplikacjach platformy uniwersalnej systemu Windows w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: H1Hack27Feb2017
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 45fa397d-d7a1-4c4c-9c97-ede6c21643bd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a41e41b4448bcec34a24464f4f62e85d0765436d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="analyze-network-usage-in-uwp-apps"></a>Analizowanie użycia sieci w aplikacjach platformy uniwersalnej systemu Windows
Visual Studio **sieci** narzędzie diagnostyczne zbiera dane dotyczące operacji sieciowych wykonywane przy użyciu [Windows.Web.Http API](/uwp/api/windows.web.http). Analizowanie danych może pomóc rozwiązać problemy, takie jak problemy dotyczące dostępu i uwierzytelniania, nieprawidłowe użycie pamięci podręcznej i wyświetlania jest niska i Pobierz wydajności.  
  
 Narzędzie sieci obsługuje tylko aplikacji platformy uniwersalnej systemu Windows. Innych platform nie są obsługiwane w tej chwili.  
  
> [!NOTE]
>  Bardziej szczegółowy opis narzędzia do sieci, zobacz [narzędzie sieci wprowadzenie do programu Visual Studio](http://blogs.msdn.com/b/visualstudio/archive/2015/05/04/introducing-visual-studios-network-tool.aspx).  
  
## <a name="collecting-network-tool-data"></a>Zbieranie danych narzędzie sieci  
 Należy uruchomić **sieci** narzędzie, otwórz projekt programu Visual Studio na komputerze programu Visual Studio.  
  
1.  Otwórz projekt w programie Visual Studio.  
  
2.  W menu, kliknij polecenie **Debug / profilera wydajności...** . Wybierz **sieci**, a następnie wybierz pozycję **Start**.  
  
3.  Narzędzia sieci rozpocznie zbierane danych ruchu HTTP w aplikacji.  
  
     Uruchom aplikację, widok podsumowania w okienku po lewej stronie automatycznie wyświetla listę przechwyconych operacji HTTP. Wybierz element w widoku Podsumowanie, aby uzyskać więcej informacji, w okienku szczegółów w okienku po prawej stronie.  
  
4.  Wybierz **zatrzymać** aby zamknąć aplikację.  
  
 Okno raportu powinna wyglądać mniej więcej tak:  
  
 ![Okno sieci](../profiling/media/network_fullwindow.png "NETWORK_FullWindow")  
  
## <a name="analyzing-data"></a>Analizowanie danych  
 Przechwycony ruch HTTP można analizować uruchomionej aplikacji lub nawet po zamknięciu aplikacji przez wybranie dowolnego operacje sieciowe wyświetlane w widoku podsumowania.  
  
 **Sieci** widok podsumowania zawiera dane dla każdej operacji sieciowej podczas uruchomienia aplikacji. Wybierz nagłówek kolumny, aby posortować listę, lub typy zawartości do wyświetlenia w **typu zawartości** filtrowanie widoku.  
  
 Wybierz **Zapisz jako HAR** do utworzenia pliku JSON, który może być zużyte przez narzędzia innych firm, takie jak Fiddler.  
  
 **Sieci** widoków szczegółów wyświetla więcej informacji na temat operacji sieciowej w widoku podsumowania.  
  
 ![Okienko szczegółów narzędzie sieci](../profiling/media/network_detailsviewpane.png "NETWORK_DetailsViewPane")  
  
|||  
|-|-|  
|**Nagłówki**|Informacje o nagłówku żądania zdarzenia.|  
|**Body**|Danych ładunku żądania i odpowiedzi.|  
|**Parametry**|Nazwy parametrów ciągu zapytania i wartości.|  
|**Plik cookie**|Dane pliku cookie odpowiedzi i żądania.|  
|**Chronometrażu**|Wykres etapy podczas uzyskiwania wybranych zasobów.|  
  
 Sieci **podsumowania** pasek pokazuje liczbę operacji sieciowych, które są wyświetlane na dowolnym etapie, ile danych zostało przeniesione, czas, jaki zajęło Pobierz je oraz ile błędy (liczba żądań z 4xx lub 5xx odpowiedzi) widoczne.  
  
### <a name="analysis-tips"></a>Wskazówki dotyczące analizy  
 Najważniejsze funkcje tego narzędzia, które niektóre obszary, które mogą być przydatne podczas korzystania z sieci związane z analizy:  
  
1.  Żądania, które są w pełni obsługiwane z pamięci podręcznej są wyświetlane jako **(z pamięci podręcznej)** w **odebrane** kolumny. Ułatwia to ustalić, czy używasz pamięci podręcznej skutecznie aby oszczędzić przepustowość użytkownika lub czy buforowanie odpowiedzi przez pomyłkę i dostarczanie użytkowników końcowych aplikacji za pomocą danych nieaktualne.  
  
2.  Błąd odpowiedzi (4xx lub 5xx) są wyświetlane w w **wyniki** kolumny z czerwonym oznaczeniem stanu kodu i są wyróżnione na pasku podsumowania. Dzięki temu ułatwiają błędy między wiele potencjalnych żądań w swojej aplikacji.  
  
3.  Przycisk pretty drukowania odpowiedzi (wewnątrz karta Treść) może pomóc przeanalizować za pośrednictwem ładunków odpowiedzi JSON, XML, HTML, CSS, JavaScript i TypeScript, zwiększając czytelność zawartości.  
  
## <a name="see-also"></a>Zobacz też  
 [Uruchom narzędzia profilowania z lub bez debugera](../profiling/running-profiling-tools-with-or-without-the-debugger.md)  
 [Visual Studio blogu: Inspektor sieci Introducing programu Visual Studio](http://go.microsoft.com/fwlink/?LinkId=535022)   
 [Wideo Channel 9: Narzędzia diagnostyki VS - nowej sieci profilera](http://channel9.msdn.com/Series/ConnectOn-Demand/206)  
 [Profilowanie w programie Visual Studio](../profiling/index.md)  
 [Przegląd funkcji profilowania](../profiling/profiling-feature-tour.md)
