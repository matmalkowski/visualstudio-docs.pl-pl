---
title: 'Porady: eksportowanie tekstury do użycia z programem Direct2D lub aplikacje Javascipt | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-designers
ms.topic: conceptual
ms.assetid: 241c25fe-764e-4e1b-ad32-b1377dcbb605
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5b4aa613339fa169770b6999b5b2a335be7330c2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-export-a-texture-for-use-with-direct2d-or-javascipt-apps"></a>Porady: eksportowanie tekstury do użycia z Direct2D lub aplikacjami JavaScript
Potok zawartości obrazu mogą generować tekstury, które są zgodne z konwencjami renderowanie wewnętrznego w Direct2D. Tekstury tego typu są odpowiednie do użycia w aplikacji, które używają Direct2D i w aplikacjach platformy uniwersalnej systemu Windows tworzone przy użyciu języka JavaScript.  
  
 W tym dokumencie przedstawiono następujące działania:  
  
-   Konfigurowanie obrazu źródłowego do przetworzenia przez potok zawartości obrazu.  
  
-   Konfigurowanie obrazu potoku zawartości do wygenerowania tekstury, którego można używać w aplikacji Direct2D lub JavaScript.  
  
    -   Wygeneruj plik .dds skompresowane bloku.  
  
    -   Generowanie wstępnie przemnożone alfa.  
  
    -   Wyłącz Generowanie mipmap.  
  
## <a name="rendering-conventions-in-direct2d"></a>Konwencje renderowania w Direct2D  
 Tekstury, które są używane w kontekście Direct2D musi być zgodna z tych Direct2D Konwencji renderowanie wewnętrznego:  
  
-   Direct2D implementuje przejrzystości i przejrzystości przy użyciu wstępnie przemnożone alfa. Używane z programem Direct2D tekstury musi zawierać wstępnie przemnożone alfa nawet wtedy, gdy nie są używane tekstury przezroczystość lub przejrzystości. Aby uzyskać więcej informacji na temat wstępnie przemnożone alfa, zobacz [porady: eksportowanie tekstury, który ma wstępnie przemnożone alfa](../designers/how-to-export-a-texture-that-has-premultiplied-alpha.md).  
  
-   Tekstury musi być podane w formacie .dds, za pomocą jednej z tych formatów bloku kompresji:  
  
    -   Kompresja BC1_UNORM  
  
    -   Kompresja BC2_UNORM  
  
    -   Kompresja BC3_UNORM  
  
-   Mipmapy nie są obsługiwane.  
  
#### <a name="to-create-a-texture-thats-compatible-with-direct2d-rendering-conventions"></a>Aby utworzyć tekstury, która jest zgodna z konwencjami renderowania Direct2D  
  
1.  Rozpoczynać się od podstawowego tekstury. Załadowanie istniejącego obrazu lub Utwórz nową, zgodnie z opisem w [porady: Tworzenie podstawowego tekstury](../designers/how-to-create-a-basic-texture.md). Aby obsługiwać bloku kompresji w formacie .dds, określ tekstury, szerokość i wysokość, które są wielokrotność czterech rozmiaru, na przykład 100 x 100, 128 x 128 lub 256 x 192. Mipmapowaniem nie jest obsługiwane, tekstury musi być kwadratowych i musi być potęgą liczby dwa rozmiar.  
  
2.  Konfigurowanie pliku tekstury tak, aby jest przetwarzany przez potok zawartości obrazu. W **Eksploratora rozwiązań**, otwórz menu skrótów dla nowo utworzonego pliku tekstury, a następnie wybierz pozycję **właściwości**. Na **właściwości konfiguracji**, **ogólne** ustaw **typu elementu** właściwości **potoku zawartości obrazu**. Upewnij się, że **zawartości** właściwość jest ustawiona na **tak** i **wykluczyć z kompilacji** ma ustawioną wartość **nr**, a następnie wybierz pozycję  **Zastosuj** przycisku. **Potoku zawartości obrazu** zostanie wyświetlona strona właściwości konfiguracji.  
  
3.  Ustaw format danych wyjściowych w jednym z formatów skompresowane bloku. Na **właściwości konfiguracji**, **potoku zawartości obrazu**, **ogólne** ustaw **Kompresuj** właściwości  **Kompresja BC3_UNORM (/ compress: BC3_UNORM)**. Można wybrać jeden z innych BC1, BC2 lub BC3 formatów, w zależności od wymagań. Direct2D nie obsługuje obecnie BC4 BC5, BC6 albo BC7 tekstury. Aby uzyskać więcej informacji o różnych formatach BC, zobacz [bloku kompresji (Direct3D 10)](http://msdn.microsoft.com/library/windows/desktop/bb694531.aspx).  
  
    > [!NOTE]
    >  Format kompresji, który jest określony Określa format pliku, który jest generowany przez potok zawartości obrazu. Różni się od **Format** właściwości obrazu źródłowego w edytorze obrazu, który określa format pliku obrazu źródłowego, jak przechowywane na dysku — to znaczy *format pracy*. Zwykle nie mają format pracy, który jest skompresowany.  
  
4.  Konfiguruje potok zawartości obrazu do generowania danych wyjściowych, która używa wstępnie przemnożone alfa. Na **właściwości konfiguracji**, **potoku zawartości obrazu**, **ogólne** ustaw **skonwertować do formatu alfa wstępnie pomnożonych** dla właściwości **tak (/ generatepremultipliedalpha)**.  
  
5.  Konfiguruje potok zawartości obrazu, tak aby nie generować mipmapy. Na **właściwości konfiguracji**, **potoku zawartości obrazu**, **ogólne** ustaw **Generowanie Mips** właściwości **Nr**.  
  
6.  Wybierz **OK** przycisku.  
  
 Podczas kompilowania projektu potoku zawartości obrazu konwertuje obraz źródłowy pracy określony format wyjściowy — konwersja uwzględnia generowania wstępnie przemnożone alfa — a wynik jest kopiowany do katalogu wyjściowego projektu.