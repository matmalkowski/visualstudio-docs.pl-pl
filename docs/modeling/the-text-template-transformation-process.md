---
title: Proces transformacji szablonu tekstowego | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: text templates, transformation process
ms.assetid: 80b3f0e0-49e7-4865-a1ac-dba068abe96b
caps.latest.revision: "30"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: cc7794959f36134b85fe7d05acf07998312f9361
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="the-text-template-transformation-process"></a>Proces przekształcania szablonu tekstowego
Proces transformacji szablonu tekstowego przyjmuje jako dane wejściowe pliku szablonu tekstowego i generuje nowy plik tekstowy jako dane wyjściowe. Na przykład szablony tekstowe służy do generowania kodu języka Visual Basic lub C# lub można wygenerować raport HTML.  
  
 Trzy składniki brać udział w tym procesie: aparat, hosta i procesory dyrektywy. Aparat kontroluje proces; interakcji z hosta i procesora dyrektywy do tworzenia pliku wyjściowego. Host udostępnia interakcji ze środowiskiem, takich jak lokalizowanie plików i zestawów. Procesor dyrektywy dodaje funkcje, takie jak odczytywania danych z pliku XML lub bazy danych.  
  
 Proces transformacji szablonu tekstowego odbywa się w dwóch krokach. Najpierw aparat tworzy tymczasowej klasy nosi nazwę klasy wygenerowanego transformacji. Ta klasa zawiera kod, który jest generowany przez dyrektywy i bloków sterowania. Po wykonaniu tej aparat kompiluje i wykonuje klasy wygenerowanego transformacji do tworzenia pliku wyjściowego.  
  
## <a name="components"></a>Składniki  
  
|Składnik|Opis|Można dostosowywać (tak/nie)|  
|---------------|-----------------|------------------------------|  
|Aparat|Składnik aparat kontroluje proces transformacji szablonu tekstowego|Nie.|  
|Host|Host jest interfejs między aparatem i środowiska użytkownika. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]jest hostem proces przekształcania tekstu.|Tak. Można napisać hosta niestandardowego.|  
|Procesory dyrektywy|Procesory dyrektywy są klasy obsługujące dyrektywy w szablonach tekstowych. Dyrektywy można użyć do udostępnienia danych firmie szablonu tekstowego ze źródła danych wejściowych.|Tak. Można napisać niestandardowego procesory dyrektywy|  
  
## <a name="the-engine"></a>Aparat  
 Aparat odbiera szablonu jako ciąg z hosta, która obsługuje wszystkie pliki, które są używane w procesie transformacji. Aparat następnie prosi hostów można znaleźć żadnych niestandardowych procesorów dyrektywy i inne aspekty środowiska. Aparat następnie kompiluje i uruchamia przekształcania wygenerowane klasy. Aparat zwraca wygenerowanego tekstu do hosta, który zwykle zapisuje tekst w pliku.  
  
## <a name="the-host"></a>Host  
 Host jest odpowiedzialny za nic, które odnoszą się do środowiska poza procesem przekształcania, takie jak następujące:  
  
-   Wyszukiwanie tekstu i plików binarnych wymaganych przez aparat lub procesora dyrektywy. Host może przeszukiwać katalogi i Globalna pamięć podręczna zestawów do lokalizowania zestawów. Hosta można znaleźć kodu niestandardowego procesora dyrektywy dla aparatu. Hosta można zlokalizować i odczytywać pliki tekstowe i zwróć ich zawartość jako ciągi.  
  
-   Udostępnianie list standardowe zestawy i przestrzenie nazw, które są używane przez aparat do utworzenia transformacji wygenerowane klasy.  
  
-   Udostępnianie domeny aplikacji, która jest używana, gdy aparat kompiluje i wykonuje przekształcenie wygenerowane klasy. Oddzielna domena aplikacji jest używany do ochrony aplikacji hosta z błędów w kodzie szablonu.  
  
-   Zapisywanie pliku wygenerowanych danych wyjściowych.  
  
-   Ustawienie domyślne rozszerzenie pliku wygenerowanych danych wyjściowych.  
  
-   Obsługa błędów transformacji szablonu tekstowego. Na przykład hosta można wyświetlić błędy w interfejsie użytkownika lub zapisywania ich w pliku. (W [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], błędy są wyświetlane w oknie komunikatu błędów.)  
  
-   Zapewnienie wymaganej wartości parametru, jeśli użytkownik ma dyrektywy o nazwie bez podawania wartości. Procesor dyrektywy można określić nazwy dyrektywy i parametr i poproś hosta, aby podać wartość domyślną, jeśli ma ona.  
  
## <a name="directives-and-directive-processors"></a>Dyrektywy i procesory dyrektywy  
 Dyrektywa jest w szablonie tekstu polecenia. Zawiera parametry, aby proces generowania. Zwykle dyrektywy zdefiniuj źródło i typu modelu i innych danych wejściowych i rozszerzenie nazwy pliku wyjściowego pliku.  
  
 Procesor dyrektywy może przetworzyć co najmniej jeden dyrektywy. Przekształcenie szablon, należy zainstalować procesora dyrektywy, które mogą dotyczyć dyrektywy w szablonie.  
  
 Dyrektywy pracy, dodając kod w klasie wygenerowanego transformacji. Wywołujesz dyrektywy z szablonu tekstowego i procesy wyszukiwarek dyrektywy wywołań podczas tworzenia klasy wygenerowanego transformacji. Po wywołaniu metody dyrektywy pomyślnie, pozostałe kod napisany w szablonie tekst może polegać na funkcje, które zapewnia dyrektywy. Na przykład można wykonać następujące wywołanie do `import` dyrektywy w szablonie:  
  
 `<#@ import namespace="System.Text" #>`  
  
 Standardowa procesora dyrektywy konwertuje wartość na `using` instrukcji w klasie wygenerowanego transformacji. Następnie można użyć `StringBuilder` klasy w pozostałej części szablonu kodu bez kwalifikujące go jako `System.Text.StringBuilder`.