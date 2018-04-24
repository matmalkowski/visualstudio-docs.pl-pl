---
title: Tabela obiektów graficznych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.datavisualizer
- vs.graphics.objecttable
- vs.graphics.bufferviewer
ms.assetid: f48f62d9-16ff-4a2e-8c01-5cbe99513788
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d58c219069efcc98fccaa52dff5bd156212ea64d
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="graphics-object-table"></a>Tabela obiektów graficznych
Tabela obiektów graficznych w Visual Studio grafiki analizy pomaga w zrozumieniu obiektów Direct3D, które obsługują ramka gry lub aplikacji.  
  
 Jest to tabela obiektu:  
  
 ![Obiekty Direct3D, które zostały utworzone przez aplikację.](media/gfx_diag_demo_object_table_orientation.png "gfx_diag_demo_object_table_orientation")  
  
## <a name="understanding-the-graphics-object-table"></a>Opis tabeli obiektów grafiki  
 Za pomocą tabeli obiektów, można analizować obiekty Direct3D, które obsługuje renderowanie określonej ramce. Problem z renderowaniem do określonego obiektu można wyznaczyć, sprawdzając jego właściwości i dane (przy użyciu innych narzędzi diagnostyki grafiki we wcześniejszej części diagnostyki sieci, można ograniczyć listę obiektów, które mogą nie być oczekiwań.) Po znalezieniu obiektem ataku, można użyć wizualizacji specyficzne dla jego typu, aby zbadać jego — na przykład służy Edytor obrazów do wyświetlania tekstury, lub *wizualizatora buforu* można wyświetlić zawartości buforu.  
  
 W tabeli obiektu obsługuje kopiowania i wklejania, dzięki czemu można użyć innego narzędzia — na przykład program Microsoft Excel — aby zbadać jego zawartość.

 Ponadto można użyć **typu** listy rozwijanej na górze lewym rogu, aby włączyć wyświetlanie obiektów typu **buforów**, **programów do cieniowania** lub **tekstury**, lub wszystkich tych elementów jednocześnie.  Ponadto służy pole wyszukiwania w prawym górnym rogu można znaleźć we wszystkich danych, które są prezentowane określonych wierszy.  Na przykład możesz można wyszukać *D32_FLOAT* można znaleźć na liście wszystkich wystąpień obiektów w tym formacie.
  
### <a name="graphics-object-table-format"></a>Format tabeli obiektów grafiki  
 W tabeli obiektu Wyświetla obiekty Direct3D i zasobów, które obsługują ramki, który został skojarzony z wybranego zdarzenia — na przykład stan obiektów, buforów programów do cieniowania, tekstury i innych zasobów. Obiekty, które zostały utworzone w poprzedniej ramki, ale nie są używane w przechwyconej ramce zostały pominięte z tabeli obiektów. Obiekty, które zostały zniszczone przez poprzednie zdarzenia w przechwyconej ramce zostały pominięte w następnych zdarzeniach. Obiekty, które nie są ustawione na D3D10Device lub D3D11DeviceContext są wyświetlane jako tekst szary. Obiekty są wyświetlane w formacie tabeli.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Identyfikator**|Identyfikator obiektu.|  
|**Nazwa**|Informacje specyficzne dla aplikacji, które została ustawiona na obiekt przy użyciu funkcji Direct3D `SetPrivateData`— zwykle dodatkowe informacje identyfikacyjne o obiekcie.|  
|**Typ**|Typ obiektu.|  
|**Aktywne**|Wyświetla "*" dla obiekt, który został ustawiony na D3D10Device lub D3D11DeviceContext w przechwyconej ramce.<br /><br /> Odnosi się do obiektów, które są wyświetlane jako tekst szare, ale zapewnia wpisem kolumny, których można użyć, aby ułatwić sortowanie tabeli obiektów.|  
|**Rozmiar**|Rozmiar obiektu w bajtach.|  
|**Format**|Format obiektu. Na przykład format obiektu tekstury lub model programu do cieniowania obiektu programu do cieniowania.|  
|**Szerokość**|Szerokość obiektu tekstury. Nie ma zastosowania do innych obiektów.|  
|**Wysokość**|Wysokość obiektu tekstury. Nie ma zastosowania do innych obiektów.|  
|**Głębokość**|Głębokość obiektu 3-tekstury. Jeśli tekstury nie jest 3-w, wartość wynosi 0. Nie ma zastosowania do innych obiektów.|  
|**MIPS**|Liczba poziomów Mipmapy, które ma obiekt tekstury. Nie ma zastosowania do innych obiektów.|  
|**ArraySize**|Liczba tekstury w tablicy tekstury. Zakres jest z zakresu od 1 do górne granice zdefiniowane przez bieżący poziom funkcji. Mapy modułu ta wartość jest 6 razy liczba modułów społeczności maps w tablicy.|  
|**Przykłady**|Liczba multisamples na piksel.|  
  
