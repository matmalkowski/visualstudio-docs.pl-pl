---
title: "Słownik programu MSBuild | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f767d8e4-24d8-4803-80eb-e857202dbe2c
caps.latest.revision: "23"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: cdbe7702711c5196de42d18379d6870ca54f4dcd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="msbuild-glossary"></a>Słownik programu MSBuild
Te terminy są używane do opisywania aparat kompilacji firmy Microsoft (MSBuild) i jej składniki.  
  
## <a name="glossary"></a>Słownik  
 AssemblyFoldersEx  
 Lokalizacji rejestru, w którym dostawców innych firm przechowywać ścieżki dla każdej wersji framework, które obsługują one, gdzie można sprawdzić rozpoznawanie czasu projektowania można odnaleźć zestawów odwołań.  
  
 przetwarzanie wsadowe  
 Przetwarzanie wsadowe oznacza podział elementów na różne kategorie znany jako *partie*, na podstawie metadanych elementu i ponownie uruchomić docelowego lub zadania raz za pomocą każdej partii. Tworzenie plików wsadowych jest odpowiednikiem MSBuild--pętli konstrukcji. Aby uzyskać więcej informacji, zobacz [wsadowe](../msbuild/msbuild-batching.md).  
  
 zakres kompilacji  
 Zakres kompilacji opisuje obiekt MSBuild, na przykład właściwością globalną, widocznego potencjalnie do projektu i do żadnego projektu podrzędne, które są tworzone w kompilacji wielu projektów.  
  
 projektu podrzędnego  
 Zobacz *projektu, podrzędne*.  
  
 Warunek  
 Wiele elementów MSBuild można zdefiniować warunkowo; oznacza to, że `Condition` atrybut występuje w elemencie. Zawartość warunkowego elementy są ignorowane, chyba że wyrażenie `true`. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).  
  
 Definicja, element  
 Zobacz *definicji elementu*.  
  
 Dodaj element  
 Podczas fazy wykonywania kompilacji można utworzony lub zmodyfikowany przez zadania, które mają podrzędnych elementów `Output` elementów, które mają `ItemName` atrybutu. Zadanie jest nazywany "Emituj" nowych elementów.  
  
 Emituj właściwości  
 Podczas fazy wykonywania kompilacji właściwości można utworzyć lub zmodyfikować przez zadania, które mają podrzędnych `Output` elementów, które mają `PropertyName` atrybutu. Zadanie jest nazywany "Emituj" nowej właściwości.  
  
 Faza oceny  
 Obliczanie jest pierwszą fazę kompilacji projektu. Wszystkie właściwości i elementy są oceniane w kolejności, w jakiej występują w projekcie. Zaimportowane projekty są oceniane po ich napotkaniu w projekcie. Elementy docelowe i zadania nie zostaną uruchomione do fazy wykonywania i żadnych właściwości ani elementy będą one zadeklarować lub Emituj są ignorowane podczas obliczania.  
  
 fazy wykonywania  
 Wykonanie jest drugiej fazy kompilacji projektu. Wybrane elementy są tworzone i zadania są uruchamiane. Utworzone lub zmodyfikowane właściwości i elementów w porównaniu z wartościami oceny.  
  
 Funkcja, właściwości  
 Zobacz *funkcja właściwości*.  
  
 działanie, element  
 Zobacz opis funkcji elementu.  
  
 element  
 Elementy są dane wejściowe w systemie kompilacji i są podzielone na na podstawie ich nazw elementu typów elementów. Elementy reprezentują zazwyczaj pliki. Ponieważ elementy są reprezentowane przez typ elementu należą one do warunków *elementu* i *wartość elementu* mogą być używane zamiennie. Aby uzyskać więcej informacji, zobacz [elementów](../msbuild/msbuild-items.md).  
  
 definicje elementów  
 Element definicji grupy zawierają definicje elementów, które Dodaj domyślny metadanych do dowolnego typu elementu. Takich jak metadane dobrze znanego metadanych domyślny jest skojarzony z wszystkimi elementami typu określony element. Domyślne metadanych może być jawnie przesłonięte w definicji elementu. Aby uzyskać więcej informacji, zobacz [definicje elementów](../msbuild/item-definitions.md).  
  
 Funkcja Item  
 Funkcje elementów uzyskać informacje na temat elementów w projekcie. Te funkcje upraszczają pobierania elementów Distinct() i szybsze niż w pętli elementy. Brak funkcji do manipulowania ścieżki elementu i ciągów. Aby uzyskać więcej informacji, zobacz [funkcje elementów](../msbuild/item-functions.md)  
  
 metadane elementu  
 Zobacz *metadanych elementu*.  
  
 Typ elementu  
 Typy elementów są nazywane listę elementów, które mogą być używane jako parametry dla zadania. Zadań użyj wartości elementu, aby wykonać kroki procesu kompilacji. Aby uzyskać więcej informacji, zobacz [elementów](../msbuild/msbuild-items.md).  
  
 metadane, element  
 Metadane elementu jest kolekcją par nazwa wartość, skojarzony z elementem. Metadane informacje opisowe dla elementu i jest opcjonalny, z wyjątkiem dobrze znanego metadanych. Aby uzyskać więcej informacji, zobacz [elementów](../msbuild/msbuild-items.md).  
  
 metadane dobrze znanego  
 Metadane dobrze znanego są metadane elementu tylko do odczytu, który został zainicjowany przy użyciu wstępnie zdefiniowanych wartości. Metadane dobrze znanego informacje opisowe dla elementu, który odwołuje się do pliku. Na przykład wartość dobrze znanego metadanych o nazwie `FullPath` jest pełną ścieżką do pliku. Aby uzyskać więcej informacji, zobacz [elementów](../msbuild/msbuild-items.md).  
  
 przeznaczanie dla wielu platform  
 Zdolność do aplikacji lub zestawu projekt pod kątem wielu różnych CLR i platform z MSBuild i Visual Studio.  
  
 Profil  
 Podzbiór pełna platformy. Służy to zminimalizować ilość, która musi zostać pobrana do komputera.  
  
 plik projektu  
 Plik projektu zawiera skrypt programu MSBuild, który kontroluje kompilacji. Pliki projektu mają zwykle rozszerzenie pliku, który kończy się wyrazem "proj", takie jak pliku .csproj lub .vbproj. Pliki projektu można zaimportować właściwości plików i pliki docelowe.  
  
 property  
 Właściwość jest pary klucz wartość, która jest używana do sterowania procesu kompilacji. Aby uzyskać więcej informacji, zobacz [właściwości programu MSBuild](../msbuild/msbuild-properties.md).  
  
 Właściwość, środowiska  
 Właściwość środowiska jest właściwością, która jest automatycznie ustawiana na wartość zmiennej środowiskowej systemu, który ma taką samą nazwę. Aby uzyskać więcej informacji, zobacz [właściwości programu MSBuild](../msbuild/msbuild-properties.md).  
  
 właściwości pliku  
 Plik właściwości to pliku projektu, który zawiera głównie właściwości grup i grup, do których prowadzą kompilacji. Konwencja musi on .props rozszerzenia pliku. Właściwość pliki zwykle są importowane na początku projektu skojarzonych plików.  
  
 Właściwość, funkcja  
 Funkcja właściwości jest systemu właściwości lub metody, który może służyć do oceny skrypty programu MSBuild. Właściwość metod może służyć do odczytu z czasem systemowym, porównywanie ciągów dopasowanie wyrażeń regularnych i wykonywać inne akcje. Aby uzyskać więcej informacji, zobacz [funkcje właściwości](../msbuild/property-functions.md).  
  
 Funkcja właściwości, zagnieżdżone  
 Funkcje właściwości mogą być łączone do formularza bardziej złożone funkcje. Na przykład  
  
 `$([MSBuild]::BitwiseAnd(32,   $([System.IO.File]::GetAttributes(tempFile))))`  
  
 Aby uzyskać więcej informacji, zobacz [funkcje właściwości](../msbuild/property-functions.md).  
  
 właściwości globalne  
 Właściwość globalna jest pary klucz wartość, która jest używana do sterowania procesu kompilacji. Globalne właściwości są ustawiane w wierszu polecenia lub przy użyciu `Properties` atrybutu [zadanie programu MSBuild](../msbuild/msbuild-task.md)i nie można zmodyfikować kompilacji w fazie oceny. Aby uzyskać więcej informacji, zobacz [właściwości programu MSBuild](../msbuild/msbuild-properties.md).  
  
 właściwości lokalne  
 Właściwości lokalnej jest pary klucz wartość, która jest używana do sterowania procesu kompilacji. Termin ten jest używany tylko do odróżnienia właściwości, która nie jest właściwością globalną.  
  
 Właściwość, rejestru  
 Właściwość rejestru ma wartość, która jest ustawiona przy użyciu składni specjalne, które odczytuje wartość podklucza rejestru systemu. Aby uzyskać więcej informacji, zobacz [właściwości programu MSBuild](../msbuild/msbuild-properties.md).  
  
 właściwości zastrzeżone  
 Właściwości zastrzeżone jest pary klucz wartość, która jest używana do sterowania procesu kompilacji. Właściwości zastrzeżone automatycznie są inicjowane ze wstępnie zdefiniowanymi wartościami. Aby uzyskać więcej informacji, zobacz [właściwości programu MSBuild](../msbuild/msbuild-properties.md).  
  
 zakres projektu  
 Zakres projektu zawiera opis obiektu MSBuild, na przykład właściwości lokalnej, która jest widoczna tylko w pliku projektu zawierającego i wszystkie projekty, które importuje.  
  
 Projekt, podrzędne  
 Projekt podrzędny jest tworzony przez zadanie programu MSBuild podczas kompilowania projektu. Ten nowy projekt jest elementem podrzędnym elementu projektu, który zawiera lub importuje docelowego, który zawiera zadanie programu MSBuild. Projektu podrzędnego dziedziczy globalnych właściwości projektu nadrzędnego, chyba że zostaną one zmienione przez `Properties` atrybutu.  
  
 Lista redystrybucyjna  
 Listy ponownej dystrybucji: listę zestawów, które odpowiadają danym framework.  
  
 Odwołanie do zestawu  
 Zestaw, który służy do tworzenia aplikacji, w czasie projektowania. Zestaw odwołania może mieć rzeczywisty kod i interfejsów prywatnych usuwane z niej, pozostawiając tylko metadane i interfejsów publicznych.  
  
 Właściwość rejestru  
 Zobacz *właściwości, rejestru*.  
  
 docelowy  
 Obiekt docelowy grupowanie zadań w określonej kolejności i udostępnia sekcji w pliku projektu jako punkty wejścia do procesu kompilacji. Aby uzyskać więcej informacji, zobacz [cele](../msbuild/msbuild-targets.md).  
  
 Wartość docelowa, kompilowanie  
 Zobacz obiektu docelowego, systemem.  
  
 Celem oceny  
 Z powodu kompilacji przyrostowej elementów docelowych musi zostać przeanalizowany potencjalnych zmian właściwości i elementów. Nawet jeśli pominięto element docelowy muszą być wprowadzane zmiany. Obliczenia docelowy oznacza wykonywanie analiz to i wprowadzania tych zmian. Aby uzyskać więcej informacji, zobacz [kompilacje przyrostowe](../msbuild/incremental-builds.md).  
  
 docelowa wykonywania  
 Wykonywanie obiektu docelowego oznacza oceny i wykonywania wszystkich zadań, które nie mają żadnych warunków lub którego warunki zwrócić wartość true. Podczas kompilacji przyrostowej elementy docelowe może być pominięte lub wykonane, ale są zawsze obliczane. Aby uzyskać więcej informacji, zobacz docelowych i oceny.  
  
 docelowym systemem  
 Element docelowy, który zawiera warunek, który nie jest spełniony nie jest uruchamiane, oznacza to, nie ma wpływu na kompilacji. Obiekty docelowe, które są uruchamiane są wykonywane lub pominięte. W obu przypadkach sprawdzane jest elementem docelowym. Aby uzyskać więcej informacji, zobacz docelowych i oceny.  
  
 obiekt docelowy, pomijanie  
 Jeśli kompilacji przyrostowej określi, że wszystkie pliki wyjściowe są aktualne, a następnie pominięto element docelowy, oznacza to, element docelowy jest obliczane, ale nie są wykonywane zadania należące do obiektu docelowego. Aby uzyskać więcej informacji, zobacz docelowych i oceny.  
  
 moniker platformy docelowej  
 Nazwę opisującą platformę (np. NETFramwork, Silverlight, itp.), wersja i profilu (na przykład klienta, serwera, itp.), który ma zostać celem.  
  
 targeting pack  
 Lista zestawów, które są dystrybuowane wraz z danym framework i zestawu zestawów referencyjnych dla tej struktury.  
  
 plik elementów docelowych  
 Plik elementów docelowych to plik projektu, który zawiera przede wszystkim obiektów docelowych i zadań, które prowadzą kompilacji. Konwencja musi on .targets rozszerzenia pliku. Pliki docelowe zwykle są importowane z końcem okresu pliki projektu skojarzone.  
  
 — zadanie  
 Zadania są jednostki plik wykonywalny jest kod [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projektów służy do wykonywania operacji kompilacji. Na przykład zadanie może skompilować plików wejściowych lub uruchomić narzędzia zewnętrznego. Aby uzyskać więcej informacji, zobacz [zadania](../msbuild/msbuild-tasks.md).  
  
 transform  
 Transformacja jest jeden do jednego konwersji jednego elementu kolekcji do innego. Oprócz włączenia projektu do przekonwertowania kolekcji elementów, transformacji umożliwia cel, aby zidentyfikować bezpośredniego mapowania między jej danych wejściowych i wyjściowych. Aby uzyskać więcej informacji, zobacz [przekształca](../msbuild/msbuild-transforms.md).  
  
 metadane dobrze znanego  
 Zobacz *metadane dobrze znanego*.  
  
## <a name="see-also"></a>Zobacz też  
 [MSBUILD](../msbuild/msbuild.md)