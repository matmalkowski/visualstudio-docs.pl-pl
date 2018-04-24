---
title: 'Porady: eksportowanie tekstury zawierającej mipmapy'
ms.date: 11/04/2016
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 3d1ad14b-44fb-4cf0-a995-5e2f60026524
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0ff27404a37eb641deb8409e6e529bf052264591
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-export-a-texture-that-contains-mipmaps"></a>Porady: eksportowanie tekstury zawierającej mipmapy

Potok zawartości obrazu mogą generować mipmapy z obrazu źródłowego, w ramach fazy kompilacji projektu. Aby uzyskać pewne efekty, czasami trzeba ręcznie określ zawartości obrazu każdy poziom Mipmapy. Jeśli nie trzeba ręcznie określ każdy poziom Mipmapy zawartości obrazu, generowania mipmapy w czasie kompilacji zapewnia, że zawartość mipmap nigdy nie stanie się poza synchronizacja. Eliminuje to koszt wydajności generowania mipmapy w czasie wykonywania.

W tym artykule omówiono:

- Konfigurowanie obrazu źródłowego do przetworzenia przez potok zawartości obrazu.

- Konfigurowanie obrazu potoku zawartości do wygenerowania mipmapy.

## <a name="export-mipmaps"></a>Mipmapy eksportu

Mipmapowaniem zapewnia automatyczne miejsca ekranu poziomu z szczegółów teksturą powierzchni w aplikacji lub gry 3D. Zwiększa wydajność renderowania gry lub aplikacji przez wstępnie obliczanie próbkowany niższych wersjach tekstury. Próbkowany wstępnie obliczanie próbkowany dół wersje oznacza, że cały tekstury musi być w dół próbkowany zawsze go.

### <a name="to-export-a-texture-that-has-mipmaps"></a>Aby wyeksportować tekstury, który ma mipmapy

1.  Rozpoczynać się od podstawowego tekstury. Załadować istniejący plik obrazu lub utworzyć zgodnie z opisem w [porady: Tworzenie podstawowego tekstury](../designers/how-to-create-a-basic-texture.md). Aby obsługiwać mipmapy, określ tekstury, szerokość i wysokość, które są zarówno samego potęgą liczby dwa rozmiaru, na przykład 64 x 64, 256 x 256 lub 512 x 512.

2.  Konfigurowanie pliku tekstury utworzonego tak, aby jest przetwarzany przez potok zawartości obrazu. W **Eksploratora rozwiązań**, otwórz menu skrótów dla utworzonego pliku tekstury, a następnie wybierz pozycję **właściwości**. Na **właściwości konfiguracji** > **ogólne** ustaw **typu elementu** właściwości **potoku zawartości obrazu**. Upewnij się, że **zawartości** właściwość jest ustawiona na **tak** i **wykluczyć z kompilacji** ustawiono **nr**. Wybierz **zastosować**.

   **Potoku zawartości obrazu** zostanie wyświetlona strona właściwości konfiguracji.

3.  Konfiguruje potok zawartości obrazu, aby wygenerować mipmapy. Na **właściwości konfiguracji** > **potoku zawartości obrazu** > **ogólne** ustaw **Generowanie Mips** właściwości **tak (/ generatemips)**.

4.  Wybierz **OK**.

Podczas kompilowania projektu potoku zawartości obrazu konwertuje obraz źródłowy pracy określona, w tym poziom Mipmapy format danych wyjściowych. Wynik jest kopiowany do katalogu wyjściowego projektu.