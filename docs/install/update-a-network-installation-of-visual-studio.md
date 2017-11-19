---
title: Aktualizowanie instalacji sieciowej programu Visual Studio | Dokumentacja firmy Microsoft
description: "Informacje o sposobie aktualizowania instalacji programu Visual Studio za pośrednictwem sieci przy użyciu polecenia — układ"
ms.date: 08/14/2017
ms.reviewer: tims
ms.suite: 
ms.technology: vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 1AF69C0E-0AC9-451B-845D-AE4EDBCEA65C
author: timsneath
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 65e54f1decc2417e4e825ccd164b28973e598e27
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2017
---
# <a name="update-a-network-based-installation-of-visual-studio"></a>Aktualizacja instalacji sieciowej programu Visual Studio

Go ma można zaktualizować sieci układ instalacji programu Visual Studio z najnowszymi aktualizacjami produktu, tak aby można go jednocześnie jako punkt instalacji używane w przypadku najnowszej aktualizacji programu Visual Studio, a także do obsługi urządzeń, które są już wdrożone do klienta stacje robocze.

## <a name="how-to-update-a-network-layout"></a>Jak zaktualizować układ sieci
Aby odświeżyć na udział sieciowy instalacji co zawierają one najnowsze aktualizacje, uruchom polecenie układu przyrostowo pobrania zaktualizowanych pakietów.

W przypadku wybrania częściowe układ podczas pierwszego utworzenia układu sieci, te ustawienia są zapisywane.  Wszystkie polecenia przyszłych układu wprowadzić poprzednie opcje i nowe opcje, które określisz.  (To jest nowa w programie 15 ustęp 3).  Jeśli używasz układu starszej wersji, należy użyć takie same parametry wiersza polecenia używane podczas pierwszego utworzenia układu (innymi słowy, tym samym obciążeń i języków) instalacji sieci można zaktualizować jej zawartości.

Jeśli host układu w udziale plików, należy aktualizować prywatną kopię układu (na przykład c:\vs2017offline) i następnie, po pobraniu wszystkich zaktualizowanej zawartości, skopiuj go do udziału plików (na przykład \\server\products\VS2017). Jeśli nie zrobisz, istnieje duże prawdopodobieństwo, że wszyscy użytkownicy, którzy uruchom Instalatora podczas aktualizowania układu nie może być można uzyskać całej zawartości z układu, ponieważ to nie jest jeszcze całkowicie aktualizowany.

Przejdźmy sposobu tworzenia, a następnie zaktualizuj układ:

* Po pierwsze poniżej przedstawiono przykład sposobu tworzenia układu z jednego obciążenia dla języka angielskiego tylko:

  ```
  vs_enterprise.exe --layout c:\VS2017Layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
  ```

* Poniżej przedstawiono sposób zaktualizować do nowszej wersji tego samego układu. Nie trzeba określać żadnych dodatkowych parametrów wiersza polecenia. Poprzednie ustawienia zostały zapisane i będą używane przez wszystkie polecenia kolejnych układu, w tym folderze układu.  

  ```
  vs_enterprise.exe --layout c:\VS2017Layout  
  ```

* Poniżej przedstawiono sposób zaktualizować do nowszej wersji układu w trybie nienadzorowanym. Operacja układu uruchamia proces instalacji w nowym oknie konsoli. Okno pozostanie otwarty, użytkownicy mogą zobaczyć wynik końcowy oraz podsumowanie wszelkie błędy, które mogły wystąpić. Jeśli przeprowadzasz operację układu w trybie nienadzorowanym (na przykład masz skryptów, regularnie uruchamiany w celu aktualizacji do najnowszej wersji układu), następnie użyć `--passive` parametru i proces zostanie automatycznie zamknięte okno.

  ```
  vs_enterprise.exe --layout c:\VS2017Layout --passive
  ```

* Poniżej przedstawiono sposób dodać dodatkowe obciążenie i języku lokalnym.  (To polecenie dodaje obciążenia Azure).  Teraz zarządzane komputerowych i Azure znajdują się w tym układzie.  Zasoby języka w języku angielskim i niemieckim uwzględniono również dla tych zadań.  I układ zostało zaktualizowane do najnowszej dostępnej wersji.

  ```
  vs_enterprise.exe --layout c:\VS2017Layout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE
  ```

