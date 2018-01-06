---
title: Dokument dziennika grafiki | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.graphics.vsglog.error
- vs.graphics.experiment
- vs.graphics.vsglog
ms.assetid: 6ccb1269-d55f-49c4-920d-baedf7de2888
caps.latest.revision: "31"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 30abe64fa54e7b63e1552ab2e4c5ce95ac11befc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="graphics-log-document"></a>Dokument dziennika grafiki
Dokument dziennika grafiki jest rekord zdarzenia grafiki, które wystąpiły podczas, gdy aplikacja była uruchomiona w obszarze sesję diagnostyki grafiki. Po rejestrowane, można sprawdzić dziennik w analizatora grafiki programu Visual Studio do diagnozowania problemów renderowania i wydajność.  
  
 To jest jakie dokument dziennika grafiki prawdopodobnie w analizatorze grafiki domen:  
  
 ![Dziennik grafiki zawierających dwie ramki przechwycone. ] (media/gfx_diag_demo_graphics_log_orientation.png "gfx_diag_demo_graphics_log_orientation")  
  
## <a name="understanding-graphics-log-documents"></a>Opis grafiki dziennika dokumentów  
 Za pomocą analizatora grafiki do sprawdzenia dokument dziennika grafiki, można zwizualizować skutków Direct3D zdarzeń w celu renderowania, który wystąpił podczas przechwytywania. Można wskazać regiony obiektu docelowego renderowania, które zawierają nieoczekiwane dane wyjściowe. Po wybraniu piksel w regionie, których dotyczy, można użyć diagnostyki grafiki do zbadania go, jego programów do cieniowania zdarzenia Direct3D, których ona dotyczy, stos wywołań aplikacji, które doprowadziło do tych zdarzeń i obiektów programu DirectX, które obsługują te zdarzenia. Te informacje można użyć do diagnozowania problemów renderowania w aplikacji lub gry.  
  
 W górnej części okna (**Experiment.vsglog grafiki**) Wyświetla bieżący renderowania danych wyjściowych zaznaczonej ramki i wyświetla część dolnej **listy ramek** zawierający obrazy miniatur ramki przechwycone.  
  
#### <a name="to-inspect-a-frame"></a>Aby sprawdzić ramki  
  
-   W **listy ramek**, wybierz ramki, w której chcesz sprawdzić. Renderowanie danych wyjściowych w górnej części dokument dziennika grafiki zostało zaktualizowane do wyświetlenia zaznaczonej ramki.  
  
#### <a name="to-inspect-a-pixel"></a>Aby sprawdzić piksel  
  
-   W górnej części dokument dziennika grafiki wybierz pikseli, który ma z danych wyjściowych docelowego renderowania. Po wybraniu piksel służy **Historia pikseli grafiki** okna, aby wyświetlić szczegółowe informacje na temat wybranego piksela. Aby uzyskać więcej informacji, zobacz [historii pikseli](graphics-pixel-history.md).  
  
## <a name="playback-machine"></a>Maszyny odtwarzania  
 Wyświetlany również w prawym górnym rogu **listy ramek** jest **maszyny odtwarzania**. Maszynie odtwarzającej jest komputera lub urządzenia, które służy do odtwarzania zdarzeń grafiki z plikiem dziennika grafiki podczas sesji diagnostyki grafiki nowsze. Przy użyciu innego urządzenia zamiast komputerze deweloperskim, aby odtworzyć zdarzeń przechwyconych, dokładniej odtworzyć środowiska wykonawczego, w której występuje problem — na przykład można użyć na komputerze, który ma inną grafiki sprzętu lub sterowników niż te, które używa na komputerze deweloperskim, lub inne rodzaje urządzeń, takich jak urządzenia z systemem tablet opartego na architekturze ARM Windows RT lub Windows Phone.  
  
 Aby uzyskać informacje o sposobie określania maszyny odtwarzania, zobacz [porady: zmiana maszyny odtwarzania diagnostyki grafiki](how-to-change-the-graphics-diagnostics-playback-machine.md).  
  
## <a name="graphics-log-summary-information"></a>Podsumowanie informacji dziennika grafiki  
 Gdy plik dziennika grafiki jest aktywny dokument **właściwości** okno wyświetla informacje o środowisku, które hostowana Sesja przechwytywania diagnostyki grafiki. Kilka kategorii informacji są wyświetlane.  
  
 **Direct3D informacji**  
 Wyświetla informacje o funkcjach sprzętu i sterownik karty wideo, który został użyty podczas sesji przechwytywania.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|**Format 10-bitowy XR High Color**|**Wartość true,** Jeśli 10-bitowy XR kolor wysokiej format jest obsługiwany; w przeciwnym razie **False**.|  
