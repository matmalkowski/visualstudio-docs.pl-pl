---
title: Wyświetl zdarzenia przy użyciu funkcji IntelliTrace | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
ms.assetid: e1c9c91a-0009-4c4e-9b4f-c9ab3a6022a7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bb117eeaf972788118b9b7284bfd2ae6aca44936
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="view-events-with-intellitrace-in-visual-studio"></a>Wyświetl zdarzenia przy użyciu funkcji IntelliTrace w programie Visual Studio
Dodatkowo do zebrania informacji dotyczących określonych zdarzeń lub kategorie zdarzeń, lub wywołania funkcji poszczególnych zdarzeń, można użyć funkcji IntelliTrace. Poniższe procedury pokazują, jak to zrobić.  
  
 Można użyć funkcji IntelliTrace w Visual Studio Enterprise edition, ale nie wersji Professional lub społeczności.  
  
##  <a name="GettingStarted"></a> Konfigurowanie funkcji Intellitrace  
 Możesz spróbować debugowanie z tylko zdarzenia funkcji IntelliTrace. Zdarzenia IntelliTrace są zdarzeń debugera, wyjątki zdarzenia .NET Framework i innych zdarzeń systemu. Należy włączyć lub wyłączyć określonych zdarzeń w celu kontrolowania zdarzenia tego rekordów funkcji IntelliTrace, przed rozpoczęciem debugowania. Aby uzyskać więcej informacji, zobacz [funkcji IntelliTrace](../debugger/intellitrace-features.md).  
  
 - Włącz zdarzenia funkcji IntelliTrace dla dostępu do plików. Przejdź do **Narzędzia > Opcje > IntelliTrace > zdarzeń funkcji IntelliTrace** strony, a następnie rozwiń **pliku** kategorii. Sprawdź **pliku** kategorii zdarzeń. To powoduje, że wszystkie pliku (dostęp, close, Usuń) można sprawdzić.

## <a name="create-your-app"></a>Tworzenie aplikacji
  
1.  Tworzenie aplikacji konsolowej C#. W pliku Program.cs Dodaj następujące `using` instrukcji:  
  
    ```csharp  
    using System.IO;  
    ```  
  
2.  Utwórz <xref:System.IO.FileStream> metody Main, odczytywać, zamknij je i usuń go. Dodaj kolejny wiersz chcemy mieć miejsce, aby ustawić punkt przerwania:  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        FileStream fs = File.Create("WordSearchInputs.txt");  
        fs.ReadByte();  
        fs.Close();  
        File.Delete("WordSearchInputs.txt");  
  
        Console.WriteLine("done");  
    }  
    ```  
  
3.  Ustaw punkt przerwania w `Console.WriteLine("done");`  

## <a name="start-debugging-and-view-intellitrace-events"></a>Rozpocznij debugowanie i wyświetlać zdarzenia funkcji IntelliTrace
  
1.  Uruchom profilowanie w zwykły sposób. (Naciśnij przycisk **F5** lub kliknij przycisk **Debuguj > Rozpocznij debugowanie**.  
  
    > [!TIP]
    >  Zachowaj **zmiennych lokalnych** i **automatycznych** windows Otwórz podczas debugowania kodu i zapisać wartości w tych z systemem windows.  
  
2.  Wykonanie zatrzymuje się na punkt przerwania. Jeśli nie widzisz **narzędzia diagnostyczne** okna, kliknij przycisk **debugowania > Windows > zdarzeń funkcji IntelliTrace**.  
  
     W **narzędzia diagnostyczne** okna, Znajdź **zdarzenia** kartę (3 tabulatory, powinien zostać wyświetlony **zdarzenia**, **użycie pamięci**, i **Procesora Użycie**). **Zdarzenia** karcie są wyświetlane chronologicznej listę zdarzeń, kończąc ostatnie zdarzenie przed debuger spowodowało przerwanie wykonywania. Powinny pojawić się zdarzenia o nazwie **WordSearchInputs.txt dostępu**.  
  
     Poniższy zrzut ekranu jest z programu Visual Studio 2015 Update 1.  
  
     ![IntelliTrace&#45;Update1](../debugger/media/intellitrace-update1.png "IntelliTrace-Update1")  
  
3.  Wybierz zdarzenie, aby rozwinąć jego szczegóły.  
  
     Poniższy zrzut ekranu jest z programu Visual Studio 2015 Update 1.  
  
     ![IntelliTraceUpdate1&#45;SingleEvent](../debugger/media/intellitraceupdate1-singleevent.png "IntelliTraceUpdate1-SingleEvent")  
  
     Można wybrać link pathname można otworzyć pliku. Jeśli pełna nazwa ścieżki nie jest dostępna, **Otwórz plik** zostanie wyświetlone okno dialogowe.  
  
     Kliknij przycisk **Uaktywnij debugowanie historyczne**, który ustawia kontekst debugera do czasu, jeśli zostało wybrane zdarzenie zbieranych, wyświetlanie danych historycznych **stos wywołań**, **zmiennychlokalnych** i innych uczestniczących debugera systemu windows. Jeśli kod źródłowy jest dostępny, Visual Studio przesunie wskaźnik odpowiedni kod w oknie źródła, więc należy ją zbadać.  
  
     Poniższy zrzut ekranu jest z programu Visual Studio 2015 Update 1.  
  
     ![HistoricalDebugging&#45;Update1](../debugger/media/historicaldebugging-update1.png "HistoricalDebugging-Update1")  
  
4.  Jeśli nie możesz znaleźć ten błąd, spróbuj badanie inne zdarzenia, które doprowadziły do usterki. Może także zawierać informacje o wywołaniach rekordów funkcji IntelliTrace, można przejrzeć wywołania funkcji. 
  
## <a name="next-steps"></a>Następne kroki

Niektóre z zaawansowanych funkcji IntelliTrace można używać z debugowania historycznego:

 - Aby wyświetlić migawek, zobacz [wyświetlić migawki za pomocą kroku zwrotnego IntelliTrace](../debugger/how-to-use-intellitrace-step-back.md)
 - Aby dowiedzieć się, jak sprawdzić zmienne i przejdź do kodu, zobacz [kontroli aplikacji za pomocą debugowania historycznego](../debugger/historical-debugging-inspect-app.md)