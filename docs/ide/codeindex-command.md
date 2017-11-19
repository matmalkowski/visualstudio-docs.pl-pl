---
title: Polecenie CodeIndex | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- command-line tools [Team Foundation Server]
- TFSConfig
- CodeIndex command [Team Foundation Server]
ms.assetid: b79568d4-6a64-4ca9-a1ee-3e57f92a9c5c
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b68d1a67055e14fce0af48fa58f805216205d4ad
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="codeindex-command"></a>Polecenie CodeIndex
Użyj **CodeIndex** polecenia do zarządzania kodu indeksowania na Team Foundation Server. Na przykład można zresetować indeks, aby naprawić informacje wskaźników CodeLens lub wyłączyć funkcję indeksowania do badania problemów z wydajnością serwera.  
  
 **Wymagane uprawnienia**  
  
 Aby użyć **CodeIndex** polecenia, musisz być członkiem **Team Foundation Administratorzy** grupy zabezpieczeń. Zobacz [uprawnienia i grup zdefiniowanych dla usługi Team Services i TFS](https://www.visualstudio.com/docs/setup-admin/permissions).  
  
> [!NOTE]
>  Nawet jeśli użytkownik loguje się przy użyciu poświadczeń administracyjnych, należy otworzyć z podwyższonym poziomem uprawnień okno wiersza polecenia, aby uruchomić to polecenie. Należy także wykonać to polecenie z warstwy aplikacji programu Team Foundation.  
  
## <a name="syntax"></a>Składnia  
  
```  
TFSConfig CodeIndex /indexingStatus | /setIndexing:[ on | off | keepupOnly ] | /ignoreList:[ add | remove | removeAll | view ] ServerPath | /listLargeFiles [/fileCount:FileCount] [/minSize:MinSize] | /reindexAll | /destroyCodeIndex [/noPrompt] | /temporaryDataSizeLimit:[ view | <SizeInGBs> | disable ] | /indexHistoryPeriod:[ view | all | <NumberOfMonths> ] [/collectionName:CollectionName | /collectionId:CollectionId]  
```  
  
#### <a name="parameters"></a>Parametry  
  
|**Argument**|**Opis**|  
|------------------|---------------------|  
|`CollectionName`|Określa nazwę kolekcji projektów zespołowych. Jeśli nazwa zawiera spacje, należy wpisać nazwę w cudzysłowie, na przykład "Fabrikam Web Site".|  
|`CollectionId`|Określa numer identyfikacyjny kolekcji projektów zespołowych.|  
|`ServerPath`|Określa ścieżkę do pliku kodu.|  
  
|**Opcja**|**Opis**|  
|----------------|---------------------|  
|**/indexingStatus**|Pokazuje stan i konfigurację usługi indeksowania kodu.|  
|**/setIndexing:**[na &#124; Wyłącz &#124; keepupOnly]|-   **na**: uruchomić indeksowania wszystkich grup zmian.<br />-   **Wyłącz**: Zatrzymaj indeksowanie wszystkich grup zmian.<br />-   **keepupOnly**: Zatrzymaj indeksowanie wcześniej utworzonej grupy zmian i uruchomić indeksowania tylko nowe grupy zmian.|  
|**/ignoreList:**[Dodaj &#124; Usuń &#124; removeAll &#124; widok]`ServerPath`<br /><br /> Na początek, koniec lub obu końców ścieżki serwera, można użyć znaku wieloznacznego (*).|Określa listę plików kodu i ich ścieżek, które nie mają być indeksowane.<br /><br /> -   **Dodaj**: Dodawanie pliku, który ma nie być indeksowane do listy plików została zignorowana.<br />-   **Usuń**: Usuń plik, który ma być indeksowany z listy plików została zignorowana.<br />-   **removeAll**: Wyczyść listy plików została zignorowana i uruchomić indeksowania wszystkich plików.<br />-   **Widok**: Zobacz wszystkie pliki, które nie są indeksowane.|  
|**/listLargeFiles [/ fileCount:** `FileCount` **/minSize:** `MinSize`]|Zawiera określoną liczbę plików, która przekracza określony rozmiar w KB. Następnie można użyć **/ignoreList** opcji, aby wykluczyć pliki indeksowania.|  
|**/reindexAll**|Wyczyść wcześniej zindeksowanych danych i uruchom ponownie indeksowania.|  
|**/destroyCodeIndex [/ noprompt]**|Usuwanie indeksu kodu i wszystkie zindeksowanych danych. Nie wymaga potwierdzenia, jeśli używasz **/noprompt** opcji.|  
|**/temporaryDataSizeLimit**: [Widok &#124; <`SizeInGBs`> &#124; Wyłącz]|Kontroli ilości tymczasowe dane CodeLens tworzy podczas przetwarzania grupy zmian. Domyślny limit wynosi 2 GB.<br /><br /> -   **Widok**: Pokaż bieżący limit rozmiaru.<br />-   `SizeInGBs`: Zmienić limit rozmiaru.<br />-   **Wyłącz**: Usuń limit rozmiaru.<br /><br /> Ten limit jest sprawdzana przed CodeLens przetwarza nowy zestaw zmian. Jeśli dane tymczasowe przekracza ten limit, CodeLens wstrzyma przetwarzania poza grupy zmian, nie nowe. CodeLens spowoduje ponowne uruchomienie przetwarzania po danych jest wyczyszczone, a spadnie poniżej tego limitu. Oczyszczanie jest uruchamiany automatycznie raz dziennie. Oznacza to, że dane tymczasowe może przekroczenia tego limitu do momentu wyczyszczenia zacznie działać.|  
|**/indexHistoryPeriod**: [Widok &#124; wszystkie &#124; <`NumberOfMonths`>]|Formant, jak długo indeksu historii zmian. Ma to wpływ na ile historii CodeLens przedstawiono. Domyślny limit wynosi 12 miesięcy. Oznacza to, CodeLens przedstawia historię zmian tylko w ostatnich 12 miesięcy.<br /><br /> -   **Widok**: Pokaż bieżąca liczba miesięcy.<br />-   **wszystkie**: indeks cała historia zmian.<br />-   `NumberOfMonths`: Liczba miesięcy, używany do historii zmian indeksu zmienić.|  
|**/collectionName:**`CollectionName`|Określa nazwę kolekcji projektów zespołowych, na którym ma być uruchamiany **CodeIndex** polecenia. Wymagane, jeśli nie używasz **/CollectionId**.|  
|**/collectionId:**`CollectionId`|Określa numer identyfikacyjny kolekcji projektów zespołowych, na którym ma być uruchamiany **CodeIndex** polecenia. Wymagane, jeśli nie używasz **/CollectionName**.|  
  
## <a name="examples"></a>Przykłady  
  
> [!NOTE]
>  Przykładowe firmy, organizacje, produkty, nazwy domen, adresy e-mail, logo, osoby, miejsca i zdarzenia opisywane w przykładach są fikcyjne.  Wszelkie rzeczywistą firmą, organizacji, produktu, nazwa domeny, adres e-mail, logo, osoby, miejscami lub zdarzeniami ma i zdarzeniami.  
  
 Aby wyświetlić kod indeksowania stanu i konfiguracji:  
  
```  
TFSConfig CodeIndex /indexingStatus /collectionName:"Fabrikam Web Site"  
```  
  
 Aby uruchomić indeksowania wszystkich grup zmian:  
  
```  
TFSConfig CodeIndex /setIndexing:on /collectionName:"Fabrikam Web Site"  
```  
  
 Aby zatrzymać, indeksowania wcześniej utworzonej grupy zmian i uruchomić indeksowania tylko nowych grup zmian:  
  
```  
TFSConfig CodeIndex /setIndexing:keepupOnly /collectionName:"Fabrikam Web Site"  
```  
  
 Aby znaleźć do 50 plików, które są większe niż 10 KB:  
  
```  
TFSConfig CodeIndex /listLargeFiles /fileCount:50 /minSize:10 /collectionName:"Fabrikam Web Site"  
```  
  
 Aby wykluczyć określony plik z indeksowania i dodać go do listy zignorowany plik:  
  
```  
TFSConfig CodeIndex /ignoreList:add "$/Fabrikam Web Site/Catalog.cs" /collectionName:"Fabrikam Web Site"  
```  
  
 Aby wyświetlić wszystkie pliki, które nie są indeksowane:  
  
```  
TFSConfig CodeIndex /ignoreList:view  
```  
  
 Aby wyczyścić wcześniej zindeksowanych danych i uruchom ponownie indeksowania:  
  
```  
TFSConfig CodeIndex /reindexAll /collectionName:"Fabrikam Web Site"  
```  
  
 Aby zapisać całą historię zmian:  
  
```  
TFSConfig CodeIndex /indexHistoryPeriod:all /collectionName:"Fabrikam Web Site"  
```  
  
 Aby usunąć limit rozmiaru na CodeLens dane tymczasowe i kontynuować indeksowanie niezależnie od rozmiaru danych tymczasowych:  
  
```  
TFSConfig CodeIndex /temporaryDataSizeLimit:disable /collectionName:"Fabrikam Web Site"  
```  
  
 Aby usunąć indeksu kod potwierdzenia:  
  
```  
TFSConfig CodeIndex /destroyCodeIndex /collectionName:"Fabrikam Web Site"  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Znajdowanie zmian w kodzie i innych elementów historii za pomocą funkcji CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md)  

 [Zarządzanie konfiguracją serwera z TFSConfig](http://msdn.microsoft.com/en-us/94424190-3b6b-4f33-a6b6-5807f4225b62)   
 [Narzędzia wiersza polecenia dla serwerów TFS](http://msdn.microsoft.com/en-us/be8c997a-b97b-4e59-97f5-04db0a601a6c)