* A na koniec poniżej przedstawiono sposób dodania dodatkowego obciążenia i język zlokalizowanego bez aktualizowania wersji. (To polecenie dodaje obciążenia sieci Web & ASP.NET).  Teraz obciążeń zarządzanego pulpitu, Azure oraz ASP.NET i sieci Web znajdują się w tym układzie.  Zasoby język angielski, niemiecki i francuski uwzględniono również dla tych zadań.  Jednak układ nie została zaktualizowana do najnowszej dostępnej wersji, podczas uruchamiania tego polecenia.  Pozostaje w istniejącą wersję.

  ```
  vs_enterprise.exe --layout c:\VS2017Layout --add Microsoft.VisualStudio.Workload.NetWeb --lang fr-FR --keepLayoutVersion
  ```

## <a name="how-to-deploy-an-update-to-client-machines"></a>Jak wdrożyć aktualizację na komputerach klienckich
W zależności od konfiguracji środowiska sieciowego aktualizacji może być wdrożone przez administratora przedsiębiorstwa albo inicjowane z komputera klienta.

* Użytkownicy mogą aktualizować wystąpienia programu Visual Studio, który został zainstalowany z folderu instalacji w trybie offline:
  * Uruchom Instalatora programu Visual Studio.
  * Następnie kliknij przycisk **aktualizacji**.

* Administratorzy mogą aktualizacji wdrożenia klientów programu Visual Studio bez interakcji użytkownika z dwa osobne polecenia:
  * Najpierw należy zaktualizować Instalator programu Visual Studio: <br>```vs_enterprise.exe --quiet --update```
  * Następnie zaktualizuj samej aplikacji Visual Studio: <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" --quiet --wait --norestart```

> [!NOTE]
> Użyj [polecenia vswhere.exe](tools-for-managing-visual-studio-instances.md) do identyfikowania ścieżki instalacji istniejącego wystąpienia programu Visual Studio na komputerze klienckim.

> [!TIP]
> Aby uzyskać więcej informacji na temat kontrolowania, kiedy powiadomienia o aktualizacji są prezentowane użytkownikom, zobacz [kontrolowanie aktualizacji do wdrożenia programu Visual Studio oparte na sieci](controlling-updates-to-visual-studio-deployments.md).

## <a name="how-to-verify-a-layout"></a>Jak sprawdzić, układ
Użyj `--verify` do przeprowadzenia weryfikacji w pamięci podręcznej offline dostarczony. Sprawdza, czy pliki pakiety są brakujący lub nieprawidłowy. Po zakończeniu weryfikacji Wyświetla listę brakujących plików i plików nieprawidłowy.

```
vs_enterprise.exe --layout <layoutDir> --verify
```

Vs_enterprise.exe może być wywoływana wewnątrz layoutDir.


