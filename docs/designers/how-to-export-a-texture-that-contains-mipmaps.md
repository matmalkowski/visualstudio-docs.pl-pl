---
title: "Porady: eksportowanie tekstury, który zawiera mipmapy | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d1ad14b-44fb-4cf0-a995-5e2f60026524
caps.latest.revision: "7"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ef8f94ae451902c8f7b5e5d2b5f3156d01107589
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-export-a-texture-that-contains-mipmaps"></a>Porady: eksportowanie tekstury zawierającej mipmapy
Potok zawartości obrazu mogą generować mipmapy z obrazu źródłowego, w ramach fazy kompilacji projektu. Kiedy nie trzeba ręcznie określ zawartości obrazu każdy poziom Mipmapy — jak może osiągnąć niektórych skutków — Generowanie mipmapy w czasie kompilacji gwarantuje, że zawartość mipmap nigdy nie staną się poza synchronizacja i eliminuje koszty wydajności generowania mipmapy w czasie wykonywania.  
  
 W tym dokumencie przedstawiono następujące działania:  
  
-   Konfigurowanie obrazu źródłowego do przetworzenia przez potok zawartości obrazu.  
  
-   Konfigurowanie obrazu potoku zawartości do wygenerowania mipmapy.  
  
## <a name="exporting-mipmaps"></a>Eksportowanie mipmapy  
 Mipmapowaniem zapewnia automatyczne miejsca ekranu poziomu z szczegółów teksturą powierzchni w aplikacji lub gry 3D. Zwiększa wydajność renderowania gry lub aplikacji przez wstępnie obliczanie próbkowany niższych wersjach tekstury, aby cały tekstury nie ma w dół-pierwotnych zawsze, gdy jest on próbkowane.  
  
#### <a name="to-export-a-texture-that-has-mipmaps"></a>Aby wyeksportować tekstury, który ma mipmapy  
  
1.  Rozpoczynać się od podstawowego tekstury. Załadować istniejący plik obrazu lub utworzyć zgodnie z opisem w [porady: Tworzenie podstawowego tekstury](../designers/how-to-create-a-basic-texture.md). Aby obsługiwać mipmapy, określ tekstury, szerokość i wysokość, które są zarówno samego potęgą liczby dwa rozmiaru, na przykład 64 x 64, 256 x 256 lub 512 x 512.  
  
2.  Konfigurowanie pliku tekstury utworzonego tak, aby jest przetwarzany przez potok zawartości obrazu. W **Eksploratora rozwiązań**, otwórz menu skrótów dla nowo utworzonego pliku tekstury, a następnie wybierz pozycję **właściwości**. Na **właściwości konfiguracji**, **ogólne** ustaw **typu elementu** właściwości **potoku zawartości obrazu**. Upewnij się, że **zawartości** właściwość jest ustawiona na **tak** i **wykluczyć z kompilacji** ma ustawioną wartość **nr**, a następnie wybierz pozycję  **Zastosuj** przycisku. **Potoku zawartości obrazu** zostanie wyświetlona strona właściwości konfiguracji.  
  
3.  Konfiguruje potok zawartości obrazu, aby wygenerować mipmapy. Na **właściwości konfiguracji**, **potoku zawartości obrazu**, **ogólne** ustaw **Generowanie Mips** właściwości **Tak (/ generatemips)**.  
  
4.  Wybierz **OK** przycisku.  
  
 Podczas kompilowania projektu potoku zawartości obrazu konwertuje obraz źródłowy z formatu pracy na format danych wyjściowych, określona, w tym poziom Mipmapy a wynik jest kopiowana do katalogu wyjściowego projektu.