## <a name="graphics-object-viewers"></a>Przeglądarki obiektów grafiki  
 Aby wyświetlić szczegółowe informacje o obiekcie, można go otworzyć, wybierając swojej nazwy w tabeli obiektów. Szczegółowe informacje dotyczące obiektu są wyświetlane w różnych formatach, w zależności od typu obiektu. Na przykład tekstury są wyświetlane w przeglądarce tekstury i stanu urządzenia, takie jak kontekst urządzenia D3D11 jest wyświetlana jako listę sformatowany. Różne wersje programu Direct3D należy używać różnych obiektów i są często wizualizatorów określonych dla najważniejszych obiektów w każdej wersji.  
  
 Oto podgląd tekstury zawartością etap potoku połączenia danych wyjściowych.  
  
 ![Podgląd tekstury, wyświetlanie połączenia danych wyjściowych](media/gfx_diag_texture_preview.png "gfx_diag_texture_preview")  
  
### <a name="d3d12-command-list"></a>Listy poleceń D3D12  
 W Direct3D 12 listy poleceń jest obiekt, który rejestruje polecenia do przydzielania polecenia, dzięki czemu może zostać przesłane do procesora GPU jako pojedyncze żądanie. List poleceń zwykle wykonać kilka ustawienia stanu, Rysuj, wyczyść i skopiuj polecenia. Są one szczególnie ważne, ponieważ jest preferowaną metodą renderowania w Direct3D 12, a można ponownie użyć między ramek do zwiększenia wydajności. Nowe okno dokumentu, informacje związane z każdym z etapów potoku wyświetlanym na osobnej karcie wyświetlane są szczegóły listy poleceń.  
  
### <a name="d3d12-pipeline-state-object-pso"></a>Obiekt stanu potoku D3D12 (PSO)  
 W Direct3D 12 obiekt stanu potoku reprezentuje znaczna część stanu procesora GPU, w tym wszystkie aktualnie zestaw programów do cieniowania i niektóre obiekty stanu funkcji stałej. Po utworzeniu obiektu stanu potoku jest niezmienialny — aplikacji można zmienić konfiguracji potoku tylko przez powiązanie obiekt stanu innym potoku. Wyświetlane są szczegóły PSO w nowym oknie dokumentu, szczegółowe informacje o konfiguracji potoku, którego układ określa się hierarchicznie.  
  
### <a name="d3d12-root-signature"></a>Podpis głównego D3D12  
 Direct3D 12 sygnaturę główną definiuje wszystkie zasoby, które są powiązane z potoku grafiki lub obliczeniowych i łączy list poleceń z zasobami, które wymaga programów do cieniowania. Zazwyczaj jest jedną główną sygnaturę grafiki i jeden dla obliczeń w aplikacji. Szczegóły podpisu głównego są wyświetlane w nowym oknie dokumentu przy użyciu szczegółów sygnaturę główną, którego układ określa się hierarchicznie.  
  
### <a name="d3d12-resources"></a>Zasobów D3D12  
 W Direct3D 12 zasoby są wychwytywania obiektów, które dostarczają dane do potoku renderowania; Dzięki temu nie trzeba Direct3D11, w którym zdefiniowana wielu konkretnych obiektów dla różnych rodzajów i wymiarów zasobów. Zasób Direct3D 12 może zawierać danych tekstury, dane wierzchołków, dane programu do cieniowania i — nawet reprezentują elementy docelowe renderowania, np. buforów głębokości. Szczegóły zasobu Direct3D 12 są wyświetlane w nowym oknie Dokument; Analizy grafiki będzie używać przeglądarkę odpowiednią dla zawartości obiektu zasobu, jeśli jest w stanie określić jego typu. Na przykład obiekt zasobu, który zawiera dane tekstury jest wyświetlany w przeglądarce tekstury, podobnie jak obiekt D3D11 Texture2D jest.  
  
### <a name="device-context-object"></a>Obiekt kontekstu urządzenia  
 Direct3D 11 i 10 Direct3D, kontekstu urządzenia (**kontekstu urządzenia D3D11** lub **urządzeniem D3D10**) obiekt jest szczególnie ważne, ponieważ posiada najważniejsze informacje o stanie i łączy do innych obiekty stanu, które są aktualnie ustawione. Szczegóły kontekstu urządzenia są wyświetlane w nowym oknie dokumentu, a każda kategoria informacji zobaczy na osobnej karcie. Zmiany kontekstu urządzenia, po wybraniu nowe zdarzenie aby odzwierciedlały bieżący stan urządzenia.  
  
