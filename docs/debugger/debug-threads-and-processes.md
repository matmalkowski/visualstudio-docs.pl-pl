---
title: Narzędzia debugowanie wątków i procesów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/21/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multiprocess debugging
- threading [Visual Studio], debugging
- processes, debugging
- debugging threads
- debugging [Visual Studio], threads
ms.assetid: 9f0c8505-b6b2-452b-adfd-076db14d8115
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f42159b15bbba4bd092dcde34404459212e26ab3
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="tools-to-debug-threads-and-processes-in-visual-studio"></a>Narzędzia debugowanie wątków i procesów w programie Visual Studio
*Wątki* i *procesów* to pojęcia pokrewne w nauce komputera. Zarówno reprezentowania sekwencji instrukcji, które należy wykonać w dowolnej kolejności. Instrukcje w oddzielnych wątkach lub procesy, jednak można wykonywać równoległe.  
  
 Procesy istnieje w systemie operacyjnym i odpowiadają co użytkownicy widzą jako programy lub aplikacje. Wątek, istnieje z drugiej strony, w ramach procesu. Z tego powodu wątki są czasami określane jako *procesów lekki*. Każdy proces składa się z co najmniej jeden wątek.  
  
 Istnienie wielu procesów umożliwia komputerowi wykonać więcej niż jedno zadanie naraz. Istnienie wielu wątków umożliwia procesu do rozdzielania pracy do wykonania równolegle. Na komputerze wieloprocesorowych procesów i wątków może działać na różnych procesorach. Dzięki temu spełnione przetwarzania równoległego.  
  
 Przetwarzanie równoległe doskonałe nie zawsze jest możliwe. Wątki czasami musi być synchronizowany. Jeden wątek może mieć oczekiwania wyników z innego wątku lub jeden wątek może być konieczne wyłącznego dostępu do zasobu, który używa innego wątku. Problemy z synchronizacją są Częstą przyczyną usterki w aplikacjach wielowątkowych. Czasami wątków może się okazać oczekiwania z zasobem, który nigdy nie stanie się dostępny. Powoduje to warunek o nazwie *zakleszczenie*.  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Debugera udostępnia zaawansowane, ale łatwa w użyciu narzędzia debugowania wątków i procesów.  
  
## <a name="tools-and-features"></a>Narzędzia i funkcje
Narzędzia potrzebne do użycia w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] są zależne od rodzaju kodu próbujesz debugowania:

- Dla procesów, podstawowe narzędzia są **dołączyć do procesu** okno dialogowe **procesów** okno i **debugowania lokalizacji** paska narzędzi.

- Wątki, podstawowe narzędzia do debugowania wątki są **wątków** okna, znaczniki wątku w systemie windows źródła **stosów równoległych** okna, **czujki równoległej** okna, i **debugowania lokalizacji** paska narzędzi.  
  