|**DirectCompute CS 4.x**|**Wartość true,** Jeśli obliczeniowe programu do cieniowania 4.0 jest obsługiwany; w przeciwnym razie **False**.|  
|**Podwójne dokładności programów do cieniowania**|**Wartość true,** Jeśli karta graficzna obsługuje podwójnej precyzji wartości zmiennoprzecinkowych (64-bitowy); w przeciwnym razie **False**.|  
|**Sterownik list poleceń**|**Wartość true,** , gdy sterownik obsługuje list poleceń; w przeciwnym razie **False**.|  
|**Tworzy współbieżnych sterownik**|**Wartość true,** , gdy sterownik obsługuje równoczesnych tworzenia (asynchronicznej); w przeciwnym razie **False**.|  
|**Rozszerzone formaty (BGRA itp.)**|**Wartość true,** Jeśli rozszerzonej formatach, takich jak BGRA są obsługiwane; w przeciwnym razie **False**.|  
|**Maksymalny poziom funkcjonalności Sprzętowej**|Wyświetla najwyższego poziomu funkcji, która jest obsługiwana przez kartę wideo.|  
  
 **Wyświetlanie informacji**  
 Zawiera informacje dotyczące karty graficznej, który został użyty podczas sesji przechwytywania.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|**Opis**|Ciąg opisu karty wyświetlania.|  
|**Wyświetlanie pamięci**|Ilość pamięci, która jest zainstalowana na karty graficznej.|  
|**Nazwa sterownika**|Nazwa sterownika karty graficznej.|  
|**Wersja sterownika**|Wersja sterownika karty graficznej.|  
|**Nazwa**|Nazwa karty graficznej.|  
  
 **Plik eksperymentu**  
 Zawiera informacje o pliku eksperymentu, który został skojarzony z sesją przechwytywania.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|**Ścieżka**|Ścieżka pliku .vsglog. **Uwaga:** w obszarze przechwytywania starszej wersji, ta właściwość jest używana.|  
  
 **Informacje o module**  
 Wyświetla nazwę i wersję bibliotek dołączanych dynamicznie (dll), które zostały załadowane przez aplikację podczas sesji przechwytywania.  
  
 **Informacje o systemie**  
 Zawiera informacje dotyczące sprzętu i systemu operacyjnego, hostującego aplikację podczas sesji przechwytywania.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|**Pamięci**|Ilość pamięci zainstalowanej w komputerze.|  
|**Architektura systemu operacyjnego**|Wartość docelowa architektura Procesora systemu operacyjnego.|  
|**Wersja systemu operacyjnego**|Wersja systemu operacyjnego.|  
|**Procesor**|Procesor, który jest zainstalowany na komputerze.|  
|**Architektura aplikacji docelowej**|Architektura Procesora w aplikacji docelowej. Może to być inna niż **architektury systemu operacyjnego**.|  
  
 **Aplikacja docelowa**  
 Wyświetla informacje o aplikacji, która jest przedmiotem sesję przechwytywania.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|**Data/godzina ostatniej modyfikacji**|Data i godzina, że aplikacja została skompilowana.|  
|**Ścieżka**|Ścieżka aplikacji.|  
|**Identyfikator procesu**|Identyfikator procesu, który zostało przekazane do aplikacji.|  
|**Wersja**|Wersja aplikacji.|  
  
 **Plik dziennika VSG**  
 Wyświetla informacje o dokument dziennika grafiki.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|**Utworzone przez**|Nazwa aplikacji, która utworzona grafiki dziennika dokumentu. Na przykład, jeśli sesja przechwytywania zostało zainicjowane w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (Ręczne przechwytywania) wartość tej właściwości jest [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].|  
|**Czas rozpoczęcia sesji**|Data i godzina rozpoczęcia sesji przechwytywania.|  
|**Rozmiar**|Rozmiar dokument dziennika grafiki.|  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Brak obiektów spowodowany cieniowaniem wierzchołków](walkthrough-missing-objects-due-to-vertex-shading.md)   
 [Przewodnik: debugowanie błędów renderowania spowodowanych cieniowaniem](walkthrough-debugging-rendering-errors-due-to-shading.md)