### <a name="buffer-object"></a>Obiekt buforu  
 Szczegóły obiektu buforu (buforu D3D11 lub buforu D3D10) są wyświetlane w nowym oknie dokumentu, który umożliwia wyświetlanie zawartości buforu w tabeli i udostępnia interfejs dla zmianę sposobu wyświetlania zawartości buforu. **Buforu danych** tabeli obsługuje kopiowania i wklejania, dzięki czemu można użyć innego narzędzia — na przykład program Microsoft Excel, aby zbadać jego zawartość. Zawartość buforu jest interpretowany zgodnie z wartością **format** pola kombi, który znajduje się nad **buforu danych** tabeli. W polu można wprowadzić formatu danych złożony, który składa się z typów danych, które są wymienione w poniższej tabeli. Na przykład "float int" Wyświetla listę struktury zawierające 32-bitowa wartość zmiennoprzecinkowa następuje wartość 32-bitowej liczby całkowitej ze znakiem. Formaty danych, których określono są dodawane do pola kombi do późniejszego użycia.  
  
 Można również przełączyć **Pokaż przesunięciami** pole wyboru, aby ukryć lub wyświetlić przesunięcie każdego elementu w buforze.  
  
|Typ|Opis|  
|----------|-----------------|  
|**float**|32-bitowych wartości zmiennoprzecinkowych.|  
|**float2**|Wektor, który zawiera dwa 32-bitowych wartości zmiennoprzecinkowych.|  
|**float3**|Wektor, który zawiera trzy 32-bitowych wartości zmiennoprzecinkowych.|  
|**FLOAT4**|Wektor, który zawiera cztery 32-bitowych wartości zmiennoprzecinkowych.|  
|**byte**|Wartość 8-bitową liczbę całkowitą ze znakiem.|  
|**bajt 2**|Wartość 16-bitową liczbę całkowitą ze znakiem.|  
|**4-bajtowy**|Wartość całkowita 32-bitowych. Taki sam jak **int**.|  
|**8-bajtową**|Wartość 64-bitowej podpisanej liczby całkowitej. Taki sam jak **int64**.|  
|**xbyte**|8-bitową wartość szesnastkową.|  
|**x2byte**|16-bitową wartość szesnastkową.|  
|**x4byte**|32-bitową wartość szesnastkową. Taki sam jak **xint**.|  
|**x8byte**|Wartość szesnastkowa 64-bitowych. Taki sam jak **xint64**.|  
|**ubyte**|Wartość 8-bitową liczbę całkowitą bez znaku.|  
|**u2byte**|Wartość 16-bitową liczbę całkowitą bez znaku.|  
|**u4byte**|Wartość 32-bitowej liczby całkowitej bez znaku. Taki sam jak **uint**.|  
|**u8byte**|Wartość 64-bitowej liczby całkowitej bez znaku. Taki sam jak **uint64**.|  
|**połowa**|16-bitowych wartości zmiennoprzecinkowych.|  
|**half2**|Wektor, który zawiera dwa 16-bitowych wartości zmiennoprzecinkowych.|  
|**half3**|Wektor, który zawiera trzy 16-bitowych wartości zmiennoprzecinkowych.|  
|**half4**|Wektor, który zawiera cztery 16-bitowych wartości zmiennoprzecinkowych.|  
|**double**|64-bitowych wartości zmiennoprzecinkowych.|  
|**int**|Wartość całkowita 32-bitowych. Taki sam jak **4-bajtowych**.|  
|**int64**|Wartość 64-bitowej podpisanej liczby całkowitej. Taki sam jak **8-bajtową**.|  
|**xint**|32-bitową wartość szesnastkową. Taki sam jak **x4byte**.|  
|**xint64**|Wartość szesnastkowa 64-bitowych. Taki sam jak **x8byte**.|  
|**uint**|Wartość 32-bitowej liczby całkowitej bez znaku. Taki sam jak **u4byte**.|  
|**uint64**|Wartość 64-bitowej liczby całkowitej bez znaku. Taki sam jak **u8byte**.|  
|**bool**|Wartość logiczna (`true` lub `false`) wartość. Każda wartość logiczna jest reprezentowany przez 32-bitową wartość.|  
  
## <a name="see-also"></a>Zobacz też  
 [Diagnostyka grafiki (debugowania grafiki DirectX)](visual-studio-graphics-diagnostics.md)   
 [Przewodnik: brak obiektów spowodowany stanem urządzenia](walkthrough-missing-objects-due-to-device-state.md)