- Kod, który używa <xref:System.Threading.Tasks.Task> w [zadań biblioteki równoległych (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl), [współbieżność środowiska wykonawczego](/cpp/parallel/concrt/concurrency-runtime/) (natywnego kodu), podstawowe narzędzia do debugowania aplikacji wielowątkowych są **Stosów równoległych** okna, **czujki równoległej** okno i **zadania** okna ( **zadania** obsługuje również okna Obiekt promise JavaScript).

- Debugowanie wątków na procesor GPU, jest podstawowym narzędziem **wątki GPU** systemu windows.  
  
 W poniższej tabeli przedstawiono dostępne informacje i akcje można wykonać w każdym z tych miejscach:  
  
|Interfejs użytkownika|Informacje są dostępne|Akcje, które można wykonać|  
|--------------------|---------------------------|-----------------------------|  
|**Dołączanie do procesu** — okno dialogowe|Dostępne procesy, które można dołączyć do:<br /><br /> -Nazwa process (.exe)<br />-Przetwarzanie numer identyfikacyjny<br />— Tytuł Menubar<br />-Type (v4.0 zarządzanych; Zarządzane w wersji 2.0, w wersji 1.1, 1.0; x86; x64; IA64)<br />-User Name (nazwa konta)<br />-Numer sesji|Wybierz proces, aby dołączyć do<br /><br /> Wybierz komputer zdalny<br /><br /> Zmień typ transportu do łączenia z komputerami zdalnymi|  
|**Procesy** okna|Dołącza procesów:<br /><br /> -Nazwa procesu<br />-Przetwarzanie numer identyfikacyjny<br />— Ścieżka do przetworzenia .exe<br />— Tytuł Menubar<br />-Stanu (podziału. Uruchomiona)<br />-Debugowania (natywne i zarządzane itd.)<br />— Typ (ustawienie domyślne, natywny bez uwierzytelniania) transportu<br />-Kwalifikator transportu (komputer zdalny)|Narzędzia:<br /><br /> -Dołączyć<br />-Odłączyć<br />— Zakończenie<br /><br /> Menu skrótów:<br /><br /> -Dołączyć<br />-Odłączyć<br />-Odłączyć po zatrzymaniu debugowania<br />— Zakończenie|  
|**Wątki** okna|Wątki bieżącego procesu:<br /><br /> — Identyfikator wątku<br />-Identyfikator zarządzany<br />-Kategorii (wątku głównego, wątek interfejsu, obsługi wywołanie procedury zdalnej lub wątku roboczego)<br />— Nazwa wątku<br />-Miejsce gdzie jest tworzony wątek<br />-Priorytet<br />-Maska koligacji<br />— Count zawieszony<br />-Nazwa procesu<br />-Flaga wskaźnika<br />-Zawieszonego wskaźnika|Narzędzia:<br /><br /> -Wyszukiwania<br />— Stos wywołań wyszukiwanie<br />-Oflaguj tylko mój kod<br />-Oflaguj niestandardowy wybór modułów<br />-Grupuj według<br />-Kolumn<br />-Callstacks Rozwiń/Zwiń<br />-Rozwiń/Zwiń grupy<br />— Wątki blokowanie/odblokowania<br /><br /> Menu skrótów:<br /><br /> — Pokaż wątki w źródle<br />-Przełącz do wątku<br />-Zablokuj uruchomiony wątek<br />-Odblokować wątku zablokowane<br />-Flaga wątku do badania dodatkowe<br />-Usuwanie oflagowania wątków<br />-Zmień nazwę wątku<br />— Pokazać lub ukryć wątków<br /><br /> Inne działania:<br /><br /> -Wyświetlić stosu wywołań dla wątku w etykietki danych|  
|Okno źródła|Wskaźniki wątku w lewym odstępu oznaczać jedną lub wiele wątków (Wyłącz domyślnie włączona przy użyciu menu skrótów w **wątków** okna)|Menu skrótów:<br /><br /> -Przełącz do wątku<br />-Flaga wątku do badania dodatkowe<br />-Usuwanie oflagowania wątków|  
|**Lokalizacja debugowania** paska narzędzi|-Bieżącego procesu<br />-Wstrzymać aplikacja<br />-Wznowić aplikacji<br />-Wstrzymywanie i zamknij aplikację<br />-Bieżącego wątku<br />— Bieżący stan wątku flagi przełącznik<br />-Pokaż tylko oflagowane wątki<br />-Pokaż tylko bieżący proces<br />-Bieżącej ramki stosu|-Przełącznika do innego procesu<br />-Wstrzymać, wznowić lub zamknij aplikację<br />-Przełączanie na inny wątek w bieżącym procesie<br />-Przełączanie do innej ramki stosu w bieżącym wątku<br />-, Flaga lub usuwanie oflagowania bieżącego wątków<br />-Pokaż tylko oflagowane wątki<br />-Pokaż tylko bieżący proces|  
|**Równoległe stosy** okna|-Stosy wywołań dla wielu wątków w jednym oknie.<br />— Ramka stosu active dla każdego wątku.<br />-Wywołań i callees dla dowolnej metody.|-Odfiltrowywania określonego wątków<br />-Przełącz do widoku zadania<br />-, Flaga lub usuwanie oflagowania wątków<br />-Powiększenia|   
|**Równoległe czujki** okna|-Flagę kolumny, zaznacz wątku, który chcesz zwrócić szczególną uwagę na.<br />— Ramki kolumny, w którym Strzałka wskazuje zaznaczonej ramki.<br />— Można konfigurować kolumny wyświetlające maszyny, proces, kafelków, zadań i wątku.|-, Flaga lub usuwanie oflagowania wątków<br />— Wyświetlenie tylko oflagowane wątki<br />-Przełącznika ramki<br />-Posortować kolumnę<br />-Grupy wątków<br />-Zablokować lub odblokować wątków<br />-eksportowania danych z okna czujki równoległej| 
|**Zadania** okna|— Informacje o <xref:System.Threading.Tasks.Task> obiektów w tym Identyfikatora zadania, stan zadania (zaplanowane, uruchamianie, oczekiwania, zakleszczone), i który wątek jest przypisana do zadania.<br />-Bieżąca lokalizacja w stosie wywołań.<br />-Delegata przekazany do zadania w czasie tworzenia|-Przełączyć się do bieżącego zadania<br />-, Flaga lub usuwanie oflagowania zadania<br />-Zablokować lub odblokować zadania|  
|**Wątków GPU** okna|-Flagę kolumny, zaznacz wątku, który chcesz zwrócić szczególną uwagę na.<br />-Bieżącego wątku kolumna, w którym żółta strzałka wskazuje bieżący wątek.<br />- **Liczba wątków** kolumny, która wskazuje liczbę wątków w tej samej lokalizacji.<br />- **Wiersza** kolumny, która wyświetla wiersz kodu, w którym znajduje się każdej grupy wątków.<br />- **Adres** kolumny, która wyświetla adres instrukcji, w którym znajduje się każdej grupy wątków.<br />- **Lokalizacji** kolumny, która jest lokalizacji w kodzie adresu.<br />- **Stan** kolumny, która wskazuje, czy wątek jest aktywny lub zablokowane.<br />- **Kafelek** kolumny, która zawiera indeks kafelka wątki w wierszu.|-Zmiana w innym wątku<br />— Wyświetlenie kafelka określonego i wątku<br />-Wyświetlanie lub ukrywanie kolumn<br />— Sortowanie według kolumny<br />-Grupy wątków<br />-Zablokować lub odblokować wątków<br />-, Flaga lub usuwanie oflagowania wątków<br />— Wyświetlenie tylko oflagowane wątki|  
  
## <a name="see-also"></a>Zobacz też  
 [Dołączanie do uruchomionego procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Debuguj aplikacje wielowątkowe](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Debugowanie kodu GPU](../debugger/debugging-gpu-code.md)