> [!NOTE]
> Niektóre pliki ważne metadane, które są wymagane przez `--verify` opcja musi być w pamięci podręcznej w trybie offline układu. Jeśli brakuje tych plików metadanych, "--Sprawdź" nie można uruchomić i Instalator zwraca błąd. Jeśli wystąpi błąd, ponownie utwórz nowy układ w trybie offline do innego folderu (lub do tego samego folderu pamięci podręcznej w trybie offline. Aby to zrobić, uruchom tego samego polecenia układu, który został użyty do utworzenia początkowego układu w trybie offline. Na przykład `Vs_enterprise.exe --layout <layoutDir>`.

Microsoft dostarczany aktualizacji dla programu Visual Studio okresowo, więc nowy układ utworzonego może być tej samej wersji co początkowego układu.  

## <a name="how-to-fix-a-layout"></a>Jak rozwiązać układu
Użyj `--fix` do przeprowadzenia tej samej weryfikacji jako `--verify` i spróbuj rozwiązać problemy zidentyfikowane. `--fix` Proces wymaga połączenia internetowego, dlatego upewnij się, że komputer jest połączony z Internetem, przed wywołuje `--fix`.

```
vs_enterprise.exe --layout <layoutDir> --fix
```

Vs_enterprise.exe może być wywoływana wewnątrz layoutDir.

## <a name="how-to-remove-older-versions-from-a-layout"></a>Jak do usunięcia starszych wersji z układu
Po wykonaniu aktualizacji układu do pamięci podręcznej offline układu folder pamięci podręcznej może być niektórych przestarzałych pakiety, które nie są już potrzebne przez najnowsze instalację programu Visual Studio. Można użyć `--clean` opcję, aby usunąć przestarzałe pakiety z folderu pamięci podręcznej w trybie offline.

Aby to zrobić, musisz ścieżki pliku do manifest(s) katalogu, zawierające te pakiety przestarzałe. Znajdziesz się, że katalog manifesty w folderze "Archiwum" w pamięci podręcznej w trybie offline układu. Są zapisywane istnieje podczas aktualizacji układu. W folderze "Archiwum" ma co najmniej jeden "GUID" o nazwie folderów, z których każdy zawiera manifest przestarzałe katalogu. Liczba folderów "GUID" powinna być taka sama jak liczba aktualizacji do pamięci podręcznej w trybie offline.

Kilka plików są zapisywane w folderze każdego "GUID". Dwa pliki najbardziej przydatnych są oraz plik "catalog.json" "version.txt". Plik "catalog.json" jest manifest przestarzałe katalogu należy przekazać do `--clean` opcji. Plik version.txt zawiera wersję tego manifestu przestarzałe katalogu. Oparte na numer wersji, można zdecydować, czy chcesz usunąć przestarzałe pakiety z manifestu tego katalogu. Możesz to zrobić takie same jak przechodzić przez innych folderach "GUID". Po podjęciu decyzji o katalogi, które chcesz wyczyścić, uruchom `--clean` polecenia, podając pliki ścieżki do tych katalogów.  

Oto kilka przykładów sposobu użycia czystą opcji:   

```
vs_enterprise.exe --layout <layoutDir> --clean <file-path-of-catalog1> <file-path-of-catalog2> …
```

```
vs_enterprise.exe --layout <layoutDir> --clean <file-path-of-catalog1> --clean <file-path-of-catalog2> …
```

Można także wywoływać vs_enterprise.exe wewnątrz &lt;layoutDir&gt;. Oto przykład:

```  
c:\VS2017Layout\vs_enterprise.exe --layout c:\VS2017Layout --clean c:\VS2017Layout\Archive\1cd70189-fc55-4583-8ad8-a2711e928325\Catalog.json --clean c:\VS2017Layout\Archive\d420889f-6aad-4ba4-99e4-ed7833795a10\Catalog.json
```  

Podczas wykonywania tego polecenia, Instalator analizuje folder pamięci podręcznej w trybie offline, aby znaleźć listę plików, które zostanie usunięta. Użytkownik będzie miał możliwość Przejrzyj pliki, które mają być usunięte i potwierdzenie operacji usuwania.

## <a name="get-support"></a>Uzyskaj pomoc techniczną
Czasami może wystąpienia problemów. W przypadku niepowodzenia instalacji programu Visual Studio, zobacz [problemy dotyczące instalacji i uaktualniania Rozwiązywanie problemów z programu Visual Studio 2017](troubleshooting-installation-issues.md) stronę porady dotyczące rozwiązywania problemów. Jak również zgłosić problemy produktu z nami za pośrednictwem [zgłosić Problem](../ide/how-to-report-a-problem-with-visual-studio-2017.md) narzędzia w programie Visual Studio IDE lub udział sugestia z nami na [UserVoice](https://visualstudio.uservoice.com/forums/121579). Można śledzić problemy z produktu w [Visual Studio Developer Community](https://developercommunity.visualstudio.com/), zadawać pytania i odpowiedzi. Można również kontaktowaniu się z nami i innymi deweloperami Visual Studio za pomocą naszych [konwersacji programu Visual Studio w społeczności Gitter](https://gitter.im/Microsoft/VisualStudio) (wymaga [GitHub](https://github.com/) konta).

## <a name="see-also"></a>Zobacz także
* [Zainstaluj program Visual Studio](install-visual-studio.md)
* [Przewodnik administratora w usłudze Visual Studio](visual-studio-administrator-guide.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Narzędzia do wykrywania i Zarządzanie wystąpieniami programu Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Formant aktualizacje do wdrożenia oparte na sieci programu Visual Studio](controlling-updates-to-visual-studio-deployments.md)
